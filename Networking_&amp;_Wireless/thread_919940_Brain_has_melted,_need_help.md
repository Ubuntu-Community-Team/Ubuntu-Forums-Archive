---
title: "Brain has melted, need help"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by jammin2222 on 2008-09-14
Hi all

I have just installed ubuntu 8.40 on my old laptop. I have been trying to connect to my wireless network using a Belkin notebook card F5D7010 version 3000uk with no real joy.
 
The card lights up and it shows my wireless networks name, but it wont accept my network key. I have even disabled wep all together but still nothing. I have read the thread "HOWTO: RT2500, etc. wireless cards" and think this is the way i need to go but whats with all the typing random stuff into the terminal? 

Also how can i download the driver without an internet connection on the laptop as in the "HOWTO: RT2500, etc. wireless card" thread it says download it using synaptic packet manager? I cant, i dont have wireless card working yet, gerrrrr. and i dont need the driver on the pc with the working wired connection im writing this plea for help on. (laptop has no wired lan socket)
 
Cant i download a file to my usb memory stick,plug it in the laptop and double click on the file and a driver for my wireless network card starts to install? Its couldn't be that simple could it?

---

### Post by lswb on 2008-09-14
Belkin unfortunately has used more than one chipset for this model card, it may not really have the RT2500. Try plugging in the card, then run the command "dmesg" in a terminal. Near the bottom of the output of dmesg you should see some info about the card. Do you see any that identifies the chipset?

---

