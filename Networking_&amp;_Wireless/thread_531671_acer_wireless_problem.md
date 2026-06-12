---
title: "acer wireless problem"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by wilrecar77 on 2007-08-21
i have an acer 5570z, specificly an acer 5570-2977. there is one acer 5570 entry in the laptops support page and unfortunately my laptop isnt the same. it uses an atheros card but im not sure which one it is specificly. when i use lspci it prints:
```
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
```
for whatever reason it says this though HAL is in use. it appears to be a HAL problem and becaude of that i have tryed to use ndiswrapper. all i really need is a HAL workaround or the driver for ndiswrapper. Thanks for all the help i (hopefully) get!

---

### Post by nosrednaekim on 2007-08-21
are you saying that it doesn't work with ndiswrapper?

could I have the output of iwconfig?

---

### Post by wilrecar77 on 2007-08-21
im saying i havent found the right driver to work with ndiswrapper, the output of iwconfig is:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```
by the way, im having trouble because it doesnt even show up in network manager.

---

### Post by aninaiian on 2007-08-21
have you tried the atheros wifi driver for the aspire 5570 at acer's website?

[http://www.acerpanam.com/flex/acerdrivers/bin/drivers.html]("http://www.acerpanam.com/flex/acerdrivers/bin/drivers.html")

---

### Post by wilrecar77 on 2007-08-21
yes. the net5211 doesnt work, and the acer site doesnt even show my specific laptop anyway, there is no link to the 5570-2977, or even a documentation

---

### Post by aninaiian on 2007-08-21
On the bottom of your laptop is there any sticker indicating the model number of your wireless chipset?

---

### Post by wilrecar77 on 2007-08-21
listed as having 802.11b/g WLAN.  on the cover of the laptop it says acer invilink, though this is a rebranding of the atheros chip inside the computer

---

### Post by ntlam on 2007-08-21
go to windows to see the detail of the card

---

### Post by gigabite on 2007-08-22
Hi. I have an Acer 5570Z too. Here's the forum post I used to get my Wi-fi adapter working.
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

Hope that helps. I'm keeping track of everything I do with the 5570Z, maybe you might find it helpful.
[http://ubuntufor5570z.blogspot.com/](http://ubuntufor5570z.blogspot.com/)

---

