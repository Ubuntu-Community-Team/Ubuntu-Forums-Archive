---
title: "Need help with Ubuntu 9.10"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by sraju on 2010-01-15
Hi all, I recently installed 9.10 and after automatic update it wont boot back. I installed it through wubi in win 7. It shows a grub message similar to this video on youtube [http://www.youtube.com/watch?v=enOV2RxWgLc](http://www.youtube.com/watch?v=enOV2RxWgLc). I have some useful stuff on that partition and want to see if there is any way i could retrieve it through windows or ubuntu live cd. Win 7 is working fine but ubuntu wont boot up. Please help me in this matter. I am a new bee trying to explore the world of Ubuntu. Thanks in advance

---

### Post by tom.swartz07 on 2010-01-15
> **sraju said:**
> Hi all, I recently installed 9.10 and after automatic update it wont boot back. I installed it through wubi in win 7. It shows a grub message similar to this video on youtube [http://www.youtube.com/watch?v=enOV2RxWgLc](http://www.youtube.com/watch?v=enOV2RxWgLc). I have some useful stuff on that partition and want to see if there is any way i could retrieve it through windows or ubuntu live cd. Win 7 is working fine but ubuntu wont boot up. Please help me in this matter. I am a new bee trying to explore the world of Ubuntu. Thanks in advance

hiya!

sorry that it happened. check the link here- [http://goo.gl/5M2M](http://goo.gl/5M2M) it should sort you out

you just need a LiveCD and boot to that. post back with any questions

---

### Post by lrcaballero on 2010-01-15
I have seen this happen many times with my school fellows, maybe you will want to consider deleting it from Wubi and installing it again, or you can try booting from a Live CD, it would have to be Ubuntu of course....ones you have booted with live cd, open up aterminal and type this:

Code 

3. sudo grub. (Should get text of which last line is grub>

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.

5. Type "root (hd0,1)", or whatever your hard disk + boot      partition numbers are for Ubuntu.

6. Type "setup (hd0)", to install GRUB to MBR

7. Quit grub by typing "quit".

8. Reboot and remove the bootable CD.

---

### Post by dzon65 on 2010-01-15
Probably kernel update.If you have a previous kernel-version ,try that one.
Someone suggested this,




     Code:
     sh:grub linux /boot /vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=ubuntu/disks/root.disk.ro 
[ENTER]

     Code:
     sh:grub initrd /boot/initrd.img-2.6.31-16-generic 
[ENTER]

     Code:
     sh:grub boot 
If that works and brings your Ubuntu back, go into a terminal and 

     Code:
     sudo update-grub2

---

### Post by mlentink on 2010-01-15
Will this really help the OP? 
The OP has installed through the Wubi-installer, which to my knowledge does not install GRUB to the Windows-partition. Furthermore, Wubi does not install a real partition, but a virtual one which is really only a file in the Windows file-system. How would you explore that from a LiveCD? And how would installing GRUB to the Windows partition help exploring that ubuntu virtual partition?

Am I all wrong here? If so, tell me, I'm always willing to learn.

EDIT: dzon65s post seems to make sense to me.

---

### Post by dzon65 on 2010-01-15
MY mistake!!Didn't read it,the wubi part.Sorry about that.

---

### Post by warfacegod on 2010-01-15
This should do the trick:

[http://ubuntuforums.org/showpost.php?p=8639887&postcount=14]("http://ubuntuforums.org/showpost.php?p=8639887&postcount=14")

---

### Post by dzon65 on 2010-01-15
So,supose you're gettin' something like GNU GRUB version 1.97
minimal bash-like line editing is supported...........?

---

