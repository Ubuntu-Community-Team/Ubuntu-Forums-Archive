---
title: "laptop boot priority"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by jameshadzess on 2011-04-30
My Toshiba P500 laptop seems to be only able to set the boot priority using a Toshiba application that works within the windows environment. So when I go to start Ubuntu 10 it first checks the optical drive before going to the hard drive as this is how I set it up before installing Ubuntu. And this takes a long time. Does anyone know how to reset the boot priority using the Ubuntu operating system. Note: Toshiba makes three classes of laptops, the other two can be reset using the CTRL key and a f#. But not the P 500. Clear? I am hoping some type of terminal command could be used. Thanks. Jim H.

---

### Post by Lateralis on 2011-04-30
Boot order is a BIOS setting and isn't one you can set using a program in an OS.  Some motherboard manufacturers, e.g. Asus, have made Win programs that allow you to flash the BIOS and do other BIOS-related tasks from within Windows but they are not in the majority.  I personally am very twitchy about allowing an OS to edit the BIOS, but that's just me. 

There will be a key that you can hit when the BIOS is posting to screen.  On most computers this will be either escape, delete or an f#.  On my laptop it is F2; on other systems it may be F10 or F12.  I would consult online information specific to your laptop or your laptops manual if you don't know which key to press for your laptop.

---

### Post by jameshadzess on 2011-04-30
I tried both F1 and F12 keys during POST as directed by the Toshiba Tec. support. All you get is loud error beeps. It seems model P500 needs the Toshiba app. to access the bios.

Maybe I can download the Toshiba application downloader into WINE, since it only works with a windows environment, and use it to reinstall the Toshiba BIOS access application. All this for a stupid little graphic interface. Ug! 

Anyone out there having real experience with this problem on the P500 Toshiba Laptop. I would appreciate hearing from you.

---

### Post by Miljet on 2011-04-30
I have been working on personal computers since 1985 and have never seen any computer that would not allow you to access the BIOS during POST (Power On Self Test). It is just a matter of finding the right key and pressing it at the right time. I am using a Toshiba P205 laptop and the correct key is F2.

I don't think that changing your boot order is going improve your boot time. The time it takes the system to check the CD drive for a bootable disk is miniscule.

---

### Post by jameshadzess on 2011-05-01
People just don't seem to believe me on this one, but if you go to the "Toshiba BIOS Access Instructions" for the P500BT2N20 or talk to the Toshiba Tec assist people and then try all the key combinations during POST and only get error beeps... The only method seems to be using Toshiba Console to run the Toshiba Hardware Utility within Windows 7. 
  
  After a quick screen showing data for the CPU, HD, etc, the Laptop takes 20 seconds with a blinking underline in the left top corner before deciding to resume normal start up. If I have a DVD or CD in the optical drive I get a "cannot read file message" at this point for 20 seconds before it starts as usual so I know its going to the optical drive first. And on my desktop build where I could easily set the boot priority the startup was fast. My previous two Toshiba laptops with Ubuntu did not have this problem. 

I think this very weird. What do you think? Jim H.

---

### Post by eriktheblu on 2011-05-01
I'm actually not finding anything on BIOS access for that model.

A consumer computer company's tech support shouldn't be confused with experts. Dell's tech support tried to sell my cousin a new motherboard for a problem fixed by a BIOS update. Seriously, I trust random guy on the internet more than I do their tech support.

It typically won't be a key combination, but try all the F keys, Esc, and Delete as well.

---

