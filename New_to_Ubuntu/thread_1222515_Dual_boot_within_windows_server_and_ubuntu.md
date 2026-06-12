---
title: "Dual boot within windows server and ubuntu"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Moe Z on 2009-07-25
hi
    i was using ubuntu and windows xp dual boot for a long time.. it's ok. no problem at all... but last night i remove windows xp and install windows server 2003 SP1. and my ubuntu has gone.. no boot selection menu appears at start up. 
pls help..

---

### Post by Zero++ on 2009-07-25
You could give this a try. [Here]("https://help.ubuntu.com/community/WindowsDualBoot") is the link to the site it came from.
**Recovering GRUB after reinstalling Windows**

 As above, when Windows is reinstalled, the master boot record will be overwritten. This can be avoided by backing up the boot sector, by following the instructions from step 2 in the above section 'Installing Windows After Ubuntu'. An alternative method, which has the advantage of not requiring forward planning, is to use the Ubuntu LiveCD to reinstall the GRUB boot sector, here are step-by-step instructions, to be run after Windows has been reinstalled: 

[LIST=1]
[*]Boot into a LiveCD 
[*]Open a terminal 
[*]Open the GRUB Command line utility by typing 
[/LIST]

sudo grub
[LIST=1]
[*]Tell GRUB where your Ubuntu partition is by entering 
[/LIST]

root (hdA,B)Where 'A' is the hard-drive number, starting at 0, and 'B' is the partition number, starting at 0. For example, if Ubuntu was installed on the second partition of the first hard-drive, the command should be 
root (hd0,1)
[LIST=1]
[*]Tell GRUB which drive to put the boot sector on 
[/LIST]

setup (hd0)(replacing 0, as above, if a drive other than the first is used as the boot device) 

[LIST=1]
[*]Leave the GRUB Command line 
[/LIST]

quitand reboot.

---

### Post by Moe Z on 2009-07-25
Thanks for the quick reply, the problem is that i've no DVD ROM (yet my Ubuntu Live is DVD).. i've only CD ROM.. is there any other way pls? if there's no other way.. i must borrow an external DVD ROM from my friend.. :(

---

### Post by Zero++ on 2009-07-25
You can grab Ubuntu ISO and burn it to a CD. or you can install it to a jumb drive and run off of that (if your BIOS will boot from USB)

Aside from that you could try downloading and running Ubuntu in windows and see if you can access the linux file system. I've never run Ubuntu from inside Windows so I'm not sure it will see the Linux partition because windows will not see it

[www.**supergrub**disk.org/]("http://ubuntuforums.org/www.supergrubdisk.org/") 
is a bootable CD download may also help if nothing else works

Hope this helps
Let us know what happens

---

### Post by Moe Z on 2009-07-25
yes, really sorry for my late reply.. i can't download ISO files.. i mean i get only 40KBps download speed (too slow to download the whole 590MB of ISO file).. i think the best way is to borrow DVD ROM and boot .. 
anyway thanks for your advise..

---

### Post by Moe Z on 2009-07-25
ahh.. it don't work buddy.. i type root (hd0,2) where my ubuntu installed partition.. it's ok
and then i type setup (hd0) and it says unable to mount this partition.. pls help again. :(

---

### Post by Moe Z on 2009-07-25
ahh.. no one reply my post.. looks like everybody is hving party.. :D

---

### Post by Moe Z on 2009-07-28
Hi, my problem still don't fixed yet, i booted into Live CD, it's all ok. And then, in terminal, i type 
root (hd0,3) (i think partition 0 is C: for Windows, D: for my data Partition, and E: for CD Rom), it's ok.. nothing happened. but when i type setup (hd0)... it says Unable to Mount Partition... i don't know what's wrong. Pls help the noob.

---

### Post by melrokz on 2009-07-28
you booted into live cd?
ok, then install the linux bootloader like this:

1. go to the places menu and click on 'computer'.
2. dbl-click on the linux root partition, to mount it.
3. it will get mounted as /media/disk.
4. take the 'applications' menu and click on 'terminal'.
5. enter this command:
sudo grub-install hd0 --root-directory=/media/disk

---

### Post by melrokz on 2009-07-28
if that didn't work, type
> man grub-install
and check out the syntax.

---

### Post by Moe Z on 2009-07-28
thx melrokz!

---

