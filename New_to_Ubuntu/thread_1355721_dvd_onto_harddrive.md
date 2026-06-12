---
title: "dvd onto harddrive"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by sallymc on 2009-12-15
I need to copy a long movie on 2 DVDs onto my hard drive.  The first DVD copied successfully  - I used sudo apt-get install dvdrip .  

Then the 2nd was unsuccessful, the message reading :  
The following packages were automatically installed and are no longer required:
  libdns35

Please could you help?  Many thanks
sallymc

---

### Post by northern lights on 2009-12-15
> **sallymc said:**
> The following packages were automatically installed and are no longer required:
libdns35
Are you certain this is a dvdrip output? It appears much more likely to stem from a packing management tool...

---

### Post by sallymc on 2009-12-15
Thanks Northern Lights.  Perhaps I should give you the whole message :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
dvdrip is already the newest version.
The following packages were automatically installed and are no longer required:
  libdns35
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
  Sallymc

---

### Post by northern lights on 2009-12-15
> **sallymc said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
dvdrip is already the newest version.
The following packages were automatically installed and are no longer required:
  libdns35
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.This is the message you'd expect to get when running *apt-get install dvdrip* on a system where dvdrip is already installed.

I'm certain that that's what you ran and not dvdrip itsself...

You could follow the advice in there and remove *libdns35*, but as for the second DVD, just run the right thing. ;)

---

### Post by sallymc on 2009-12-15
Thanks NL.  I am a very simple soul and new to this game!  What is the right thing?  I ran 'dvdrip' and this came up :

[filterlist] (re)scanning transcode's module path /usr/lib/transcode...

Plus a programme that I didn't understand!

Sorry to be so green - the actual command would be useful.

sallymc

---

### Post by LowSky on 2009-12-15
dvdrip is in your Applications menu, click on the icon to open the program. insert the DVD and hopefully it works, if not, you will needa file called

libdvdcss, which you can install using this code in a open terminal
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

if DVDrip still doesn't work, try handbrake. I think its a much friendlier application
download this link and run the file to install,
[http://handbrake.fr/rotation.php?file=HandBrake-0.9.4-Ubuntu_GUI_i686.deb](http://handbrake.fr/rotation.php?file=HandBrake-0.9.4-Ubuntu_GUI_i686.deb)

---

### Post by northern lights on 2009-12-15
You do not need to use the CLI/shell for the actual ripping. Just open DVDrip from the gnome menu. Applications > Sound & Video > dvd::rip

---

### Post by Darce on 2009-12-15
Go to the Applications menu at the top left of your screen. Then select the Sound & Video submenu. Then select dvd::Rip

---

### Post by CaptainMark on 2009-12-15
@lowsky
thanks i hadnt noticed handbrake had finally been packaged for 9.10, been waiting ages, then i just sorta forgot. someday ill get round to learning how to compile from source and not have to worry about it

---

### Post by LowSky on 2009-12-15
> **CaptainMark said:**
>  someday ill get round to learning how to compile from source and not have to worry about it

Compile what from source, they have DEB file?
Or are you talking about how Handbrake didn't work on 9.10, in that case even compiling it form source would work as the dependencies were gone because of the replacements made to Ubuntu.

---

### Post by CaptainMark on 2009-12-15
> **LowSky said:**
> Compile what from source, they have DEB file?
Or are you talking about how Handbrake didn't work on 9.10, in that case even compiling it form source would work as the dependencies were gone because of the replacements made to Ubuntu.
Oh okay, i heard that you could get it to work if you compiled it, my mistake, now the debs been packaged it doesnt matter anyway

---

