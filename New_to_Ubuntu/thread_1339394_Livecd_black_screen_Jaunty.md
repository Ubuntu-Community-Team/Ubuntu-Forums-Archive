---
title: "Livecd black screen Jaunty"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Xarver on 2009-11-27
Hello I'm trying to install Jaunty, and I get a black screen when done booting. I think it may be my screen resolution, as anything else besides 1280 x 768 will be a black screen on my current mandriva box. How can I force xorg to use 1280 x 768 as my resolution?

P.S. I will not use 9.10 no matter what.
Please don't suggest it.
I'm on a Compaq Presario 2309US
Also, Ctrl alt f1 through f7 do nothing.
I have a Intel Corporation 82852/855GM Integrated Graphics Device

---

### Post by ukripper on 2009-11-27
ok let us see what you got in your xorg.conf:
```
gedit /etc/X11/xorg.conf
```

and post output of this command too:
```
cvt 1280 800 60
```

---

### Post by Buuntu on 2009-11-27
The black screen happens when booting from the live CD??? I've never heard of that happening when booting off the live CD, so it's possible that the CD might not be working correctly.  Try running a MD5SUM check on your CD to verify it's integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Xarver on 2009-11-27
> **ukripper said:**
> ok let us see what you got in your xorg.conf:
```
gedit /etc/X11/xorg.conf
```

and post output of this command too:
```
cvt 1280 800 60
```

I can't even access the file.
And I'm sure it's right.

---

### Post by Xarver on 2009-11-27
I can't even access the desktop, all I see is a black screen and I can't do any input.

---

### Post by ukripper on 2009-11-27
need more info like any error you getting or what else?

---

### Post by Buuntu on 2009-11-27
You still weren't very clear on whether this is when booting off the live CD or booting off the hard drive with a fresh install... If it's the latter, do you at least get past grub (the menu that lets you choose your OS)?

---

### Post by cabrey on 2009-11-27
Why won't you use 9.10? 9.04 had problems with Intel graphics chips, while Karmic fixes that (mostly).

---

### Post by Xarver on 2009-11-27
I'm on karmic via a VM on mandriva.
The problem is I want Jaunty because the distribution is based off of it.
trisquel is completely free software, and it's based on Jaunty.

---

### Post by anewguy on 2009-11-27
> **Xarver said:**
> I'm on karmic via a VM on mandriva.

So, you are trying to install Jaunty to the VM?  If so, just create a new VM.

> The problem is I want Jaunty because the distribution is based off of it. trisquel is completely free software, and it's based on Jaunty.

Trisquel from what I've seen is just another small Linux - so what exactly are you trying to do that you want Jaunty and another Linux - not to mention Ubuntu is free as well.

Could you please try to be more specific:

(1) Are you BOOTING your computer using a LiveCD or other Live media?

(2) Are you trying to install Jaunty in a VM in Mandriva, trying to install it in place of Mandriva, or trying to install it to dual-boot with Mandriva?

(3) I'm a little lost on your reference to trisquel - it's another Linux OS.  How does trisquel play into the picture of what you are trying to do?  Hopefully you can understand how we can be confused when you mention another type of Linux and mention free software, as Ubuntu is free Linux software as well.  Is there some part of trisquel, some program with it, that you are trying to do something with?

Obviously, we need a lot more information from you to understand first off what you are trying to accomplish, and then try to work on a solution with you.

Dave :)

---

### Post by Xarver on 2009-11-28
Actually, I'm fine now.
I was trying to install trisquel. (not a vm)
I used to use Mandriva.
I ran a karmic vm on mandriva.
now I switched to Karmic. :P

---

