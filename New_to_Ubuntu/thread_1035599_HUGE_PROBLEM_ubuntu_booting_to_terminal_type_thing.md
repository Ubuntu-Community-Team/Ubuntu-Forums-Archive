---
title: "HUGE PROBLEM ubuntu booting to terminal type thing"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Vendettaseve on 2009-01-09
Hey everyone

Ubuntu us now booting up into some sort of Cprompt instead of the usual ubuntu GUI and tells me there is no resume image, booting as normal, it then asks me for my user name and password in DOS style layout, and just lets me mess about in a 100% terminal interface.


This is obviously very bad since I cant really do anything worthwhile. Can someone please help me with this.

Thanks

---

### Post by Vendettaseve on 2009-01-09
Anyone?

---

### Post by Amranu on 2009-01-09
what happens if you type 'startx'?

---

### Post by fedira on 2009-01-09
Try entering startx into the terminal, and hit enter.

---

### Post by Vendettaseve on 2009-01-09
blackscreens for a cople seconds, gives me a cursor then jumps back to terminal and says alot of stuff, the most relevant being "waiting for X server to shut down(EE) fglrx(0): [drm] failed to remove DRM signal handler
freefontpath:FPE "/usr/share/fonts/x11/misc" refcount is 2, should be 1; fixing.

then gives me a terminal line again starting in ~

---

### Post by devdeblib on 2009-01-09
why not remove and reinstall X from the shell prompt?

sudo /etc/init.d/gdm restart <<< you could try this 

Try re-configuring the X server.

sudo dpkg-reconfigure xfree86-server

or ...
sudo apt-get remove x-window-essentials 

or how about a little....
sudo apt-get remove x-window-system-core

---

### Post by Vendettaseve on 2009-01-09
How would I go about doing that.

---

### Post by Sealbhach on 2009-01-09
You could try this, it fixes a lot of X server probs:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

.

---

### Post by Vendettaseve on 2009-01-09
> **Sealbhach said:**
> You could try this, it fixes a lot of X server probs:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

.

This did something at least, when I starx now it gives me a flickering black screen for a few seconds then opens up this really splotchy looking hazy light and dark blue screen, but I cant do anything from this :(

---

### Post by Vendettaseve on 2009-01-09
Still no luck with anything :( Does anyone know whats wrong?

---

### Post by Vendettaseve on 2009-01-10
Anyone? :(

---

### Post by Vendettaseve on 2009-01-10
wow this must be a bad problem :(

---

### Post by Norm24 on 2009-01-10
Check this thread out:
[http://ubuntuforums.org/showthread.php?t=1011010](http://ubuntuforums.org/showthread.php?t=1011010)

---

### Post by oldos2er on 2009-01-10
Which Ubuntu version are you using? Which video card? Did you have a working GUI before this happened; if so, did you change anything just prior to this problem? Do you know which video drivers you're using?

---

### Post by HunterThomson on 2009-01-10
> **devdeblib said:**
> why not remove and reinstall X from the shell prompt?

sudo /etc/init.d/gdm restart <<< you could try this 

Try re-configuring the X server.

sudo dpkg-reconfigure xfree86-server

or ...
sudo apt-get remove x-window-essentials 

or how about a little....
sudo apt-get remove x-window-system-core

Vendettaseve
> How would I do that?

They are all commands you can execute form the terminal. You just type them in.

However, If you Remove the X windows system you will also have to reinstall it. You will also have to do>>>>

```
sudo apt-get install x-window-essentials

OR

sudo apt-get install x-window-system-core

```

Respectfully 

Then 

```
sudo dpkg-reconfigure xfree86-server
```

If you want to know what i really think.....

This is a really pain problem to trouble shoot with someone over the web. You have shell access so you can just copy all important files over to a new storage medium. Then reinstall. Will probably save you time in the long run but you will learn less.

---

### Post by HunterThomson on 2009-01-10
> I have decided to take your advice and reinstall ubuntu.

Can you instruct me on the method used to copy over files I wish to keep onto a memory stick through terminal?

thanks

Well, it mite still auto mount.... 

Plug in your USB thumb drive and then navigate to the media directory>>>

```
cd /media
```

then list the contents>>>

```
ls
```


then it always mount to the /media/disk directory on my computer... So if you see it there then navigate to it ( cd "Change Directory"). if not do this....

(((
On my computer my Hard Disk is /dev/sda and my USB sticks are at /dev/sdb

you can see all your partitions and stuff it this command>>>

```
df
```

I think this is for everyone.... so do this.....

```
cd ~
mkdir usb
mount /dev/sdb ~/usb,,,,,,,,,,,,,,,,,,,,,
ARG I can never remember the mount command........... and it take me hr's to find every time........


```
)))))))

So if it did auto mount you can then use the copy command to copy the files over to /media/disk

```
cp /home/username/important-files /media/disk
```

or 

```
cp ~/important-files /media/disk
```

---

### Post by HunterThomson on 2009-01-10
also if you set up a partition for your /home directory ((which should be most of your harddrive. The root partition "/" only needs to be like 15-20GB and you don't need any other partitions. root "/" 20GB and '/home' the rest of the harddrive)) when you install.

Then the next time you reinstall with the "manual partition" option you can re-label the partition /home and chose NOT to format it. Then chose the same user name and password. Then all your configuration's and files and stuff on the /home partition will sill be there and save you a lot of set up. + no lost data on the home partition.

---

### Post by HunterThomson on 2009-01-10
ya it is so hard to find the REAL way to use the mount comand. Google is full of Bull. None of the mount comands on the first three pages of Google work. it is realy something like....


sudo mount -o loop /dev/sdb ~/usb

and the mount man page is more like a man book

---

### Post by Vendettaseve on 2009-01-10
> **HunterThomson said:**
> ya it is so hard to find the REAL way to use the mount comand. Google is full of Bull. None of the mount comands on the first three pages of Google work. it is realy something like....


sudo mount -o loop /dev/sdb ~/usb

and the mount man page is more like a man book

When I do this I  get a "no media found" error

and doing the df command lists the same stuff regardless of my USB stick being in

---

### Post by Norm24 on 2009-01-10
> **Norm24 said:**
> Check this thread out:
[http://ubuntuforums.org/showthread.php?t=1011010](http://ubuntuforums.org/showthread.php?t=1011010)

Seriously.Check this thread out.

---

### Post by Vendettaseve on 2009-01-10
> **Norm24 said:**
> Seriously.Check this thread out.


pressing control H doesnt do anything for me -_-

---

### Post by Vendettaseve on 2009-01-10
Also doing the gdm thing just brings up a thing that says "starting gnome display manage     [fail]"


also I have no graphical support at all, im in for lack of a better discription, DOS

---

### Post by HunterThomson on 2009-01-10
ya hold on I will find out the real mount comand....

---

### Post by HunterThomson on 2009-01-10
Geeeeez I finaly fount it......Arg

```
sudo mount /dev/sdb1 /media/cdrom
```

then coppy all your important files with the copy command

```
cp ~/important-files /media/cdrom
```

you will want to un-mount the usb befor you take it out with this comand

```
sudo umount /media/cdrom
```

---

### Post by Vendettaseve on 2009-01-10
> **HunterThomson said:**
> Geeeeez I finaly fount it......Arg

```
sudo mount /dev/sdb1 /media/cdrom
```

then coppy all your important files with the copy command

```
cp ~/important-files /media/cdrom
```

you will want to un-mount the usb befor you take it out with this comand

```
sudo umount /media/cdrom
```

Does not work

mount: special device sdb1 does not exist

---

### Post by Vendettaseve on 2009-01-10
i have discovered that my sd card is called sdc when i do that command with sdc instead of sdb1 it says i need to specify the file system type

---

