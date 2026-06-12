---
title: "access to xfce desktop lost"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by liatodua on 2011-02-05
Hi

I have ubuntu OS with xfce desktop installed in addition (my old laptop was very slow with standard ubuntu. Xfce was fine). Today I wanted to change appearance of the windows and was trying the different options in the windows menu, just one by one and when I almost reached the end of the list, computer logged out and since than it does not allow me to enter xfce any more. It kind of does not accept my password to enter the xfce session. But I have the same password for ubuntu standard and it works.

What could have happened? And how to return my xfce now?

---

### Post by liatodua on 2011-02-05
Tom - no answer. Ok. I'll try to uninstall and reinstall xfce...

---

### Post by liatodua on 2011-02-06
I uninstalled xfce4 (from software center) and installed xubuntu desktop. The things only got worse - It seems you can not really uninstall anything in ubuntu. Although the software center showed that xfce4 is uninstalled the relevant logging option still stayed there. And in addition xubuntu desktop added. Although it was also inaccesible.  And uninstallation of the later did not change anything. I tried to install xubuntu desktop and ended up completely banned from changing log-in screen ('unlock' button become unresponsive).

So I ended up completely stuck with default ubuntu desktop. Which seems to be very heavy for my laptop. So I had to give up with ubuntu. Now trying lubuntu instead.

---

### Post by cascade9 on 2011-02-06
You can unistall with ubuntu. 

Your problem is because there is a a hidden folder with the xfce4 settings in it (.config/xfce4). When you installed xubuntu-desktop it (probably) tried to use the settings from that folder, and so it didnt work either. 

I'd love to know what setting you were playing with when that happened. If you dont remember thats cool, I'm just wondering.

---

### Post by XubuRoxMySox on 2011-02-06
It wouldn't let you choose an Xfce **session** at login? You might have had the "default" set to Gnome, or auto-login.

I hear all kindsa good things about Lubuntu now, but I decided I very much prefer Xubuntu and all the sweet li'l panel apps like analog clock and weather. Seems much more customizable than the LXDE panel.

You can always just get Xubuntu and install it...

-Robin

---

### Post by liatodua on 2011-02-06
I'll try to run ubuntu live CD to recall what setting I chosed which did this thing. Will be back.

---

### Post by liatodua on 2011-02-06
My laptop is quite old and I understood that I should be looking for light versions of OS. I am not sure that xubuntu is light. And when I tried to download the installation package it said it needed 4 hours. So I took lubuntu (it downloaded in 30 mins). 

The worst thing with lubuntu is that it has unchangable wallpaper on desktop which does not exactly match my taste. And sometimes machine still becomes stuck (I guess there still are bugs there). But the computer definitly works easier than with the standard ubuntu (although I added to lubuntu some of Gnome environment, to have its Software center and Dictionary).

---

### Post by liatodua on 2011-02-06
Oh, I just realised, that it was not Ubunu feature, but xfce4 desktop feature which caused the strange thing. So I can not try it from Ubuntu live CD.

I believe it was within options for different layouts of windows (you know, in xfce the appearance adjustments are organised the different way then in ubuntu, you do them from "windows sth", not "appearance sth"), somewhere at the end, before the last one (which was xfce standard). I think its name started with 'W"

---

### Post by fugazi32 on 2011-02-06
> **liatodua said:**
> Hi

I have ubuntu OS with xfce desktop installed in addition (my old laptop was very slow with standard ubuntu. Xfce was fine). Today I wanted to change appearance of the windows and was trying the different options in the windows menu, just one by one and when I almost reached the end of the list, computer logged out and since than it does not allow me to enter xfce any more. It kind of does not accept my password to enter the xfce session. But I have the same password for ubuntu standard and it works.

What could have happened? And how to return my xfce now?

I had the EXACT same problem yesterday:
[http://ubuntuforums.org/showthread.php?t=1681985](http://ubuntuforums.org/showthread.php?t=1681985)

You have described it better though, lol...

---

### Post by liatodua on 2011-02-06
> **fugazi32 said:**
> I had the EXACT same problem yesterday:
[http://ubuntuforums.org/showthread.php?t=1681985](http://ubuntuforums.org/showthread.php?t=1681985)

You have described it better though, lol...

So you resolved it! How?

---

### Post by waynefoutz on 2011-02-07
You can change the wallpaper in Lubuntu, you can even change the color of the panel at the bottom. (task bar) Lxde is very configurable.

---

### Post by liatodua on 2011-02-07
> **waynefoutz said:**
> You can change the wallpaper in Lubuntu, you can even change the color of the panel at the bottom. (task bar) Lxde is very configurable.

I changed position and color of the bottom panel. But there were no other alernative wallpapers. Guess I have to get them from somewhere or use photos or whatever else. It would be good if the desktop itself had alternative wallpapers, or at least allow to change the color of the existing one.

---

### Post by waynefoutz on 2011-02-07
> **liatodua said:**
> I changed position and color of the bottom panel. But there were no other alernative wallpapers. Guess I have to get them from somewhere or use photos or whatever else. It would be good if the desktop itself had alternative wallpapers, or at least allow to change the color of the existing one.

I don't have Lubuntu installed at the moment, but there is a application in the menus that changes the wallpaper. My daughter has it installed and I was working on it remotely for her, so I know it's there.

---

### Post by waynefoutz on 2011-02-07
LXDE uses pcmanfm to manage the desktop. Open up the file manager, click Edit > Preferences > Desktop tab

---

### Post by liatodua on 2011-02-14
> **waynefoutz said:**
> LXDE uses pcmanfm to manage the desktop. Open up the file manager, click Edit > Preferences > Desktop tab

Lubuntu 10.10 does not have Desktop tab at Edit>Preferences of the file manager.

But finally I managed to change the wallpaper. For someone who faces same problem: download wallpapers from [https://launchpad.net/ubuntu-wallpapers](https://launchpad.net/ubuntu-wallpapers) (select the lucid). Rights-click the downloaded file and select Extract here. The directory will be created which has wallpapers in it. Do not do anything there, just remember the path. Minimize all windows. Right-click on desktop and select Desktop Preferences. in Appearance tab there is wallpaper indication. Go from there to the ubuntu wallpapers directory and select one of these new wallpapers.

---

