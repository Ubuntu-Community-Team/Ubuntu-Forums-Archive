---
title: "How can I change my boot command.........."
date: 2009-03-20
forum: New to Ubuntu
---

### Post by blandman3 on 2009-03-20
**in a previous problem, I couldn't get my ubuntu live cd to run**
eventually I figured out the trick, but do I have to do this everytime I want to run the CD?  

How can I install ubuntu 8.10 and save the commands I have to use in order to get it started so that I can have ubuntu as a partition?

---

### Post by SunnyRabbiera on 2009-03-20
Once the system is installed you wont have to worry, but yes a lot of computers bypass the CD boot to keep users locked in to windows.

---

### Post by supersonicdarky on 2009-03-20
**deleteme**

---

### Post by egalvan on 2009-03-20
In a liveCD, the drive is not touched, so you will have to repeat
the commands every time.
I may be wrong on this, having used the LiveCd very little.
If so, others will correct me, I'm sure.

In a regular install, modifying GRUB's 'menu.lst' file will let you
make the changes permanently.

ErnestG

---

### Post by blandman3 on 2009-03-20
okay, here is the problem:

at the LIVE CD main menu, I must first hit F6, then type at the end of the command string there:

acpi=off noapic nolapic hw-detect/start_pcmcia=false netcfg/disable_dchp=true xforcevesa

this enabled me to run my live cd

before i tried this code, i did have it installed on my computer, but was getting a frozen black or orange screen.  The same for the LIVE CD, until I discovered through trial and error the above combination of command.

So you mean to tell me that if I try to install ubuntu again, I won't have to type this again?

---

### Post by blandman3 on 2009-03-20
okay...........I am very new.

how do I access the "grub", and what necessary steps will I have to do in order to modify the boot menu?

---

### Post by kanikilu on 2009-03-20
> **blandman3 said:**
> okay, here is the problem:

at the LIVE CD main menu, I must first hit F6, then type at the end of the command string there:

hw-detect/start_pcmcia=false netcfg/disable_dchp=true irqpoll xforcevesa

this enabled me to run my live cd

before i tried this code, i did have it installed on my computer, but was getting a frozen black or orange screen.  The same for the LIVE CD, until I discovered through trial and error the above combination of command.

So you mean to tell me that if I try to install ubuntu again, I won't have to type this again? If you install ubuntu again, you can add those options to your /boot/grub/menu.lst once, and then you won't have to manually add it each time.

// Edit - Just saw your other post - to edit the menu.lst file, you can press ALT+F2 and type ```
gksudo gedit /boot/grub/menu.lst
``` enter your password when it asks, edit the file as necessary, then save & close the file

---

### Post by blandman3 on 2009-03-20
That's it?  Great, I will try to do that and give you a heads up when I find something out, although, I have been messing with this thing all day just to get the live cd to work correctly, so I will be logging off pretty shortly.

I appreciate your help, and fast too, LOL!:P

---

### Post by blandman3 on 2009-03-20
it didn't work.

I have installed ubuntu, but when I get to the password and username area, once I input my information, the screen goes orange and stays there.

I can't hit alt F2, the screen is orange, with a cursor, but the system freezes.

Any suggestions on an alternate way to modify the boot?

---

### Post by kanikilu on 2009-03-21
Try getting to one of the other virtual terminals, for instance, CTRL+ALT+F1, then log in to the terminal and you'll have to edit the file from a text editor such as nano, for example ```
sudo nano /boot/grub/menu.lst
```

---

### Post by blandman3 on 2009-03-21
after I press ctrl alt F1, all i have to do is type that command?

---

