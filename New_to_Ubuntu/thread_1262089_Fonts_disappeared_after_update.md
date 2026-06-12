---
title: "Fonts disappeared after update"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by nightshade209 on 2009-09-09
Hi, i updated my Ubuntu 9.04 using the update manager. After the update was done, all my font appearing in applications has disappeared. I can only see the text in the GNOME menus, the titlebars of all the windows and Nautilus icons and toolbars. However, the fonts cannot be seen in firefox, OpenOffice, GDM login window etc. If i type, i can see the cursor moving forward but cannot see any letters forming.
Did something go wrong during the update that caused this? I believe there were a couple of display driver updates (Intel). Could something have gone wrong with the display of fonts?? Pls help soon, as i am unable to use my PC and have to resort to booting up from the LiveCD (like now).

---

### Post by wojox on 2009-09-09
Huh

Mount the filesystem and open the terminal and refresh the font cache:

```
sudo fc-cache -fv
```

---

### Post by nightshade209 on 2009-09-09
I got the following output:
```
suyash@suyash-desktop:~$ sudo fc-cache -fv
/usr/share/fonts: caching, new cache contents: 0 fonts, 4 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 83 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/cmap: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 2 fonts, 19 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/sazanami: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 51 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bengali-fonts: caching, new cache contents: 5 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-kannada-fonts: caching, new cache contents: 7 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-oriya-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-telugu-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/wqy: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/suyash/.fonts: skipping, no such directory
/usr/share/texmf/fonts/type1/public/lm: caching, new cache contents: 92 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/home/suyash/.fontconfig: cleaning cache directory
fc-cache: succeeded

```
And the problem hasn't been solved.

---

### Post by wojox on 2009-09-09
What does it look like in System > Preferences > Appearance > Fonts

---

### Post by nightshade209 on 2009-09-10
If i select anything except Subpixel Smoothing (LCDs) under Rendering, ALL the font disappears. And changing the application or desktop fonts does not help : it stays blank.

---

### Post by blueball81 on 2009-09-10
I have the same problem since someday.
and, some Asian characters also disappeared.

---

### Post by kovzol on 2009-09-11
I got into a similar situation. I use Ubuntu 9.04 and after an update and a reboot I experienced there are no fonts anymore under X.

I tried a few things to solve the problem:

dpkg-reconfigure xserver-xorg
apt-get remove xfonts-base; apt-get install xfonts-base
apt-get remove xserver-xorg; apt-get install xserver-xorg

No luck yet. But my plan is to find out which font files are open in a working Ubuntu and try to check what is going on in the updated 9.04:

[FONT="Courier New"][SIZE="1"]kovzol@laptop:~$ lsof | grep font | tail
lxtermina 5085     kovzol  mem       REG        3,7   118264      57858 /usr/share/fonts/truetype/openoffice/opens___.ttf
lxtermina 5085     kovzol  mem       REG        3,7    40766     153209 /usr/share/fonts/X11/Type1/c0419bt_.pfb
lxtermina 5085     kovzol  mem       REG        3,7    23616     155252 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
lxtermina 5085     kovzol  mem       REG        3,7    24904     155246 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
lxtermina 5085     kovzol  mem       REG        3,7   138776     155254 /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
lxtermina 5085     kovzol  mem       REG        3,7     8200     155250 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
lxtermina 5085     kovzol  mem       REG        3,7     1688      44087 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
lxtermina 5085     kovzol  mem       REG        3,7    26208     155248 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
lxtermina 5085     kovzol  mem       REG        3,7     5184     156501 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
lxtermina 5085     kovzol  mem       REG        3,7   172592       1523 /usr/lib/libfontconfig.so.1.3.0
[/SIZE][/FONT]

---

### Post by kovzol on 2009-09-11
A screenshot about my problem is available on

[http://160.114.33.20/~kovzol/fontsdisappeared.png](http://160.114.33.20/~kovzol/fontsdisappeared.png)

---

### Post by kovzol on 2009-09-11
OK, I successfully fixed this problem. The bug is in the X video driver which have been updated by Ubuntu on 2009-09-09.

I installed a fail-safe /etc/X11/xorg.conf as follows:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Now when I restart X (CTRL-ALT-Backspace) the fonts are appearing. However, the displaying is much slower than before.

I realized that today there is a new fix for the X drivers. I downloaded them. Hopefully these updates are fixing the font problem as well.

---

### Post by kovzol on 2009-09-11
No, the latest fixes from Ubuntu do not fix this problem. So I had to revert to the fail-safe configuration.

Probably this is helpful for you, so I attach the output of my "lspci | grep VGA":

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

So, probably the Intel driver has problems.

---

### Post by kovzol on 2009-09-11
I reported this to Ubuntu Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/427744](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/427744)

---

### Post by kovzol on 2009-09-11
I reported this problem to the developers:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/427744](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/427744)

---

### Post by nightshade209 on 2009-09-11
Ya, that is the same problem i was facing. Thanx for all the help! I hope it gets fixed soon. Meanwhile, can someone pls tell me what kovzol did to fix it, in a simple point-click-type way?? I am not great with the terminal.:(

---

### Post by Wandel on 2009-09-11
There's no simple point-click way of doing this, that's what makes it Linux :P
I've created a script you can use. Granted, you should never run a script you get from some random guy on the Internet, unless you know exactly what it does, so you really should get more comfortable with the command line.

[Download the script]("http://dl.getdropbox.com/u/21660/xorg-failsafe"), to say, your Desktop. Open the terminal and type "cd Desktop".
First you'll have to make it executable, by typing "chmod +x xorg-failsafe" and then run the script(since you'll be changing some pretty important files, you'll need to use sudo) by typing "sudo ./xorg-failsafe".

What this script will do is rename your old xorg.conf to xorg.conf.old, and then create a new one, containing the information kovzol wrote. This assumes you're running a LiveCD on the system, and that Ubuntu is sda1(ie, you've only got Ubuntu installed on that machine). If that's not the case, let me know and I can update the script for you.

---

### Post by nightshade209 on 2009-09-13
Thanx, tht solved the font problem. However, nw my resolution is stuck at a maximum of 1024x768, cant get it up to my usual of 1350x768.
N btw, i sed point-click-type, nt point-click. I realy dont xpect to use Linux w/o using the terminal; al i meant was give me a step by step procedure, nt smthing like "oh, u just have to backup the appropriate file and then change the options to default". I wudnt mind following instructions tht go something like "open this file as root, edit these lines to read this and save it".:D

---

### Post by Wandel on 2009-09-14
Oh, sorry I thought you meant say "point-click type of way" at first.
And yeah, the resolution is a problem, also it's a bit more sluggish. Apparently, according to someone on the launchpad page, there's an update that'll fix the problem completely. For some reason, I haven't received that one. That guy is using a newer kernel than me, so maybe that has something to do with.

---

### Post by nightshade209 on 2009-09-14
Neither have i, guess i m stuck at this res til ubuntu comes out wid an update...

---

### Post by stonki on 2009-09-16
I was facing the same problem on my kubuntu installation, after performing an X-ORG update. On a 12h longhaul flight I did some checks and found a workaround:

My problem was that all KDE3 application had no text. KDE4 application were fine. This did not occur on a brand new test account, so I digged a little deeper. After opening the "KDE settings" dialog the problem started. I noticed that a new file called ".fonts" were created   in my home directory. After removing this file again (which seems to make no difference) all application had their text again.

So, please check on your system as well if renaming .fonts to .fonts.BACKUP might do the trick. I will do some further research as well.

Stonki

---

### Post by stonki on 2009-09-16
the file is called .fonfs.conf. 
On another system I also had to remove .kde/share/config/systemsettingsrc

The problem seems to be related with the Antialiasing of the fonts.

---

### Post by nightshade209 on 2009-09-17
Thanx! Deleting the fonts.conf file seems to have solved the problem.

---

