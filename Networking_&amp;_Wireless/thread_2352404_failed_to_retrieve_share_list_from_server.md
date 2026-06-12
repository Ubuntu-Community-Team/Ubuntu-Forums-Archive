---
title: "failed to retrieve share list from server"
date: 2017-02-12
forum: Networking &amp; Wireless
---

### Post by carusoswi on 2017-02-12
So, I have a WDTVLiveHub plugged into my wireless router. It has been working flawlessly with 16.04 and many versions before that, although I have encountered this problem previously during upgrades.  Normally, I stumble around, try different things, and, eventually, it works.  I usually reset my router, restart it, re-boot the WDTV live, reboot, reboot, reboot.  This time, so far, no joy.
It's very frustrating, and, to my thinking, nothing that I have done incorrectly.
Can anyone offer some clear routes to resolution.

I have browsed this error message on the forum and elsewhere, and many offer solutions, but they generally assume navigational knowledge that leaves me grouping to implement their suggestions.
Comments/advice truly welcome.

Machine is an Asus gs74, dual boot with Win10 (WDTVlive is working fine in Win10), running Ubuntu 16.10 64.

Thanks.

Caruso

---

### Post by TheFu on 2017-02-12
I don't have a WD-Hub, but have used a WD-TV Live as a very very very very cheap NAS for about a week (5 yrs ago).

Linux and WD use normal IP networking. That is the only trick.  Put the WD device on a static IP (NOT DHCP).  Setup any clients to find that IP in their /etc/hosts files.  Then you can use any samba client to access the storage on the WD device.  People tend to use fuse and **gigilo** because they are easier, but also 30-60% slower than direct samba mounts.  Then you can use almost any file browser to access the storage by the name you give the HUB in your /etc/hosts file.

After you setup a proper IP network where all the clients and servers know about each other, almost all these sorts of issues go away. I don't know of any automatic way that works 100%. This is a manual process.  You will need to understand networking sufficiently to choose subnets and IPs that will work correctly on your setup.  There are a few gotchas around that - like never pick a static IP that is inside a DHCP range. Standard network stuff.  Forget the point-in-click for this part of the solution. It won't help.

IMHO.

---

### Post by carusoswi on 2017-02-12
I appreciate the reply, but (and I probably should have made this clear in my original post), but have had this setup for many years across several Ubuntu versions (have also experienced this frustrating problem before).  Recently had to re-install 16.10, and now, what was working is no longer working.  I can see the drive in Ubuntu, but cannot open it.  What is different now to cause it to stop working.
The drive works fine from Windows 10.
In the past, trial and error finally just sorted the problem out.  Maybe that will happen this time.
Additional comments welcome.
Caruso

---

### Post by TheFu on 2017-02-13
If you want it to always work, setup a proper IP network.  Do all your systems have forward and reverse name resolution?  Is there an NMB daemon running on the hub to broadcast "i'm here, I'm here?"  Is Avahi running on your Linux system?  Does the "hub" send out avahi compatible network announcements?  This is sometimes called zeroconf.

> The drive works fine from Windows 10.
Windows is a different OS and **every** vendor tests with it. Most don't test with Linux compatibility.  It is very common for vendors to run an old version of samba on these sorts of devices that hasn't been updated in many years. Whether that matters for compatibility is an unknown. It works on Windows (because they test it), but other OSes tend to follow specifications for the protocol.

It is good to know that it does work with Windows. To me, that means it is a network name resolution issue or something else. Name resolution isn't hard, but it has to be done.  For most home networks, the easy answer is to use dhcp reservations and edit the /etc/hosts file.  Alas, grandma won't do this so she finds that things don't always work consistently.   For network connections that work consistently, the devices need to be on the same dedicated, internal, IP from day to day. Static IPs and/or DHCP reservations make that happen, but they have to be configured.  After a power outage or when a new router gets installed, the old IPs often get changed. You may be able to force an update by using **arp** and **ping**ing all the different devices on the internal network by IP/name.

Setup DHCP reservations - [https://lifehacker.com/5822605/how-to-set-up-dhcp-reservations-so-you-never-have-to-check-an-ip-address-again](https://lifehacker.com/5822605/how-to-set-up-dhcp-reservations-so-you-never-have-to-check-an-ip-address-again)
and my article on the subject (posted 1 day before): [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)  Whitson probably did a better job of explaining the how. I think I cover the "why" better.  A few of the sentences are stolen verbatim from my article.

---

### Post by Morbius1 on 2017-02-13
As a side note you might consider this a "teaching moment". All of these interim ubuntu releases between LTS releases are "technology previews" not something anyone expects regular users to use. 16.10 is not better than 16.04 because it's numerically higher.

Anyhoo, in terms of overall efficiency and most importantly reliability the following is how I view network connectivity - in order of best to worse::

** Static IP address as TheFu demonstrated above.
** Avahi ( mDNS ) where you would be able to connect to the device with something like WDTVLiveHub.local.

*[COLOR=#0000cd]Regrettably and as a proof of my first statement 16.10 made a mess of avahi. They tried to get fancy smancy with nsswitch and just made a mess of things. Easy enough to fix ( [https://ubuntuforums.org/showthread.php?t=2340042&p=13557382#post13557382](https://ubuntuforums.org/showthread.php?t=2340042&p=13557382#post13557382) ) but this is something that shouldn't need to get fixed.[/COLOR]*

** Telegraphy
** Jungle Drums
** Smoke Signals
** NetBIOS

The last one is the one you are struggling with in this topic. If you choose to ignore TheFu's advice and want to get this working change the way name resolution is performed on your Linux box:

Edit /etc/samba/smb.conf
Right under the "workgroup = workgroup" line add another:
```
name resolve order = bcast host lmhosts wins
```
THen restart samba in this order - assumming you have the samba server installed:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```

---

