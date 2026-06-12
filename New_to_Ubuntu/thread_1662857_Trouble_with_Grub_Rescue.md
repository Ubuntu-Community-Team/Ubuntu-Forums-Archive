---
title: "Trouble with Grub Rescue"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by vamaar on 2011-01-08
Today I decided to install Linux on my Laptop. My desktop had run Linux for a while, but Windows 7 basically did what I wanted it to do, so I left it on my laptop. However, I'm currently enrolled in a university course that teaches about the Unix shell, so I thought I should put Ubuntu on my computer again. Having been years since I did an installation, I decided to go with what seemed simplest, using Wubi.

Things seemed more or less correct; it installed and I got into Ubuntu reasonably well. Upon entering the world ob Ubuntu again, I was told my system needed updating. This made sense, so I went along with it. Part of the updating involved putting grub on my hard drives. Not really knowing what Grub was I agreed, and it asked which one. It further said that if I wasn't sure which one it was supposed to go on, it could go on both. I have two 500 GB hard drives, and selected both. My computer then informed me that it had to reset. 

Upon rebooting, I have received an error message: 

error: no such device: 9f0d3278-1e36-43b3-9ff0-dc0d64a33029.
grub rescue>

This appears to be a command line environment, so I tried a sh commands I knew, but the only command that has worked thus far was 'ls', which returned the results
(hd0)(hd1)

I tried to follow the advice in this guide ([https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)) but it didn't work, and I'm still stuck at grub rescue. I have no idea what else to do. Can anyone help? I'm running a Toshiba Laptop, intel i7 core.

---

### Post by drs305 on 2011-01-08
Welcome to the Ubuntu forums.

Wubi installs are a bit different than normal installations, so the commands that usually work may not solve Wubi problems, or have to be run differently.

Forum member *Rubi1200* has written a guide to solving Wubi installation problems related to Grub2. Take a look and if you can't solve it yourself post the boot info script RESULTS.txt in that thread.
[WUBI MEGATHREAD]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by wilee-nilee on 2011-01-08
If this is just a wubi install, you can reload a MS bootloader to the MBR or lilo from linux. Do you have a recovery windows disc, or a ubuntu disc, same as the wubi install?

This thread addresses the fix; problem 1 then solution 1 or 2 will work most likely.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by vamaar on 2011-01-08
Thanks for the advice! The Wubi megathread's guide helped me out, things are running smoothly. I have a question, however; is my Ubuntu still running using Wubi and if it is, is it worth it to remove it and install a fresh copy with my disk?

---

### Post by drs305 on 2011-01-08
> **vamaar said:**
> Thanks for the advice! The Wubi megathread's guide helped me out, things are running smoothly. I have a question, however; is my Ubuntu still running using Wubi and if it is, is it worth it to remove it and install a fresh copy with my disk?

From what you described you are running Wubi. With a Wubi installation, the first menu you see will have Windows first (above) and then Ubuntu. If you select  Ubuntu from that menu, you will then see the Ubuntu menu, with "GNU GRUB" at the top of the screen.

If you are seeing "GNU GRUB" at the top of the first menu you boot to, it is probably Ubuntu.

I'd give Wubi a try for a while. Make sure all your hardware works. You can migrate your Wubi installation to a real installation at any time. Here is a link to a guide by forum member *bcbc* to help do that when you are ready:
[HOWTO: migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354")

---

### Post by wilee-nilee on 2011-01-08
> **vamaar said:**
> Thanks for the advice! The Wubi megathread's guide helped me out, things are running smoothly. I have a question, however; is my Ubuntu still running using Wubi and if it is, is it worth it to remove it and install a fresh copy with my disk?

Fortunately drs305 and I posted at the same time as I did; the link I forgot was the one they added, sorry. :(

---

