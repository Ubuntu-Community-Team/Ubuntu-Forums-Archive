---
title: "Can't find Floppy disk"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by brawd on 2009-05-20
I'm fairly sure I used to have a floppy disk detected when I first installed Ubuntu on these machines. Now I rarely use a floppy disk myself but I have to look after about 30 windoze machines for friends and family and they often use them, and ask me to check them because they don't work.

This happens on both my machines. The first is a dual core AMD running 64 bit Ubuntu 8.04 and the other is an old banger running Ubuntu 8.10. Neither show any trace (or indeed any interest at all in) floppy disk drives.

Any help or guidance greatly appreciated.

regards,

brawd.

---

### Post by Didius Falco on 2009-05-20
> **brawd said:**
> I'm fairly sure I used to have a floppy disk detected when I first installed Ubuntu on these machines. Now I rarely use a floppy disk myself but I have to look after about 30 windoze machines for friends and family and they often use them, and ask me to check them because they don't work.

This happens on both my machines. The first is a dual core AMD running 64 bit Ubuntu 8.04 and the other is an old banger running Ubuntu 8.10. Neither show any trace (or indeed any interest at all in) floppy disk drives.

Any help or guidance greatly appreciated.

regards,

brawd.

Hi,

You could add a line like this to your /etc/fstab file:

/```
dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

And then create a /media/floppy0 folder. That should allow you to auto-mount floppy disks when they are inserted.

Regards,

Didius

---

### Post by rbc on 2009-05-20
Go to terminal, and type:
gksu gedit /etc/modules

Add the word "floppy" (without the quotes), Save and close.

---

### Post by gandaran on 2009-05-20
> **brawd said:**
> I'm fairly sure I used to have a floppy disk detected when I first installed Ubuntu on these machines. Now I rarely use a floppy disk myself but I have to look after about 30 windoze machines for friends and family and they often use them, and ask me to check them because they don't work.

This happens on both my machines. The first is a dual core AMD running 64 bit Ubuntu 8.04 and the other is an old banger running Ubuntu 8.10. Neither show any trace (or indeed any interest at all in) floppy disk drives.

Any help or guidance greatly appreciated.

regards,

brawd.
you could upgrade to jaunty 9.04 this bug is fixed now.
check the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651") on how to fix it

---

### Post by Sir Jasper on 2009-05-20
Hi all,

In the unlikely case that Didius's  suggestion doen't work, try;
sudo modprobe floppy
which worked for me.

Hi Sir Didius, good to be with you once again.

My regards

Addendum:
Hi again Sir Didius, re your reply below:
my typing skills aren't either and I detest typing.
Is there a good speech to text progam for general use, commands and shortcuts?
If you find one, with your googling skills, a new thread would be of interest, at least to me.

---

### Post by Didius Falco on 2009-05-20
The ```
sudo modprobe floppy
``` and the ```
gksu gedit /etc/modules
``` solutions both look more elegant than my own. I'm sure mine would work, but it'd be more work, and more prone to error, especially if your typing skills are like mine...

Another pair for my Useful.Commands file!

Always good to "see" you Sir Jasper!

Regards,

Didius

---

### Post by rbc on 2009-05-20
I was under the impression that sudo modprobe floppy was only a temporary fix, but the bug is definitely fixed in Jaunty

---

### Post by Didius Falco on 2009-05-20
> **rbc said:**
> I was under the impression that sudo modprobe floppy was only a temporary fix, but the bug is definitely fixed in Jaunty

Yes, the first one would be temporary, but good enough for occasional use.

The bug was fixed so well that I have a floppy listing and no floppy drive. <G>

Thanks for adding to my knowledge, both of you.

Regards,

Didius

---

### Post by Sir Jasper on 2009-05-20
Hi again,

The first time I used "sudo modprobe floppy" the effect was temporary.

I repeated it long ago and I still have  "Floppy Drive" in my "places" menu.

That's using Xubuntu and Thunar - in case that  may make a difference.

My regards

---

### Post by joeray on 2009-06-07
The bug fix in jaunty may be back in karmic kernel. 
Thanks to one and all. I upgraded my jaunty install kernel to 2.6.29.2062904 generic (which helped a lot) because of intel chip problems yesterday and lost my self-installed floppy drive. I got it back this morning thanks to the info in this thread. You people are great. Joeray says freedom isn't free.

    Compaq Presario RZ537AA-ABA SR5010NX Intel Integrated 945 Chipset, 1.5GB Ram Intel(R) Celeron(R) D Firefox 3.0

---

