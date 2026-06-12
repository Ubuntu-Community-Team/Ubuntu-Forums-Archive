---
title: "Mac address spoofing problems with the Ubuntu 14.04 update"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by GigabyteProduction on 2014-05-03
I created this really complicated setup with Xubuntu 13.10 that routed all my traffic through my VPN and hid everything that identifies the laptop and I recreated the setup on 14.04 but just about the most important feature is missing: the ability to spoof the mac address. I can get the mac address to change on either of my wifi devices or ethernet controller (all of which had the ability before I recreated the setup). Even macchanger fails every time I call "macchanger -r" saying the mac address is still the same, I believe this is a sign of either a glitch making a library call act like a stub or maybe even a real stub.

The piece of my setup I investigated the most before I came to the conclusion that it's not the problem is my Broadcom drivers. I thought for sure something changed in my driver due to an update but when trying all variations of the driver, and even importing the firmware from the backup of my old setup, the problem still persisted. I then tried to use a different adapter entirely. Then I noticed it seems none of my devices can change properly. They all appear to change when looking at their hardware address in ifconfig, but they can't connect to anything. Changing the mac address with "ip set dev wlan0 address **:**:**:**:**:**" seems to execute without error, but I still can't get a connection with a spoofed address.

There's so many possibilities of where this bug may lie, and I am not sure where to start, so I need some advice.

---

### Post by GigabyteProduction on 2014-05-06
This happens any time I try connecting to a router with a spoofed mac address, but only when i have a spoofed mac address...

```
[  214.296350] wlan0: authenticate with 98:fc:11:f2:f7:43
[  214.305098] wlan0: send auth to 98:fc:11:f2:f7:43 (try 1/3)
[  214.307421] wlan0: authenticated
[  219.367559] wlan0: deauthenticating from 98:fc:11:f2:f7:43 by local choice (reason=3)
```

 I found out error 3 is "Deauthenticated because sending STA is leaving (or has left) IBSS or ESS" from [http://www.aboutcher.co.uk/2012/07/linux-wifi-deauthenticated-reason-codes/](http://www.aboutcher.co.uk/2012/07/linux-wifi-deauthenticated-reason-codes/) I'm really not sure what sense that makes as i am literally a room away from the routers i am testing with. Maybe changing the mac address is making linux clear the cache of routers in range or something...

I also tested whether it's because of networkmanager by adding the 13.10 repository and reinstalling networkmanager and the applet, it seemed to be successfully backdated, but i'm not sure how reliable that was as it did install a lot of packages that didn't autoremove which eventually made me reinstall xubuntu, but trying to backdate networkmanager didn't seem to help, so i'll have to try manually using wpa_supplicant or something from a test install of ubuntu server 14.04 to see if it truely is networkmanager or one of it's components... but other than that i'm really not sure why this is happening. I've been searching since this problem started occuring and nobody else has posted online about this problem.

---

### Post by ridgeland on 2014-05-06
Hi GigabyteProduction,

I subscribed to this thread because I have the same problem. Thanks for the update.
I also am using Xubuntu 14.04.
I've tried removing apparmor, using wicd rather than networkmanager,  messing with the config files for both /etc/network and /etc/NetworkManager.  I haven't gotten anywhere but I haven't quit trying.  I found this
[http://ubuntuforums.org/showthread.php?t=2189864&page=2](http://ubuntuforums.org/showthread.php?t=2189864&page=2)
and will try the script on #17 once I get Xubuntu reinstalled.  I've trashed around so much I need to start over.
My situation is a home LAN with just a few PCs.  My spouse's laptop was using a cloned MAC plus a router with a MAC filter than would block the PC's true MAC.  This was my way to block Windows from connecting to the internet if the laptop ever boots to Windows (very rare).  I also have an HTPC that I'm using as a sandbox to try to get Xubuntu 14.04 up to the functionality I have with Debian 7 on the laptop.  Ubuntu 12.04 was not a problem.
Let us know if you solve this.  Thanks.

---

### Post by hbuntuone on 2014-05-11
I'm also subscribing to this post as I think I have the same problem: I could spoof MAC addresses without a problem on 13.10, but can't anymore with a clean install of 14.04. The address shown by ifconfig shows the spoofed MAC address, but I'm unable to connect to any networks.

Edit: I should note that I'm using desktop Ubuntu 14.04, not Xubuntu.

---

### Post by diegogmx2000 on 2014-05-12
i guess its a problem with networkmanager, if i do the "normal" procedure (deactivate wireless(wether ifdown or simply declick wirelles on nm) macchanger -m mac reactivate) it does work like a charm,  despite i know C and C++ i dont know how to fix this (im a micro controller/ oth hardware guy)

---

### Post by hbuntuone on 2014-05-12
Hmm, you're right. I can uncheck "Enable Wifi" from the network manager menu, run macchanger, then re-enable wifi and it works as expected. However, it resets to the original physical address every time I put the computer to sleep and resume it. 

Is there any way to reliably run the macchanger command every time the computer resumes?

---

### Post by GigabyteProduction on 2014-05-19
Wow, why wasn't I getting emails for all these replies? whatever...  anyway, I got around to testing mac changing with ubuntu server 14.04,  where network-manager isn't installed, and yeah, i was also able to get  it working. I must be network-manager, has anyone here filed a bug  yet?

> **diegogmx2000 said:**
> i guess its a problem with networkmanager, if i do the "normal" procedure (deactivate wireless(wether ifdown or simply declick wirelles on nm) macchanger -m mac reactivate) it does work like a charm,  despite i know C and C++ i dont know how to fix this (im a micro controller/ oth hardware guy)

I'm glad i have that tip now. Despite how glad I am with figuring out how to do this, I'ver been booting directly into my backup of when i had 13.10 just to continue to use my setup, now that I know a workaround, I won't have to do that anymore.

I wonder if setting the mac address in /etc/network/interfaces will be of any use.

---

### Post by joshua.atkins on 2014-06-03
maybe not

---

### Post by tweenk2 on 2014-08-06
> **GigabyteProduction said:**
> I wonder if setting the mac address in /etc/network/interfaces will be of any use.

I tried adding "hwaddress ether aa:bb:cc:dd:ee:ff" stanza to /etc/network/interfaces. This works only the first time, after you run "sudo ifup eth0" (where eth0 is the interface with the changed MAC address). Unfortunately, it seems that when you do this, udev stops delivering events related to your interface, so the connection will break when you unplug the network cable and plug it back again. Furthermore, the connection is not brought up correctly after a reboot.

It seems that there is no reliable way of getting MAC address in Ubuntu 14.04. Using the Cloned MAC address in the Network Manager applet doesn't work at all. I submitted this as a bug:
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1353718](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1353718)

---

### Post by GigabyteProduction on 2014-08-07
I've actually forgot about this issue as I haven't used my laptop for a couple of months, but I've tested connecting to a network and spoofing the address on a minimalistic Ubuntu 14.04 Server, and the I didn't have this problem. Since Network Manager is just about the only networking difference that I can think of between Ubuntu with a GUI and Ubuntu without, I'd say it's a problem with Network Manager, so you should move your bug report from systemd to network-manager.

I've been using a workaround stated earlier in this thread. I've been disabling wifi from within Network Manager, then I manually changed the mac address on the interface, and enabled wifi from within Network Manager. I can only connect to networks that are set to use the cloned mac address that I manually set my adapter to.

I've tested using cloned mac addresses again with my laptop and updated packages. The bug still persists with the same behavior as [http://ubuntuforums.org/showthread.php?t=2221802&p=13015871#post13015871](http://ubuntuforums.org/showthread.php?t=2221802&p=13015871#post13015871) and the same workaround is still needed.

---

### Post by GigabyteProduction on 2014-11-06
This problem is still persistent in 14.10. The dmesg output has changed slightly, but the stated reason hasn't changed.
```
[ 5890.564387] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 5896.141049] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5897.274984] wlan0: authenticate with 92:f6:52:91:6e:62
[ 5897.285104] wlan0: send auth to 92:f6:52:91:6e:62 (try 1/3)
[ 5897.287389] wlan0: authenticated
[ 5902.286220] wlan0: aborting authentication with 92:f6:52:91:6e:62 by local choice (Reason: 3=DEAUTH_LEAVING)
```
/var/log/syslog isn't giving much more information on this other than this after the very last repetition of data that's extremely similar to dmesg above
```
Nov  6 20:43:00 A3 NetworkManager[1122]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
```
I'm not sure what more to look at.

---

### Post by ketici on 2014-11-07
It's been 7 months since 14.04 was released and now 14.10 is out and this bug isn't going anywhere.

Whoever Googles upon this thread take 30 seconds and click "this bug affects me" and "subscribe" on the bug report page [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1320752) which adds BUG HEAT


I merged 4 other bugs with the same issue to the bug report and cleaned up the description. I figure we need maybe 10 more people to subscribe for this bug to make it close enough to the top for the powers that be to notice.

Again guys, 14.10 DOES NOT fix it. That means we need to do something ourselves.

---

### Post by david322 on 2014-12-19
Found a good work around that does wonders:

```

[FONT=comic sans ms]sudo service network-manager stop[/FONT]
[FONT=comic sans ms]sudo ifconfig wlan0 down[/FONT]
[FONT=comic sans ms]sudo macchanger -A wlan0[/FONT]
[FONT=comic sans ms]sudo ifconfig wlan0 up [/FONT]
[FONT=comic sans ms]sudo service network-manager start [/FONT]

```
[FONT=comic sans ms][FONT=lucida console]
1) Disconnect from target network.
2) First Stop network manager
3) take down your interface
4) use macchanger, note -r does not work correctly.
5) bring your interface back up
6) restart network manager. 
7) reconnect to target network. 

[/FONT]Now you mac address should be changed. I have done this a few times here at work. We have a log in system that prompts for a new mac address. Every time I have used this script, I have been prompted to log in through the web portal. Our system shows a new mac address has logged in each time as well. So, I hope this works for you all. 

The root of the problem is in network manager, Network manager well restart an interface. Thus, stop network manager, disable that interface, then do what you need to do. Bring back the interface before network manager or network manager will do it for you. When network manager does it for you, it will change any and all settings that it thinks the interface should have. But if the interface is up and running before network manager is, then it will accept it as is. At least this is my theory. 

If you want a script for it, here you go:
[/FONT]```
#!/bin/bash
if [ $# -eq 0 ]; then
    echo "Please select an interface."
    exit 1
else
intface=`ls /sys/class/net | grep $1`
  if [[ $1 == $intface ]]; then
    sudo echo "Thank you for Sudo Rights."
    sudo service network-manager stop &> /dev/null
    sudo ifconfig $1 down &> /dev/null
    sudo macchanger -A $1 &> /dev/null
    sudo macchanger -A $1 &> /dev/null
    sudo macchanger -A $1 &> /dev/null
    sudo macchanger -A $1 &> /dev/null
    sudo ifconfig $1 up &> /dev/null
    sudo service network-manager start &> /dev/null
    echo ""
    echo "Your Mac Address has Been Changed!"
    echo ""
    macchanger -s $1
    echo ""
  else
    echo "Please select the correct interface."
    ls /sys/class/net
    exit 1
  fi
fi
```
[FONT=comic sans ms]
[/FONT]

---

### Post by ubun4 on 2015-05-09
> **david322 said:**
> Found a good work around that does wonders:

```

[FONT=comic sans ms]sudo service network-manager stop[/FONT]
[FONT=comic sans ms]sudo ifconfig wlan0 down[/FONT]
[FONT=comic sans ms]sudo macchanger -A wlan0[/FONT]
[FONT=comic sans ms]sudo ifconfig wlan0 up [/FONT]
[FONT=comic sans ms]sudo service network-manager start [/FONT]

```
[FONT=comic sans ms][FONT=lucida console]
1) Disconnect from target network.
2) First Stop network manager
3) take down your interface
4) use macchanger, note -r does not work correctly.
5) bring your interface back up
6) restart network manager. 
7) reconnect to target network. 

[/FONT]Now you mac address should be changed. I have done this a few times here at work. We have a log in system that prompts for a new mac address. Every time I have used this script, I have been prompted to log in through the web portal. Our system shows a new mac address has logged in each time as well. So, I hope this works for you all. 

The root of the problem is in network manager, Network manager well restart an interface. Thus, stop network manager, disable that interface, then do what you need to do. Bring back the interface before network manager or network manager will do it for you. When network manager does it for you, it will change any and all settings that it thinks the interface should have. But if the interface is up and running before network manager is, then it will accept it as is. At least this is my theory. 

If you want a script for it, here you go:
[/FONT]```
#!/bin/bash
if [ $# -eq 0 ]; then
    echo "Please select an interface."
    exit 1
else
intface=`ls /sys/class/net | grep $1`
  if [[ $1 == $intface ]]; then
    sudo echo "Thank you for Sudo Rights."
    sudo service network-manager stop &> /dev/null
    sudo ifconfig $1 down &> /dev/null
    sudo macchanger -A $1 &> /dev/null
    sudo macchanger -A $1 &> /dev/null
    sudo macchanger -A $1 &> /dev/null
    sudo macchanger -A $1 &> /dev/null
    sudo ifconfig $1 up &> /dev/null
    sudo service network-manager start &> /dev/null
    echo ""
    echo "Your Mac Address has Been Changed!"
    echo ""
    macchanger -s $1
    echo ""
  else
    echo "Please select the correct interface."
    ls /sys/class/net
    exit 1
  fi
fi
```
[FONT=comic sans ms]
[/FONT]

Sorry for being a terrible noob but when I copy paste this script in to text editor, save it and then run it from terminal, all i get is Please select an interface

How di I select an interface? All I did is copy pasted this without altering anything.

Btw your solution is the only thing that worked out of many things I tried to solve this issue.

---

