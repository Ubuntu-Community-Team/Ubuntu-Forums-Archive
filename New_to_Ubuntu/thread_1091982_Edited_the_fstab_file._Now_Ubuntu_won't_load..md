---
title: "Edited the fstab file. Now Ubuntu won't load."
date: 2009-03-09
forum: New to Ubuntu
---

### Post by kvan393 on 2009-03-09
I added a line to my fstab to mount my windows partition every time my laptop boots. Now, when I load Ubuntu, there is some sort of error and it tells me to check my hard drive.
It ends with something saying, "Dropping to shell"

What do I do?
I typed in help for a list of commands, but I don't know what to do from there.

:(

---

### Post by taurus on 2009-03-09
Are you able to boot to into recovery mode from GRUB menu?

Otherwise, you need to boot your machine with Ubuntu LiveCD.  Mount the partition where / (root filesystem) is and fix your /etc/fstab.

---

### Post by iaculallad on 2009-03-09
Could you post your current fstab file.

---

### Post by Crafty Kisses on 2009-03-09
What are the results of these commands?
```
sudo cat /etc/fstab
sudo fdisk -lu
```

---

### Post by kvan393 on 2009-03-09
I'm new to Ubuntu, so I kind of don't know what a GRUB menu is.
How do I boot it with the LiveCD.

I would if I could, but I don't know how to get into Ubuntu with a command. I did it before, but I don't remember what I typed in.

---

### Post by sandyd on 2009-03-09
when it drops to shell, enter in the commands they said above......

if it asks you to enter in your username, enter it in
the password is hidden, so when you type it in, nothing will show up

---

### Post by kvan393 on 2009-03-09
I tried booting Ubuntu again, but it went back to BusyBox

I can get to the GRUB menu also, but I don't know what to do from there either.

EDIT!

I put  something like
"/dev/sda2 /media/windowslol ntfs-3g 0 0"
in the fstab.

Was that wrong?

---

### Post by sandyd on 2009-03-12
> **kvan393 said:**
> I tried booting Ubuntu again, but it went back to BusyBox
 
I can get to the GRUB menu also, but I don't know what to do from there either.
 
EDIT!
 
I put something like
"/dev/sda2 /media/windowslol ntfs-3g 0 0"
in the fstab.
 
Was that wrong?
 
Whoah!!
 
that was sooo wrong buddy
 
there should be the mounting options AFTER "ntfs-3g"
 
well at least you know whats wrong now
 
boot a livecd, delete that line, and boot up ubuntu again :)

---

### Post by kanikilu on 2009-03-12
FWIW, I always find it's a good idea to manually test a new mountpoint before adding it into fstab. Also, once you make changes to fstab, issue ```
sudo mount -a
``` to make sure it's working before your next reboot.

---

### Post by taurus on 2009-03-12
> **kvan393 said:**
> I tried booting Ubuntu again, but it went back to BusyBox

I can get to the GRUB menu also, but I don't know what to do from there either.

EDIT!

I put  something like
"/dev/sda2 /media/windowslol ntfs-3g 0 0"
in the fstab.

Was that wrong?

It should at least look something like

```
/dev/sda2 /media/windowslol ntfs-3g **[COLOR="Blue"]defaults[/COLOR]** 0 0
```

---

### Post by kvan393 on 2009-03-12
> **carlee said:**
> Whoah!!
 
boot a livecd, delete that line, and boot up ubuntu again :)

Well, I tried but I think I did it wrong because I couldn't edit the real fstab. 
How do I do it?

Another thing I did.
Somehow I booted into Ubuntu with no problems. Then I deleted the line in fstab through terminal.
But when I restarted, it still said I had that line in.

---

### Post by oldos2er on 2009-03-12
Are you able to boot into recovery mode? Did you make a backup copy of fstab before you edited it?

---

### Post by stchman on 2009-03-12
> **kvan393 said:**
> I'm new to Ubuntu, so I kind of don't know what a GRUB menu is.
How do I boot it with the LiveCD.

I would if I could, but I don't know how to get into Ubuntu with a command. I did it before, but I don't remember what I typed in.

You should have installed the NTFS config package.

```
sudo apt-get install ntfs-config
```

This will bring up a GUI to mount NTFS drives.  The only thing is that ntfs-config wants to make your mounts read/write.

---

### Post by kvan393 on 2009-03-12
> **oldos2er said:**
> Are you able to boot into recovery mode? Did you make a backup copy of fstab before you edited it?
I cannot. And stupid me forgot to do that. 

> **stchman said:**
> You should have installed the NTFS config package.

```
sudo apt-get install ntfs-config
```

This will bring up a GUI to mount NTFS drives.  The only thing is that ntfs-config wants to make your mounts read/write.

I installed that app, but then it only had the bottom option available to check. (Not the top one also). When I pressed okay, nothing else happened. I uninstalled and installed again, but the same thing happens.

---

### Post by oldos2er on 2009-03-12
Now you know (to always back up system files before altering them). 

 To edit your fstab from the LiveCD, you first must mount the partition it's on. Open a terminal (Applications, Accessories, Terminal) and enter
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```
assuming your boot partition is sda1.
Then run
```
gksu gedit /media/sda1/etc/fstab

```
to remove or edit the offending line.

---

