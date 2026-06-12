---
title: "bcmwl5"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by Keithod on 2006-11-07
Hi,

I have installed nsiswrapper (the version that came with my ubuntu cd, mainly because i couldnt compile a newer version!) I have managed to install a driver and it will say:

bcmwl5 driver installed

but it doesnt say hardware present, then I use this command to bind it to the hardware:

ndiswrapper -d 14e4:4318 bcmwl5

after trying that it then says

bcmwl5 driver installed, hardware present

but still the hardware doesnt get listed under the networking GUI program in systems>admin.

I have also tried using bcmwl5a but no joy their either! Here is the info about my hardware:

14e4:4318
Chipset: BCM4317 rev02 [Airforce One 54g 802.11g Wireless LAN Controller]
It's a Belkin card and it the drivers on the CD are the bcmwl5/5a ones.

I have read many tutorials on the net to try gain help but there is nothing useful.

Can anyone please help me???

Edit:
I found drivers that the ndiswrapper automatically binds with the hardware!! Still no light on my PCI card and still no way of configuring the card in the GUI app...

---

### Post by ckonrad on 2006-11-07
My card uses the same driver and i was able to get my card to work using this method here, [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

i am using dapper drake not edgy, i wasnt able to get my wireless working in edgy for some reason.

---

### Post by Keithod on 2006-11-08
Hi mate, many thanks for your help. I will try your advice and hope that it works... Again thanks. All help is appreciated.

---

### Post by Keithod on 2006-11-08
OK I got that to work (I think).

The green light comes on my card whcih means network activity however if I go into the web browser it still wont connect to the internet!!! I have entered my network settings by going to Networking and I entered my WEP key and ESSID...

Hope you can help, thanks in advance.

---

### Post by Keithod on 2006-11-10
It does work! It wouldn't connect because of WEP ncryption but I switched that off and now Im using filter by MAC address so great  it works!!!! :) :) :)

---

