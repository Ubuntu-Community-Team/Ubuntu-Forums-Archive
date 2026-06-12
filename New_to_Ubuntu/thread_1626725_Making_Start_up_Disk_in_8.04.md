---
title: "Making Start up Disk in 8.04"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by lilyphoenix on 2010-11-20
I'm trying to install ubuntu 10.10 netbook but I currently have 8.04 (as installed by dell) and there is no start up disk creator in the system menu. How do I create a start up disk?

If no one answers, I'll try making it from my windows computer :,(

---

### Post by sikander3786 on 2010-11-20
Please see this page.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

And this one also,

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Don't use any software from the 8.04 repository. Instead download the latest version from the related website and use it to create the USB as the software in 8.04 repositories will be older and I doubt if it would be able to handle 10.10 correctly.

Good Luck!

---

### Post by blazemore on 2010-11-20
The startup disk creator isn't included in the 8.04 repositories.
You seem to know how to do it in Windows (I'd recommend Linux Live USB Creator), so I'd recommend doing that.
I tend to use this Windows tool and it always works for me.

---

### Post by theozzlives on 2010-11-20
If your netbook is 10.10 and 8.04 has less than a year left, I fail to see why you want an 8.04 startup disk.

---

### Post by theozzlives on 2010-11-20
I'd recommend upgrading to 10.04.1 LTS

---

### Post by blazemore on 2010-11-20
> **theozzlives said:**
> I'd recommend upgrading to 10.04.1 LTS

I think he means he wants to create a 10.10 startup disk, but doesn't have the tools to do so in 8.04

---

### Post by Rex Bouwense on 2010-11-20
You can't go wrong if you follow the advice in post #2.

---

### Post by beew on 2010-11-20
> **blazemore said:**
> The startup disk creator isn't included in the 8.04 repositories.
You seem to know how to do it in Windows (I'd recommend Linux Live USB Creator), so I'd recommend doing that.
I tend to use this Windows tool and it always works for me.


If OP is already running Linux why should he/she use Windows tools? Actually Linux tools work very well too if you give them a chance. :)

---

### Post by lilyphoenix on 2010-11-20
> **sikander3786 said:**
> 

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Good Luck!

I tried using the program mentioned, and I seem to have created the usb start up, but I can't get my dell mini 9 to boot from the usb. I pressed esc on start up, choose the option for usb and the screen from unetbootin keeps telling me it will boot in 10 seconds and counting down, then starting again. Any further ideas?

Also, I'm a she, apparently my user name is not girly enough...

---

### Post by sikander3786 on 2010-11-20
> **lilyphoenix said:**
> I tried using the program mentioned, and I seem to have created the usb start up, but I can't get my dell mini 9 to boot from the usb. I pressed esc on start up, choose the option for usb and the screen from unetbootin keeps telling me it will boot in 10 seconds and counting down, then starting again. Any further ideas?

Also, I'm a she, apparently my user name is not girly enough...
I have used that software often and never had a problem like that.

You can boot back into 8.04 and see what does the USB contain. Check the space used on it. It should be something around 700 MB.

And you might also need to check the integrity of downloaded image used to prepare the USB.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Rex Bouwense on 2010-11-20
I have one.  Occasionally, a flash drive is not recognized as a flash drive.  Check the BIOS to insure that your flash drive is recognized as a flash drive and not another hard drive.  I had that happen on a Dell Inspiron.  If it thinks that it is another hard drive then just adjust it to boot first in the BIOS.  Not a biggie.

---

### Post by lilyphoenix on 2010-11-20
> **sikander3786 said:**
> 

You can boot back into 8.04 and see what does the USB contain. Check the space used on it. It should be something around 700 MB.


Hmm, 92KB, I guess I'll try again.

---

### Post by lilyphoenix on 2010-11-20
I start UNetbootin again and, apparently, I'm missing the packet mtools and 7z...any ideas where to find these?

Nevermind, opened synaptic packet manager and searched.

---

### Post by sikander3786 on 2010-11-20
> **lilyphoenix said:**
> I start UNetbootin again and, apparently, I'm missing the packet mtools and 7z...any ideas where to find these?
I don't think those 2 packages should be causing some problem. You can try intalling them from Applications > Accessories > Terminal by using this command.

```
sudo apt-get install mtools p7zip-full
```

I am not using 8.04 so can't guess exactly what is going wrong there.

---

### Post by lilyphoenix on 2010-11-20
Now, before I actually install (I'm just going to test it out for now) what's the quickest way to backup my system?

---

### Post by sikander3786 on 2010-11-20
> **lilyphoenix said:**
> Now, before I actually install (I'm just going to test it out for now) what's the quickest way to backup my system?
Has the USB been created successfully? Are you able to boot from that?

Regarding backup, in my opinion, the easiest and the simplest is clonezilla.

[http://clonezilla.org](http://clonezilla.org)

---

### Post by lilyphoenix on 2010-11-20
Okay, apparently the missing packets were the issue.

So, 10.10 netbook ed. is very different. Apparently I need a proprietary driver for my wireless (boo dell). Now to test stuff and make sure all my hardware still works, and figure out how to back up my files before I make the switch.

Oddly enough, I'm still getting programs with options menus with okay buttons off the bottom of my 9" screen, so much for being tuned for netbooks... (evolution set up).

---

