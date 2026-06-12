---
title: "nvidia low res mode-how to fix or tutorial please?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by flyingsolo on 2010-06-22
Since upgrading to 10.04 I've been getting this message at login about ubuntu can only run in low res. mode etc. which is very common I realize.  In spite of reading other posts on this, i still can't seem to get it fixed once and for all.  Would someone be willing to assist me to fix this or just direct me to the best tutorial or post already existing?
(I actually had quite good resolution but was getting the message anyway & so tried following a solution in another post that has resulted in me actually having lower res now than what I started with!  Sorry, I didn't mark the post I followed to go back to it)
thanks
(and, yes, I know this has probably been asked lots of times before...just looking for a good comprehensive discussion/solution)

---

### Post by cariboo on 2010-06-23
Have you tried:

```
sudo nvidia-xconfig
```

to create a new /etc/X11/xorg.conf? Once the new file has been created, reboot.

---

### Post by rollin on 2010-06-23
I had some nice issues with my nvidia card recently =( 

First thing I did was:

```
lspci -v | grep VGA

```Now download the correct driver version with wget from nvidia.com. I only say this because the ubuntu restricted driver failed.
If this suggestion is on the right track for you. Once you've got the file downloaded. Go to tty1 and do the following:

```
sudo /etc/init.d/gdm stop (to kill the x session)
cd to the directory where the driver you downloaded is...
sudo sh <NVIDIA.file name> (use the command "ls" in the directory if you can't remember the name)
```If you get an error about hash sum mismatch you'll see why I used wget to download it!!

---

