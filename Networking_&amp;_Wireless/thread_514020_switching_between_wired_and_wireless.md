---
title: "switching between wired and wireless"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by dbzdeath on 2007-07-31
ok so i have NetworkManager so it switches between my wired and wireless interface but what i want to do is make it so they both have the same ip address so i get less disruption when i switch interfaces over.. the best way i can see to do this(since you can't set NetworkManager to use a static address) would be to place a script in /etc/network/if-up.d/ (i have already written one to set the ip of the interface) but is there an easy way to grab what interface is being brought up? so i can make sure that my wired and wireless interfaces do not have the same ip address at the same time? if not i can always make my bash script check the output of ifconfig to see if my wired interface has a ip address set on it and if it does to leave the wireless interface alone.. i'm open to any other suggestions on how to do it

---

### Post by ugm6hr on 2007-07-31
Wicd allows static IP for wired and wifi.  Worth considering...

---

### Post by dbzdeath on 2007-07-31
> **ugm6hr said:**
> Wicd allows static IP for wired and wifi.  Worth considering...

does it allow switching automatically between a wired and wireless interface depending on whether or not the wired interface is plugged in? and does it support wpa supplicant?

EDIT i also need eap-tls support too

---

### Post by ugm6hr on 2007-07-31
> **dbzdeath said:**
> does it allow switching automatically between a wired and wireless interface depending on whether or not the wired interface is plugged in? and does it support wpa supplicant?

EDIT i also need eap-tls support too

In the newer testing versions - auto-switching to wired is available:
[http://wicd.sourceforge.net/phpbb/viewtopic.php?f=6&t=139&st=0&sk=t&sd=a&sid=bae8f4945fc8bf0d7f0f9c7144186752&start=20](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=6&t=139&st=0&sk=t&sd=a&sid=bae8f4945fc8bf0d7f0f9c7144186752&start=20)

I use v1.3.1 - so have to select wired (but I don't use wired very often).

As for eap-tls - dunno...  maybe ask on the wicd forum?

---

### Post by imdano on 2007-07-31
You know, we have EAP, LEAP, PEAP, and EAP-TTLS, but I don't think we have EAP-TLS.  It's actually pretty easy to add support for a new encryption method though.  If you go into the /opt/wicd/encryption/templates directory you'll find a file called "active", and then a bunch of wpa_supplicant.conf templates for different types of encryption.  Make your own template following the format the others are in, then add the name of the file to the end of "active".  If that's too much work or you're not sure how to do it, ask over on the wicd forums and adam or I will be able help you out.

---

### Post by dbzdeath on 2007-07-31
> **imdano said:**
> You know, we have EAP, LEAP, PEAP, and EAP-TTLS, but I don't think we have EAP-TLS.  It's actually pretty easy to add support for a new encryption method though.  If you go into the /opt/wicd/encryption/templates directory you'll find a file called "active", and then a bunch of wpa_supplicant.conf templates for different types of encryption.  Make your own template following the format the others are in, then add the name of the file to the end of "active".  If that's too much work or you're not sure how to do it, ask over on the wicd forums and adam or I will be able help you out.

hmm wicd won't even connect to my wireless interface.. i just wrote a script to look for the ip i've set to be assigned to the mac address for my wireless interface and if the ip is there it sets the wireless ip to be the same as my wired ip and that seems to work ok

---

