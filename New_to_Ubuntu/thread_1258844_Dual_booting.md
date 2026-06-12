---
title: "Dual booting"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Miscible21 on 2009-09-05
Okay, so I asked something along these lines before but I just need some clarification. I have just installed Jaunty on a second hard drive, and i am running XP on a my primary hard drive. The install went well but I have not attemped a dual boot yet. I just keep unplugging the drives according to which OS i would like to boot into. This is kind of stupid, so I would like to attempt a dual boot. What exactly do I do?

Is it safe to plug both hard drives in and go into the bios settings when my pc boots up? Will this affect grub? or will ubuntu affect the boot settings in my windows drive? Really not sure about this...:confused:

---

### Post by arochester on 2009-09-05
Look at [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by Paqman on 2009-09-05
When you install the system, did you have both drives plugged in? IF so, Grub will have detected both OSes and you'll be able to boot into either just by picking them.

If not (ie: you don't have a Windows option in Grub), then you'll have to add a Windows entry to Grub manually.

---

### Post by Miscible21 on 2009-09-05
> **Paqman said:**
> When you install the system, did you have both drives plugged in? IF so, Grub will have detected both OSes and you'll be able to boot into either just by picking them.

If not (ie: you don't have a Windows option in Grub), then you'll have to add a Windows entry to Grub manually.
No i took the XP hard drive out just incase I made an oopsie.How do I add a windows enrty into GRUB mannually?

---

### Post by LewRockwell on 2009-09-05
plug both drives in making sure that any jumpers are correctly set

you might check to see that your BIOS recognizes both hard drives

you'll probably find that the Super Grub Disk will assist you in fixing this and any other grub questions/problems you might encounter in the future

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by nothingspecial on 2009-09-05
> **Miscible21 said:**
> No i took the XP hard drive out just incase I made an oopsie.

Sensible idea.

As I don`t and never have had windows, I`m loath to instruct you directly but have a look at these 2 links.
[URL="http://members.iinet.net/~herman546/index.html"][COLOR="Magenta"]
Herman`s[/COLOR][/URL]

[[COLOR="Magenta"]super grub[/COLOR]]("http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems")

---

### Post by Bartender on 2009-09-05
Miscible -
AFAIK all modern BIOS'es will respond to a certain keystroke as the PC is booting up.  BIOS pauses, you get a screen that lists all the bootable devices that BIOS detects, you arrow up or down to the one you want, Enter and you're off to the races.  This is NOT the same thing as going into BIOS and changing the boot priority.
I don't remember which key mine was, as I haven't done it like this in a while.  Post your PC and/or BIOS and someone should know.

This is a great technique for someone who's done as you did, installing Ubuntu and the Linux bootloader entirely to a second drive.

A quick google search indicates F8 is the most common key.  I think that's what mine was, because you have to tap on F8 BEFORE Windows starts to load.  Once Windows gets going, F8 brings up Safe Mode.

---

### Post by louieb on 2009-09-05
> **Miscible21 said:**
> No i took the XP hard drive out just incase I made an oopsie.How do I add a windows enrty into GRUB mannually?

I did the same thing 1st time I set up a dual boot. Can't screw it up if its unhooked. 

Connect both so that it boots to Ubuntu.    

then to edit the grub menu press <alt+F2> (run dialog) and enter ```
gksudo gedit /boot/grub/menu.lst 
```try this for the windows entry. paste it  to the very bottom of the file.
```

title Win XP  
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1

```Might need a little tweaking - I just assume XP is on the 1st partition.

---

### Post by Miscible21 on 2009-09-06
Thanks to everyone who repleid to this post. I am happy to say that after reading everyones replies and following the links you posted I found the best solution and I think i have accomplished a dual boot :D

When i switch my pc on it now gives me various ways of starting up Ubuntu and right at the bottom i have the option of booting into windows xp. If this is a dual boot then my problem is solved. Thanks everyone!

---

### Post by nothingspecial on 2009-09-06
Excellent :guitar:

---

