---
title: "More than one version on CD/DVD?"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-13
Hey there folks, is there a way to put more than one version of Ubnuntu, i.e., Kbuntu, etc., so I can choose to install these at will?  I notice you have to create an iso for each one of them; alot of wasted CD/DVDs.

---

### Post by hansolo4949 on 2011-05-13
Yes, there is a program called Xboot. It is a free application, and you can download it from here:[http://sites.google.com/site/shamurxboot/download](http://sites.google.com/site/shamurxboot/download)

You can use xboot on both disks, and USB drives (I think).

Hope that helps!

---

### Post by rosencrantz on 2011-05-13
Would booting from an USB drive be an option for you? IMO, it's the easiest way to try out live systems - or booting a CD image from a virtual machine...

---

### Post by dniMretsaM on 2011-05-13
You could try a minimal .iso. I believe it would allow you to choose what you install.

---

### Post by TAspr on 2011-05-25
> **rosencrantz said:**
> Would booting from an USB drive be an option for you? IMO, it's the easiest way to try out live systems - or booting a CD image from a virtual machine...

How do you setup a choice among the different systems on a USB Drive as well, how do you set up a Virtual Machine?

---

### Post by TAspr on 2011-05-25
> **dniMretsaM said:**
> You could try a minimal .iso. I believe it would allow you to choose what you install.

Is minimal .iso part of the Software Update Center in Ubuntu?

---

### Post by sandyd on 2011-05-25
> **TAspr said:**
> Is minimal .iso part of the Software Update Center in Ubuntu?

No, the minimal .iso is a seperate download. It installs the 'bare bones' required to run Ubuntu. From there, you can choose what you want to install. Might be a problem if you have a slow internet connection.

And if you try it.... and you click right past the message...

```

sudo tasksel
``` after your installation to choose what is installed. Use spacebar to choose, enter to accept

---

