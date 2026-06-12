---
title: "Old Kernal Version in Grub not shown in Synaptic"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by droadtrip on 2010-05-21
[FONT=Microsoft Sans Serif][SIZE=2][COLOR=Black]I am on Ubuntu 10.04. Upon my computer laptop system start-up, my black Grub screen shows kernal:

2.6.31-17

However, after running update manager, I have the latest kernal

2.6.32-22

What I want is to get rid of (delete) old version 2.6.31-17. 
I know how to do this in Synaptic Package Manager but the problem is that this old version can not be located. 

Could you please give me step-by-step instructions to go at it through the terminal? Do I first have to sign on to gedit? Please help, as I still consider myself a newbie. Thanks. [/COLOR][/SIZE][/FONT][FONT=Microsoft Sans Serif][COLOR=DarkRed]
[/COLOR][/FONT]

---

### Post by Elfy on 2010-05-21
You don't need gedit - remove it from synaptic - search for linux-image - find the -17 kernel and mark for removal. Update-grub should run and it will not be there in grub next time you boot.

Personally though I keep the current and previous versions installed.

---

### Post by droadtrip on 2010-05-21
[FONT=Microsoft Sans Serif][SIZE=2][COLOR=Black]That's my problem. "-17" is not in Synaptic Package Manager to remove. I tried a lot of different ways and could not locate this old version, which was the version that was on the install disc prior to getting the latest updates. [/COLOR][/SIZE][/FONT]

---

### Post by Elfy on 2010-05-21
Try updating grub 

```
sudo update-grub
```

If it shows it's found the -17 use the name to remove the kernel - mine are generic kernels - there are others such as PAE 

```
sudo apt-get remove linux-image-2.6.32-17-generic
```

update-grub should run again.

I am wondering why it is not there in synaptic - it should be there - even if it is not installed.

```
sudo update-grub
[sudo] password for kevin: 
Generating grub.cfg ...
Found background image: SmoothMoment.png
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found PCLinuxOS on /dev/sdb1
done
```

---

### Post by droadtrip on 2010-05-21
[FONT=Tahoma][COLOR=Black][SIZE=2]E:  Couldn't find package linum-image-2.6.31-17-generic

I ran update grub command in terminal again and saw the line with -17-generic was still there. It is bizarre to me why Synaptic is not picking this up and the terminal sees the grub screen but can't find the package to remove it. I guess i could just leave it there. Anyway that I could at least edit Grub by hiding this line "-17" ?

I appreciate you helping out. [/SIZE][/COLOR][/FONT]

---

### Post by Elfy on 2010-05-21
Couldn't find package **linum**-image-2.6.31-17-generic

try looking for linux

changed the spelling in the command I have

---

### Post by droadtrip on 2010-05-21
[FONT=Tahoma][SIZE=2][COLOR=DarkRed]I tried typing "linux" in the place of "linum" and got the same error response that the package was not found. [/COLOR][/SIZE][/FONT]

---

### Post by Elfy on 2010-05-21
Can you run sudo update-grub and paste the whole output please.

---

### Post by droadtrip on 2010-05-21
[FONT=Impact][SIZE=2][COLOR=DarkRed][COLOR=Black]stmpoodle@stmpoodle-laptop:~$ sudo update-grub
[sudo] password for stmpoodle: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
stmpoodle@stmpoodle-laptop:~$ [/COLOR]
[/COLOR][/SIZE][/FONT]

---

### Post by Elfy on 2010-05-21
aah :) try this 

```
sudo apt-get remove linux-image-2.6.31-17-generic
```

---

### Post by Soul-Sing on 2010-05-21
```
sudo apt-get remove linux-image-2.6.31-17-generic
```

```
sudo update-grub
```

first line had a small syntax error.

---

### Post by droadtrip on 2010-05-21
[FONT=Impact][SIZE=2]stmpoodle@stmpoodle-laptop:~$ sudo update-grub
[sudo] password for stmpoodle: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
stmpoodle@stmpoodle-laptop:~$ sudo apt-get remove linux-image-2.6.31-17-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.31-17-generic
stmpoodle@stmpoodle-laptop:~$ 
[/SIZE][/FONT]
[SIZE=2][COLOR=Blue]
LOL - it's just not my night on this one. I got the error message again "couldn't find package"[/COLOR][/SIZE]

---

### Post by rnerwein on 2010-05-21
hi
ok - try this:
sudo apt-get remove --purge 2.6.31-17-generic
sudo update-grub

have fun
ciao

---

### Post by droadtrip on 2010-05-21
[SIZE=2]stmpoodle@stmpoodle-laptop:~$ sudo apt-get remove --purge 2.6.31-17-generic
[sudo] password for stmpoodle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]E: Couldn't find package 2.6.31-17-generic[/COLOR]
stmpoodle@stmpoodle-laptop:~$ sudo apt-get remove purge 2.6.31-17-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]E: Couldn't find package purge[/COLOR]
stmpoodle@stmpoodle-laptop:~$ sudo apt-get remove -purge linux-image-2.6.31-17-generic
[COLOR=Red]E: Command line option 'p' [from -purge] is not known.[/COLOR]
stmpoodle@stmpoodle-laptop:~$ sudo apt-get remove --purge linux-image-2.6.31-17-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Red]E: Couldn't find package linux-image-2.6.31-17-generic[/COLOR]
stmpoodle@stmpoodle-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
stmpoodle@stmpoodle-laptop:~$ [/SIZE]

[FONT=Impact][SIZE=2][COLOR=Navy]It looks like the PURGE command is treated the same as REMOVE and the system can't find the package or line to remove it, even though "2.6.31-17-generic" is there in grub.[/COLOR][/SIZE][/FONT]

---

### Post by mikewhatever on 2010-05-21
Alright, lets see what kernel versions are installed:

dpkg -l | grep linux-image

---

### Post by droadtrip on 2010-05-21
[FONT=Impact][SIZE=2]stmpoodle@stmpoodle-laptop:~$ dpkg -l | grep linux-image
rc  **[COLOR=Red]linux-image[/COLOR]**-2.6.32-21-generic        2.6.32-21.32                                    Linux kernel image for version 2.6.32 on x86
ii  [COLOR=Red]**linux-image**[/COLOR]-2.6.32-22-generic        2.6.32-22.33                                    Linux kernel image for version 2.6.32 on x86
ii  [COLOR=Red]**linux-image**[/COLOR]-generic                  2.6.32.22.23                                    Generic Linux kernel image
stmpoodle@stmpoodle-laptop:~$ 

I typed the terminal command in and this is what I received in response.[/SIZE][/FONT]

---

### Post by mikewhatever on 2010-05-21
As expected, there is not linux-image-2.6.31-17-generic. I suspect that you must have upgraded, and what grub finds is a bunch of old config files, probably in /boot. What's the output of **ls /boot**?
Also try:
sudo apt-get --purge autoremove

---

### Post by droadtrip on 2010-05-21
[FONT=Impact][SIZE=2][COLOR=DarkRed]to mikewhatever: I agree. But I'll have to put this little project temporarily on hold while the PC is being serviced. It's nothing to do with Linux or Ubuntu. In fact it was giving me serious problems of flickering screen in Windows Vista. So to test if whether it was software or hardware, I worked in Ubuntu (its dual booted) for a few days. Ironically, the same problems only happened about 10% of the time in Ubuntu compared to 100% in Windows. But that was still evident that it was the system bios misbehaving and needed professional help under warranty. 

As soon as I get it back in healthy shape again, I will contact you here. Please keep the subscription to this thread for a while. Thanks. [/COLOR][/SIZE][/FONT]

---

