---
title: "After installing Ubuntu 11.04(along Win 7), No boot Menu Display"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by lng on 2011-04-29
[SIZE=2]Guys,
I Installed [COLOR=Blue]**UBUNTU 11.04 64 Bit Version**[/COLOR] along[COLOR=Red] [COLOR=Blue]**WINDOWS 7.**[/COLOR][/COLOR]
now on start up a display of an ICON written " **[COLOR=Red]Hz ??[/COLOR]**" - similar to no supply- appears.
i madly tried some keyboard keys & boots to any 1 OS.
either Windows or UBUNTU.
wat to do ??


My System Config : 

AMD Athlon 64 X2 Dual core Processor 4200+ 2.21GHz. 
1GB RAM & NVIDIA Geforce 6150SenForce430 Graphics Driver.  [/SIZE]

[LEFT][SIZE=3][COLOR=Indigo]<<!ng>>[/COLOR][/SIZE]
[/LEFT]

---

### Post by Hedgehog1 on 2011-04-29
Please boot (somehow) into Ubuntu, and then do this to get your grub menu back:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by lng on 2011-04-29
[SIZE=3]Thank u sir,

now Its fixed. :)
earlier it was "[COLOR=Red]\[/COLOR]" which took me to UBUNTU.

[COLOR=Blue]<<!ng>>[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-04-29
Hurray!  Happy Ubuntu(ing)!!!!!

---

### Post by rlmorrisonwy@hotmail.com on 2011-05-01
Don't panic - your grub boot menu may not be displaying!

(Note: I wrote the note below to post before I found this thread.  In short, I came to the same conclusion but solved in a slightly different manner.)

I had a dual boot system with MS Windows 7 and Ubuntu 10.10 using the grub boot loader to select the desired O/S.  I upgraded to Ubuntu 11.04 - but when I rebooted, I had no boot loader menu and Ubuntu automatically loaded.

I did some searching and found the article "Top 10 Tips and Tricks for Ubuntu 11.04" - [http://blog.sudobits.com/2011/05/01/top-10-tips-and-tricks-for-ubuntu-11-04/](http://blog.sudobits.com/2011/05/01/top-10-tips-and-tricks-for-ubuntu-11-04/)
Tip #9 discussed installation and configuration of the startupmanager.  In the startupmanager window I found Windows 7 as an option for the default O/S.  I selected Windows 7 and rebooted - only to find I had booted right back to Ubuntu with no grub boot menu.

It was then I remembered since upgrading Ubuntu, I had been getting a strange message on my monitor that had to do with resolution.  I went back into the startupmanager and changed resolution settings to 1024x768 (instead of the default 640x480) - and when I next rebooted, the grub boot menu displayed.

Still, Windows 7 was not set as the default O/S.  So I looked at \boot\grub\grub.cfg and found a line: set default="7".  In the grub boot menu I noted Windows 7 was the 7th line - but Ubuntu numbers the lines 0-6.  So, I changed "7" to "6" in the grub.cfg file and Windows 7 booted by default on the next restart.

---

### Post by lng on 2011-05-02
[SIZE=2]Thank you sir,
My issue was solved by #2.
I wanted to choose the OS, each time i start & that is Ok for now.
As a Fresher to UBUNTU, your Post on the Issue is definitely Valuable.
Thanks alot .......!!!:KS

[SIZE=3][COLOR=Purple]
**<<!ng>> **[/COLOR][/SIZE][/SIZE]

---

### Post by djmerk on 2011-06-09
total noob here. i had same issue and tried Hedgehog1's solution. works great now. thanks so much.

---

