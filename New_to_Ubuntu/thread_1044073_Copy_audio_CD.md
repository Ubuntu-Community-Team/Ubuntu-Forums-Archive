---
title: "Copy audio CD"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by AopicieR on 2009-01-19
Hi, 

after two hours of Googleing I'm pretty frustrated as I was not able to make a backup copy of an audio CD in Ubuntu.
I tried creating an image using genisoimage in order to burn it using wodim, but the size of the image is only 100K.
I tried using "cdrdao copy" but after 15 minutes it was still hanging on the first track and I aborted the process.
I tried "burn -C", but it asks me to insert a blank CD/DVD which doesn't make any sense as I want to copy a CD.

I'd prefer a terminal solution as I'm not using Gnome/KDE/whatsoever.
Thank you very much.

---

### Post by Kobalt on 2009-01-19
Did you try [Jack]("http://www.home.unix-ag.org/arne/jack/") ?

---

### Post by dnRoyston on 2009-01-19
For terminal use, than I agree with Kobalt, try Jack. I use that to burn stuff from telnet, and I don't know of any other burners/copiers out there that support terminal use.

---

### Post by AopicieR on 2009-01-19
Thanks for the suggestion. 
I'm now using 
icedax dev=/dev/cdrom -vall cddb=0 -B -Owav
wodim dev=/dev/cdrw -v -dao -useinfo -text *.wav
It didn't work with the CD I first tried because of some problem with the CD info and I've only realized just now that it does work with other CDs. For the first CD I have to remove the -useinfo to get it working.
I'll try jack if I run into other problems.

---

### Post by philinux on 2009-01-19
Why not just use brasero or k3b from the repo. K3b Works a treat.

---

### Post by Sorivenul on 2009-01-19
Try "dd" or "cat".

dd
```
dd if=/dev/cdrom of=/tmp/filename.iso
```

cat
```
cat /dev/cdrom > filename.iso
```

Good luck!

---

### Post by AopicieR on 2009-01-19
Sorivenul: Thanks, but I had actually tried that before and I just get "Input/output error" for both commands.
I've now defined two aliases for the commands mentioned above and it works fine.

philinux: I don't know why but I prefer not to install any gnome/kde/xfce programs. But thanks for the suggestion, maybe I'll come back to it when I miss any features in the terminal programs.

---

### Post by andrew.46 on 2009-02-04
Hi,

Have you tried the most under-appreciated guide I have ever written:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

I have yet to create a coaster with this method.

Andrew

---

