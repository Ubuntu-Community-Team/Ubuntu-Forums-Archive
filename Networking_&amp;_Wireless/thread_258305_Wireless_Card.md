---
title: "Wireless Card"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by NewWaves on 2006-09-15
Hi,
I recently purchased a wireless G pci card...  It's a linksys and ubuntu does find it as it returns this from lspci: 0000:01:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


I'm not sure if the card isnt working because i don't have a proper antenna for it, or what is going on.  Any ideas? Should I buy an antenna, and if so, what kind.... There's so many types!

---

### Post by NetworkGuy on 2006-09-15
The card probably isn't working properly unless you made some changes to your system to allow it to work

In case you haven't, here is a howto I found for you on getting it working correctly in Ubuntu

[http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

After you get the card working correctly, you should be able to determine if you need an antenna or not.

---

### Post by NewWaves on 2006-09-15
Hi,
I did try ndiswrapper, it installed fine, but it just cant find a signal... I don't know if thats because of a misconfiguration or what...  That guide didnt help much im afraid.

---

### Post by NetworkGuy on 2006-09-15
What do you get back when you type ```
iwconfig
``` and ```
iwlist wlan0 scan
```
*Exchange wlan0 for whatever your wireless card is being called.

---

### Post by NewWaves on 2006-09-15
Oops,
I had the wrong driver!  I found the right one, used the ndiswrapper and all of the sudden i get a 100% signal!  Now to see if it will work two flights upstairs without an antenna!:p

---

### Post by NetworkGuy on 2006-09-15
Sweet.  Good job.

---

### Post by NewWaves on 2006-09-15
Thanks for taking the time to find that tutorial!  I do wonder if you knew what type of antenna this card takes as I plan on buying one regardless if it works two flights up stairs or not. :D 

Here is the card: [http://www.amazon.com/Linksys-WMP54G-Wireless-G-PCI-Adapter/dp/B000085BD8](http://www.amazon.com/Linksys-WMP54G-Wireless-G-PCI-Adapter/dp/B000085BD8)

---

### Post by NetworkGuy on 2006-09-15
Sorry, I can't help on that one..

---

