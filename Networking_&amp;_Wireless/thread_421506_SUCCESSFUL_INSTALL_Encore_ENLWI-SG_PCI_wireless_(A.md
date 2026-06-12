---
title: "SUCCESSFUL INSTALL: Encore ENLWI-SG PCI wireless (Atheros 5212 chipset)"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by apureevil1 on 2007-04-24
I did a complete reinstall of Edgy 6.10 again this morning, I enabled all replositories and did all the updates for 6.10 then I followed this..
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-19b0a03ec0e66fadc9426778724825dd585178a5](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-19b0a03ec0e66fadc9426778724825dd585178a5)
( I only had to do these 2 steps and then a reboot)
1.)  **sudo apt-get install network-manager-gnome**
2.)  **sudo /etc/init.d/dbus restart**
upon reboot I had the icon in the corner, my wireless connection was listed, I chose connect, it asked for my Keyring password (I used the same one as my log in to the system) and WPA key(password) It stll asks for my keyring password on every reboot but that is a very minor annoyance( I think the fix for this is included in the above link however I am uncertain if its for Edgy or Fiesty)..I am just happy as hell to have my wireless working. and it's connecting with a signal of 75%
I have an** Encore ENLWI-SG **PCI card which has an **Atheros 5212** chipset.
**ASUS A8V-VM SE** Motherboard socket 939 with an AMD Athlon 64 (2.2 ghz processor) and 1 GIG of Ram
all necessary drivers installed with ubuntu 6.10 after I enabled all repositories. I believe that it is using the madwifi i386 generic drivers (which I  installed with synaptic as well).
I hope this helps..I am going to stick with Edgy for a bit, I want to enjoy my wireless for at least a week ( then I will try to get it to work with Fiesty...

---

### Post by stchman on 2007-04-25
> **apureevil1 said:**
> I did a complete reinstall of Edgy 6.10 again this morning, I enabled all replositories and did all the updates for 6.10 then I followed this..
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-19b0a03ec0e66fadc9426778724825dd585178a5](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-19b0a03ec0e66fadc9426778724825dd585178a5)
( I only had to do these 2 steps and then a reboot)
1.)  **sudo apt-get install network-manager-gnome**
2.)  **sudo /etc/init.d/dbus restart**
upon reboot I had the icon in the corner, my wireless connection was listed, I chose connect, it asked for my Keyring password (I used the same one as my log in to the system) and WPA key(password) It stll asks for my keyring password on every reboot but that is a very minor annoyance( I think the fix for this is included in the above link however I am uncertain if its for Edgy or Fiesty)..I am just happy as hell to have my wireless working. and it's connecting with a signal of 75%
I have an** Encore ENLWI-SG **PCI card which has an **Atheros 5212** chipset.
**ASUS A8V-VM SE** Motherboard socket 939 with an AMD Athlon 64 (2.2 ghz processor) and 1 GIG of Ram
all necessary drivers installed with ubuntu 6.10 after I enabled all repositories. I believe that it is using the madwifi i386 generic drivers (which I  installed with synaptic as well).
I hope this helps..I am going to stick with Edgy for a bit, I want to enjoy my wireless for at least a week ( then I will try to get it to work with Fiesty...

All that means is that the kernel supports your wireless card out of the box.  I needed to install the madwifi drivers:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Try it when you go to Feisty if you have problems.

---

### Post by apureevil1 on 2007-05-17
I made the plunge and installed fiesty..and ....holy crap miy wireless is still working...:lolflag:

---

