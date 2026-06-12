---
title: "Wireless access in 9.10 using Dlink DWL-G122"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by crazedwombats on 2009-10-29
I am trying to connect to my WPA2 wireless network using a DLink DWL-G122 Rev B. I just installed ubuntu 9.10 which happens to be my first experience with linux. I am able to detect surrounding wireless networks fine, but when I choose my network to connect to and enter my password, it just sits for a while and ends unsuccessfully. After searching online I've seen conflicting posts that say I need ndiswrapper, and others that say it has native linux drivers and does not require it. Any help would be greatly appreciated!

---

### Post by theozzlives on 2009-10-29
> **crazedwombats said:**
> I am trying to connect to my WPA2 wireless network using a DLink DWL-G122 Rev B. I just installed ubuntu 9.10 which happens to be my first experience with linux. I am able to detect surrounding wireless networks fine, but when I choose my network to connect to and enter my password, it just sits for a while and ends unsuccessfully. After searching online I've seen conflicting posts that say I need ndiswrapper, and others that say it has native linux drivers and does not require it. Any help would be greatly appreciated!

I'm assuming the DLink is a router.(?) NDISWrapper is for cards not routers. Double check your settings, or just to see if you can connect, try no security at all temporarily.

---

### Post by soni1770 on 2009-10-29
hi, maybe you should have a look at what security ubuntu is sending out, might be different from wpa, click on your network, then when the connect to box comes up, check out what the security is, might pay to change it about and keep entering your passcode.

---

### Post by crazedwombats on 2009-10-29
theozzlives: No I'm using a linksys router. The DLink DWL G122 is a Wireless USB card.

soni1770: I have the security setting set to "WPA & WPA2 Personal" so that shouldn't be the problem.

---

### Post by crazedwombats on 2009-10-29
Problem solved! All I did was change my routers settings from TKIP+AES to just AES and everything worked.

---

### Post by harshad on 2009-10-31
For some unknown reason, changing my Linksys router security settings from TKIP+AES to just AES worked for me as well. 

However I suppose all users wont have control over router security, so this can be termed as a bug introduced in 9.10. Dlink DWL-G122  worked fine with 9.04

---

### Post by Johnasp on 2009-10-31
I am having similar problems with a D-Link DWA-140 802.11n wireless router. I have no problems with it in 8.40 but using 9.10 and Grub 2  it is reported as disconnected.

---

### Post by akiratheoni on 2009-10-31
> **Johnasp said:**
> I am having similar problems with a D-Link DWA-140 802.11n wireless router. I have no problems with it in 8.40 but using 9.10 and Grub 2  it is reported as disconnected.

I had the same issue; Ubuntu recognized wireless networks but didn't connect to any of them (I have a wireless usb adapter). If you're having the same problem, try this:

> Fixed with:

Step1: add "blacklist rt2800usb" to:
/etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
/etc/modules
Step3: Reboot.


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323)

---

### Post by cafe.orquidea on 2009-11-15
Hi everyone,
I'm quite new to Ubuntu and I'm having the same problem... I've tried adding the lines to the files blacklist.conf and modules, but it didn't work.
I was trying to change the routers settings from TKIP+AES to AES but, sorry for the stupid question, how do I do it? What settings are that? I opened the router page but I didn't find anything like that. I'm using an Alice router.
Thanks in advance.
Silvia

---

### Post by Lemuel111 on 2010-01-09
[B]You wrote:-

Re: Wireless access in 9.10 using Dlink DWL-G122[/B] 			
 			 			 		   		 		 		Problem solved! All I did was change my routers settings from TKIP+AES to just AES and everything worked.



How do you acutally do this? I am very new to Ubuntu (I'm using 9.1) and need things explianing in a little more detail. Thanks.

---

### Post by akshunj on 2011-01-01
Can confirm that the change to AES is necessary for the DWL-G122 rev.B1 adapter.  I know this USB stick had overheating and dropped connection issues, so I am currently stress-testing. I will report back on results...

---

### Post by akshunj on 2011-03-05
works perfect!

---

