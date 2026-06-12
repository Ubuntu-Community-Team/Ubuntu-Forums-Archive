---
title: "Lucid Intsallation Failed - &quot;Unrecoverable Error&quot;"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by mulluysavage on 2010-04-29
A dialog box pops up when booting Lucid LiveCD, saying it can't install because of 'unrecoverable error.' Happens consistently. Is there a log file somewhere with the info? Can someone help me read it if so?

Asus M3N78 Pro
AMD Phenom x4
4 GB RAM

---

### Post by Sealbhach on 2010-04-29
I would suggest downloading again and burning a fresh CD. Make sure to check the MD5sum.

.

---

### Post by mulluysavage on 2010-04-29
cool how do you do that?

---

### Post by DLM955 on 2010-04-29
It does sound like a disk error and make sure you burn new disk at slowest speed possible...If burnt at high speed it will cause read errors..I know I learned the hard way...

---

### Post by Sealbhach on 2010-04-30
> **mulluysavage said:**
> cool how do you do that?

You just go

```
md5sum whatever.iso

```

Then you compare the output with what is on the Ubuntu download page for that particular iso. If they match exactly, then you have a good download.
.

---

### Post by Soul-Sing on 2010-04-30
or try the alternate iso.

---

### Post by mulluysavage on 2010-04-30
Okay, I have a good ISO. I also burned at a slower speed - same result. I did a good md5sum on the .iso, but I can't seem to check the cd rom, I go

```
cd sro
cd cdrom
md5sum

```

and it just hangs there no cd activity

---

### Post by ravi_buz on 2010-04-30
guys i think there is some bug. i downloaded the Rc burned it into a CD and a USB tried booting into my system with it .. the Cd showed the above error and the USB kept loading ubuntu for 1 hr and i restarted the system after loosing patience . I tried those on my laptop and it worked well . so there is no question of error in the iSO . today i tried downloading and doing the same with the final version and the result was the same

---

### Post by zephyrblade on 2010-04-30
I had the same frustrating error about 4 times ...

I downloaded the iso again via torrent, and then burnt it at the lowest speed possible (using a different burner).

Now I like purple.

---

### Post by samstreet101 on 2010-04-30
There's an official repsons to this bug on the ubuntu website for the Lucid release notes:
 
[http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)
 
Look under 'desktop installer sometimes crashes on startup' it describes this bug exactly. Their response is to restart your computer and on the first purple screen (the one with the keyboard and accessibility icon at the bottom) press any key and select 'try ubuntu without installing' so it goes into Live desktop mode. Then just select 'install ubuntu' from the desktop. Worked for me...(i had this errror too if you didn't already guess).
 
Hope this helps

---

### Post by Sealbhach on 2010-04-30
> **mulluysavage said:**
> Okay, I have a good ISO. I also burned at a slower speed - same result. I did a good md5sum on the .iso, but I can't seem to check the cd rom, I go

```
cd sro
cd cdrom
md5sum

```and it just hangs there no cd activity

Right. You only need to md5sum the .iso.

.

---

### Post by MisFitt on 2010-05-12
I would just like to add that I've been having the same error message as has my friend who has a Canonical official copy of Lucid 32bit desktop he sent away for.

---

