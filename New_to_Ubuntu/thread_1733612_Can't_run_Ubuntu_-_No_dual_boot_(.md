---
title: "Can't run Ubuntu - No dual boot :("
date: 2011-04-19
forum: New to Ubuntu
---

### Post by reivann on 2011-04-19
Hi everyone. :S. Big noob here.


I installed Windows 7 then Ubuntu after. I partitioned my drive during my installation in Windows 7. When I was installing Ubuntu, I did manual partitioning, used ext4 and mounted it on /.

I was able to finish the installation in Ubuntu, but when my computer restarted, it went straight to Windows 7.

I've been reading this forum the whole night and afternoon, but I can't solve the problem. Please please help. :(

I already used supergrub... but it didnt work. I tried the codes for the terminal, but there are too many error messages, I don't know what I'm doing. X__X :<

---

### Post by L Campbell on 2011-04-19
> **reivann said:**
> Hi everyone. :S. Big noob here.


I installed Windows 7 then Ubuntu after. I partitioned my drive during my installation in Windows 7. When I was installing Ubuntu, I did manual partitioning, used ext4 and mounted it on /.

I was able to finish the installation in Ubuntu, but when my computer restarted, it went straight to Windows 7.

I've been reading this forum the whole night and afternoon, but I can't solve the problem. Please please help. :(

I already used supergrub... but it didnt work. I tried the codes for the terminal, but there are too many error messages, I don't know what I'm doing. X__X :<


Welcome to Ubuntu and I hope we can make you happy.

I have a dual boot setup and when my machine boots it gives me a choice of WinXP or Ubuntu.  Do you not see that choice?

If you do, you have to then click the down arrow, click enter, then click enter again.

Please write back if you need more help.

---

### Post by chellrose on 2011-04-19
Which version of grub are you using?

If you have a relatively new version of Ubuntu, then it's probably grub 2.  Here's what works for me...

1. Boot from the Ubuntu Live CD.
2. Open a Terminal and type
```

sudo fdisk -l
sudo mkdir /media/sda#

```where "sda#" should be replaced with the designation of *your* Ubuntu partition, e.g. sda0, hda6, etc.
```

sudo mount/dev/sda# /media/sda#
```(again, replacing "sda#" with your Ubuntu partition)
```

sudo grub-install --root-directory=/media/sda# /dev/sda
```(again, replacing "sda#" with your Ubuntu partition)

3. Reboot without the live CD and you should have a boot menu.

---

### Post by reivann on 2011-04-19
@L Campbell: Thank you! .. howver, that's my problem, I can't see the part wherein I can choose the OS I want :< It goes directly to windows.

@Sissy13: I tried it, but there was an error on the last command. 

ubuntu@ubuntu:~$ sudo mkdir /media/sda6
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /media/sda6/boot/grub (is /dev mounted?). 

X__X :(

---

### Post by chellrose on 2011-04-19
Hmm... I've not seen that error.  But try this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by reivann on 2011-04-19
Thank you sissy! I'll try it and report my progress. :D Thank you!. :D

---

### Post by ashickur.noor on 2011-04-19
> **reivann said:**
> Hi everyone. :S. Big noob here.


I installed Windows 7 then Ubuntu after. I partitioned my drive during my installation in Windows 7. When I was installing Ubuntu, I did manual partitioning, used ext4 and mounted it on /.

I was able to finish the installation in Ubuntu, but when my computer restarted, it went straight to Windows 7.

I've been reading this forum the whole night and afternoon, but I can't solve the problem. Please please help. :(

I already used supergrub... but it didnt work. I tried the codes for the terminal, but there are too many error messages, I don't know what I'm doing. X__X :<
Please give the error msg shows in terminal

---

### Post by GWBouge on 2011-04-19
> **Sissy13 said:**
> ```
sudo fdisk -l
sudo mkdir /media/sda#

**sudo mount /dev/sda# /media/sda#**

sudo grub-install --root-directory=/media/sda# /dev/sda
```

> **reivann said:**
> ubuntu@ubuntu:~$ sudo mkdir /media/sda6
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /media/sda6/boot/grub **(is /dev mounted?)**.

Did you miss the **mount** command?

---

### Post by reivann on 2011-04-28
@ashikur.noor : Oh, it's okay, now. Thank you!

@GWBouge: Haha, yes! Wooohoooo.Thanks for pointing that out! :D  ^_______^ Finally, it's working. 

I hope to learn the terminal commands so I won't be pawned by a 'space' next time, haha. Thanks everyone! :D XD. A nice community indeed. :D

---

