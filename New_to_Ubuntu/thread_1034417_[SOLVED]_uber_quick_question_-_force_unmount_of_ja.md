---
title: "[SOLVED] uber quick question - force unmount of jacked up CD"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by earthpigg on 2009-01-08
yeah. i know its screwed up, thanks ubuntu ;)

whats the terminal command to:

1) find out what it is (/media/sda3 or whatever)... if someone can tell me what the command is to see everything mounted, ill recognize it.... the command is something -l. cant remember what 'something' is.

2) force it to unmount. currently, when i push the eject button on the CD drive it tells me: "Cannot unmount volume: An application is preventing the volume '[cd title]' from being unmounted." nothing is running that i am aware of that is trying to read the cd, but its making noises like something is.... dont care, want it to STFU and let me eject the cd.

thanks in advance!

---

### Post by Malalo on 2009-01-08
1. just typing "mount" without parameters will show you all current mounts and their mount points...

EDIT : (clicked the button too quick)

2. Try umount -f /dev/"yourCDdrive"

---

### Post by earthpigg on 2009-01-08
> ep@ep-laptop:~$ sudo umount /media/cdrom0 -f
[sudo] password for ep: 
umount2: Device or resource busy
umount: /media/cdrom0: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy


grrr

edit: i know i can turn my computer off and eject it when ubuntu isn't paying attention - i want to learn the proper way :)

---

### Post by earthpigg on 2009-01-08
LOOK AT ME MA, IM LEARNING TO RTFM.

```
ep@ep-laptop:~$ sudo umount /media/cdrom0 -f
umount2: Device or resource busy
umount: /media/cdrom0: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
ep@ep-laptop:~$ man lsof
ep@ep-laptop:~$ lsof /media/cdrom0
COMMAND   PID USER   FD   TYPE DEVICE    SIZE NODE NAME
python  26762   ep   15r   DIR   11,0   32768 1792 /media/cdrom0
python  26762   ep   17r   REG   11,0 2115548 2345 /media/cdrom0/_MG_4171.jpg
ep@ep-laptop:~$ kill 26762
ep@ep-laptop:~$ sudo umount /media/cdrom0 -f
ep@ep-laptop:~$ 
```

yeah, so sorry for a useless thread lol

---

### Post by Malalo on 2009-01-08
I agree with your edit ....
The error message showed the "lsof" command...
Can you post the output of 

```
lsof | grep /mount/cdrom 
```

if this shows nothing, try identifying which device is associated to your /mount/cdrom and type 

```
lsof | grep /dev/cdromdevice
```

EDIT : oops took too long a time to write heh... glad it worked then ;-)

---

### Post by earthpigg on 2009-01-08
i always see grep.

RTFM of 'man grep' still explodes my brain.

---

### Post by hyper_ch on 2009-01-08
```
eject
```

---

### Post by handydan918 on 2009-01-08
> **hyper_ch said:**
> ```
eject
```

[sarcasm]
See, that's the kind of cryptic, non-intuitive stuff that keeps Linux from pwning winbloze. If it was just easier to figure out, then every one would use it!
[/sarcasm]


:P

---

### Post by Theory5 on 2009-07-22
I have followed your instructions but when I type 
eject /dev/sda2 I get the error 
Input/output error
please help. everything that happens is the same as earthpigg

---

### Post by pyutaros on 2011-09-09
> **earthpigg said:**
> LOOK AT ME MA, IM LEARNING TO RTFM.

```
ep@ep-laptop:~$ sudo umount /media/cdrom0 -f
umount2: Device or resource busy
umount: /media/cdrom0: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount2: Device or resource busy
ep@ep-laptop:~$ man lsof
ep@ep-laptop:~$ lsof /media/cdrom0
COMMAND   PID USER   FD   TYPE DEVICE    SIZE NODE NAME
python  26762   ep   15r   DIR   11,0   32768 1792 /media/cdrom0
python  26762   ep   17r   REG   11,0 2115548 2345 /media/cdrom0/_MG_4171.jpg
ep@ep-laptop:~$ kill 26762
ep@ep-laptop:~$ sudo umount /media/cdrom0 -f
ep@ep-laptop:~$ 
```

yeah, so sorry for a useless thread lol
Not useless at all.  thanks for putting it out there for others to learn from!  Helped me with my problem.

---

### Post by HermanAB on 2011-09-09
Uhmm, for future reference, the correct command is 'lazy unmount': 
$ sudo umount -l /dev/cdrom

---

### Post by kouchris on 2012-01-24
useless? FAR from it ! thanks a lot. I must have typed killall nautilus 100 times!!! User 1 - Program 0 :)
Thanks a lot!

---

