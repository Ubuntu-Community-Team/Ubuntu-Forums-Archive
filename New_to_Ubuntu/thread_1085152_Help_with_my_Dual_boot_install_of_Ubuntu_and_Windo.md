---
title: "Help with my Dual boot install of Ubuntu and Windows"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Oz-1313 on 2009-03-02
Hi There,

Ive just installed a Dual boot of ubuntu with vista from a Live CD i got with Linux Format.  However when i boot up I expected to see just a choice between vista and ubuntu.
  However what i see is a choice between a couple of ubuntu's one called generic and one with generic and recovery.  When i chose the singe generic option it took me to a screen which was the same as when i was selecting my boot.  A non gui. Just some lines of code.  It asked me to log in etc which i did but didnt allow me to acess a desktop at all and seemed to stop where it was.  I had to force shut down and went back into my pc via vista.  Ive rebooted onto the live cd at the moment.  Could anyone tell me if there is a quick fix to my problem or how i could do a full uninstall of ubuntu so that i could start again and try to install it again.  

With the uninstalling i would like to completely remove ubuntu and get the space back into my vista partition so that i could start again from complete scratch.

Sorry if this seems a bit rambling.  Im very new to linux and Im not a very tech guy, I understand a bit but not too much.  SO not too much techno speak please, baby talk may be best for me!!  Thanks
Rob

---

### Post by fiddler616 on 2009-03-02
> **Oz-1313 said:**
> Hi There,

Ive just installed a Dual boot of ubuntu with vista from a Live CD i got with Linux Format.  However when i boot up I expected to see just a choice between vista and ubuntu.
  However what i see is a choice between a couple of ubuntu's one called generic and one with generic and recovery.  When i chose the singe generic option it took me to a screen which was the same as when i was selecting my boot.  A non gui. Just some lines of code.  It asked me to log in etc which i did but didnt allow me to acess a desktop at all and seemed to stop where it was.  I had to force shut down and went back into my pc via vista.  Ive rebooted onto the live cd at the moment.  Could anyone tell me if there is a quick fix to my problem or how i could do a full uninstall of ubuntu so that i could start again and try to install it again.  

With the uninstalling i would like to completely remove ubuntu and get the space back into my vista partition so that i could start again from complete scratch.

Sorry if this seems a bit rambling.  Im very new to linux and Im not a very tech guy, I understand a bit but not too much.  SO not too much techno speak please, baby talk may be best for me!!  Thanks
Rob
Once you get to the text-only login screen, try pressing <Ctrl><Alt><F7>. If that works, it means that for whatever reason you're booting to a tty (I can explain that later, if you want). If that doesn't work, then chill here for a bit longer and somebody smarter than me will come help you :)

For reinstallation, just start the installation sequence off the Live CD, and when it comes time to pick the partitions have it overwrite the current Ubuntu partitions. That really shouldn't be necessary though.

Good luck!

---

### Post by charliehorse55 on 2009-03-02
You booted into single user mode, which has no GUI, Next time boot into one called "generic".

---

### Post by Oz-1313 on 2009-03-02
Hey thanks for the replies so far!

Ive tried rebooting into it again and ive noted down the options i have which seem odd in the choosing a boot.  Ill put it here just now.  Ive chosen the generic one which took me to the non gui option and recovery which seemed to take me a longer way round with nmore option to the same login section.  ANyways here are my choices.

Ubuntu 9.10 Kernel 2.6.27-7-generic

Ubuntu 9.10 Kernel 2.6.27-7-generic (recovery drive)
Other operating systems:
Dell utility Systems
Windows Vista/Longhorn (loader)

Dont know if that will help!

If i have somehow ended up with a tty"??" how can i sort that so that im just on the plain simple Ubuntu option for my choice of boot?

Thanks, Rob

---

### Post by joshaman on 2009-03-02
i'm a complete newb, but - ```
/etc/init.d/gdm start
``` will start the GUI (not sure if you need to type "sudo" before that) and then press ctrl+alt+F7 (i think) to switch to the desktop.

i think you can restore Vista to the grub bootloader by: 

1. opening a terminal (once in the desktop) and type sudo gedit /boot/grub/menu.lst 

2. scroll to the very bottom and type the following strings
```
title Windows Vista 
root (hd0,1) 
makeactive 
chainloader +1
``` - save, exit and reboot

you might want to wait for a real Linux user to help you with this, i've only been using it for a couple of days, but i don't think this could hurt anything, and i think it will work.

e: whoops - that *way *too late.  jeez, this guy gets answers already?  how about someone answers my simple question: [http://ubuntuforums.org/showthread.php?t=1085101]("http://ubuntuforums.org/showthread.php?t=1085101")

---

### Post by fiddler616 on 2009-03-02
TTYs in a nutshell:
Ubuntu pretends to have 7 computers (which don't actually exist) running off a sort of a server (which is actually your computer). Each one is a tty--<Ctrl><Alt><F1>, <Ctrl><Alt><F2>, etc. The first six are normally terminals, each waiting for somebody--be it you or a different user, to log in. The seventh is usually GNOME or KDE, also waiting for someone to log in. This is an especially nice feature if GNOME crashes--you can go to a tty and either restart GNOME, or just reboot.
(Note: Purists wouldn't find the above to be exactly correct, but it's all you need to know).

---

### Post by Oz-1313 on 2009-03-02
Hey,
Ive tried going through the generic option (the first one).  It starts to load with a loading bar but then goes into the text only screen asking me to log in.  I did so and then tried the ctrl-alt-F7 thing.  WHich didnt do anything.  My vista is fine it seems i can boot into it no problems so i dont really want to touch that.  Just that if i decide to uninstall it how do i wipe ubuntu and get the space back into vista?  I do have the live cd and i have heard mutterings about gparted, though im not sure exactly what it will do.  

Thanks and keep the replies coming!!! Rob

---

### Post by joshaman on 2009-03-02
> **fiddler616 said:**
> I know this because I've broken GRUB a LOT, and always gotten nice people here to fix it for me:
I'm pretty sure that the "(hd0,1)" bit is not written in stone--you need to figure which partition *your* Vista is on, and use those numbers. But I think it's a moot point, since you have it as an option in GRUB at the moment...am I missing something?that was a *late* post, i didn't know he had Vista in the menu, and i assumed he'd installed ubuntu onto the first partition for some reason.

---

### Post by fiddler616 on 2009-03-02
> **joshaman said:**
> that was a *late* post, i didn't know he had Vista in the menu, and i assumed he'd installed ubuntu onto the first partition for some reason.
I've edited it away to clear things up. Thanks for saying that.

---

### Post by fiddler616 on 2009-03-02
> **Oz-1313 said:**
> Hey,
Ive tried going through the generic option (the first one).  It starts to load with a loading bar but then goes into the text only screen asking me to log in.  I did so and then tried the ctrl-alt-F7 thing.  WHich didnt do anything.  My vista is fine it seems i can boot into it no problems so i dont really want to touch that.  Just that if i decide to uninstall it how do i wipe ubuntu and get the space back into vista?  I do have the live cd and i have heard mutterings about gparted, though im not sure exactly what it will do.  

Thanks and keep the replies coming!!! Rob
I'd wait 24 hours, and if nothing helpful happens, make a new thread, and call it something helpful like "Fresh Ubuntu install boots to all-text".
GParted, which is included in the installer, and can also be run off the LiveCD (<Alt><F2>+"gksu gparted") lets you partition your HDD. But if you just remove the Ubuntu partitions it will mess up GRUB. You can probably find an answer by Googling, but if not post a thread here.

---

### Post by Oz-1313 on 2009-03-02
Sorry i should have put all my options into the first post but i could remember them and was keen for help!!  Any other ideas about the ubuntu and getting it working properly?

---

### Post by joshaman on 2009-03-02
> **Oz-1313 said:**
> Just that if i decide to uninstall it how do i wipe ubuntu and get the space back into vista?you can do it from windows, but only if vista is on the first partition.  

go to control panel, administrative tools, computer management, disk management (under classic menus).  vista partition must be on the left.  the entire instructions can be found [here]("http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html").  if vista's the second (right) partition, you can still do it, but you won't be able to extend the first partition (at least not under windows).  you could probably that with gparted.

---

### Post by russet_wolf on 2009-03-02
Hey, I'm pretty new, but I've installed and uninstalled a tonne trying to get everything just right. I can't help you get a GUI, but if you really want to completely wipe ubuntu you can do the following from the LiveCD:

Go to System > Administration > Partition editor. This will open GParted, a really nice partition program. Your Ubuntu partitions should be two logical drives on sda in an extended partition. you can just select them and click delete (you may have to right click and "unmount" them first) make sure you delete the individual "sub-partitions" (logical drives) before you delete the extended partition. Then you can select your Vista partition and click "Resize/Move" to fill the rest of the space.

That may take some time, but it should get your computer back into pre-Ubuntu condition.

And if it does mess up your GRUB, you can use the following comands in the terminal to restore your Vista MBR so that you can do a fresh install of GRUB along with Ubuntu:

```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```

---

