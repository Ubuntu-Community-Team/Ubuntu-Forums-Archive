---
title: "ubuntu installation"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by mark6241 on 2009-03-25
Hi, I have installed ubuntu via wubi several times and cannot get past logging in. After logging in all I have is a curser and have to do a hard shut down. I have the newest directx, Dell deminsion 2400, 80 gb hard drive, and 2 gb ram, xp sp3 home edition. Any help with this would be appreciated.

Thank you,
Mark
[email]mark6241@comcast.net[/email]

---

### Post by cariboo on 2009-03-25
Either your video card or you monitor isn't getting detected properly. Start in recovery mode and at the menu select xfix, when it is finished select resume, and you should get back to your desktop. TO load the restricted drivers for your video card, go to System-->Administration-->HArdware Drivers.

Jim

---

### Post by mark6241 on 2009-03-26
Thanks Jim but after 8 hours of up dating drivers that did not need it and uninstalling and reinstalling I am still where I was yesterday. I do appreciate the effort though. i give up for now.

Mark

---

### Post by LowSky on 2009-03-26
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)
> Hangs with desktop effects on Intel 830MG and 845G video cards
There is a bug in the Intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and will freeze the system. For new installations, please install using the safe graphics mode (press F4 in the startup screen) on these systems and disable desktop effects via System -> Preferences -> Appearance, clicking on "Visual effects" and choosing "None". 


Intel 845GV is your video chipset and it beahves badly, not your fault but it does, but there is a fix. Now follow my instructions carefuly and we might get things working. Since you used Wubi (I personally dislike) we need to do this this way.

boot into recovery mode, choose the option for command prompt
log in then type this out

```
sudo nano /etc/X11/xorg.conf
```

find a line that looks similar to this (note this is someone elses it will not be exact

```
Section "Device"
Identifier "Intel 845"
Driver "i810"
BusID "PCI:0:2:0"
VideoRam 8000
Option "UseFBDev" "true"
EndSection
```

change Driver "i810" to "intel"

then save and close

then type
```

sudo apt-get install xserver-xorg-video-intel

```

reboot and it should work

---

### Post by mark6241 on 2009-03-26
ok thanks, i will let you know how it goes

mark

---

### Post by mark6241 on 2009-03-27
Thanks very much,

Installing in safe graphics mode did the trick. :)
Hope your day is a good one.

Mark

---

### Post by mark6241 on 2009-04-08
Ok thanks for your help in the past and I was really enjoying my new os until now. All of a sudden I have no network connection! I used it early this am and all was fine. It says firefox is running in 'offline' mode, switch to online mode!! Ha....what the hell is this all about and how do I do that? Why would it be in offline anyway? As you can see I am online now so there is not a connectivity issue. It works fine in windows. I tried re-booting in repair mode but same problem. I really do not want to get rid of ubuntu because it is great for what I do but do not have the time or patience for this. Any help would be appreciated.

Thanks,

Mark

---

### Post by Jakey_TheSnake on 2009-04-08
What does your network monitor applet on the taskbar say? 

If it's not there, run:

```
nm-applet &
```

Are you connecting wirelessly, or wired?

Funnily enough, I have the reverse problem, Ubuntu recognises all network connections automatically, but Windows is being an a-hole about them.

---

