---
title: "not playing dvds"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by als123 on 2009-06-26
Hi Everyone,
 
I've been playing with different distros for a few months now and have landed on Ubuntu 8.04. Very nice from what I've seen so far.
 
My problem lies in getting dvds to play. A lot of what I read has to do with have the libdvdcss2 file. I have it and it still will not play.
 
My dvd drive is recognized as /media/cdrom0, I read somewhere that you have to create a symbolic link in the /dev/ directory, but that option is greyed out on the right-click menu.
 
I tried doing it manually, but keep getting an error that the directories do not exist. I think I'm not in the right dir is why I get that error, but I don't know how to get in the root dir, i think?
 
Any help would be greatly appreciated, Thanks.

---

### Post by bhadotia on 2009-06-26
> **als123 said:**
> Hi Everyone,
 
I've been playing with different distros for a few months now and have landed on Ubuntu 8.04. Very nice from what I've seen so far.
 
My problem lies in getting dvds to play. A lot of what I read has to do with have the libdvdcss2 file. I have it and it still will not play.
 
My dvd drive is recognized as /media/cdrom0, I read somewhere that you have to create a symbolic link in the /dev/ directory, but that option is greyed out on the right-click menu.
 
I tried doing it manually, but keep getting an error that the directories do not exist. I think I'm not in the right dir is why I get that error, but I don't know how to get in the root dir, i think?
 
Any help would be greatly appreciated, Thanks.
Do you have vlc? Install it using:
```
sudo apt-get install vlc
```
You will need the [medibuntu]("http://medibuntu.org/") repository for the above command to work. But because you say you already have libdvdcss2, then most probably you also already have the medibuntu repos added to your sources.list.
After that launch vlc from Applications>Sound and Video>vlc menu and press ctrl-D (or go to Media>Open Disc menu), select DVD and press play button.

---

### Post by Polaris96 on 2009-06-26
absolutely apt-get install vlc

For what it's worth, I freakin' LOVE kde's kaffeine player.  After months of trying to "fix" it, it's still broke.  Mplayers works a little better.

vlc just works.  use it

---

### Post by Zzl1xndd on 2009-06-26
The way Totem is setup by default doesn't like DVD's with Menus. 

So +1 to VLC.

---

### Post by Steelmourne on 2009-06-26
Check out the help page for playing dvd's in ubuntu's documentation - search for dvd's.

---

### Post by als123 on 2009-06-27
Thanks, I when to Medibuntu's site and downloaded and install libdvdread2 from here

[http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html)

and now totem works fine.

Thanks again

---

### Post by bhadotia on 2009-06-27
> **als123 said:**
> Thanks, I when to Medibuntu's site and downloaded and install libdvdread2 from here

[http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html)

and now totem works fine.

Thanks again

But it will be better if you add the medibuntu repository and then install the software. This will help in easy and clean running of the system. The instructions are [here]("https://help.ubuntu.com/community/Medibuntu").

---

