---
title: "Ahhh i lost everything!!"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by xhaansx on 2010-05-17
Well, the title pretty much explains it. I upgraded to 10.04, and all my windows had no title bars/you couldn't resize them or move them/there was no taskbar, so I tried installing some themes while in Failsafe Gnome - to see if it would reset the missing components to their defaults or at least something usable...

I managed to get my taskbar etc back while under regular Gnome - which is quite nice, but I'm afraid it might have gone a little too far. Now, I have nothing. My desktop is gone, and so is my documents, and my music, and yeah well pretty much everything...

Here is the output of "history" in the terminal:
```
1  sudo add-apt-repository ppa:bisigi
    2  sudo aptitude update
    3  sudo aptitude install bisigi-themes
    4  sudo aptitude install balanzan-theme
    5  systemsettings
    6  gnome-panel
    7  gconftool-2 – -shutdown
    8  rm -rf ~/.gconf/apps/panel
    9  pkill gnome-panel
   10  run ps -A | grep gnome-panel
   11  ps -A | grep gnome-panel
   12  alt-f2 gconftool –recursive-unset /apps/panel && killall gnome-panel
   13  alt-f2 gconftool –recursive-unset /apps/panel && gnome-panel
   14  gconftool – -recursive-unset /apps/panel
   15  pkill gnome-panel
   16  rm -rf ~ /.gconf/apps/panel
   17  sudo rm -rf ~ /.gconf/apps/panel
   18  gconftool – -recursive-unset /apps/panel 
   19  gconftool-2 – -shutdown
   20  rm -rf ~ /.gconf/apps/panel
   21  pkill gnome-panel
   22  logout
   23  exit
   24  history
```

---

### Post by ubername on 2010-05-17
Have the files actually gone or have you just lost them when you log in? try 'nautilus' from the terminal and see what you get. Look in home/<you username>

I am assuming that you actually have a GUI to work in, based on your post.

Another thing to try could be to create a new user and see if you can piece together what you had before.

run

```
users-admin
```

and create a new user, then login with that. You might want to make the new user an admin as that will be easier to work with if you can't easily recover your previous user.

---

### Post by xhaansx on 2010-05-17
--> Yes, I do have a usable GUI at the moment.

Also, all my base folders (Documents, Downloads, Music etc) are empty under my home directory. Other user's folders aren't empty - only mine are missing. I'll try creating another user though and seeing what happens, not sure how it will help though?

---

### Post by ubername on 2010-05-17
Oh dear - I am afraid you're right, creating a new user probably won't help. I had thought perhaps that you were simply having some kind of problems seeing your data. 

A look at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) may help.

---

### Post by eeperson on 2010-05-17
```
rm -rf ~ /.gconf/apps/panel
```

I think the lines you have like this are the cause of your problems.  You have an extra space in there so 'rm' thinks you are trying to delete two things '~' and '/.gconf/apps/panel'.

---

### Post by ubername on 2010-05-17
> **eeperson said:**
> ```
rm -rf ~ /.gconf/apps/panel
```

I think the lines you have like this are the cause of your problems.  You have an extra space in there so 'rm' thinks you are trying to delete two things '~' and '/.gconf/apps/panel'.


Very good spot! But bad news.

---

### Post by xhaansx on 2010-05-17
Uh oh... Hmm, do you know what type of DataRecovery I should attempt? (Based off of ubername's [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) link). Tentatively I would say this is considered a "damaged filesystem or drive"? The only other thing that looks plausible is perhaps "Ntfsprogs"?

---

### Post by flyfishingphil on 2010-05-17
> **xhaansx said:**
> Well, the title pretty much explains it. I upgraded to 10.04, and all my windows had no title bars/you couldn't resize them or move them/there was no taskbar, so I tried installing some themes while in Failsafe Gnome - to see if it would reset the missing components to their defaults or at least something usable...

I managed to get my taskbar etc back while under regular Gnome - which is quite nice, but I'm afraid it might have gone a little too far. Now, I have nothing. My desktop is gone, and so is my documents, and my music, and yeah well pretty much everything...

Here is the output of "history" in the terminal:
```
1  sudo add-apt-repository ppa:bisigi
    2  sudo aptitude update
    3  sudo aptitude install bisigi-themes
    4  sudo aptitude install balanzan-theme
    5  systemsettings
    6  gnome-panel
    7  gconftool-2 – -shutdown
    8  rm -rf ~/.gconf/apps/panel
    9  pkill gnome-panel
   10  run ps -A | grep gnome-panel
   11  ps -A | grep gnome-panel
   12  alt-f2 gconftool –recursive-unset /apps/panel && killall gnome-panel
   13  alt-f2 gconftool –recursive-unset /apps/panel && gnome-panel
   14  gconftool – -recursive-unset /apps/panel
   15  pkill gnome-panel
   16  rm -rf ~ /.gconf/apps/panel
   17  sudo rm -rf ~ /.gconf/apps/panel
   18  gconftool – -recursive-unset /apps/panel 
   19  gconftool-2 – -shutdown
   20  rm -rf ~ /.gconf/apps/panel
   21  pkill gnome-panel
   22  logout
   23  exit
   24  history
```
I totally sympathize with you. I have Vista and upgraded from 9.10 to 10.04. Found some compatibility problems, and no answers to overcoming them, and decided to remove the 10.04 and try again. OE! OE!OE! (Operator Error!) When it was done it had formatted the entire drive. Lost everything and, since I had placed copies of the my files in from the external HD, including the backup/restore that I had there. (Pretty new to Ubuntu, if you hadn't figured that out.)

Wrong Button!! Bad User! Bad, Bad User!

OK, now I've got Vista back in, from the restore discs I made when I first got this laptop, but would love to go back to using the 10.04. Unfortunately it won't talk to my Sony Ericsson W760/PC Suite, my Magellan gps, and a couple of other things.

I will probably re-install 10.04 as the only operating system but there are a few things I use for business that currently require windows. Does anybody know of a good (for Dummies) style guide to VBox? I've looked at a couple of the guides on the VBox website but they seem to start at the "already knows how to install and use it, just needs to tweak it" point.

Thanks for any guides or threads you may know of.

Love Ubuntu

---

### Post by 2hot6ft2 on 2010-05-17
> **eeperson said:**
> ```
rm -rf ~ /.gconf/apps/panel
```

I think the lines you have like this are the cause of your problems.  You have an extra space in there so 'rm' thinks you are trying to delete two things '~' and '/.gconf/apps/panel'.
I think you hit the nail on the head.
Ouch

---

### Post by 2hot6ft2 on 2010-05-17
You can try to get some back with testdisk. I don't know how much luck you'll have though.
[How to: Recover data with testdisk!]("http://ubuntuforums.org/showthread.php?t=387922")

Good luck.
:popcorn:

---

### Post by DGortze380 on 2010-05-17
> **xhaansx said:**
> Uh oh... Hmm, do you know what type of DataRecovery I should attempt? (Based off of ubername's [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) link). Tentatively I would say this is considered a "damaged filesystem or drive"? The only other thing that looks plausible is perhaps "Ntfsprogs"?

get yourself some extra storage space.
Image your drive using dd
Run photorec on the image.

---

### Post by xhaansx on 2010-05-17
Sorry spoke too soon, before resigning as below, how does one go about imaging their drive with "dd"?

Yeaaah I think it's all gone for good. TestDrive didn't seem to help much, if anyone has some epic-heroic-messiah program they know of I'm all ears, otherwise, tentative RIP my many months of school work.. and more importantly none-school work(:

---

### Post by DGortze380 on 2010-05-18
> **xhaansx said:**
> Sorry spoke too soon, before resigning as below, how does one go about imaging their drive with "dd"?

Yeaaah I think it's all gone for good. TestDrive didn't seem to help much, if anyone has some epic-heroic-messiah program they know of I'm all ears, otherwise, tentative RIP my many months of school work.. and more importantly none-school work(:

This will make a forensic copy of you drive in case you mess up any recovery procedures, this should ALWAYS be your FIRST step.


Find you hard drive

```

sudo fdisk -l

```

replace /dev/sdx with the path for your drive

```

dd if=/dev/sdx of=/path/to/external/drive/image.dd

```

Then run photorec against your image or drive but not both.
Photorec is a totally different approach to data recovery than testdisk, and will like recover many of your files if you haven't mounted the drive and overwritten the data (another reason to image immediately).

---

### Post by -humanaut- on 2010-05-18
> **xhaansx said:**
> Well, the title pretty much explains it. I upgraded to 10.04, and all my windows had no title bars/you couldn't resize them or move them/there was no taskbar, so I tried installing some themes while in Failsafe Gnome - to see if it would reset the missing components to their defaults or at least something usable...

I managed to get my taskbar etc back while under regular Gnome - which is quite nice, but I'm afraid it might have gone a little too far. Now, I have nothing. My desktop is gone, and so is my documents, and my music, and yeah well pretty much everything...

Here is the output of "history" in the terminal:
```
1  sudo add-apt-repository ppa:bisigi
    2  sudo aptitude update
    3  sudo aptitude install bisigi-themes
    4  sudo aptitude install balanzan-theme
    5  systemsettings
    6  gnome-panel
    7  gconftool-2 – -shutdown
    8  rm -rf ~/.gconf/apps/panel
    9  pkill gnome-panel
   10  run ps -A | grep gnome-panel
   11  ps -A | grep gnome-panel
   12  alt-f2 gconftool –recursive-unset /apps/panel && killall gnome-panel
   13  alt-f2 gconftool –recursive-unset /apps/panel && gnome-panel
   14  gconftool – -recursive-unset /apps/panel
   15  pkill gnome-panel
   16  rm -rf ~ /.gconf/apps/panel
   17  sudo rm -rf ~ /.gconf/apps/panel
   18  gconftool – -recursive-unset /apps/panel 
   19  gconftool-2 – -shutdown
   20  rm -rf ~ /.gconf/apps/panel
   21  pkill gnome-panel
   22  logout
   23  exit
   24  history
```

wooo why is there a sudo rm -rf?!

---

### Post by xhaansx on 2010-05-19
DGortze380!! THANK YOU VERY MUCH!! I imaged and photorec'd successfully, and while it's hard to find files since there are thousands and thousands found and the file names are skewed, most if not all are saved! Learned a lot with this mistake, thanks guys.

> **-humanaut- said:**
> wooo why is there a sudo rm -rf?!

Hmm well at the time I didn't really know what sudo rm -rf did... Rookie mistake if ever there was one, but it was what I was told to do on some website I found while searching for fixes to my disfunctional 10.04.

---

### Post by DGortze380 on 2010-05-19
> **xhaansx said:**
> DGortze380!! THANK YOU VERY MUCH!! I imaged and photorec'd successfully, and while it's hard to find files since there are thousands and thousands found and the file names are skewed, most if not all are saved! Learned a lot with this mistake, thanks guys.



Hmm well at the time I didn't really know what sudo rm -rf did... Rookie mistake if ever there was one, but it was what I was told to do on some website I found while searching for fixes to my disfunctional 10.04.

Glad you got your files back.  In the future, as soon as you realize your mistake, stop using the drive and image immediately.

Your mistake was:
sudo - run with root privileges
rm   - remove (delete permanently)
-r   - recursive (delete all sub folders and files)
-f   - force (don't ask for confirmation, just do it)
~    - your home directory

So sudo rm -rf ~ means as root, don't ask for confirmation and delete all files and folders in my home directory.

---

