---
title: "Trouble installing drivers for wireless ethernet card"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by snoopunit on 2011-05-17
So i took an old HDD that i had and i decided to wipe it and install Ubuntu from a cd i had. Everything went very well, except i can't figure out how to get my ethernet card to work. I was looking at a thread yesterday and it had a nice in-depth tutorial on my exact card, but none of the solutions that were suggested worked. I may have installed the wrong .inf or something the first time, because the install went fine. After restart, it still didn't work. I believe the files i am looking for are bcmwl5.inf/.sys ? it's a belkin wireless card, but i can't get the exact information at the moment, i'll post the specific card information when i get home, but right now im still in school. just wondering if anyone else had a similar problem and could suggest another solution for me

---

### Post by seawolf167 on 2011-05-17
Before you try to manually use the bcm cutter and extract drivers to install, try physically plugging in your ethernet card and going to System -> Administration -> Hardware Drivers and seeing if you can install drivers for your card. Use the STA drivers versus the B43 drivers if given a choice.

---

### Post by snoopunit on 2011-05-17
well the problem is that it's a pci card.. not usb. Should i try reinstalling without the card plugged in or something?

---

### Post by seawolf167 on 2011-05-17
No, make sure you have the card plugged in when you start your computer so the system recognizes that the card is in the PCI slot. Then when it boots and you have internet access (with a physical cable), it should be able to detect your card make and model and display any available drivers for it under the Hardware Drivers section.

---

### Post by snoopunit on 2011-05-17
oh, alright. that seems a hell of a lot simpler than what i was trying to do :D is there a way i can connect through another computer thats running windows? i can connect directly to the router if i need to, it's just gonna be a hassle that's all. I have a laptop that would like to bridge a connection or something, but i dont know much about that at this point

---

### Post by seawolf167 on 2011-05-17
It would be ***way*** easier to directly connect to the router - it should only be a one-time thing. After the drivers get installed you should be good to go to disconnect the physical connection and enter your router's SSID/passphrase info and have a wireless connection active.

---

### Post by snoopunit on 2011-05-17
alright, i might as well then. i should probably uninstall the ndiswrapper-utility and bcmwl5 drivers beforehand, right?

---

### Post by seawolf167 on 2011-05-17
If you can yea

---

### Post by snoopunit on 2011-05-17
ok, so i have my desktop plugged into the router, but when i go to hardware drives it says it cant find anything

---

### Post by snoopunit on 2011-05-17
sry for double-post. i updated to ubuntu 10.04, and it now provides the option to install B43 drivers, but i can't find anything related to STA drivers. do you know where i might be able to acquire them?

---

### Post by seawolf167 on 2011-05-18
The STA drivers are the new versions since Broadcom released their device(s) info. If it doesn't show up in the Hardware Drivers, you can use the B43 drivers instead and it should work.

---

