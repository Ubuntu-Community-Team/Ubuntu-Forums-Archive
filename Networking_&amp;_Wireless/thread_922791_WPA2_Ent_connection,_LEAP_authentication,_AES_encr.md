---
title: "WPA2 Ent connection, LEAP authentication, AES encryption"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by sheaiden on 2008-09-17
I have an Intel 2200BG, running Ubuntu 8.04, and am trying to connect to my workplace's Wireless.  the information I have is:
Authentication: LEAP
Connection Mode: WPA2 ENT, WPA ENT
Encryption AES

The procedure I'm following is:
Click on Connect to Other Wireless Network from the applet
Enter Network Name, 
---------------------------
under Wireless security, select WPA2 Enterprise
Under EAP method, I see that LEAP is not available, so I go back a step.
---------------------------
Under wireless Security, select LEAP.
Under encryption, I see that AES is not an option.
Tear my hair out in frustration....


I have actually tried various permutations of the options available ([WPA2, TLS, AES], [LEAP, WPA-EAP], [LEAP, IEEE 802.1x], etc...) and all have been unsuccessful. the LEAP options seem to give up after waiting for a key, and I haven't been able to get info on why the WPA2 stuff is failing.

I do know that PEAP would need me to have a cert, and I don't have one, so the PEAP option (which our network engineers tell me does exist) wouldn't work for me.

I do know that even on windows, Cisco requires a new version of their client.  Is there a program that will do the combination of LEAP, WPA2, and AES?

---

### Post by pytheas22 on 2008-09-19
You might want to try using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.  I'm not sure how much better it might work, but it's worth a try (installing wicd will require you to uninstall NM; if you want NM back later, just type: 'sudo apt-get install network-manager-gnome').

Also do you have explicit directions on how to configure this in Windows, or is the information in your post the only thing you have about how this should be set up?

---

### Post by sheaiden on 2008-09-25
The information listed above is really the sum of what I have available.  The only other thing I know is that to connect in windows, you use the latest Cisco client.  Since I've never seen a cisco client specifically to connect to wireles accounts, I'm not sure about what client they use.  I will find out.

In addition, I will try the wicd, as suggested.

I'll post back.  

Thanks!

---

### Post by sheaiden on 2008-09-25
Network admin just got back to me...turns out, it was the setup of our wireless...the only way you had authority to authenticate was if you were an admin...

He was wondering why he was the only one allowed to authenticate!

Plus, even had he had the network set up properly, my account was not authorized for vpn access.  

comedy of errors....

---

