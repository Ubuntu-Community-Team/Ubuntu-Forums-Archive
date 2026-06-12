---
title: "Gnome Crash (liveCD)"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by mastablasta on 2010-08-13
On this computer only LXDE (Lubuntu) works with no problems it seems. XFCE (Xubuntu) crashes completelly.

Gnome (on liveCD) has this to say:
[http://yfrog.com/3uscreenshotguop](http://yfrog.com/3uscreenshotguop)

What could be causing this? I could otherwise do things normally on it (just slow due to low ram). And obviously i lost the whole bottom pannel. the line was still there but programmes weren't showing.

---

### Post by Paddy Landau on 2010-08-13
How much RAM do you have?

Lubuntu is significantly lighter than Xubuntu, so you may want to stick with Lubuntu.

---

### Post by mastablasta on 2010-08-14
still 256MB (229MB actually), but GNOME in live session takes about 120-140, so there should still be enough. mainly live session seems to be slow cause CD drive is probably low speed.

I just found out yesterday that in Lubuntu sound volume buttons are not working (though i can still reduce it with the sound preferences). also if we can believe the baterry monitors, the GNOME was showing 2h15m left, while Lubuntu said 1h30 min left. So i was thinking in all to try gnome and try and get it as light as possible. for soem strange reason Lubuntu only allows to reduce monitor brightness to a certail level. which is slightly darker, but not more...

apparently Debian Lenny is lighter than ubuntu (also showing less than 100 MB ram, maybe more options than LXDE?!), however after downloading and running it i found out i got the wrong CD. apparently LiveDebian is a whole different project.#-oATM i ran out of empty CDs.

Anyway i am just afraid something else might not be working as it should in Lubuntu. i already saw there might be some issues using different character in PCMan0.95 that Lubuntu uses.

---

### Post by Paddy Landau on 2010-08-14
Apparently, it's possible to "convert" Ubuntu to Lubuntu by downloading the right packages and window manager. I don't know how to do that, so search this forum; I saw it described recently. It may help your problems with the sound, etc.

Alternatively, you may find it easier to live with Lubuntu and its minor problems. Report the problems to the Lubuntu team so that the members are aware of them and can fix them.

Be aware that Lubuntu is still beta. The team members are hoping that Lubuntu 10.10 (due in three months) will be a full release, approved by Canonical -- but they need error reports to be able to progress. You could help with that.

---

### Post by mastablasta on 2010-08-16
well after trying the Debian Live which worked really really fast, but also crashed (probabyl because it was live?!) i decided to install Ubuntu to see where it would take me. deleted the whole windows disk (including recovery partition - ups!). and so far it works ok. i change the theme to lighter one, removed the background pic. but i haven't got a chance to really test it. OOo loads slow but after it loads it seems to work ok. computer boots in 1 minute. sound buttons work, Fn buttons work, sound works, movies play ok, mic doesn't work, but i am not sure there is a mic on this computer... super. still i find it still a bit slow i am switching to Debian. If that one is still too slow then Lubuntu :-)
 
only thing that doesn't work and is bothering me a bit is hibernation (or at least some sort of sleep mode). i wonder if there is a way to fix that. also there are a few more buttons above keyboard that don't work, but i wonder if one could make them work. such as for example e-mail button (to launch evolution) or help button to lunch help or suspend (windows sleep button). will post this in a new thread since it's a separate issue.

---

### Post by Paddy Landau on 2010-08-16
> **mastablasta said:**
> OOo loads slow...
This will happen on slower computers. Lubuntu uses Abiword by default, but you can install OpenOffice if you want.

> **mastablasta said:**
> only thing that doesn't work and is bothering me a bit is hibernation (or at least some sort of sleep mode).
How big is your swap partition? With 256Mb, I'd recommend at least 512Mb swap, preferably 1Gb for safety.

> **mastablasta said:**
> ... buttons above keyboard that don't work, but i wonder if one could make them work.
Go to System > Preferences > Keyboard Shortcuts. Click on Launch e-mail client (under Desktop) and press the key that you want to launch it. You can do the same thing for other items listed there, e.g. Help browser.

---

### Post by mastablasta on 2010-08-16
i know about office, but i need office for functional ocmputer.
 
Swap is i think 3GB now or maybe even 4. since disk is 20GB and it says in system monitor that arround 4 GB out of 17 is occupied.
 
thanks about the keys tip i will have to try it later when i get home.

---

### Post by Paddy Landau on 2010-08-16
> **mastablasta said:**
> Swap is i think 3GB now or maybe even 4. since disk is 20GB and it says in system monitor that arround 4 GB out of 17 is occupied.
Open a terminal and type the command:
```
sudo parted -l
```Post the results here.

---

### Post by phillw on 2010-08-16
If you're on a system with 256MB RAM (and using part of it for graphics), you are pushing the Ubiquity installation. A couple of things to try.
1) Check the ISO file you downloaded and the CD you burned --> [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/CheckCD](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/CheckCD)
2) Try the minimal installation route --> [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall)

As noted above, if you want to use OpenOffice, you will need a decent sized swap partition. The reason lubuntu uses abiword and gnumeric is because Open Office needs a lot of RAM to run, as you do not have much it will run slowly.

In addition to posting up the result of ```
sudo parted -l
``` would you also post up the result of ```
free
```
See [About LXTerminal](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/LXTerminal) for how to type in commands.

As also noted, lubuntu is a real small team. If you have specific queries about it please do take a few minutes to [Join the mailing list](https://wiki.ubuntu.com/Lubuntu/GettingInvolved) 

You can find out more about Lubuntu by following the links in my Signature.

Regards,

Phill.

---

### Post by mastablasta on 2010-08-16
ok thanks for all the suggestions, however i currently have Ubuntu (GNOME) installed. Lubuntu still has some drawback, however it ran very fast (even on live) and very good (appart from a few issues). 
 
IF Ubuntu prooves to be too slow (and the same goes for Debian) i will wait for Lubuntu 10.10 and put it on as i simply admired the Live CD speed it brought. not to mention that of all distros i tried in live session (and it was many) Lubuntu was the stable one. 
 
However i still went with Ubuntu for now (pelase see the Lubuntu issues i found menitoned above).
 
Backing up the data won't be such a problem as i bought a large disk for backups. Plus there is always additional (though not so secure) DVD backup.

---

### Post by Paddy Landau on 2010-08-16
> **mastablasta said:**
> ... i still went with Ubuntu for now...
You still need a decent swap area. Please do post the results of the following two commands.
```
sudo parted -l
free
```

---

### Post by mastablasta on 2010-08-16
```
Model: ATA HITACHI_DK23DA-2 (scsi)
Disk /dev/sda: 20.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  19.3GB  19.3GB  primary   ext4            boot
 2      19.3GB  20.0GB  701MB   extended
 5      19.3GB  20.0GB  701MB   logical   linux-swap(v1)


.......


             total       used       free     shared    buffers     cached
Mem:        234480     230292       4188          0       8224      77364
-/+ buffers/cache:     144704      89776
Swap:       685048      10848     674200

```

Here is the info.

I couldn't get the keys to work though....When i press them in the settings nothing happens. so the only keys that do work are for sound. i am attachign a few pics...

Also hibernation works, suspend doesn't (computer can't recover from it). strange. Battery life is same or perhaps even better than in windws.

I also installed printer via samba (printer is on WinXP computer) but i am not sure why i need to type in the password every time i print. :o it doesn't do this on other Linux computer.

---

### Post by mastablasta on 2010-08-19
I'm gonna **bump** this one in the hope that someone knwos how to use / set up the keys that are not working at the moment.

---

### Post by Paddy Landau on 2010-08-19
Glad you bumped; for some reason I didn't see your last post.

We have some clarity, then. Your swap area is 701Mb, which should be more than sufficient for hibernation. You have said that hibernation does work, so that's OK.

I don't know about the suspend. I can only guess it's something to do with the ACPI. Sorry, I know very little about this, but you can experiment with the options, either [FONT=Courier New]pci=noacpi[/FONT] or [FONT=Courier New]acpi=off[/FONT] when you boot. If that works, you can make it permanent. Please search the forums for how to do this, because I don't remember how.

Regarding why the keys you indicate don't work, you may need to contact the Lubuntu team. I have no knowledge in that area.

Post again with any problems.

---

### Post by mastablasta on 2010-08-19
Thanks for response. Maybe the ACPI could clear my other computer susped issue that just appeared.
 
Actually i have Ubuntu 10.04 instaleld as more of the upper keys work with it. Also some other things...

---

