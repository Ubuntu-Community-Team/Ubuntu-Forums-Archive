---
title: "Unable to connect with Edimax EW-7318USG"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by eden360 on 2008-06-24
I'm new to Ubuntu, but my experience so far is great.  The only only problem I have is connecting to the wireless network in my apartment.  I'm running Hardy and using an Edimax EW-7318USG, and I'm using Wicd instead of gnome's network manager.  
The problem occurs when I try to initially connect to the network.  I think the problem occurs when Wicd tires to connect to the DHCP server because it takes serveral tries to just to get an IP.  When I am finally assigned an IP address, the connection is dropped almost immediately.  I first assumed it was the network, but I can connect without any problem with my laptop running XP.  Also, I'm duel booting Vista and it connects using the Edimax usb adapter.
Again, I'm new to Ubuntu and not really sure how to troubleshoot from here.  Any help would be greatly appreciated.

---

### Post by mavi_yelkenler on 2008-06-24
hi eden360,
i have the same usb adapter. i experience no problem. but i should also say that your adapter may be about to broken. i had one more of the Edimax EW-7318USG and when it was broken ifconfig -a sometimes showed the interface and sometimes not. now i have the new same Edimax and there is no problem. when your connection is droped please look the output of ifconfig -a and check that your interface up or down.

---

### Post by pokipoki08 on 2008-06-24
I have the same card and it is working flawlessly in Hardy. What I did 

 - blacklist some modules
 - download a patched driver
 - recompiled a new module
 - edited /etc/network/interfaces

and it connects to a WPA2 network on boot.

For a start, try these commands at the terminal & post the output here :

```
cat /var/log/messages | grep wlan
cat /etc/network/interfaces
ifconfig
iwlist wlan0 scan
iwconfig wlan0
```

---

### Post by eden360 on 2008-06-24
Thanks for the quick replies.  I may have fixed it by blacklisting some drivers.  I connected to the network using gnome's network manager instead of wicd and it connected instantly, so I'm hoping the problem was the blacklisted modules.  *crosses fingers*:)

---

### Post by orkinoks on 2009-06-18
Hi;
remove the ethernet adaptors if you have then 2 already in your computer.Try disabling the onboard ethernet for example, that solved my problem.I had 2 ethernets and ew7318, disabling one of the ethernets solved it.

---

### Post by ugm6hr on 2009-08-01
[http://ubuntuforums.org/showthread.php?p=7716964#post7716964](http://ubuntuforums.org/showthread.php?p=7716964#post7716964)

---

