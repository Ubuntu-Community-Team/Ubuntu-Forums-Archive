---
title: "No Gui"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by mikeab on 2011-01-15
HI, I've been using Ubuntu for a couple of months and found it quick and enjoyable, but I tried installing an old Nvidia graphics card and somehow stuffed up my display settings? Maybe something to do with the driver? I thought the card might be faulty so got rid of it. I'm not much of a computer person, so not too sure what went wrong or how to fix it, though I'm sure it must be something easy.

When I now try to boot into Ubuntu, it just comes up with a terminal? I think that's what you call it? lol I've just been frustrating myself trying to look for a solution..

Startx?

(EE) no devices detected
fatal server error: no screens detected...

ddxsiggiveup: closing log
giving up
xinit: no such file or directory (error 2): unable to connect to server
xnit: no such process (error3): server error

I'm having to use windows now and write everything down to list on here  lol

Any help would be much appreciated. I'm thinking about re-installing but don't want to lose all my bookmarks and passwords from firefox - most I'll never remember lol, plus a few other things.

Thanks alot.

---

### Post by yeats on 2011-01-15
> I'm not much of a computer person, so not too sure what went wrong or how to fix it, though I'm sure it must be something easy.

Don't be too sure!  Graphics problems are not really beginners' territory, and they are tricky to diagnose.  There are problems with 10.10 and nVidia graphics cards, so it looks like you hit one of those.

> I'm thinking about re-installing but don't want to lose all my bookmarks and passwords from firefox - most I'll never remember lol, plus a few other things.

If you can boot up with a liveCD (the install CD will do) you can go in and copy your /home/[yourusername]/.mozilla folder (which contains your firefox profile) to a USB drive and move it back to /home/[yourusername]/ after installing (and before opening firefox for the first time).  You can actually copy the entire /home/[yourusername/ folder and preserve all your settings if you wish.

---

### Post by davidmohammed on 2011-01-15
you installed the nvidia graphics driver how?

What graphics card are you now using?

You might have a xorg.conf file that is incompatible with your current graphics card.

Suggest login

then type

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then reboot

---

### Post by sdowney717 on 2011-01-15
I would download the nvidia graphics driver and run it like this
you can use wget to download at the command line, but you need to know which file to get. this one might work. I dont know where the others are on the nvidia site, you should be able to get the right one.

> wget [http://us.download.nvidia.com/XFree86/Linux-x86_32/256.53/NVIDIA-Linux-x86_64-256.53.run](http://us.download.nvidia.com/XFree86/Linux-x86_32/256.53/NVIDIA-Linux-x86_64-256.53.run)

ls lists the files

> scott@scott-desktop:~$ ls NVIDIA*
NVIDIA-Linux-x86_64-256.53.run
scott@scott-desktop:~$ 



run it as 
./nameoffile.run

---

### Post by sdowney717 on 2011-01-15
I cant seem to post that, it keeps destroying the url
so i post a screen shot showing how it reads

here is an ftp site of all the nvidia drivers
[ftp://download.nvidia.com/XFree86/Linux-x86_64/](ftp://download.nvidia.com/XFree86/Linux-x86_64/)

---

### Post by mikeab on 2011-01-15
> **yeats said:**
> Don't be too sure!  Graphics problems are not really beginners' territory...
 
 That sounds like it might be the go. I can boot from the Ubuntu CD I  installed from, and can copy the files to my Windows HD (a completely  separate HD), or memory stick if I want. Although I've tried copying the  entire /home/myusername file, some files won't copy - they're  restricted, but hopefully they're not important lol. In my other HD,  I've got like 10Gigs in the Ubuntu system file, and 130Gigs! in a fat32  file partition (for downloads and stuff and being compatible with  windows - but I wouldn't need to touch that with a re-install?), and 10  in a swap file partition. Maybe with a re-install I can give more space  to the Ubuntu partition also - I think it could do with more lol - and  not lose anything from the fat32 partition? I'm somewhat ignorant on  these matters  lol
 
 
> **davidmohammed said:**
> you installed the nvidia graphics driver how?...

I used the drivers update thing? Can't remember exactly - need to go back to the Gui to find out lol

I've tried renaming the xorg.config file, and no go. Also tried editing where it says nvidia
driver to vesa. But then xstart comes up with "kernel modesetting in  use, refusing to load". So I dunno, maybe there's something simple needs  to be changed, but for the life of me, I just don't have a clue  lol  

Well, at least I'm learning about how Linux works  lol

---

### Post by mikeab on 2011-01-15
> **sdowney717 said:**
> I cant seem to post that, it keeps destroying the url
so i post a screen shot showing how it reads

here is an ftp site of all the nvidia drivers
[ftp://download.nvidia.com/XFree86/Linux-x86_64/](ftp://download.nvidia.com/XFree86/Linux-x86_64/)

I'm just going to discard the nvidia graphics - I'm not sure if it's any good - plus I don't think my system doesn't get much improvement from it

---

### Post by davidmohammed on 2011-01-15
** removed**

---

### Post by davidmohammed on 2011-01-15
to turn off kernel modesetting you need to alter your boot option

during boot press shift to display your grub

press e to edit

find the line ending with quiet splash

add the following before "quiet splash"

nomodeset

then boot with

CTRL+X

to remove your old nvidia graphics drivers I think you need to use something like

sudo apt-get remove nvidia*

---

### Post by A_M_S on 2011-01-15
> **mikeab said:**
> 
Any help would be much appreciated. I'm thinking about re-installing but don't want to lose all my bookmarks and passwords from firefox - most I'll never remember lol, plus a few other things.


To avoid losing your bookmarks in the future you can install in your browser a bookmark synchronization plugin like xmarks or other similar.

---

### Post by mikeab on 2011-01-16
> **davidmohammed said:**
> to turn off kernel modesetting you need to alter your boot option

during boot press shift to display your grub

press e to edit

find the line ending with quiet splash

add the following before "quiet splash"

nomodeset

then boot with

CTRL+X

to remove your old nvidia graphics drivers I think you need to use something like

sudo apt-get remove nvidia*

Well that's done the trick! Start-up is a bit different - get a bit of text on the, what do you call it, the splash screen? Then some flickering before I hear the friendly Ubuntu drums and my desktop appears.  :p

Now, do I have to find a way to permanently alter the grub thingy? Don't want to have to keep adding "nomodeset" every time I boot.

Oh and I guess I should mark this as solved? As I've got the GUI - but with still a bit of tinkering to be done.

Oh and another thing. Thanks people!  :D

---

### Post by davidmohammed on 2011-01-16
to add nomodeset permanently

sudo nano /etc/default/grub

change the following line to read

GRUB_CMDLINE_LINUX="nomodeset"

CTRL O
CTRL X

then

sudo update-grub

---

### Post by mikeab on 2011-01-16
> **davidmohammed said:**
> to add nomodeset permanently

sudo nano /etc/default/grub

change the following line to read

GRUB_CMDLINE_LINUX="nomodeset"

CTRL O
CTRL X

then

sudo update-grub

Thanks for all your help Dave. I'd already researched what I needed to  do to permanently edit the GRUB, although at first I was looking for a  menu.lst, and wondering why I didn't have one lol

But I edited it (/etc/default/grub) how you said previously - put in  "nomodeset" before "quick splash" and just left it at that - so it says:  GRUB_CMDLINE_LINUX="nomodeset quick splash". And of course update-grub  afterwards. But I guess it has the same result - I'm back to all the  Ubuntu goodness  :smile:

---

### Post by mikeab on 2011-01-16
oops

---

