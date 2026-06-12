---
title: "Display problems"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by SwatKat on 2009-11-13
Hey all,
Ubuntu leaves about 2 centimetres of screen blank at the top, bottom and sides(each). I get a full screen display in windows and Suse . I cant get the desktop visual effects working either. My current resolution is  1064*768 ant the maximum available resolution is 1152*864 (which makes the letters look tiny and cramped). 

My display card details are:

description: VGA compatible controller
                product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:f8000000-fbffffff(prefetchable) memory:fd000000-fdffffff memory:feaf0000-feafffff(prefetchable)

Is there any way I can get a full screen display, any free driver that I can install ? Any help would be much appreciated, thanks.

---

### Post by ukripper on 2009-11-13
Check this thread - [http://ubuntuforums.org/showthread.php?t=1316933](http://ubuntuforums.org/showthread.php?t=1316933) you will get good idea about VIA graphic chipsets

Here is wiki for VIA - [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

goodluck!

---

### Post by SwatKat on 2009-11-13
> **ukripper said:**
> Check this thread - [http://ubuntuforums.org/showthread.php?t=1316933](http://ubuntuforums.org/showthread.php?t=1316933) you will get good idea about VIA graphic chipsets

Here is wiki for VIA - [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

goodluck!

Thanks for the links :)
So, now I have downloaded and saved the tar file . The wiki says, [B]Make a backup of your xorg.conf.

[/B]But when I runsudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
I get

cp: cannot stat `/etc/X11/xorg.conf': No such file or directory

Could someone guide me through the installation, please?

---

### Post by coldReactive on 2009-11-13
> **SwatKat said:**
> Thanks for the links :)
So, now I have downloaded and saved the tar file . The wiki says, [B]Make a backup of your xorg.conf.

[/B]But when I runsudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
I get

cp: cannot stat `/etc/X11/xorg.conf': No such file or directory

Could someone guide me through the installation, please?

9.10 uses autodetection for xorg conf. By default; when installing new drivers that aren't in jockey, a new xorg.conf is created. Unlike ATI though I believe, nvidia checks other non-etc directories for conflicting xorg.confs then backs them up.

---

### Post by SwatKat on 2009-11-13
> **coldReactive said:**
> 9.10 uses autodetection for xorg conf. By default; when installing new drivers that aren't in jockey, a new xorg.conf is created. Unlike ATI though I believe, nvidia checks other non-etc directories for conflicting xorg.confs then backs them up.

Okay, please help me understand here. I am a complete newbie. So you are saying that I dont need to backup and should just go ahead with the installation?
Again, could someone guide me through the installation process please? most of the information obtained by googling is usually outdated.

---

### Post by ukripper on 2009-11-13
> **SwatKat said:**
> Okay, please help me understand here. I am a complete newbie. So you are saying that I dont need to backup and should just go ahead with the installation?
Again, could someone guide me through the installation process please? most of the information obtained by googling is usually outdated.
 copy paste in terminal it will back it up for you:
```
sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by SwatKat on 2009-11-13
> **ukripper said:**
> copy paste in terminal it will back it up for you:
```
sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

I'm getting

cp: cannot stat `/etc/X11/xorg.conf': No such file or directory

---

### Post by ukripper on 2009-11-13
> **SwatKat said:**
> I'm getting

cp: cannot stat `/etc/X11/xorg.conf': No such file or directory

i think your xorg.conf doesn't exist because the new X server doesn't need an xorg.conf file anymore and getting the devices from dbus

You can go ahead with the tar install as you were doing. if something happens we can fix it but make sure you have important data backed up in case.

---

### Post by SwatKat on 2009-11-15
Okay,
I botched up the installation. Now I get a horribly flickering screen, and ubuntu wont boot. Is there anything I can do now, other than reinstall?

---

### Post by ukripper on 2009-11-15
> **SwatKat said:**
> Okay,
I botched up the installation. Now I get a horribly flickering screen, and ubuntu wont boot. Is there anything I can do now, other than reinstall?


you can boot normally and once it reaches login screen just pres CTRL + ALT +F2 this will take you into tty and from there you can get rid of /etc/X11/xorg.conf by following command:
```
sudo mv -v /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

after that just reboot again by typing below command:
```
sudo reboot now
```

---

