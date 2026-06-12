---
title: "NVIDIA 96.43.19 installed, xorg.conf may have altered settings?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by g-money on 2010-12-22
[FONT=Arial]After a full week test driving Ubuntu, Fedora, and Puppy… then Ubuntu… then Fedora (in where I learned more about NVIDIA driver installation, linux syntax, and was able to compare other distros' “out of the box” drivers and applications)…….. then full circle back to Ubuntu 10.10. [/FONT]
 
[FONT=Arial][FONT=Arial]As I ponder here at work, Im noticing a gradual addiction to Linux… always went the Microsoft way instead of Apple, and now I’m moving away from Microsoft to Linux based distros. I know I’m a late bloomer / newbie, and wishing I learned more Linux from the very start.[/FONT]
 
Enough of the introduction, and here goes my rant:
 
[FONT=Arial]I believe the 96.43.19 driver is installed about 90% of the way. The installation process overwrote the original xorg.conf file (which is backed up as well). The pc did reboot to a pretty desktop with a higher resolution than 800x600… problem is the task panel and program menus were missing, the desktop was literally bare (could only see the mouse cursor and wallpaper). Strange part was I rebooted again, and task panel / programs appeared however without the wireless icon, I noticed here the system booted as “guest.” Anyhow, I rebooted once again and it went back to the nice resolution desktop with only wallpaper and the cursor – Im suspecting the xorg.conf installed by NVIDIA (NVIDIA-Linux-x86-96.43.19-pkg0.run) is causing this, luckily the installer reconfirmed it would create a backup.[/FONT]
 
[FONT=Arial][FONT=Arial]Here’s what I have _planned_ when time opens up at home, hopefully I’m headed in the right direction… Input, caution, any advice is appreciated:[/FONT]
 
**[FONT=Arial]//Browse for backup file[/FONT]**
[FONT=Arial]Sudo cd /etc/X11[/FONT]
 
**//Stop X server console**
sudo /etc/init.d/gdm (or gdm) stop
sudo /etc/init.d/gdm (or gdm) start [FONT=Wingdings][FONT=Wingdings]ß[/FONT][/FONT] For Later
 
[FONT=Arial]**//Backup the current xorg.conf**[/FONT]
[FONT=Arial]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.new_backup_name[/FONT]
[FONT=Arial]**[FONT=Arial]//Restore the xorg.conf_my_backup_name file [/FONT]**
sudo cp /etc/X11/xorg.conf.orginal_backup_name /etc/X11/xorg.conf
 
[FONT=Arial]**//Edit/Manually configure the _restored_ xorg.conf **[/FONT]
[FONT=Arial]Before restarting X, can I manually edit xorg.conf through the start up console (via nano/gedit)? Instead, I was thinking of rebooting (hopefully successfully w/ the restored xorg.conf), then use nano/gedit to configure the restored file to include the following..[/FONT]
[/FONT]
[FONT=Arial](Per NVIDIA documentation…)[/FONT]
 
[SIZE=3][FONT=Times New Roman]Remove the line:[/FONT][/SIZE]
Driver "nv"
(or Driver "vesa")
(or Driver "fbdev")
 
[SIZE=3][FONT=Times New Roman]and replace it with the line:[/FONT][/SIZE]
Driver "nvidia"
 
[SIZE=3][FONT=Times New Roman]Remove the following lines:[/FONT][/SIZE]
Load "dri"
Load "GLCore"
 
[FONT=Times New Roman][SIZE=3]In the [/SIZE][/FONT]Module[SIZE=3][FONT=Times New Roman] section of the file, add the line (if it does not already exist):[/FONT][/SIZE]
Load "glx"
 
[FONT=Arial]After the file is saved, reboot.[/FONT]
 
[COLOR=black][FONT=Arial]Its crunch time as Christmas is only around the corner, I can't guarantee more testing tonight but would like to post results asap... hopefully some feedback could expedite my projected procedure so I don’t keep my baby girl in front of Linux commands any longer.[/FONT][/COLOR]
 
[FONT=Arial]Thanks an advance! and apologies for the newbie language![/FONT]
 
Update:
Forgot to add, Ubuntu10.10 was installed in a Gateway Profile PC (3.06GHz P4/512RAM/NVIDIAGeForce4 MX400): 
[/FONT][/FONT]

---

### Post by bwhite82 on 2010-12-22
Did you run Nvidia's xconfig utility? The driver installation itself creates no xorg.conf. You need to run that utility separately after the install to generate a new xorg.conf:

```
sudo nvidia-xconfig
```

---

### Post by g-money on 2010-12-22
@Soldierboy.. I will definitely try that first!  
 
was under the assumption the installation process covered the xconfig utility (given it prompted me to overwrite and automatically created a backup - just not sure if it was xorg.conf)
 
I will post results as soon as i can... many thanks!

---

### Post by g-money on 2010-12-23
Results:

Note, PC had been off for almost 20 hours.

Pressed the power button...

And viola... a rich desktop appeared without issues.

I wont question how it happened. Probably a good laugh for some of you after reading my long rant.

Thanks.

---

