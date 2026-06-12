---
title: "Dual Boot Install How to  (please!!!)"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by OlmecHead on 2010-07-08
Hi I must confess that I am totally new in anything concrening Linux/Ubuntu. I feel comfortable in windows and I can do a lot of stuff, but here I hit I paranoid wall. This is what I want to do

a) I have a system with Xp sp3. An hd is only for OS and apps. The second Hd is for my data. 

b) I want to add a third hd where I want to install ubuntu 10.4. I must admit that I have downloaded  different distros and I feel more confortable in Ubuntu (openSuse, Kubuntu, Ubuntu, Mint, Debian).

c) I did some research and I foound that: 
c.1 Each guide assumes that you are only using one hd for all your stuff. As I described above, not me
c.2 Somewhere I read that when you do dualboot with xp and lucid you are asking for trouble.
c3. I am totally lost!!

d)In short I want to dual boot with lucid in its own hd

Can any one help me or point me in the right path?

Thanks before hand

Olmec Head

---

### Post by Zzl1xndd on 2010-07-08
If you have a fully empty drive just select it and let it install. 

However if the disk has data on it you will have to repartition it. That being said I have not encountered any problem dual booting Windows XP and Ubuntu 10.04 on the same drive.

---

### Post by kingbirdy on 2010-07-08
pop in the install CD, and you should be able to chose which HD to install on, and chose the third one. as for XP/lucid compatibility, I haven't heard of any problems, but if its on its own harddrive, there shouldn't be any problems.

---

### Post by akrobert on 2010-07-08
Hello
I ran a dualboot between windows 7 and Ubuntu 9.10 for about 6 months and never had any issues. I did it on the same drive. I just partitioned the hard drive and it ran fine. I just installed windows first and then when I installed Ubuntu I just told it where I wanted it to install and when the grub loader came up at boot I had the option of Ubuntu and then other windows version. It worked fine for the short time I ran it using both but eventually when 10.04 came out I just converted the whole thing to Ubuntu. I found that I used the windows partition less and less and was able to do everything I wanted to do in Ubuntu..

Robert

---

### Post by PRC09 on 2010-07-08
Personally I disconnect the other drives and install as a stand alone install.This eliminates any confusion as to where to install and where to install grub.When finished all you have to do is reconect your other drives,SET THE UBUNTU DRIVE TO BOOT FIRST and when it has booted to the desktop open a terminal and run sudo update-grub, enter your password hit enter,close your terminal,restart your machine and you have a trouble-free dual boot.....Hope this helps....

---

### Post by garvinrick4 on 2010-07-08
If you want to install in 3rd drive boot off of CD and choose the drive at install, will ask a few questions on time, language, user name and so on. On last page will be a advanced button on lower right, page 8 I believe click on it and put boot in sdc if is third drive sdb if second drive and sda if first drive. You say the 3rd drive so not sdc1 or sdc2 but sdc always. When you boot up into your Ubuntu install. Go to Applications to Accessories to Terminal and put this code in the Terminal.

```
sudo update-grub
```

Here are a few manuals of instructions: 2nd one is a pdf file that is a beginner must.
1st one will help you set up.

[Main Page -]("http://ubuntuguide.org/wiki/Main_Page") 

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

Here are a few on Grub2 which is the boot loader.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by oldfred on 2010-07-08
+1 on        garvinrick4's suggestions

I prefer to pay attention to the advanced button and make sure of where grub is installed rather than mess with the inside of my pc case. ( I have yet to not disconnect something and create more problems everytime I open case). It is not all that difficult to reinstall windows or grub boot loaders, even if you do get grub in the wrong place. Make sure you set BIOS to boot the Ubuntu drive.

It says two but works for any more than one.
Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by OlmecHead on 2010-07-09
Thanks a lot guys!!I will give it a try and let you know.
:popcorn:

The Big Olmec Head

---

