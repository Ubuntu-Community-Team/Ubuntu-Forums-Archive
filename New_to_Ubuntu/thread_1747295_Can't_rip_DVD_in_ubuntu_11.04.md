---
title: "Can't rip DVD in ubuntu 11.04"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by johnw230873 on 2011-05-02
In the past I have ripped my DVDs to a central server, this allowed me to play them from mutiple locations (within the house) but more importantly stops my little girl from damaging them. I found with Ubuntu 11.04 I can't rip a DVD with all the applications  saying  
 Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed. 

 I have checked for libdvdcss2 and it is installed, I can even watch DVD's but I can't rip them.
 

 Any ideas?

---

### Post by _0R10N on 2011-05-02
Are you able to play them?

---

### Post by johnw230873 on 2011-05-02
> **_0R10N said:**
> Are you able to play them?
 
 
Yes I can play them back, I had to install some libs to do this as at first the playback also popped up this message

---

### Post by corncob on 2011-05-02
What program are you using?
[http://www.youtube.com/watch?v=OPLquAvs7eQ&playnext=1&list=PLBA292A2B4B88BAFA](http://www.youtube.com/watch?v=OPLquAvs7eQ&playnext=1&list=PLBA292A2B4B88BAFA)

---

### Post by K_45 on 2011-05-02
Try

```
dd if /dev/cdrom of=/tmp/name.iso
```

This doesn't remove encryption though.

---

### Post by johnw230873 on 2011-05-02
Thanks guys, I'm away from my PC at the moment so will try these things after work. I would like to remove the encryption as it make watching them easiler but if I can't then I can't.
 
As for programs I have tried mutiple such as AcidRIP,DVD::RIP & thoggen. 
 
I haven't tried handbrake yet.

---

### Post by K_45 on 2011-05-02
Try Wine + DVDFab, which may work too. Good link here:

[http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html](http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html)

---

### Post by johnw230873 on 2011-05-02
> **K_45 said:**
> Try Wine + DVDFab, which may work too. Good link here:
 
[http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html](http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html)
 
 
Hmmmm, will do and tell you how I got on.

---

### Post by johnw230873 on 2011-05-02
So Wine and DVDFAB kind of work, it does rip the dvd but if I minimize the windows I can't get it back.

---

### Post by K_45 on 2011-05-02
So you have the decrypted files? Maybe try loading Wine on a different workspace, if you are using Unity then some apps may not play nice with the panel/launcher.

---

### Post by johnw230873 on 2011-05-03
spoke too soon DVDFAB dies with an error reading at 70%

I'm no long using Unity, just not my cup of tea

---

### Post by K_45 on 2011-05-03
Try adjusting the compatibility settings, and try DVD Decrypter too. Otherwise try out the other Linux options too.

---

### Post by corncob on 2011-05-04
> **K_45 said:**
> Try

```
dd if /dev/cdrom of=/tmp/name.iso
```

This doesn't remove encryption though.

Tried it:
```
corncob@EB1012P:~$ dd if /dev/cdrom of=/tmp/name.iso
dd: unrecognized operand `if'
Try `dd --help' for more information.
corncob@EB1012P:~$
```
--help didn't help - said 'if' was correct.  Do I need to install a library or something (running 64 bit Natty, classic desktop)?

---

### Post by QLee on 2011-05-04
[QUOTE=corncob]Tried it:
```
corncob@EB1012P:~$ dd if /dev/cdrom of=/tmp/name.iso
dd: unrecognized operand `if'
Try `dd --help' for more information.
corncob@EB1012P:~$
```--help didn't help - said 'if' was correct.  Do I need to install a library or something (running 64 bit Natty, classic desktop)?[/QUOTE]

Does it work any differently if you use dd if=/dev/cdrom (with the equal sign), in your command?

---

### Post by corncob on 2011-05-04
> **QLee said:**
> Does it work any differently if you use dd if=/dev/cdrom (with the equal sign), in your command?

It worked!  I am a little puzzled that it only copied 708 KB to the iso yet it says 4 GB on the DVD (as does the original).  Busy with other things right now but will see if it works tomorrow.  I don't have a stack of DVDs I have any reason to rip but am interested in the technology.

---

### Post by K_45 on 2011-05-04
No guarantees dd will work with some discs. There is always one that doesn't work.

---

### Post by Automat2 on 2011-09-16
> **johnw230873 said:**
> So Wine and DVDFAB kind of work, it does rip the dvd but if I minimize the windows I can't get it back.
 
I had this problem a way back, but since some update of DvdFAB and Ubuntu, everything has worked OK.
 
I'll have to try DVD Decrypter, though.

---

### Post by soap1 on 2011-11-26
I installed libdvdcss2 and thoggen, which works quite well for me.  Here is libdvdcss2
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
and here is thoggen
[http://thoggen.net/](http://thoggen.net/)

---

