---
title: "Is it possible to do an MD5SUM check form the live CD?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by lukeinvancouver on 2009-04-23
I tried to do a MD5SUM check after loading Jaunty Jackalope as Live CD but it couldn't find the downloaded file. (Or I couldn't point it to the right place, which is: C:\Documents\Linux\Ubuntu9-04)

Is it necessary to install an MD5SUM program on my Vista machine to check the integrity of the download or is it possible to do it from the Live CD?

Or could I take the chance of wasting a blank CD and burn it and then do the integrity check under Linux? (Chances are probably not that great that the download is corrupted and the disk cost me only about 50 cents when I bought a spindle.)

If so, would somebody please tell me how to do it?

Thank you in advance.

---

### Post by oldos2er on 2009-04-23
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

 Scroll down a bit to find directions for Windows.

---

### Post by lukeinvancouver on 2009-04-23
> **oldos2er said:**
> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

 Scroll down a bit to find directions for Windows.

Thank you kindly. 

A related question I forgot to ask is if I install Jaunty Jackalope would I be back to square one just as I seem to be getting somewhere with Intrepid Ibex or if not do I just install it leaving the present partition (equal to the whole drive except for the partition Ubuntu adds, which I assume to be the "system area".)in place? Would Jaunty Jackalope resize the partitions, or make suggestions?

---

### Post by lukeinvancouver on 2009-04-23
I had read that before asking for help. So if I understand correctly I MUST download and isntall MD5SUM for Windows. Right?

---

### Post by oldos2er on 2009-04-23
Right.

---

### Post by lukeinvancouver on 2009-04-23
> **oldos2er said:**
> Right.

Quote from the above link:

"Windows does not come with md5sum. You must download one from another location, preferably one that you trust. There are command line utilities (md5sum.exe) that work similarly to the Unix utility; one public domain version with source is available from Fourmilab, but the version available from Cygwin is probably easier to install and update, and Cygwin is also recommended and trusted as the source for many more Unixy utilities. Once installed, Cygwin's md5sum behaves exactly as described in MD5SUM on Linux above."

It sounds just a little less than total confidence to me (except for Cygwin perhaps). So I downloaded Ubuntu 9.04 again on my Linux machine and I'll burn it and do the check there.

There's **something interesting** though that I'd like to share:

I downloaded it twice on my Vista machine because I had made a mistake and selected "open" instead of "save".

Three downloads of the same program  from the same server and using the same internet connection. Windows took about an hour and fifteen minutes each time. Linux did it in 15 minutes!

I'm loving this more and more as I go on!

Thanks again for your kind help.

:D

---

### Post by michy99 on 2009-04-23
I'm pretty sure you can do an MD5 check from the live CD. You just have to mount the drive the file is on first because the live CD does not mount internal drives automatically.

---

### Post by lukeinvancouver on 2009-04-23
> **michy99 said:**
> I'm pretty sure you can do an MD5 check from the live CD. You just have to mount the drive the file is on first because the live CD does not mount internal drives automatically.

Thanks but as I said I downloaded it again on my Ubuntu machine. Just have to find that "hidden" place where I can get the hash for 9.04. It's there (and I've been there and will find it again) but almost all the links lead to version 8.10 or below.

It is defintely possible to do it from a Live CD, I just wasn't able to direct it to the right place.

:confused:

---

### Post by michy99 on 2009-04-23
The MD5SUMS are here:

[http://releases.ubuntu.com/releases/9.04/MD5SUMS](http://releases.ubuntu.com/releases/9.04/MD5SUMS)

---

### Post by lukeinvancouver on 2009-04-23
> **michy99 said:**
> The MD5SUMS are here:

[http://releases.ubuntu.com/releases/9.04/MD5SUMS](http://releases.ubuntu.com/releases/9.04/MD5SUMS)


Thank you very much mich99. As I said, I had been there before.

I'm so glad I'm making the progress I am making. (Not the best English, is it)

You have no idea what trip I'm living: After YEARS of trying to change to Linux, it's finally happening!!!

I'm 67 years old, and if you had told me three days ago that I'd go gaga over an OS, I would have told you that you are nuts.

It's the best thing that has happened to me for a long time.

Thank you all!

---

