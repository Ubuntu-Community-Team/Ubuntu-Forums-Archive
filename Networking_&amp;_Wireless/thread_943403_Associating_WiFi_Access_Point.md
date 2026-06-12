---
title: "Associating WiFi Access Point"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by sjrlaw on 2008-10-10
I am having problems with a wifi connection.  When I type iwconfig, part of the output is:

```

wlan0     IEEE 802.11g   ESSID:""
          Mode: Managed  Channel:0  Access Point: Not-Associated

```

I know how to set the essid, but how do I associate an access point with wlan0?  What is the console command? (Or even better, the procedure in Gnome).

Thanks!

---

### Post by hyper_ch on 2008-10-10
is this a server?

---

### Post by sjrlaw on 2008-10-10
No, it is not.  It is a Hardy workstation (desktop) using a Linksys wireless NIC that I am trying to connect to my WAP to gain access to the Internet.

---

### Post by hyper_ch on 2008-10-10
try to replace the default network manager with WICD: [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by sjrlaw on 2008-10-10
Hyper_CH:

I would if I could get a connection to the Internet!  :)

I just need to get it connected once, so I can download what I need for a more lasting solution.

And before you suggest it, a hardline Ethernet connection to do this initially is impractical for several reasons I won't go into.  I also want to learn the ins and outs of this, as I do like to tinker and get a better understanding of how things work under the hood.

I was hoping for a switch for iwconfig that would associate the access point in order to zero in on the solution.

I also noted that the Linux laptop I am writing this on ID's the wireless device as eth1, while my desktop IDs it as wlan0.  I don't know if that makes a difference.

---

### Post by huwnet on 2008-10-10
Do you have NetworkManager?

Which model / chipset is your card?

---

### Post by sjrlaw on 2008-10-10
Huwnet:

No I do not have Network Manager (as far as I know).  Just the standard Hardy install.

Card is a Linksys; I believe it is a Broadcom chipset.

---

### Post by 73ckn797 on 2008-10-12
> **hyper_ch said:**
> try to replace the default network manager with WICD: [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

I get the impression that WICD is a better network manager. If that is the case, then I ask the following:

  	 	 	 	 	 	  Laptop = Toshiba Satellite M115-S3094. Ubuntu worked right away in dual boot and now as only OS. 80gb HDD, 1.5gb ram.


The wireless will not connect to some systems that previously were accessible with the WinXP, OEM installation.


I travel around the area daily and have places that offer open Wifi and secured Wifi. The secured connections give the password but I cannot get connected. I have been cataloging the passwords but Ubuntu does not connect to many of those as they did in the past.


WICD will replace the OEM manager, correct?
Does/can it do a better job of detecting and connecting?

---

### Post by hyper_ch on 2008-10-12
try it out yourself... the provide a repo... so it's simple to de/install... default network manager will get replaced by wicd... but you can replace wicd later on again with the default network manager.

---

### Post by 73ckn797 on 2008-10-12
> **hyper_ch said:**
> try it out yourself... the provide a repo... so it's simple to de/install... default network manager will get replaced by wicd... but you can replace wicd later on again with the default network manager.

Thanks. I was aware it is in the repo but wanted to clarify a few things first. I will see what happens. I knew any changes could be reversed.

Edit:
Where would any wireless network info be stored under Ubuntu. In particular, any passwords/keys used to logon to secure sites.

---

### Post by hyper_ch on 2008-10-13
wicd is in the default repos? I added the one given by them.

hmmm, that depends on the network manager you use and if you use no network manager then it would be /etc/network/interfaces

---

### Post by 73ckn797 on 2008-10-13
> **hyper_ch said:**
> wicd is in the default repos? I added the one given by them.

hmmm, that depends on the network manager you use and if you use no network manager then it would be /etc/network/interfaces

It is not in the default repo but I used the link given. When reloading Synaptic it gives an error about the wicd link signing key being invalid but I was still able to install on laptop and it works fine. Today will determine if it is able to detect other wifi connections as I am out and about around Atlanta.

---

### Post by hyper_ch on 2008-10-13
did you import the gpg keys as it says here? [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by 73ckn797 on 2008-10-13
> **hyper_ch said:**
> did you import the gpg keys as it says here? [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)


No on the gpg keys but I will. Today Wicd worked flawlessly at every place I went. Those, though, typically do not give problems connecting to. Tomorrow will be another test.


FYI: I am in and out of automobile dealers and independent repair shops all day. Many have wireless internet for customer use. Some are secured but give a password to access their systems. It has been some of those that have been at issue with Ubuntu. I enter the password but cannot connect. Maybe Wicd will better detect the security mode they use. Sometimes, in shops where I have connected before but on a particular day cannot, probably need to reset their routers. That has occurred on several occasions in the past.

I am running Hardy on the laptop and it has been mostly trouble-free. I do not tinker with that set-up like I do with my desktop, so that avoids most of the problems I have had with the desktop. I keep very little on the laptop so could probably use Xubuntu on it. Hardy runs great on it.

---

