---
title: "troubles with rtl8187B"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by luiggirobles on 2007-11-06
Hi, 

I have installe Gutsy on my Toshiba L45 with an integrated Realtek RTL8187B wireless card and first I couldn't get it to work.  Now I've managed to have it working thanks to a driver patch here ([http://ubuntuforums.org/showthread.php?t=571046&page=6](http://ubuntuforums.org/showthread.php?t=571046&page=6)), but I have to run 'wlan0up' each time if I want it to work, ubuntu doesn't recognise the card automatically.  Also, the network manager applet doesn't show the strenght of the signal, wifi-radar won't work (it starts, but doesn't allow me to manage the networks) and my on-off switch doesn't work (it doesn't go off if I turn it off).
Does anyone know of a way to get it to work better?  Thanks.

---

### Post by skanxalot on 2007-11-15
I'm in the same boat - would love to see a solution. I have to manually activate the card on every boot.

---

### Post by 007WRX on 2008-03-11
I have a buddy with a Gateway Laptop and the realtek ftl8187b wireless and his drivers arent automatic. I do not have his laptop with me atm, but I will try the above driver fix to get his wifi working. However I may just tell him to get an intel card if you guys cant fix the other problems. This kid doesnt even know what terminal is, much less would he want to have to wlan0 up every time. SOMEONE HELP!

---

### Post by cslaght on 2008-06-07
Okay my name is curtis, I have looked around on the internet for drivers and fixes for this wireless card.  Just the other day i found a website that has the drivers for this card.  The only thing that does not work on this card is that you can get full strength but it will only show that you have 1 bar.  
The website is   [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

my email is [email]curtis.slaght@gmail.com[/email] you can email me and i will give you help if needed.  Hope this helps

---

### Post by befana on 2008-06-09
cslaght, how to remove the folder rtl8187b-modified from my desktop?
And how to remove the driver?
The problem with the driver from the link you provided is not only with the signal bar, but this driver does not support WPA Personal.
My rtl8187b worked only few days with this driver: [http://www.fileshare.ro/531529970.58](http://www.fileshare.ro/531529970.58) and started to disrupt my router,because of that I installed the driver your provided.
And now rtl8187b can not connect to a WPA secured network, and I have a useless folder on my desktop.
My pc is Toshiba Satellite L40 14F with rtl8187b wifi.

---

### Post by sayid on 2008-06-12
> **cslaght said:**
> Okay my name is curtis, I have looked around on the internet for drivers and fixes for this wireless card.  Just the other day i found a website that has the drivers for this card.  The only thing that does not work on this card is that you can get full strength but it will only show that you have 1 bar.  
The website is   [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

my email is [email]curtis.slaght@gmail.com[/email] you can email me and i will give you help if needed.  Hope this helps

Hello curtis, I have a Olibook 520 that uses the same chipset RTL8187b.
A few days ago I follow the same steps that say the link [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b).
After this all work perfect but using non-encrypted protocols

Summary: 

**Disadvantages of this driver**
 * Can't use encrypted protocols (WEP,WPA,WPA2, and variants). WEP freeze your machine. WPA and WPA2 are not working too.      
 * Permit connect only when the signal is perfect, if you try the same with windows, the same wireless card enable you connect in more distant places.
 * The driver reports Link Quality=0  Signal level=0. (I try modify this with iwconfig but the driver module reports something like 'changes not possible')
 * KNetworkManager always see a simple bar of signal.

**Advantages **  
 * Permits connect to any wireles router without encryption, only if you are really near the router.

Anybody knows if this problem will be resolved in future kernel's implementations? 
Have any other solution?

I'm really confused with this :confused:.
Thanks to all people that post solutions and knowledge!

---

### Post by sayid on 2008-06-12
Hello again, I have good news, WEP with cuervos's drivers works correctly! :)

The only problem that I found whit this is that i must use 64 bit passphrase and in hexadecimal format (I tried putting the passphrase in human readable, but i never was connected).

Regards,
Sayid...

---

### Post by Curtis Slaght on 2008-07-04
Anyone that does not have the wireless internet working email me at [email]curtis.slaght@gmail.com[/email] and i will show you how to get it up and running.

---

