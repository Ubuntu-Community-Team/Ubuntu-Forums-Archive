---
title: "Have a problem with intel 3945 wireless"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by nettnovice on 2007-09-08
I have installed UBUNTU 7.04.it is showing my wireless card as restricted driver package(enabled and in use) but I am unable to use it. (my laptop only use wire lan to connect internet). Anyone has any suggestion? please give me some advice :)

Here is my hardware config...................

laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


laptop:~# lspci -v|grep 3945
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation PRO/Wireless 3945BG Network Connection
root@nokyoong-laptop:~# lshw |grep 3945
                product: PRO/Wireless 3945ABG Network Connection
                configuration: driver=ipw3945 latency=0

---

### Post by wjp.reg on 2007-09-08
Did you configure the NIC with the correct ESSID ?

---

### Post by Zorael on 2007-09-08
```
$ lshw -C network
```

Is it in an UNCLAIMED state?

---

### Post by nettnovice on 2007-09-08
for Zorael :: It's an unclaimed driver

-laptop:~# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:d4000000-d4000fff irq:3

for wjp.reg :: really sorry, I am really new for ubuntu. I don't know what to do, thanks a lot!!!

---

### Post by nettnovice on 2007-09-09
Doesn't anyone have suggestions for me T_T  got stuck and tried of config it T_T

---

### Post by Zorael on 2007-09-09
I haven't the slightest clue as to what to do when it's stuck as UNCLAIMED, I'm afraid, so bear with me.


What happens if you do this?
```
$ sudo ipw3945d-$(uname -r)
```

Does it say it's already running, or does it start the daemon?

If it's not running, your machine may not be loading the ipw3945 driver upon boot. You can force this by adding 'ipw3945' to the /etc/modules file.

---

### Post by styles. on 2007-09-13
Zoreal: I joined just to respond since he didn't. 
```
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-09-13 05:18:32: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```
I copied what you suggested into my modules file and it didn't do anything.

---

### Post by Zorael on 2007-09-13
Most curious.


I'm afraid I don't have the slightest idea what might be causing it, though. Perhaps installing a more recent kernel (and accompanying restricted drivers package), or compiling the driver from scratch would help?

[LIST]
[*]As for installing kernels, the safest way would be to download Gutsy Tribe 5 and just launch the Live CD. If it works there, then you just have to wait for the stable release, install (the experimental and non-stable) tribe 5, or install the kernel atop of your 7.04 installation; which is possible, though not recommended.

[*]As for compiling, if you do manage to succeed, please do recount what you did. I just end up breaking things and having to reinstall, so I wouldn't be much help.
[/LIST]

---

### Post by styles. on 2007-09-13
Thanks for your advice. One of my friends at school has wireless running on his system, I'll see if I can get him to post how he did it.

---

### Post by Zorael on 2007-09-13
Hmm. Well, most who've gotten wireless to work never had any issues with unclaimed devices, so unless he actually managed to assign the driver to the interface (from an unclaimed state) he might not be of much help. It's a minority issue.

Much like my problem with Intel 3945 (interface breaking and spamming "Detected Geography" in dmesg), so I sympathize.

---

### Post by odin1965 on 2007-09-16
> **Zorael said:**
> Hmm. Well, most who've gotten wireless to work never had any issues with unclaimed devices, so unless he actually managed to assign the driver to the interface (from an unclaimed state) he might not be of much help. It's a minority issue.

Much like my problem with Intel 3945 (interface breaking and spamming "Detected Geography" in dmesg), so I sympathize.

Mine also continually post the same message in syslog. I posted a separate bug in Launchpad as my symptoms were quite different, but i posted a comment on your bug with a link to mine.

---

### Post by peteseats on 2007-09-17
I have the same problem and when I run the line $ sudo ipw3945d-$(uname -r) i get :
"
[COLOR="DarkRed"]ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-09-17 18:10:20: ERROR: ipw3945d already running.  If ipw3945d is not running then you
need to remove '/var/run/ipw3945d.pid' and try again.[/COLOR]
"

The actual wireless router can be seen on the network, but it just can't connect.  First I thought it was the encryption but I have removed the security and it still doesn't work.  

I am very new to linux so people break it down very clearly.

thanks

---

### Post by odin1965 on 2007-09-19
> **peteseats said:**
> I have the same problem and when I run the line $ sudo ipw3945d-$(uname -r) i get :
"
[COLOR="DarkRed"]ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-09-17 18:10:20: ERROR: ipw3945d already running.  If ipw3945d is not running then you
need to remove '/var/run/ipw3945d.pid' and try again.[/COLOR]
"

The actual wireless router can be seen on the network, but it just can't connect.  First I thought it was the encryption but I have removed the security and it still doesn't work.  

I am very new to linux so people break it down very clearly.

thanks

Look at these posts;
[http://ubuntuforums.org/showthread.php?t=530352](http://ubuntuforums.org/showthread.php?t=530352)
[http://ubuntuforums.org/showthread.php?t=533331](http://ubuntuforums.org/showthread.php?t=533331)
[http://ubuntuforums.org/showthread.php?t=525152](http://ubuntuforums.org/showthread.php?t=525152)

Also look at the launchpad bugs mentioned in the threads.

What is your output from dmesg?

---

### Post by cherry316316 on 2007-09-22
> **styles. said:**
> Thanks for your advice. One of my friends at school has wireless running on his system, I'll see if I can get him to post how he did it.

even i have the exact same to same problem , i am using debian kernel 2.6.18-5-amd64 

if u found the solution the let us know

---

### Post by odin1965 on 2007-09-23
> **cherry316316 said:**
> even i have the exact same to same problem , i am using debian kernel 2.6.18-5-amd64 

if u found the solution the let us know

No solution yet. I imagine most are busy preparing for Gutsy. I expect a fix will (hopefully) be ready in gutsy then eventually get back ported to the older releases.

---

### Post by jarocooke on 2007-09-23
Hi, I think I have been having a similar problem with my Intel 3945 wireless.  What I have come across however is the post half way down this page.

[http://ubuntuforums.org/showthread.php?t=551325&highlight=3945+doesn%27t+connect+at+first](http://ubuntuforums.org/showthread.php?t=551325&highlight=3945+doesn%27t+connect+at+first)

It is the one that talks about blacklisting IPv6.  I seem to remember some sort of problem with the wired version of this that occurred during the development of one of the earlier Ubuntu's (Warty or something).  Anyway I haven't yet had an opportunity to try the blacklisting of IPv6 to see if it works any better, as my computer is backing up data (2.5 hours left to go, so a lot of data).

Just for clarity what my computer would do is hang while trying to connect to the wireless AP.  One solution that I found was to simply unplug the router wait a few seconds and then plug it up again.  For some reason this would allow the laptop to connect without issue.  However no one else in the house has to go through this rigmarole, so I am assuming the problem is at my end.  In fact there is another AP that I have tried connecting to and it didn't work either.

Once I know whether the blacklisting of IPv6 has made any difference I will let you know.

---

### Post by jarocooke on 2007-09-23
For anyone interested, blacklisting IPv6 made the wireless connect up faultlessly, so that is the work around for this problem as far as I can see.  At least until the stable finished Gutsy is released anyway.

Cheers, let me know if it fixes the problem for you guys.
:popcorn:

Ahh, seems to be fixed in the updates I just applied, so I have unblacklisted IPv6 and everything seems to still be working fine.

---

### Post by odin1965 on 2007-10-01
> **jarocooke said:**
> Hi, I think I have been having a similar problem with my Intel 3945 wireless.  What I have come across however is the post half way down this page.

[http://ubuntuforums.org/showthread.php?t=551325&highlight=3945+doesn%27t+connect+at+first](http://ubuntuforums.org/showthread.php?t=551325&highlight=3945+doesn%27t+connect+at+first)

It is the one that talks about blacklisting IPv6. 

I  just tried this and my wireless is now working for the first time in WEEKS. I'll keep everyone up to date on whether or not it keeps working. It's currently connected to our encrypted network at work. I'll see if it works on my home network in a few hours.

---

