---
title: "installed?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by AJHunter on 2009-09-22
Hey, I think i just installed XUbuntu, and a black screen popped up at the end of instalation. It's covered in text and looks like it wants input: "ubuntu@ubuntu:~$" is the exact thing it says (minus the quote marks). now for a n00bish question: is this good!?

:confused:
:???:

---------------- Now playing: [Jonathan Coulton - Skullcrusher Mountain](http://www.foxytunes.com/artist/jonathan_coulton/track/skullcrusher_mountain) via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by halitech on 2009-09-22
means you got the base install done so thats a step in the right direction :)

Did you use the server install or a minimal install to get things going? If you did either of them, then you need to install the desktop. This should work:
```
sudo apt-get install xubuntu-desktop
```

if you used a live cd, then we have another issue to deal with.

---

### Post by AJHunter on 2009-09-23
is it live cd if i used a cd but just hit install instead of "try xubuntu with no change to my computer"?

---

### Post by QIII on 2009-09-23
Yes.

Be advised, however, that it will run very slowly from the CD.  This is not how it will perform after installing it.

---

### Post by laffinet on 2009-09-23
> **QIII said:**
> Yes.


I think you misread his post: he said he hit "Install".

In which case the answer is No, you're not using the liveCD, you installed Xubuntu on your computer.

---

### Post by AJHunter on 2009-09-23
THANK YOU!!!
I have been trying for days to get Xubuntu to install on my piece of junk computer.
 
[-o<I  litteraly had to pray that Xubuntu would install!
:lolflag:

---

### Post by QIII on 2009-09-23
> **laffinet said:**
> I think you misread his post: he said he hit "Install".

In which case the answer is No, you're not using the liveCD, you installed Xubuntu on your computer.

Quite right.  I blame it on the bifocals.

---

### Post by 3rdalbum on 2009-09-23
> **AJHunter said:**
> Hey, I think i just installed XUbuntu, and a black screen popped up at the end of instalation.

In other words: You chose "Install Xubuntu", there was a progress bar, and at the end of it you've just got a terminal.

Unless you were given a graphical screen for setting up your username, language, how much space you want etc, then you have **not** installed Xubuntu. It looks like it is having trouble detecting the right settings for your monitor.

The "Install Xubuntu" option at the menu will actually boot up Xubuntu and then a very minimal session which runs the GUI installer program.

Try Xubuntu in Safe Graphics Mode (if I remember correctly, the option is there on the initial menu), and if you can get to the desktop, then double-click on the Install icon on the desktop to run the installer.

---

### Post by AJHunter on 2009-09-23
> **halitech said:**
> means you got the base install done so thats a step in the right direction :)

Did you use the server install or a minimal install to get things going? If you did either of them, then you need to install the desktop. This should work:
```
sudo apt-get install xubuntu-desktop
```if you used a live cd, then we have another issue to deal with.


  I did this and now it says
```
reading package lists... done
building dependency tree
reading state information... done
xubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$
```

I've used computers enough to know that ":~@" is asking for string input, which I find funny, a computer asking for string. (stupid joke)
so, now what?

---

### Post by halitech on 2009-09-23
try this
```
startxfce
```

---

### Post by LewRockwell on 2009-09-23
maybe it's not playing nicely with your hardware

.

---

### Post by AJHunter on 2009-09-24
> **halitech said:**
> try this
```
startxfce
```
now what?

---

### Post by halitech on 2009-09-24
> **AJHunter said:**
> now what?

what happened?

---

### Post by AJHunter on 2009-09-26
> **halitech said:**
> what happened?
This: (sorry its a picture, I don't have time to type it in!)
The link is so that the picture is still of a manageable size. It's actual HUGE!

[http://yfrog.com/0jdscn1698sj](http://yfrog.com/0jdscn1698sj)

If it were full sized:

[IMG]http://img98.imageshack.us/img98/8118/zomgbig.png[/IMG]

---

### Post by 3rdalbum on 2009-09-26
It looks like your CD is bad. The error messages are most likely saying that it can't read the data from the CD.

Burn the disc again, but make sure you use good quality CD media, and burn at 8x speed. When you boot up the CD, the system should load up and then either take you to the desktop or bring up an installer screen.

---

### Post by aljoriz on 2009-09-26
what are the specs of the pc? 

I tried installing xubuntu 9.4 on a pentium3 450mhz machine and it didn't work they say using a 8.04LTS is a better option.  You might consider that.

---

### Post by theozzlives on 2009-09-26
If you noticed OPs first post, the prompt says ubuntu@ubuntu. Live CD user. No it's not installed. It didn't have you partition your hard drive, ask your name-username-password. Somethings wrong with the CD or .ISO.

---

### Post by AJHunter on 2009-09-26
> **theozzlives said:**
> If you noticed OPs first post, the prompt says ubuntu@ubuntu. Live CD user. No it's not installed. It didn't have you partition your hard drive, ask your name-username-password. Somethings wrong with the CD or .ISO.

  no, I went through the install proscess.

---

### Post by halitech on 2009-09-26
found this on another site:

These errors can be due to a variety of reasons:

* bad media (solution: try burning the iso image to a new disc)
* a bad dvd drive (solution: if possible, try using a different cd/dvd drive)
* bad memory modules (solution: use memtest86+ to check your memory)
* a corrupted iso image (solution: run an md5 checksum, and if they don't match, download the iso image again)
* an optical drive connected via SATA instead of PATA and running in Enhanced mode (solution: change the IDE configuration to "compatible" in the BIOS)

[https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)

---

