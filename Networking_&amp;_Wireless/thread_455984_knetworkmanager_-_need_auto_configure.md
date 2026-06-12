---
title: "knetworkmanager - need auto configure?"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by candtalan on 2007-05-27
(kubuntu 7.04)
Yesterday I connected successfully to a friends wireless network, using the wep 64 bit hex key, it all worked ok.

Something seems to have changed in my configuration now (or then) because for the same hardware and location I am only offered manual configuration (KNetworkManager) and although wireless card is shown as enabled, I cannot see any available wireless networks - I know there is one in the house and one next door at least.

pcmcia wirelsss card (prism54 chip) works ok in this distro (kubuntu 7.04) aand the activity led is on and steady.

I recall that when I connected to this network yesterday, and after putting in the wep key, I was asked to setup a new password, and I did this, with a confirmation field. There was a password strength meter included so I sort of think it might have been a type of wallet manager, (sorry not sure). At the time I just wanted to get online  and expected any need for the new password to be indicated later if needed. However, if it is needed now, I am not being asked for it and I have no idea where it might be relevant (I do know what is was...).

The system settings, network settings show that wlan0 and wmaster0 are both dhcp and are enabled wireless devices.

I need to know either how to make the wireless connection non manual (ie automatic) now or how to successfully get through to the internet..

Part of the mystery is quite why things do not just connect today as they did yesterday.

tia

---

### Post by luisromangz on 2007-05-27
I think you used the manual configuration tool. That's the reason you were prompted to introduce your password. After using manual configuration, knetworkmanager isn't able to manage your wireless conection.

You can check if my guess is right by checking your /etc/network/interfaces file. If it has a section labeled wlan0 or your other wireless network interface, you should remove it.

Hope it works!

---

### Post by candtalan on 2007-05-27
sounds likely :-( 

I will look at this 

thanks!

---

### Post by Cimmo on 2007-10-27
[http://launchpad.net/bugs/125767](http://launchpad.net/bugs/125767)

---

