---
title: "WEIRD wireless problem caused by screen resolution change?"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by thomasaaron on 2006-11-16
OK, guys. I've got an intersting problem with my Internet connection. Anybody got any ideas? Here is what I did:

1. I was having screen resolution problems on my ACER Aspire 3000. I did some searches and found that I needed to add the proper resolution on /etc/X11/xorg.conf. So, I did added the desired resolution. But before experimenting with it, I actually saved a copy of the original file. (THis comes into play later).

2. Following the instructions in xorg.conf, I went to the command line and typed. sudo dpkg-reconfigure -phigh xserver-xorg. When it pulled up the screen, I hoped that the default setting was correct, and I just hit enter. (I think it was on VESA or something). Yeah, I know. Stupid move.

3. My screen went ape crap. I had to press the off button on my computer. When I restarted it everything seemed normal. Same old bad screen resolution too. I decided that I shouldn't experiment any more just then. I put the original verion of xorg.conf back into the directory. Restarted my computer. Everything seems to be going fine....EXCEPT...

4. Now my Internet connection isn't working like it used to. To switch from wireless to DSL or vice versa, I have to go to the network manager, activate one and deactivate the other, and then restart my computer. Otherwise, I cannot switch back and forth. I used to be able to do it very easily, and as far as I can tell, mucking with the resolution was point at which it broke.

Any ideas?

---

### Post by Joe_CoT on 2006-11-16
The screen resolution shouldn't have caused that. The issue is probably tangentially related, because of the cold restart you did to the machine.

Does it work correctly using ifconfig, ie with ifup/ifdown? I tried to find the package to reinstall gnome's networking, but I'm at a loss. You might want to try network-manager-gnome

---

