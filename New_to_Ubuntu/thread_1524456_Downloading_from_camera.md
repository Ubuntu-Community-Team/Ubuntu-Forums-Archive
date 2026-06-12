---
title: "Downloading from camera"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by ian19jam on 2010-07-05
I possess a new Fuji-film Bridge Camera Finepix S1600 and I am unable to download my photos onto the computer using Ubuntu 10. It won't read the Fuji-film 4GB SD card. It is strange as before I upgraded Ubuntu from 9 to 10 it read the card. Why does the Ubuntu 10 not read this card. I have some valuable photos on this card, especially my niece's wedding and very anxious to down load them without loosing them. Any kind suggestions as to how I can solve this problem please.

ian

---

### Post by Nano Geek on 2010-07-07
Will it read other cards? It might be that the SD card reader was broken during the upgrade. 

Also, most cameras have usb ports. Can you connect via USB instead?

---

### Post by ian19jam on 2010-07-08
It does not read other cards for some reason. I do connect it to the USB port and a camera symbol appears on the desktop. It states it is a USB PTP port. When I open it there is a padlock symbol over the USB PTP and the card does not open It seems that permission has not been granted. Is there any mehtod that can unscramble this locked up card??:)

---

### Post by philinux on 2010-07-08
> **ian19jam said:**
> It does not read other cards for some reason. I do connect it to the USB port and a camera symbol appears on the desktop. It states it is a USB PTP port. When I open it there is a padlock symbol over the USB PTP and the card does not open It seems that permission has not been granted. Is there any mehtod that can unscramble this locked up card??:)

Open a terminal and use 

```
gksu nautilus 
```

You should be able to get access with the root browser.

It might need permissions changing.

---

### Post by ian19jam on 2010-07-08
i TRIED YOUR ADVICE WITH THE TERMINAL AND THE DESKTOP SYMBOL APPEARED AND i CLICKED ONTO IT AND ALL THE DISCS APPEARED INCLUDING THE CAMERA. hOWEVER IT STILL WONT OPEN THE CARD AND SAYS PERMISSION NOT GIVEN. HOW DO I CHANGE THE PERMISSIONS? tHANKS

---

### Post by blur xc on 2010-07-08
Do you have a usb card reader?  Also, I've heard some cameras handle being plugged into a computer different than others- is there a menu option in the cameras setup regarding it's usb port?  Is there a mass storage option?  (I don't recall the exact terms- it's been years since I've messed with that).  

Not exaclty related, but my Sandisk Sanza media player would be recognized by ubuntu either until I changed a usb option in its menu as well.

BM

---

### Post by Goolie on 2010-07-08
> **ian19jam said:**
> i TRIED YOUR ADVICE WITH THE TERMINAL AND THE DESKTOP SYMBOL APPEARED AND i CLICKED ONTO IT AND ALL THE DISCS APPEARED INCLUDING THE CAMERA. hOWEVER IT STILL WONT OPEN THE CARD AND SAYS PERMISSION NOT GIVEN. HOW DO I CHANGE THE PERMISSIONS? tHANKS

Unfortunately, my knowledge of Ubuntu is too small to offer any sort of practical Ubuntu help.  But I do know that some supermarkets, etc., do take SD cards and print / save the pictures to a CD for you.  Not the best answer, but I figured it might be an option because you have alot of important pictures on there.  Good luck, mate.

---

