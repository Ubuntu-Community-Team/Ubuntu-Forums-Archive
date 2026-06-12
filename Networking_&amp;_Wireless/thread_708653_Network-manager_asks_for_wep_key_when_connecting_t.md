---
title: "Network-manager asks for wep key when connecting to university network"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by LinuxD on 2008-02-26
I've been having this problem recently connecting to my university network.

Normally, to connect I use the settings that they recommend on their guide to connecting through network-manager. 

[http://helpline.concordia.ca/network/wireless/Linux.shtml]("http://helpline.concordia.ca/network/wireless/Linux.shtml")

Recently, I haven't been able to connect because network-manager started asking me to provide the a key for the network. This puzzles me since I haven't needed to give it before since I thought providing my username and password took care of authentication. After a clean install I had done not too long ago, I found that this problem only started after I put my laptop through hibernation.

I haven't had any luck in finding information that could help me, so I was wondering if anyone has had any experience with this or any tips on how I could go about debugging this...

Thanks in advance

---

### Post by deragon on 2008-02-27
Greetings.


  I have a different problem.  I always use wpa_supplicant on my old nc6000, using madwifi driver.   It still works.  However, I tried NM and wpa_supplicant on Hardy Heron 08.04 A4 on a new laptop with a ipw2200 and never got connected.  I plugged on the same laptop a pcmcia card DWL-G630 (madwifi driver) and it worked like a charm.

  The driver of the card or the card itself affects how WPA works.


Best regards,
Hans Deragon

---

### Post by lemoonad3 on 2008-03-11
> **LinuxD said:**
> I've been having this problem recently connecting to my university network...



I just decided to try Ubuntu Gutsy, and I'm also using the ipw2200 driver (I think).  As such, I followed the same guide from Concordia's website and I get the same error as yourself. 

Sadly, I have no idea what I'm doing, and I don't even know if I'm editting the wpa_supplicant.conf file properly, but I'll try to fool around with different drivers and see if I can get connected somehow. 

cheers

---

### Post by LinuxD on 2008-03-11
Well let me first say welcome to Ubuntu!

Also, I'm not sure that the driver is the problem. At first, I was able to connect to the network just fine unless I put my lappy into hibernation. Now however, it refuses to connect even after a fresh install. Because of this, I'm thinking that it may have been an update to network-manager that brought this problem about. I used to have some debugging output that I was hoping to post but it seems like I may have deleted it when I tried a fresh install a short while ago. Like you, my plan was to try out editing wpa_supplicant.conf and see if that helps. Until I learn more about it, and get through the exams and assignments I've got coming up, this is being on put on hold. 

If you are using a different driver than me (my computer uses ipw3945), then maybe using ndiswrapper will help. Although I was under the impression that the intel wireless cards were rather well supported by Ubuntu.

Best of luck!

---

### Post by deragon on 2008-03-12
WPA Enterprise, which Concordia uses, is not often seen.  My internal intel ipw2200 wireless card worked with normal WPA wifi hotspots.  It is only with WPA Enterprise that it would fail.

---

### Post by LinuxD on 2008-03-14
I've been talking with my research supervisor recently (we're both linux fans) , and it turns out he's been among many faculty members who have been suggesting to IITS that they change the security scheme so that it will be more compatible for Linux/Mac users... Still a rumor for now, but we may see a more easily accessed network in the future.

---

### Post by deragon on 2008-04-18
**This post could be related to an Ubuntu bug filed at**: 217653 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				A bug report has been filed regarding this issue:  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/217653](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/217653)

---

