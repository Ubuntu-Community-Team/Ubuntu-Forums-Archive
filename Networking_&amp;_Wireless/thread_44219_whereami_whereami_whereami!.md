---
title: "whereami whereami whereami!"
date: 2005-06-25
forum: Networking &amp; Wireless
---

### Post by rsay on 2005-06-25
I have been trying to configure whereami using a combination of the guide provided by blueplazma, the manpages and google searching for whereami. The program almost works. The problem is that when it runs during bootup the tests don't work right and my network gets configured as wireless when I am plugged in. If I re-run whereami from the cli after booting it usually works but occasionally I have to run it twice before the tests all work right. 

Here is my detect.conf:
```
default wireless

set DEBUGWHEREAMI 1


### Check and see if we are plugged in
testmii eth0 lan


#  If a network cable is attached, assume we will use that
if lan
        set interface eth0
        testdhcp '*.*.*.*'     dhcp
        testdhcp '192.168.2.*' home-wired
        testdhcp '152.11.5.*'  wake-wired
        notat down
else
        notat home-wired,wake-wired
        always set INTERFACE eth1
        always testap scan wlan
fi

### If a network cable is not plugged in, then try to find a wireless network
if wlan
        testssid Gammaman home-wireless
        testap scan wlan wireless
        always notat wlan
fi
``` 

Here is my whereami.conf
```
=rm /etc/network/interfaces.last

+lan ifconfig eth1 down

+home-wired cp /etc/network/interfaces /etc/network/interfaces.last
+home-wired cp /etc/network/interfaces.home-wired /etc/network/interfaces
+home-wired route del default
+home-wired route add default gw 192.168.2.1
+home-wired /etc/init.d/networking restart
+home-wired cp /etc/resolvconf/resolv.conf.home-wired /etc/resolv.conf
+home-wired /etc/init.d/iptables restart

+wake-wired cp /etc/network/interfaces /etc/network/interfaces.last
+wake-wired cp /etc/network/interfaces.wake-wired /etc/network/interfaces
+wake-wired route del default
+wake-wired route add default gw 152.11.5.254
+wake-wired /etc/init.d/networking restart
+wake-wired cp /etc/resolvconf/resolv.conf.wake-wired /etc/resolv.conf
+wake-wired /etc/init.d/iptables restart

+home-wireless cp /etc/network/interfaces /etc/network/interfaces.last
+home-wireless cp /etc/network/interfaces.home-wireless /etc/network/interfaces
+home-wireless route del default
+home-wireless route add default gw 192.168.2.1
+home-wireless /etc/init.d/networking restart
+home-wireless cp /etc/resolvconf/resolv.conf.home-wireless /etc/resolv.conf
+home-wireless /etc/init.d/iptables restart
-home-wireless ifconfig eth1 down
``` 

whereami starts in rc2-5.d  as S35whereami 

Any thoughts about why this isn't working the first time (during bootup)

I am thinking of writing a script to re-run whereami twice at the end of the boot sequence but it seems a bit hackish.

---

### Post by AndreasMeier on 2005-08-19
Have you solved your problem ?

Perhaps it is possible to give whereami a starting number, which comes later in the boot process.

Or perhaps attach the whereami detect.conf after ifplugd is detecting a wired connection.

Regards
Andreas

---

### Post by pestilence4hr on 2005-08-19
[QUOTE=rsay]I have been trying to configure whereami using a combination of the guide provided by blueplazma, the manpages and google searching for whereami. The program almost works. The problem is that when it runs during bootup the tests don't work right and my network gets configured as wireless when I am plugged in. If I re-run whereami from the cli after booting it usually works but occasionally I have to run it twice before the tests all work right. 
[/QUOTE]

I am having a very similar problem, and I believe that it is caused by one of the following
1)  the interface is not up when testmii is called.  If you run mii-tool with the interfaces down, it will not give correct results.  Solution is to bring the interfaces up before trying mii-tool.  Which brings me to

2)  the interface has been brought up, but for some reason it's not in a completely useable state yet.  This is more tricky.  The only solution I have found so far is to sleep 10.  I don't like this solution, and the choice of 10 is sort of arbitrary based on trial-and-error on my machine, and probably won't work for everyone.

To sum up what I have done to fix testmii on my machine....add the following (in bold) to /usr/share/whereami/tests/testmii :

```
#!/bin/sh
# $Id: testmii,v 1.7 2004/05/19 21:40:42 andrew Exp $
#
# by Andrew McMillan, Catalyst IT Ltd, (c) 2001 licensed
# for use under the GPL version 2
#
[B]# Modified by John Fettig to check to make sure the interface is brought up
# before running any tests[/B]

# Turn on execution tracing, for debugging...
[ "$DEBUGWHEREAMI" = "1" ] && set -o xtrace

[B]IFSTATE="`ifconfig | egrep \"^${1}[\t ]\"`"
if [ "$IFSTATE" = "" ] ; then
      # Some systems need the interface "up", some don't
        ifconfig $1 up > /dev/null 2>&1 && sleep 10
fi[/B]

#
# Use apparently more reliable mii-tool...
if [ -x /sbin/mii-tool ] ; then
  /sbin/mii-tool $1 2>&1 | grep "link ok" >/dev/null && exit 0
elif [ -x /usr/sbin/ethtool ] ; then
  # Fall back to ethtool, which can give false positives on this
  /usr/sbin/ethtool $1 2>&1 | grep "Link detected: yes" >/dev/null && exit 0
fi


# Interface is not connected - bring it down to remove it from
# routing table
ifconfig $1 down

exit 1

```

I will file a bug for this, as it completely prevents whereami from functioning properly on my machine (a dell 700m laptop).

---

### Post by coaxx on 2005-09-16
same problem here, I had only a "Configuring network interfaces..." message during booting and it stopped there. While booting with the wifi pcmcia card ejected everything worked well and I couldt reinsert it while in init 3/5. Then whereami seemed to work well.

Your workaround did the job btw!

---

### Post by mlomker on 2005-09-16
Thanks for pointer.  I spent a fair bit of time trying to get a script called get-mac-address.sh to work for me but had no luck at all.  I'll take a look at this package.

---

### Post by coaxx on 2005-09-19
[QUOTE=coaxx]

Your workaround did the job btw![/QUOTE]


Unfortunatly it does not. I had to remove whereami because it did not work in every location.  :roll:

---

### Post by mlomker on 2005-09-19
[QUOTE=rsay]The program almost works. The problem is that when it runs during bootup the tests don't work right and my network gets configured as wireless when I am plugged in. [/QUOTE]

I've spend the last couple of days tweaking my config and I don't have that problem.  Did you install ifplugd and disable hotplug's handling of the network interfaces?  If you don't disable hotplug then it's going to try to bring it up and ifplugd won't do its job.

```

chmod 600 /etc/hotplug/net.ifup

```

---

### Post by coaxx on 2005-09-20
[QUOTE=mlomker]I've spend the last couple of days tweaking my config and I don't have that problem.  Did you install ifplugd and disable hotplug's handling of the network interfaces?  If you don't disable hotplug then it's going to try to bring it up and ifplugd won't do its job.

```

chmod 600 /etc/hotplug/net.ifup

```[/QUOTE]

I formerly had ifplugd installed but removed it before I tried whereami. 

During my tests with whereami it tried both - enabled and disabled hotplug-functionality for eth1 (which is my wlan interface). They way I disabled it was different, I just commented out the line "map eth1" in /etc/networking/interfaces.

The only difference when disbaled I saw was the PCMCI Card not coming up when it was reinserted after ejecting during running system. At boottime the interface came up normally but the whereami symthoms were the same.

---

### Post by mlomker on 2005-09-20
>  "map eth1" in /etc/networking/interfaces.

after ejecting during running system. At boottime the interface came up normally but the whereami symthoms were the same.

Which tells you that the **map** line wasn't the answer, right?  My approach does actually keep hotplug from touching it at all.  Even with the **map** line out of interfaces it still brings the interface up during boot because it wants to set the time using **ntpdate**.

When I'm feeling more energetic I'm going to post a how-to regarding customizing the start-up scripts in more detail.  I have things working pretty slick, but you have to juggle the scripts and commands around a bit from the defaults.

---

