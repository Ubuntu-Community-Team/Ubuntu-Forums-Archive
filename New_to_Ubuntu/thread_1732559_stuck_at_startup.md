---
title: "stuck at startup"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by alexvsc on 2011-04-18
Hi,
i installed Ubuntu 10.1 trough Windows Installer. 
But when i rebooted, Ubuntu got locked up, here:

[IMG]http://img690.imageshack.us/img690/9783/c06b9ecbe170909f101e44c.jpg[/IMG]

What is the problem?

---

### Post by Terry of Astoria on 2011-04-18
What kind of hardware are you using? If you have an Intel 82852/855GM Integrated Graphics Device you might want to read the following. I had a similar problem. My Thinkpad R51 SOMETIMES would boot after about an hour or so, but usually would stay at the symbol like yours. It wouldn't boot reliably until I added the following:
```
i915.modeset=1
```to the command before booting. See here where Carl clearly explains. 
[http://all-tech-thoughts.blogspot.com/2011/03/ubuntu-on-dell-latitude-d505-laptop.html]("http://all-tech-thoughts.blogspot.com/2011/03/ubuntu-on-dell-latitude-d505-laptop.html")
   Basically to boot with the i915 driver one time, do the following, according to him:

1) Hold down Shift while booting to enter the GRUB menu.

2) Press 'e' to edit.

3) Add "i915.modeset=1" after "quiet splash".

4) Ctrl+x to boot.



To boot the live CD:


1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu.

2) Hit Enter to select your language, and then press F6 and then Esc.

3) Add "i915.modeset=1" after "quiet splash".

4) Press Enter to boot the LiveCD.

And to set your computer up permanently do:

```
sudo gedit /etc/default/grub
```

and add 'i915.modeset=1' (without the quotes) so the line will probably look like:

GRUB_CMDLINE_LINUX="i915.modeset=1"

then save and quit gedit, then do:

```
sudo update-grub
```

The problem I had was due to the 82852/855GM Integrated Graphics Adapter in my Thinkpad R51 not working properly until the right driver is loaded. What is your computer hardware (model #, or what brand graphics card, etc . .)? You need to give more information about your system when you ask a question. Happy computing!

---

### Post by Rubi1200 on 2011-04-18
Hi and welcome to the forums alexvsc :)

Do you see this screen immediately after completing the Wubi install in Windows and rebooting OR after completing the reboot to finish the installation and on subsequent boots?

Here is some more information for you to look at:
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

By the way, as Terry of Astoria pointed out, this is likely a video issue so please tell us what graphics card you have installed.

Thanks.

---

### Post by alexvsc on 2011-04-18
Intel Celeron CPU 2.80GHz
1GB RAM
NVIDIA RIVA TNT2 Model 64 (it really sucks).

After installation in Windows, a message apperead saying that the intallation was successful, and that i must reboot the computer to check or complete instalation. 
At the reboot, the computer got stucked there, like the pic shows.

---

### Post by Rubi1200 on 2011-04-19
Did you try the options in the link I posted or are you not even able to get that far?

---

### Post by alexvsc on 2011-04-19
It worked nomodeset.
Thanks a lot!

---

### Post by Rubi1200 on 2011-04-19
Excellent! Glad this worked for you :-)

If this is resolved, please mark the thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

