---
title: "2 problems, mounting an iso + desktop help."
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Blue Summer on 2010-09-27
My biggest problem is i've got the starcraft2 iso file on my desktop and i've tried to follow some mounting script tutorials but they've all failed, so if anyone can tell me how to mount an iso, so I can install the game it'd be really appreciated!

Second problem is sometimes randomly when I click on the taskbar to oepn a program it moves it to another desktop a random one and it also makes it impossible to get back it's like half on one screen and half on another and it won't recognise me clicking on it.

Thanks guys!

---

### Post by 0N3 on 2010-09-27
Have you tried furiousISO or g-MountISO have you the desktop cube enabled in compiz????

---

### Post by Paqman on 2010-09-27
> **Blue Summer said:**
> if anyone can tell me how to mount an iso, so I can install the game it'd be really appreciated!

Sure: double click it. This is a legally obtained ISO, I take it?

> 
Second problem is sometimes randomly when I click on the taskbar to oepn a program it moves it to another desktop a random one and it also makes it impossible to get back it's like half on one screen and half on another and it won't recognise me clicking on it.


That sounds pretty random. Do you mean this happens when you click on the bottom panel to switch to a window that's already open, or do you mean this happens when you launch an app from the menu? Are you using Compiz? Have you got any special window placement rules in the Place Windows plugin?

---

### Post by 0N3 on 2010-09-27
Furius ISO Mount sorry :-<

---

### Post by Blue Summer on 2010-09-27
Double clicking it just opens it in winrar through wine.

Gmount iso doesn't work it just kicks up an error for me.

And yeah i've got compiz desktop cube enabled, it's when I go to open a window that's minimized

edit: And yes it's a legally obtained ISO

---

### Post by 0N3 on 2010-09-27
Im not a gamer but ive never had a problem using gmount-iso mounted DVD ISO images ect and played them and by the way why have you installed winrar using wine?? 

sudo apt-get install unrar

or archive manager should open .rar extension

---

### Post by Blue Summer on 2010-09-27
I've no idea lol I couldn't figure out how to install winrar for linux so I just downloaded it in wine, it was easy enough although it's crap when you open winrar while playing a game and it hides in the background.

This is the error I get with gmount:

An error occured
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

trying to mount it in a folder called isoimage which is in the same directory as cdrom and cdrom0, i'm not sure if I made that folder myself during a mounting tutorial.

---

### Post by MooPi on 2010-09-27
Magicdisc : Don't know how that will work in Wine but does wonders in virtual desktop.
[http://www.magiciso.com/tutorials/miso-magicdisc-overview.htm]("http://www.magiciso.com/tutorials/miso-magicdisc-overview.htm")

---

### Post by Blue Summer on 2010-09-27
I got it mounted finally using some mount command in terminal I found but the installer is giving me an error saying there's no data lol.

It's also saying the mounted file is only about 115mb when it should be 7.3gb

---

### Post by Paqman on 2010-09-27
> **Blue Summer said:**
> I got it mounted finally using some mount command in terminal I found but the installer is giving me an error saying there's no data lol.

It's also saying the mounted file is only about 115mb when it should be 7.3gb

Have you verified that the ISO actually is what it's supposed to be? Depending on where this ISO comes from it might be highly prudent to make sure the MD5 or SHA hash is what it should be.

---

### Post by Blue Summer on 2010-09-27
it should be, no one else has had a problem installing it on windows

---

### Post by ajgreeny on 2010-09-27
If I right click on an ISO file in nautilus I get an option in the context menu to "Open with Archive Mounter" which mounts it on my desktop.

I assume that is something that all Ubuntu installs can do, as I don't remember installing anything myself to carry out that action.

Perhaps different ISOs act differently, but all of those that I have seen seem to work that way with no problem.

---

### Post by beew on 2010-09-27
Since you want  to mount the iso for installation (rather than just to view it or play music files, say) I don't think the tools mentioned here would work because for installation purpose 1) you need to know the directory where the iso is mounte (so furiusiso for example would not work) d and 2) you need root privilege (so gmount wouldn't work either).

It seems that you have to do command line.

First create a directory where the iso would be mounted (I don't remember whether you need "sudo" or not here)

```
mkdir mount
``` ("mount" is a directory in your home folder, but you can place it elsewhere, just remember to enter the path name)

Then mount the iso
```

sudo mount -t iso9660 -o loop path_of_your_iso  /mount 
``` (it seems that you can't run the installer in the following step if  you mount your iso in any other way,--though it is just my experience) Then you cd into mount directory and run the installer.

Someone knowlegeable may point you to some mount tools whhich would automate the process, but I don't know of any.
'
**Edited:** If you are trying to install Windows programs then I would simply extract the iso into a folder (using acetoneiso for example) and run the install.exe file with WINE.--never try to run WINE with sudo even though I am not sure whether mounting with sudo counts, but just to be on the safe side...

---

### Post by Blue Summer on 2010-10-06
> **beew said:**
> Since you want  to mount the iso for installation (rather than just to view it or play music files, say) I don't think the tools mentioned here would work because for installation purpose 1) you need to know the directory where the iso is mounte (so furiusiso for example would not work) d and 2) you need root privilege (so gmount wouldn't work either).

It seems that you have to do command line.

First create a directory where the iso would be mounted (I don't remember whether you need "sudo" or not here)

```
mkdir mount
``` ("mount" is a directory in your home folder, but you can place it elsewhere, just remember to enter the path name)

Then mount the iso
```

sudo mount -t iso9660 -o loop path_of_your_iso  /mount 
``` (it seems that you can't run the installer in the following step if  you mount your iso in any other way,--though it is just my experience) Then you cd into mount directory and run the installer.

Someone knowlegeable may point you to some mount tools whhich would automate the process, but I don't know of any.
'
**Edited:** If you are trying to install Windows programs then I would simply extract the iso into a folder (using acetoneiso for example) and run the install.exe file with WINE.--never try to run WINE with sudo even though I am not sure whether mounting with sudo counts, but just to be on the safe side...


Unfortunatly the installer just opens a blank wine box and then closes, I talked to someone I knew and they said if you're mounting it for installation you have to find out which type of iso it is. This is so much simpilar in windows just get daemon tools and it's done ffs lol

---

