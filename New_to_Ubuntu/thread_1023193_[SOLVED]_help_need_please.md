---
title: "[SOLVED] help need please"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by sunshine2 on 2008-12-27
was told to do 

sudo apt-get remove alsa-base alsa-utils linux-sound-base && sudo apt-get install alsa-base alsa-utils linux-sound-base

to try and help solve a problem with the sound but it has wiped the notebook and now it wont load up (this is not my notebook)and it wont re-boot from disk

---

### Post by ercferret18 on 2008-12-27
would it be possible to reinstall?

---

### Post by sunshine2 on 2008-12-27
have tryed the recovery disk but it wont run

---

### Post by Michael.Godawski on 2008-12-27
hi sunshine2,

> was told to do 

sudo apt-get remove alsa-base alsa-utils linux-sound-base && sudo apt-get install alsa-base alsa-utils linux-sound-base

to try and help solve a problem with the sound but it has wiped the notebook and now it wont load up (this is not my notebook)and it wont re-boot from disk

I guess something like this happened:

[http://ubuntuforums.org/showthread.php?t=627906](http://ubuntuforums.org/showthread.php?t=627906)

you removed your ubuntu-desktop and gdm and perhaps some other packages with the mentioned alsa packages. You can access the files on the drive with this guide:


[LIST]
[*][http://godawski.oxyhost.com/accesshd.html](http://godawski.oxyhost.com/accesshd.html)
[/LIST]
Have you tried to boot into the recovery mode and reinstall the ubuntu-desktop? Just guessing here, because I do not know which packages were removed together with the alsa ones.

Try to boot into the recovery mode and run:
```

apt-get install ubuntu-desktop
```

---

### Post by sunshine2 on 2008-12-27
how do i get it in to recovery mode?

---

### Post by Michael.Godawski on 2008-12-27
**Recovery Mode**

 
[LIST]
[*]Boot into Recovery Mode: during the start-up press ESC while you see the *GRUB Loading Stage* entry.
[*]From the Boot Menu select *Recovery Mode*
[*]Select *Drop to root shell prompt*
[/LIST]

But be cautious. You are acting as root, so every command will be executed, also the "harmful" ones; but you can try to reinstall the ubuntu destkop with

```
apt-get install ubuntu-desktop
```

To leave the root shell run
```
exit
```

Then select 
resume normal boot.

---

### Post by ugm6hr on 2008-12-27
In Hardy:

```
sudo apt-get remove -s alsa-base alsa-utils linux-sound-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  alsa-base alsa-utils fast-user-switch-applet gdm linux-sound-base
0 upgraded, 0 newly installed, 5 to remove and 15 not upgraded.
Remv alsa-base [1.0.16-0ubuntu4]
Remv fast-user-switch-applet [2.22.0-0ubuntu2]
Remv gdm [2.20.7-0ubuntu1.1]
Remv alsa-utils [1.0.15-3ubuntu2]
Remv linux-sound-base [1.0.16-0ubuntu4]

```

So it does look like you have removed GDM.  Presumably the reinstall command didn't reinstall it.

You should be dropped at a command prompt.  In which case, you can still log in (same username and password), and reinstall GDM:
```
sudo apt-get install gdm fast-user-switch-applet
```

---

### Post by hyper_ch on 2008-12-27
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Michael.Godawski on 2008-12-27
> **ugm6hr said:**
> In Hardy:

```
sudo apt-get remove -s alsa-base alsa-utils linux-sound-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  alsa-base alsa-utils fast-user-switch-applet gdm linux-sound-base
0 upgraded, 0 newly installed, 5 to remove and 15 not upgraded.
Remv alsa-base [1.0.16-0ubuntu4]
Remv fast-user-switch-applet [2.22.0-0ubuntu2]
Remv gdm [2.20.7-0ubuntu1.1]
Remv alsa-utils [1.0.15-3ubuntu2]
Remv linux-sound-base [1.0.16-0ubuntu4]

```So it does look like you have removed GDM.  Presumably the reinstall command didn't reinstall it.

You should be dropped at a command prompt.  In which case, you can still log in (same username and password), and reinstall GDM:
```
sudo apt-get install gdm fast-user-switch-applet
```

hey ugm6hr,

nice idea to simulate the output of the command with the -s suffix:P.
For all the others:
```

sudo apt-get install -s something
```
is not going to install anything, it will only simulate the execution.

---

### Post by sunshine2 on 2008-12-27
it has all the bits that is is supposed to do and it is now says root@toshiba-user:~# i have not put anything in yet should i put in her user name and password

---

### Post by Michael.Godawski on 2008-12-27
as ugm6hr suggested...
try to reinstall the (probably) missing packages with 
```
apt-get install gdm fast-user-switch-applet
```

---

### Post by sunshine2 on 2008-12-27
that is not working this is what it is saying 

E: unable to fetch some archives, maybe run apt-get update or try with --fix-missing

---

### Post by sunshine2 on 2008-12-27
i dont know what i have done but i have managed to get it all back now

---

