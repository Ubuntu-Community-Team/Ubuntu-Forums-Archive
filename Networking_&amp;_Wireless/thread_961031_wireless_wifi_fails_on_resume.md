---
title: "wireless wifi fails on resume"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by fredknex on 2008-10-27
Finally with the newest 8.10 beta standby/hibernate does not hang on resume.  But now network-manager fails to connect to the network on resume. A reboot fixes the problem, but standby is essentially useless.  Hopefully this will be fixed when 8.10 is out of beta, but does anyone else have this problem/know the cause/have a solution?

---

### Post by beta.tester on 2008-10-28
Hi Fred

I had similar problems with the beta! However the RC version of 8.10 (release is in 3 days :) solves my problems here. Suggestion:

Download and burn the 8.10 RC version if you cannot wait for the release :)

Run it live!  have found they have really worked hard on this and for me, the network was identified and I simply had to supply my WAP/PSK password and it worked brilliantly! The problem of losing wifi connection/settings after an update also seems to have been fixed (I have the Aheros chip) and working as advertised.

Hope this helps,

Kind regards   john

ps after running live for 2 hours, I reinstalled 8.10 RC applied all updates, and rebooted. Now been running with no problems since then ;)

---

### Post by fredknex on 2008-10-30
ahh 8.10 fixed it after a quick change listed on the release notes!




[B]"Wireless doesn't work after suspend with ath_pci driver

Wireless devices that use the ath_pci kernel driver, such as the Atheros AR5212 wireless card, will be unable to connect to the network after using suspend and resume. To work around this issue, users can create a file /etc/pm/config.d/madwifi containing the single line:

SUSPEND_MODULES=ath_pci

This will cause the module to be unloaded before suspend and reloaded on resume. "[/B]

---

### Post by Bigfork on 2008-10-31
> **fredknex said:**
> ahh 8.10 fixed it after a quick change listed on the release notes!

Thank you sir!  That was exactly my issue and that solved it for me.

'Fork

---

### Post by dbsanders on 2008-11-01
Hmmm didn't quite work for me. My wifi works on reboot, but after suspend/resume I see a "networking disabled" icon in the menu bar.

Before I did the workaround, the network would appear to search for networks and find nothing (icon spinning). Now after the workaround I see the behavior above.

---

### Post by Arabiest on 2008-11-01
gents,

I have the same problem and when boot, it seems that its picking up the network but after some time it loosses and even after feeding the network IP and other details, still the same.

Please help.

---

### Post by dbsanders on 2008-11-01
> **dbsanders said:**
> Hmmm didn't quite work for me. My wifi works on reboot, but after suspend/resume I see a "networking disabled" icon in the menu bar.

Before I did the workaround, the network would appear to search for networks and find nothing (icon spinning). Now after the workaround I see the behavior above.

Oddly enough I tried it again and it does work properly now. The workaround does work (around).

---

### Post by andnobodyslept on 2008-11-02
I had a very similar problem, and there is a workaround for those who use the rt61pci driver

To find out if this is your driver 
```
lcpci -v | less
```
Scroll down until you see your wireless card, should say something like kernel driver in use: rt61pci

There is a bug report with a workaround
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780")

Hope this helps some people

---

### Post by danmarycap on 2009-03-12
> **fredknex said:**
> ahh 8.10 fixed it after a quick change listed on the release notes!




[B]"Wireless doesn't work after suspend with ath_pci driver

Wireless devices that use the ath_pci kernel driver, such as the Atheros AR5212 wireless card, will be unable to connect to the network after using suspend and resume. To work around this issue, users can create a file /etc/pm/config.d/madwifi containing the single line:

SUSPEND_MODULES=ath_pci

This will cause the module to be unloaded before suspend and reloaded on resume. "[/B]


Had a very similar problem on a Dell mini9 running Intrepid 8.10 using a Broadcom 43xx wireless adapter.  I used a combination of this trick and another I stumbled upon to get a permanent fix.  Posted here: [http://ubuntuforums.org/showthread.php?p=6883391#post6883391](http://ubuntuforums.org/showthread.php?p=6883391#post6883391)

-Dan

---

