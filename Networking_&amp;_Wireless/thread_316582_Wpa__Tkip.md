---
title: "Wpa / Tkip"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by towel on 2006-12-11
Hi first day with Ubuntu and so far so good.

Earlier today I managed to configure my 1390 broadcom card to authenticate using wep to my local network.

The problem I'm having is I want to be able to use my wireless at my school.  For that I need to use WPA with TKIP encryption, EAP-MSCHAP v2 authentication, and 
Protected EAP (PEAP).  I want to have two seperate profiles and just sort of switch back.

I've searched the forums and from what I've read so far I'm lost.  I sort of need someone to point me in the right direction.

I have wpa_supplicant open in the console but, is there a gui possibly out there for this?  I don't mind editing config files usually but, I would prefer not to with my laptop to say the least.

I'm researching as we speak but, lol I'm hoping to figure this out tonight so I won't have to boot up to Windows tomorrow at school :(


Thanks!

---

### Post by wieman01 on 2006-12-11
Oh well... This is what I can offer... A few sample scripts in the appendix, but none of them have been tested. Nonetheless I'd like to help if you are willing to put some effort into it.

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

### Post by tribaal on 2006-12-11
You might want to try/install "networkmanager", it has a nice gui for tkip, and you can save settings based on the network's ESSID.

This works wonders for me at least (WPA2 at home and WPA/TKIP/EAP2 at school too). It even handles windows certificates.

-  trib'

---

### Post by towel on 2006-12-11
Thanks I'll read through that. 

I'm definitely willing to put in some effort.  If I could get this working it would really help me a ton at school.

---

### Post by towel on 2006-12-11
> **tribaal said:**
> You might want to try/install "networkmanager", it has a nice gui for tkip, and you can save settings based on the network's ESSID.

This works wonders for me at least (WPA2 at home and WPA/TKIP/EAP2 at school too). It even handles windows certificates.

-  trib'


Sounds like what I'm looking for.  I'll download it now.  *Crosses fingers*

---

### Post by wieman01 on 2006-12-11
If NetworkManager supports EAP (which I was not aware of), then this is the right way to go. If it doesn't, drop me a line. PEAP is a Windows standard.

---

### Post by tribaal on 2006-12-11
Hum hope I'm not mistaking and confusing EAP with something else...

- trib'

---

### Post by wieman01 on 2006-12-11
> **tribaal said:**
> Hum hope I'm not mistaking and confusing EAP with something else...

- trib'
Well, we'll see. It's just that EAP is such a broad term, there a tons of different protocols out there (e.g. LEAP, PEAP, TTLS, to name a few). We'll know soon enough I reckon.

---

### Post by towel on 2006-12-11
Okay I installed NetworkManager via Add/Remove.

I see the applet running but when I click on it, it says no network connection.  When I plug an ethernet cable it detects a connection.

I'm able to surf wireless although I'm a bit confused what its doing.  Possibly a conflict of some sorts?  

Earlier I loaded Wifi-Radar and Wireless Assistant looking for a solution. I think I might remove them and try it again reboot.

---

### Post by towel on 2006-12-11
Hmm I couldn't see the network manager because I had to add the notication area.  Now my next problem is network manager only sees my wired connection but, the wireless is working fine.

I'm determined lol!

```
auto lo
iface lo inet loopback 
``` in /etc/network/interfaces/ Fixed the problem with the wireless not showing up in net manager --  I read that in another post and it worked for me also.



I'm still not sure if network manager supports peap but, I'm going take it to school and find out.

---

### Post by wieman01 on 2006-12-11
There is something: [http://www.ubuntuforums.org/showthread.php?t=278603&page=2]("http://www.ubuntuforums.org/showthread.php?t=278603&page=2")

Their configuration is not my preferred setup. I'd rather use "/etc/network/interfaces" to configure PEAP. If you need help, let me know. Apparently NetworkManager does not support PEAP.

---

### Post by towel on 2006-12-11
Network Manager at my school detects the network as:

[ATTACH]20915[/ATTACH]

Looks like Network Manager will do the job however, with Network Manager I'm unable to connect to any wlan at all. 

I'll be doing some more research once I get home later tonight.

Thanks for your help so far.  So close to success lol

---

### Post by wieman01 on 2006-12-11
Wow, great! NetworkManager has considerably improved. I am really impressed. If it was not for its lack of support for Static IP...

You'd do best to set this up together with your school's network administrator. He can give you all the details/credentials that you need.

Have you managed to connect to  your home network yet? Try NetworkManager with a WEP network first... Keep it simple in the first place.

---

### Post by towel on 2006-12-12
Well using Network Manager I'm only able to connect to unsecure networks.  It won't allow me to connect to secure networks at all.

At this point I'm not sure if Network Manager will work or if I'll have to use wpa_supplicant.


Second day using Ubuntu.  I like everything but, setting up wireless with this broadcom card :[

---

### Post by wieman01 on 2006-12-12
Suggest you try to figure out what's wrong with NetworkManager first. If you fail to get it working, I can help you configuring wpa-supplicant.

---

### Post by towel on 2006-12-13
:-D  I uninstalled wifi-radar and I connected to my schools wlan with network manager!  I'm assuming it will connect flawless now when I go home as well.

Aww snap! 


I love not having to boot into Windows anymore!

Thank you for all your help!

---

