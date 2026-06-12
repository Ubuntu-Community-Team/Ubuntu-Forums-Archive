---
title: "Problem updating to 9.10, computer froze"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by jimhoff on 2009-10-24
Last night I ran the update program, updating from 9.4 to 9.10. The program was downloading the updates and said it would take seven hours so I let it run all night and didn't look at it for about 24 hours. When I got back today the computer was frozen on a step asking about changing the boot process or something (I think it was upgrade from grub to grub2 but cannot be sure. I did a hard reboot on the system by removing the battery. When it loaded back up I was able to boot into Ubuntu and the system information lists the OS as 9.10. But my trackpad mouse and associated buttons do not work, but the nub mouse and those buttons do work. The system is also running incredibly slow. I opened up System Monitor and it shows the first CPU (dual core) running at around 5-7 percent, but the second one in running at a constant 100%, even when I am idling. 

I'm not sure if this is 'normal' with an upgrade and I just need to change settings to make it work, or if the associated problems I am experiencing have to do with rebooting before installation was completely finished. 

Any advice? I'm not sure if I can run the update manager again and have it finish the process or something else might be done. Thanks!

---

### Post by Dark_Stang on 2009-10-25
No... something got screwed up. I'd recommend a fresh install at this point. That's usually the better option to begin with.

---

### Post by coolbrook on 2009-10-25
Do you have the facility to download and burn a Karmic CD?  When you boot it, there's a menu option to 'rescue a broken system' or something along those lines and that might help.  Someone with experience can shed light for us.

Dark_Stang is probably right.  You can back up whatever data you need and consider a clean install.

---

### Post by Dark_Stang on 2009-10-25
> **coolbrook said:**
> Do you have the facility to download and burn a Karmic CD?  When you boot it, there's a menu option to 'rescue a broken system' or something along those lines and that might help.  Someone with experience can shed light for us.

Dark_Stang is probably right.  You can back up whatever data you need and consider a clean install.
I haven't used a full disc in a while. So that rescue option may be worth looking into. I'm kinda old school when it comes to OS issues and I keep my data on a separate partition so... I'm all about reinstalling.

---

### Post by jimhoff on 2009-10-25
I was afraid of that. I'll try the rescue option and if that fails just do the clean install. 

Two questions on the clean install: Do I need to format the partition that ubuntu is currently on before hand? Also, is there any way to backup the customization (default programs, styles, etc.) so with the new install will look much like the old without me retweaking everything?

---

### Post by Dark_Stang on 2009-10-25
You don't need to reformat but one of the major advantages of 9.10 is the use of Ext4, so it is recommended. You could dump everything to another machine or an external hard drive, then reformat, and copy it all back over. Or, if you have a separate partition for /home you could just reformat your / partition for now and worry about /home later.

---

