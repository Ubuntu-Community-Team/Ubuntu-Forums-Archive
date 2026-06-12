---
title: "Can not mount volume"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by jonpon on 2009-08-18
I wanted to access my 2nd hard drive from boot, I've don something
stupid and now I can't access my 2nd HD.at all. I get a message
"**Can not mount volume**
Invalid mount option when attempting to mount the volume."
can anyone please please help

---

### Post by Locke_99GS on 2009-08-18
By what method are you attempting to mount the volume? What options are you passing it?

---

### Post by jonpon on 2009-08-18
> **Locke_99GS said:**
> By what method are you attempting to mount the volume? What options are you passing it?

I'm clicking on the button in the drop-down menu.

---

### Post by Buuntu on 2009-08-18
Post what is in your fstab file.  
```
sudo gedit /etc/fstab
```

---

### Post by jpeddicord on 2009-08-18
As a temporary solution, have you tried restarting? It's possible there's a stale device entry for the hard drive that is preventing it from being mounted again.

---

### Post by jonpon on 2009-08-18
> **Buuntu said:**
> Post what is in your fstab file.  
```
sudo gedit /etc/fstab
```
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=96522c58-2c02-467b-bf37-d253ab6f8ce1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7891fb5b-158f-4eb7-8b85-e6d426b95dd7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=f75ddf72-138b-4ca9-a9a8-571cd6d5b9c8   /dev/sdb1     /media/disk   ext3   auto,rw,user   0   2
```

this where all the fun started I wanted to mount on boot and changed the bottom line from 'default' to 'auto,rw,user
nothing happened so I tried graphically by right clicking on the icon and changing the  Mounting opions to 'auto,rw,user'
but that was a big mistake!!!
Do you have any ideas?

---

### Post by jonpon on 2009-08-18
> **jacobmp92 said:**
> As a temporary solution, have you tried restarting? It's possible there's a stale device entry for the hard drive that is preventing it from being mounted again.

yes, restart was the 1st thing I tried

---

### Post by kayvortex on 2009-08-18
You have one too many fields in your last fstab entry: use either UUID=... or the device name (/dev/sdb1). As it is, mount thinks that "ext3" is a mount option.

Tip: you also don't need to remove "defaults": you can put "auto,rw,user" after it and they will override any similar settings in "defaults".

---

### Post by jonpon on 2009-08-18
> **kayvortex said:**
> You have one too many fields in your last fstab entry: use either UUID=... or the device name (/dev/sdb1). As it is, mount thinks that "ext3" is a mount option.

Tip: you also don't need to remove "defaults": you can put "auto,rw,user" after it and they will override any similar settings in "defaults".

so, I changed the fstab file, to this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=96522c58-2c02-467b-bf37-d253ab6f8ce1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7891fb5b-158f-4eb7-8b85-e6d426b95dd7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=f75ddf72-138b-4ca9-a9a8-571cd6d5b9c8      /media/disk   ext3   defaults,auto,rw,user   0   2
```
but it still doesnt mount on boot or let me mount graphically from the menu
on start up I had to press 'ctrl D' because it couldn't mount media/disk

---

### Post by kayvortex on 2009-08-18
Does the directory /media/disk already exist? I think mount will complain if it doesn't: you will have to create it with mkdir.

What does mounting it manually print out? Type:
```
sudo mount -v -U f75ddf72-138b-4ca9-a9a8-571cd6d5b9c8
```

---

### Post by bagle on 2009-08-18
oh you might want to change the line back to the way it was at the start (before the changes) if you need any thing off it.:popcorn:

---

### Post by fela on 2009-08-18
Try mounting it manually from the CLI:

```
sudo mkdir /media/disk && sudo mount /dev/sdb3 /media/disk
```

Where sdb3 is the device name.

---

### Post by jonpon on 2009-08-18
> **kayvortex said:**
> Does the directory /media/disk already exist? I think mount will complain if it doesn't: you will have to create it with mkdir.

What does mounting it manually print out? Type:
```
sudo mount -v -U f75ddf72-138b-4ca9-a9a8-571cd6d5b9c8
```
```

jonpon@jonpon-laptop:~$ sudo mount -v -U f75ddf72-138b-4ca9-a9a8-571cd6d5b9c8
[sudo] password for jonpon: 
mount: mount point /media/disk does not exist
jonpon@jonpon-laptop:~$ 
```

---

### Post by fela on 2009-08-18
> **jonpon said:**
> ```

jonpon@jonpon-laptop:~$ sudo mount -v -U f75ddf72-138b-4ca9-a9a8-571cd6d5b9c8
[sudo] password for jonpon: 
mount: mount point /media/disk does not exist
jonpon@jonpon-laptop:~$ 
```

You need to create the mount point /media/disk:

```
sudo mkdir /media/disk
```

It should then work fine.

---

### Post by kayvortex on 2009-08-18
Well, that's pretty conclusive! You need to create /media/disk:
```
sudo mkdir /media/disk
```

It *should* automount at startup now. Post back if there are any problems.

Edit: beat me to it fella, fela!

---

### Post by fela on 2009-08-18
> **kayvortex said:**
> Well, that's pretty conclusive! You need to create /media/disk:
```
sudo mkdir /media/disk
```

It *should* automount at startup now. Post back if there are any problems.

You have to be a quick typer on these forums!

---

### Post by jonpon on 2009-08-18
> **kayvortex said:**
> Well, that's pretty conclusive! You need to create /media/disk:
```
sudo mkdir /media/disk
```

It *should* automount at startup now. Post back if there are any problems.

Edit: beat me to it fella, fela!

 I have many files on that 2nd HD. I used to access just fine.if I mkdir will I not wipe the files which used to be on media/disk ?

---

### Post by fela on 2009-08-18
> **jonpon said:**
> I have many files on that 2nd HD. I used to access just fine.if I mkdir will I not wipe the files which used to be on media/disk ?

/media/disk, unless the drive is mounted, is just an empty folder. By creating the directory, you are actually just making a normal folder to mount your drive in. You could mount your drive anywhere if you wanted, even on your desktop.

---

### Post by jonpon on 2009-08-18
that worked thank-you guys!!!

---

### Post by fela on 2009-08-18
> **jonpon said:**
> that worked thank-you guys!!!

Great, no problem! We're here to help remember ;)

---

### Post by kayvortex on 2009-08-18
> I have many files on that 2nd HD. I used to access just fine.if I mkdir will I not wipe the files which used to be on media/disk ?

In short, no. For one thing you have not mounted your disk onto your file system yet, so there's nothing to overwrite; and, in any case, mkdir does not allow you to overwrite extant directories: it will complain and exit without doing anything. You see, when you mount a disk you are sort of telling your system where that disk's folders should be accessed. If mount doesn't succeed in mounting the disk, your files are still fine, but your system simply can't access them, so you can't do *anything* with them, let alone overwrite them (unless you do more complicated things with fdisk or dd etc.; but we'll ignore that for now!).


fela: you just made an enemy today...


Edit: OK, can everybody stop responding so damn quickly!!

---

### Post by fela on 2009-08-18
> **kayvortex said:**
> fela: you just made an enemy today...


Edit: OK, can everybody stop responding so damn quickly!!

Just set your mail client to check for messages every 1 minute and you'll be fine! ;)

---

### Post by kayvortex on 2009-08-18
> Just set your mail client to check for messages every 1 minute and you'll be fine!

Yeah, like I'm going to take advice from my sworn enemy. HA! I'LL SEE YOU IN HELL, FELA!!

Edit:
(> that worked thank-you guys!!!
Happy to help.)

---

### Post by fela on 2009-08-18
> **kayvortex said:**
> Yeah, like I'm going to take advice from my sworn enemy. HA! I'LL SEE YOU IN HELL, FELA!!

Erm...because I beat you at replying to someone on ubuntuforums.org? Get a life ;).

---

### Post by kayvortex on 2009-08-18
Oh, no more pretend animosity? Well, forget you: I'll make my own humour, with blackjack, and hookers! In fact, forget the humour and blackjack! Ah, screw the whole thing...

(OK, enough!)

---

