---
title: "old installation to new computer"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by fattyz on 2010-11-25
Hi I am getting a new laptop and would like to transfer my current installation of ubuntu 10.04 to it.  I have searched and cannot find out how this is done.  If I could put the entire c drive on a usb stick I'd be all set.  Any help would be greatly appreciated.  I spent a lot of time getting my current install the way I like it and don't want to set it up all over again!

thanks in advance,
Happy Thanksgiving,

Fattyz:popcorn:

---

### Post by Rubi1200 on 2010-11-25
One option worth considering is Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by cavh on 2010-11-25
Suggest running a LiveCD of 10.04 on the new laptop first to ensure its hardware is supported okay.

---

### Post by pawhtiobo on 2010-11-25
Hi :)

First, you need to be aware, that your current installation may not work correctly in the new laptop, that depends on the new hardware.
The easy way is to download a Hirens Boot CD:

[http://www.hirensbootcd.org/cd-contents/136-hbcd-106.html](http://www.hirensbootcd.org/cd-contents/136-hbcd-106.html)

and use Norton Ghost to create an HDD image.

See ya...

---

### Post by Sylos on 2010-11-25
I think Remastersys would allow you to make a custom install CD to transfer that OS and all your post installation tweaks across. Then you would just need to transfer your media from /home etc to the new drive via USB drive or even set up a basic network to share the files from the old to the new.

---

### Post by HermanAB on 2010-11-25
Howdy,

Remastersys is probably the way to go.  You can transfer an old system by doing a low level copy of the HD, but it will take much longer and some things will not work, so it is not worth the trouble to do that.  

The exception is when the two machines are absolutely identical in which case you can simply swap the HD and even then you would have to tweak the ethernet configuration in udev.

If it was me, I would not even bother with remastersys, since it is easier and faster to install afresh.

---

### Post by Joe of loath on 2010-11-25
Install from scratch, and copy your home directory over. That way all your settings will be saved.

---

### Post by fattyz on 2010-11-25
ok, got it.  getting up early to pick up a lappy.  I've installed 10.04 on several computers now and your right, the settings don't matter as much as I thought.  As long as I have compiz fusion and vlc media player, I'm good to go.

Thanks 
FattyZ

---

