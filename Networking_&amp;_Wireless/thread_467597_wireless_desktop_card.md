---
title: "wireless desktop card"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by michaelbmcgee on 2007-06-07
about a week ago i put ubuntu feisty on my laptop and loved the os. it worked well with my wireless card. today i put it on my desktop computer but have not been able to use my usb wireless card. i am going to buy a pci wireless card for my desktop but am not sure which one to get. can anyone recommend a wireless card for my desktop that will work right out of the box with ubuntu feisty?
thnx,
-michael

---

### Post by madmetal on 2007-06-07
> **michaelbmcgee said:**
> about a week ago i put ubuntu feisty on my laptop and loved the os. it worked well with my wireless card. today i put it on my desktop computer but have not been able to use my usb wireless card. i am going to buy a pci wireless card for my desktop but am not sure which one to get. can anyone recommend a wireless card for my desktop that will work right out of the box with ubuntu feisty?
thnx,
-michael

give a look here 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
and also search forums for users feedback..

better look for a good chipset ;)

---

### Post by SkyScrap on 2007-06-08
> **michaelbmcgee said:**
> about a week ago i put ubuntu feisty on my laptop and loved the os. it worked well with my wireless card. today i put it on my desktop computer but have not been able to use my usb wireless card. i am going to buy a pci wireless card for my desktop but am not sure which one to get. can anyone recommend a wireless card for my desktop that will work right out of the box with ubuntu feisty?
thnx,
-michael

Hi,

I've started a [similar thread]("http://ubuntuforums.org/showthread.php?t=467786"). I'm close to believe that there is no such thing as out-of-the-box support for wireless in Feisty.

---

### Post by madmetal on 2007-06-08
> **SkyScrap said:**
> Hi,

I've started a [similar thread]("http://ubuntuforums.org/showthread.php?t=467786"). I'm close to believe that there is no such thing as out-of-the-box support for wireless in Feisty.

i have a compaq armada laptop and got a Linksys WPC54GS pcmcia card..
the only thing i did was 
```
 sudo aptitude install bcm43xx-fwcutter 
```
and i got wireless network with WEP and WPA without anything else..
so this is out of box... ;)

---

### Post by SkyScrap on 2007-06-08
> **madmetal said:**
> i have a compaq armada laptop and got a Linksys WPC54GS pcmcia card..
the only thing i did was 
```
 sudo aptitude install bcm43xx-fwcutter 
```
and i got wireless network with WEP and WPA without anything else..
so this is out of box... ;)

I found [your report in the other thread]("http://ubuntuforums.org/showthread.php?p=2721112&highlight=WPA#post2721112") also. Unfortunatly my PC does not have a PC-Card slot :( 

But thanks for answering! :)

---

### Post by madmetal on 2007-06-08
yeap pcmcia is mainly for laptops...
but you can search for a pci card that will work out of box under ubuntu..
chipset is all about ;)

---

