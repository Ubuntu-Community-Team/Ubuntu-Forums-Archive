---
title: "Problem Installing my Wireless USB Adapter (Ralink 2573)"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by Blots on 2007-06-23
Hey everyone, I've been having a problem trying to install my USB wireless card on my laptop, do you think you could help? I'm not that new to Ubuntu, but I do have trouble with command lines/terminal. I have downloaded the Linux driver for my USB card, but now I'm just having trouble following the USB instructions. For example, it says..

[INDENT]   This driver implements basic IEEE802.11. Infrastructure and adhoc mode 

   with open or shared or WPA-PSK or WPA2-PSK authentication method. 

   NONE, WEP, TKIP and AES
=======================================================================

Build Instructions:  

====================

1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.

2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]

3> [kernel 2.4]

    $chmod 755 Configure

    $make config         # config build linux os version

4> $make all            # compile driver source code encryption. [/INDENT]

How do I know which makefile I'm supposed to choose? And I'm assuming that the words written after the # are just instructions/explanations and do not need to be put into the terminal, is that right?

I really can't use my laptop if there's no internet. :(

- Blots

---

### Post by Blots on 2007-06-24
Bump... can some one please help me on this?

---

