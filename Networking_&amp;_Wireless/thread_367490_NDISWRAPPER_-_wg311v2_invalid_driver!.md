---
title: "NDISWRAPPER - wg311v2 invalid driver!"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by edjanx on 2007-02-22
Hello all,

First post here, so I appreciate your patience. Over the last two weeks I've tried like crazy to get my wireless working on several Linux distributions. I settled on Ubuntu and am happy with it. However, I have yet to achieve my goal - a stable WiFi connection using WPA upon boot up. I wasted so much time trying to get my native Netgear card's Linux firmware to work (acx111) only to learn that it doesn't support WPA although the card itself does if you use the latest Windows XP drivers (v2.0.0.7) in combination with NDISWRAPPER. 

On to this thread, when I finally beleive I have everything I need to achieve the impossible. [http://ubuntuforums.org/showthread.php?p=1833014](http://ubuntuforums.org/showthread.php?p=1833014)

Problem is, I am getting the following endless loop of frustration below:
edjanx@Ubuntu-Linux:~/Desktop/Driver$ ndiswrapper -l
Installed drivers:
wg311v2 invalid driver!
edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -i wg311v2.inf
wg311v2 is already installed. Use -e to remove it
edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -e wg311v2.inf
Driver wg311v2.inf is not installed.Use -l to list installed drivers
edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -i wg311v2.inf
wg311v2 is already installed. Use -e to remove it
edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -e wg311v2.inf
Driver wg311v2.inf is not installed.Use -l to list installed drivers
edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -l
Installed drivers:
wg311v2 invalid driver!

Can anyone assist before I just give up and go back to Windows and admit I am a Linux failure?

Thanks!
Janx

---

### Post by renzokuken on 2007-02-22
sometimes the XP drivers dont work in ndiswrapper. for my card (which is different to yours) it turned out i had to use the win98 drivers.

---

### Post by edjanx on 2007-02-22
Thanks for the suggestion. :-) Unfortunately, no matter what version I try, I still get this strange, never ending loop:

edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -i wg311v2.inf
wg311v2 is already installed. Use -e to remove it
edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -e wg311v2.inf
Driver wg311v2.inf is not installed.Use -l to list installed drivers
edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -l
Installed drivers:
wg311v2 invalid driver!
edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -e wg311v2.inf
Driver wg311v2.inf is not installed.Use -l to list installed drivers
edjanx@Ubuntu-Linux:~/Desktop/Driver$ sudo ndiswrapper -i wg311v2.inf
wg311v2 is already installed. Use -e to remove it

---

### Post by lunchbox_1973 on 2007-02-22
I hear ya. Same problems for me. Still working on it two weeks later....:(

---

### Post by RomeReactor on 2007-02-22
Hi. Try this

```
sudo ndiswrapper -e wg311v2
```

---

### Post by edjanx on 2007-02-23
Rome Reactor - this worked!! Thank you. Now I get a separate error when trying to load the driver again:

edjanx@Ubuntu-Linux:~/Desktop/Driver_1.2$ sudo ndiswrapper -i wg311v2
Installing wg311v2
couldn't copy wg311v2 at /usr/sbin/ndiswrapper-1.8 line 144.

At least after this I can unload the driver successfully and keep trying:
edjanx@Ubuntu-Linux:~/Desktop/Driver_1.2$ sudo ndiswrapper -l
Installed drivers:
wg311v2 invalid driver!
edjanx@Ubuntu-Linux:~/Desktop/Driver_1.2$ sudo ndiswrapper -e wg311v2
edjanx@Ubuntu-Linux:~/Desktop/Driver_1.2$ sudo ndiswrapper -l
No drivers installed

Regards,
Ed

---

### Post by renzokuken on 2007-02-23
is that the XP driver? some xp drivers dont work, you may have to use a win98 driver (can usually get from manufacturers website). also, is there a .sys file in the same directory as the  .inf file

EDIT, just noticed something

to install you need to add the .inf extension, and to uninstall you leave it off......so the correct install command should be

```
sudo ndiswrapper -i wg311v2[color=red].inf[/color]
```

whereas the correct uninstall option should be 

```
sudo ndiswrapper -e wg311v2
```

---

### Post by edjanx on 2007-02-24
renzokuken, thanks for your observation. However, in my endless tinkering, I beleive that I screwed things up beyond repair, so I'm going to do a fresh install, start over, taking into consideration the help you and others have provided.

---

