---
title: "Ubuntu doesn't recognise my CD/DVD drive"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by Templar00 on 2010-08-21
Hi Guys,

Long time reader (mainly when I've broke it), first time poster (mainly 'cause this time I can't fix it).

I'm sorry to bring you a problem you've probably seen before, but I've searched for the last 3 hours, tried it all, and had no luck.

I'm running Ubuntu 10.04 on a Toshiba Satellite Laptop, and have been doing so with generally great success for the last year. 

Now, after 12 months of Ubuntu, I decided to get adventurous, and test out Kubuntu, and possibly flash up Puppy Linux as well (just out of curiosity, I hear that is only dangerous to cats). This may or not be relevant, I don't know.

Today my DVD drive refuses to mount. More than that, the laptop won't even believe it is there. I've flipped over to Vista (Which I dual boot, but haven't needed to for the last 6 months) to prove it isn't a hardware issue, and indeed, it recognises the blank disc I currently have in there.

When I put in a CD the drive spins gently for a little while, then decides it can't be bothered, and stops. I've tried going to "Places" to see if the CD drive is on there - it was earlier, and I tried mounting it, but it wouldn't let me. Now it isn't even there.

I spotted this thread dated a week or so ago ([http://ubuntuforums.org/showthread.php?t=1549545&page=2](http://ubuntuforums.org/showthread.php?t=1549545&page=2)), and tried it all. When I got to the Wodim stage it recognises my USB modem (I'm on one of those stupid broadband dongle things), but not my DVD drive. It seems to me that when I plug the USB in, the DVD drive stops working. Does that make any sense to you?

Thanks guys in advance. I'll buy the guy/girl who fixes this a beer (but only if you're in London!)

Rich

---

### Post by jonnywombat on 2010-08-21
Have you confirmed that if you remove the usb dongle your dvd works again?

As you think the issue is usb related what is the output of the ```
lsusb
```

---

### Post by Templar00 on 2010-08-21
Hey Johnny,

That's the weird thing - if I put in the USB, then the DVD drive sometimes stops working. But if I take it out again, the DVD drive doesn't restart. I did get it working earlier, by restarting it with a CD in, but right now it doesn't recognise it again, even though I just started it with CD in place.

Lsusb gets me this:


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



I will admit I'm not great with the terminal - I follow instructions quite well, but I haven't memorised all the commands, nor know what many of them do. So please, be gentle!


Oh, and I am pretty sure it isn't a BIOS problem, as I have been booting Puppy Linux all day from CD (Though I can't get the ****ing thing booting from USB, like I want to!)

---

### Post by Templar00 on 2010-08-24
Any ideas at all? I've just had the same problem happen again - suddenly not recognising the DVD drive, then recognising it but swearing blind it's empty, then eventually after a restart or two, believing me when I say there is a DVD in there.

---

