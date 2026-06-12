---
title: "Login box not appearing"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by subhan.mps on 2010-06-16
Hello, my name is Subhan.I am a new user of linux Ubuntu.I have  installed Ubuntu 10.04 using Wubi and it was working very good but today  the login box is not appearing !!!!!:confused:

Can anyone help me plzzzzzzzzz 
and
Thanks in advance !!!!!

---

### Post by HomeSlixe on 2010-06-16
Click on  System -> Administration -> Login Window and change your setting as you see fit

---

### Post by subhan.mps on 2010-06-16
but how can i login?????
as login box is not appearing !!!!

---

### Post by HomeSlixe on 2010-06-16
are you logged in right now?

---

### Post by subhan.mps on 2010-06-16
nope
i am using windows xp !!!

---

### Post by HomeSlixe on 2010-06-16
so when you try to boot into ubuntu what does the screen look like?

if you can at least get past the kernel loading then you can hit ctrl alt f1 login the type sudo stop gdm then start gdm

---

### Post by subhan.mps on 2010-06-16
whenever I open ubuntu, its default background appears with no login box !!!
i can even open command-line by ctlr+alt+f1 ...........
yup i have entered sudo service gdm stop
then                      sudo service gdm start
but nothing changed

---

### Post by sydbat on 2010-06-16
Can you do anything when you go into Ubuntu? Like open a browser or anything?

It might be yet another case of file corruption due to Windows/ntfs not playing nice with the wubi install.

I hate wubi. Worst. Idea. Ever. I have seen nothing but problems with it.[/rant]

---

### Post by subhan.mps on 2010-06-16
I can't 
I can't even login so how can i open browser or something....!

and there is no problem with Wubi, it was working fine for me !

---

### Post by HomeSlixe on 2010-06-16
if you cant ctrl alt f1 this becomes tricky... sounds like xserver might be tweaking out on you. If i were you I would pop in my live cd go to try ubuntu open a command promt 

if you don't know the partion number of your ubuntu disk:
```
sudo cfdisk /dev/sda (or hda depending on your disk) 
```in fdisk type p 

now for the tricky part:
```
sudo -i
``````
mkdir /mnt/work
``````
mount /dev/(ubuntu drive eg. /dev/sda1) /mnt/work
``````

mount -o bind /dev /mnt/work/dev
mount -o bind /proc /mnt/work/proc
cp /proc/mounts /mnt/work/etc/mtab
``````
chroot /mnt/work/ /bin/bash
``````
dpkg-reconfigure xserver-xorg
```hope this helps!

---

### Post by subhan.mps on 2010-06-16
i can ctlr+alt+f1

---

### Post by HomeSlixe on 2010-06-16
login with ctrl alt f1 stop gdm then try reconfiguring xserver
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by HomeSlixe on 2010-06-16
if all else fails and you have nothing really important on ubuntu you can always re-install... might take less time to do that then to troubleshoot?


sorry forgot you were using wubi :S ... I would highly recommended downloading the ubuntu live cd

---

### Post by subhan.mps on 2010-06-16
sudo apt-get install --reinstall gdm
worked for me :D

thank you !!!

---

