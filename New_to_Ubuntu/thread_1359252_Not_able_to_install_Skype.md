---
title: "Not able to install Skype"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by bungz on 2009-12-19
Hi

I'm a newbie to Ubuntu. I am having trouble installing skype. Everytime i try to install it i get an error message: 

Failed to install package 'skype-ubuntu-hardy_2.1.0.47-1_386.deb'

Terminal
dpkg: unable to read filedescription flags for <package status and program fole descriptor>: Bad file descriptor
[IMG]http://picasaweb.google.co.in/lh/photo/VDW1tGSgxvLMqslqdwl4bw?feat=directlink[/IMG]

HELP!

---

### Post by Merk42 on 2009-12-19
Judging by your windows, it looks like you're running 9.10 Karmic Koala.  If that the case you should [go back and download](http://www.skype.com/download/skype/linux/choose/) Ubuntu 8.10+.
If you're unsure whether or not you have 32 or 64bit run this in the terminal```
uname -a
```

---

### Post by bungz on 2009-12-19
I am running on ubuntu 9.10 karmic koala, indeed.

Ummm. I got this when i typed in 'uname -a': 

Linux the 2.6.31-11 generic #36-Ubuntu SMP Fri Sep 25 06:37:51 UTC 2009 i686 GNU

How do i figure out whether 32 bit or 64 bit from this?

Thanks for responding. Really appreciate it.

---

### Post by HermanAB on 2009-12-19
Howdy,

Note that you can always download the 'static' version from the Skype website and install that in your home directory.  It should 'just work'.

---

### Post by Merk42 on 2009-12-19
> **bungz said:**
> I am running on ubuntu 9.10 karmic koala, indeed.

Ummm. I got this when i typed in 'uname -a': 

Linux the 2.6.31-11 generic #36-Ubuntu SMP Fri Sep 25 06:37:51 UTC 2009 i686 GNU

How do i figure out whether 32 bit or 64 bit from this?

Thanks for responding. Really appreciate it.

That's 32bit
you can run ```
uname -m
``` to double check.

---

### Post by tacantara on 2009-12-19
Bungz:  The i686 that came up on uname -a (and should also come up on uname -m) indicates that the processor is 32-bit.  If you had seen AMD64 or ia64, that would have indicated a 64-bit processor.

---

### Post by chuina on 2009-12-19
i've just learned it from this forum.

```
sudo cat  /proc/cpuinfo
```look for a "lm" in the "flags" line. if lm is there then it is 64 bit.

---

### Post by bungz on 2009-12-19
i686 did appear. So it is 32 bit. 

Just downloading Skype for Ubuntu 8.10+ 32 bit. Yet to install. 

Herman AB - Will try the 'static' too.

---

### Post by bungz on 2009-12-19
I still get the same error message. :(

---

### Post by brookie on 2009-12-19
Hello bugz,
You can also add the [Medibuntu Repository]("https://help.ubuntu.com/community/Medibuntu")
to your Software Sources. 

Once it's updated you can just go into Synaptic Package Manager and search for Skype and select it and install it. 

It will be updated this way when Medibuntu gets a new version of Skype. 

Using repositories is a much easier way to keep software updated. 

It's not like WinXP where you have to update every application seperately. 

Enjoy the [Repositories]("https://help.ubuntu.com/community/Repositories"). 

Cheers, 
Brook

---

### Post by bungz on 2009-12-19
Newer discovery. It seems to be the case with anything that i try to install. I just tried installing picasa as well. And i got the same error message. :( :(

---

### Post by bungz on 2009-12-19
@Brookie - This is what i got.

There seems to be some error.

---

### Post by tacantara on 2009-12-19
Judging from the screenshot of your terminal, either you have some unusual file/folder names, or you misspelled medibuntu and sources.

---

### Post by brookie on 2009-12-19
should be sources.list not cources.list in your first line. 

sometimes it's easier to copy and paste into your terminal, however, be careful when doing this, and don't randomly run commands you see posted on the net.

---

### Post by bungz on 2009-12-19
@tacantara - Yep. I did. Corrected it and i got a different error message. Uploaded screenshot again.

---

### Post by brookie on 2009-12-19
okay, i checked your last post with the image. it looks like the last two errors are because you might have the cd rom checked in software sources: 

System>Administration>Software Sources 

make sure that the first four boxes are ticked, i don't have "Source code" ticked. 

next make sure that the Installable from CD ROM is unticked. 

Now trya again. Those errors should be gone. 

The first error seems like the  Medibuntu Key is not working. I'll have to check on that one.

---

### Post by bungz on 2009-12-19
Thank you, all! Finally, managed to install Skype!

---

### Post by hobo14 on 2009-12-20
> **brookie said:**
> Hello bugz,
You can also add the [Medibuntu Repository]("https://help.ubuntu.com/community/Medibuntu")
to your Software Sources. 

Once it's updated you can just go into Synaptic Package Manager and search for Skype and select it and install it. 

It will be updated this way when Medibuntu gets a new version of Skype. 

Using repositories is a much easier way to keep software updated. 

It's not like WinXP where you have to update every application seperately. 

Enjoy the [Repositories]("https://help.ubuntu.com/community/Repositories"). 

Cheers, 
Brook

This is the only way Skype works for me.

---

