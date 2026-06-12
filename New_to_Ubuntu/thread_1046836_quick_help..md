---
title: "quick help."
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Zach.Town on 2009-01-21
Alright, i'm in my live CD right now I have ubuntu on 1 partition and windows 7 on the other. I was messing around with something in the xorg.conf or something.

So now. when i start ubuntu i get the orange loading bar, then it's a black screen white text (grub? is that the name?) asks for my username and password and it acts like a terminal and that is it, no desktop no mouse, nothing.

So! how can I...

1. Completely overwrite my current ubuntu partition with another install (I won't mind doing this I had just reinstalled anyway.) I don't want 2 ubuntus going though.

2. OR! how can i simply fix the problem :D is there some magic shortcut or something?

---

### Post by yeats on 2009-01-21
It sounds like your X-server isn't starting, which is likely due to whatever changes you made.  Did you back it up before you edited xorg.conf?

---

### Post by Zach.Town on 2009-01-21
Heh, I think I did :/ not so sure. It asked me to and i copy pasted the command for it, I was doing something with multiple monitors.

---

### Post by adult swim on 2009-01-21
if you start your computer to ubuntu and login where it is all text, run this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` after it is done try ```
startx
```

---

### Post by Zach.Town on 2009-01-21
> **adult swim said:**
> if you start your computer to ubuntu and login where it is all text, run this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` after it is done try ```
startx
```


Gonna try this real quick be right back :D

---

### Post by Zach.Town on 2009-01-21
Didn't work :(

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111):unable to connect to x server
xinit:No such process (errno3): Server error.

That mean anything? it's what I got after doing start x

---

### Post by yeats on 2009-01-21
You could post the contents of your /etc/X11/xorg.conf file here to see if someone can help troubleshoot . . .

---

### Post by Zach.Town on 2009-01-21
I can't get to it >_< 

Is there a way i can just format over my current ubuntu?

---

### Post by yeats on 2009-01-21
You sure can, but why don't you 

```
ls /etc/X11/
```

to see if there's a file there like "xorg.conf.orig" or "xorg.conf~"

If there is, 

```
sudo cp xorg.conf[orig/~] xorg.conf
```

which will overwrite your "bad" xorg.conf with the original settings, then

```
startx
```

as adult swim suggested.

---

### Post by Zach.Town on 2009-01-21
I tried what he said, i'll attempt it with your varient.

but just incase it doesnt work how can i just cover over the ubuntu partition I have with a new one and keep my windows intact?

---

### Post by yeats on 2009-01-21
The install CD will detect that you have Windows installed - no worries.  If you're not sure, though, post back with a question.  Good luck ;-).

---

### Post by Zach.Town on 2009-01-21
tried what you said. didn't work same thing as adult swim's. 

for redoing the whole thing I looked at it earlier, it looked as if it wasn't touching the ubuntu I have right now, are you sure I wont have 2 ubuntus going with my windows?

---

### Post by yeats on 2009-01-21
:-)

Actually, yes it will assume that you want to keep all of your installed operating systems.

When it gets to the partitioner screen, select "Manual."  It will send you to a screen with color-coded representations of your hard drive partitions.  Make sure you're able to identify the Ubuntu partition (type ext3) and leave the Windows partitions (NTFS or FAT) and the swap as-is.  Once you know what's what, delete the Ubuntu partition and use that space to install your new Ubuntu (type ext3, mount point / ).  If that throws you, post back and someone can point you in the right direction.  

You can refer to this:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

but please post back if you're unsure.  It's always better to ask.

---

### Post by Zach.Town on 2009-01-21
I really appreciate all your help ^_^ Had to leave for a bit to watch some TV with the family, But i'll give it a try :D

I re-read what you wrote, i'm lost once you get past the select manual i know where that is but what is that other stuff haha.

---

### Post by adult swim on 2009-01-21
after you have selected manual in step 4, double click the partition that you currently have ubuntu installed on and make it look like this [IMG]http://farm4.static.flickr.com/3078/3126101691_7755d0e918_o.png[/IMG]
EDIT:  what has been messed up really shouldnt require a reinstall.  were you following a guide or something when xorg messed up?

---

### Post by Zach.Town on 2009-01-21
eh yes, multiple guides at once sort of haha. I think i edited my xorg thing before I had nvidia drivers. and then I got those then did it again and then a backup and yeah. It was a multi-monitor guide.

---

