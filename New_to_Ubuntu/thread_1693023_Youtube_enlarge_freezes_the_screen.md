---
title: "Youtube enlarge freezes the screen"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Defoe22 on 2011-02-22
Hello!

I'm new to Ubuntu and have a lot of questions - so expect to see more of me!

Might as well start with this -

on Youtube. The video freezes and does not play when I enlarge it, but is fine when it plays in its normal size.

Any ideas?

---

### Post by komputes on 2011-02-22
Plenty of ideas, but where to start.

What version of ubuntu do you run and which version of flash do you have installed.

```
$ lsb_release -a
$ dpkg -l | egrep "flash|gnash|swf"
```

Please post the output of these commands.

What I would recommend for best flash video output is to open the flash video file (in /tmp, but in newer versions ~/.mozilla/firefox/??????.default/Cache/) directly with a video application such as VLC.

---

### Post by Defoe22 on 2011-02-22
Ubuntu:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

Flash:
ii  adobe-flashplugin                    
10.2.152.27-0maverick1                            Adobe Flash Player plugin version 10


Realised there are other pages on this and so far, unchecking hardware acceleration didn't work.
I have been using download helper to play the videos locally if I really want them in enlarge. Similar to viewing from temp, only without saving the video?

---

### Post by sydbat on 2011-02-22
What is your hardware? CPU, RAM, Graphics card, etc? Your specs might only be minimum for running Ubuntu, therefore causing your problems.

Also, have you installed [Restricted Extras]("https://help.ubuntu.com/community/RestrictedFormats") and [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")?

Finally, after making sure the above have been installed, [this Firefox add-on]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") will help alot.

---

### Post by NightwishFan on 2011-02-22
This bug happens on my Asus laptop if I am using the 32-bit flash from the repos with the 64-bit Ubuntu. Do you have 64-bit? If so you can try downloading the 64-bit flash preview from adobe. It is easy to install. You can download it here:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)

[LIST=1]
[*]Remove the installed flash plugin using the software center.
[*]Download the tar.gz file from adobe and open it.
[*]Open your home folder under the places menu.
[*]Press CTRL+H and show hidden files.
[*]Find the folder .mozilla, and open it, while in it, create a folder called (without quotes): "plugins".
[*]Copy the flashplugin.so (or whatever it is called) from the adobe tar.gz file into the "plugins" folder.
[*]Restart Firefox.
[/LIST]

---

### Post by sydbat on 2011-02-22
> **NightwishFan said:**
> This bug happens on my Asus laptop if I am using the 32-bit flash from the repos with the 64-bit Ubuntu. Do you have 64-bit? If so you can try downloading the 64-bit flash preview from adobe. It is easy to install. You can download it here:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)

[LIST=1]
[*]Remove the installed flash plugin using the software center.
[*]Download the tar.gz file from adobe and open it.
[*]Open your home folder under the places menu.
[*]Press CTRL+H and show hidden files.
[*]Find the folder .mozilla, and open it, while in it, create a folder called (without quotes): "plugins".
[*]Copy the flashplugin.so (or whatever it is called) from the adobe tar.gz file into the "plugins" folder.
[*]Restart Firefox.
[/LIST]No need to go through all that, just use Flash-Aid.

---

### Post by NightwishFan on 2011-02-22
Flash aid: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by komputes on 2011-02-22
[@Defoe22]("http://ubuntuforums.org/member.php?u=1249065")

Can you please try to remove adobe-flashplugin and install flashplugin-nonfree:

```
$ sudo apt-get remove adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree
```

Then either quit all firefox windows or log out/in and test again. If it still crashes, can you post your video card settings:

```
$ lspci | grep -i VGA | awk '{print "sudo lspci -knn -s "$1}' | bash
```

---

### Post by Defoe22 on 2011-02-23
Thanks everyone! Fixed

Worked after following @sydbat's suggestions

EDIT: It worked ONCE after following those suggestions! Freezes again now.....

---

### Post by Defoe22 on 2011-02-23
> **komputes said:**
> [@Defoe22]("http://ubuntuforums.org/member.php?u=1249065")

  If it still crashes, can you post your video card settings:


Did what you said Komputes and still freezing

Video Card Settings:
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:0261]
    Kernel driver in use: i915
    Kernel modules: i915


Not sure the exact specs (duh). Buts its fairly new, 2-3gb of ram I think and dual core

---

### Post by stdrogo on 2011-02-23
Minitube is an option.

---

