---
title: "Old IDE hard drives"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by sqrooup on 2008-12-28
I have some old IDE hard drives, I also have an IDE to USB converter (this one; [http://www.maplin.co.uk/Module.aspx?ModuleNo=35057&DOY=28m12](http://www.maplin.co.uk/Module.aspx?ModuleNo=35057&DOY=28m12) )but it is not compatible with LINUX, is there any way to make it compatible? or is it a case of getting a new PCMCIA IDE card?

I have photos and music on some of them.

---

### Post by gn2 on 2008-12-28
Have you actually tried it yet?

Although it says on the page that Linux isn't supported, it might work anyway.

The only way to find out is to try it.

---

### Post by Bucky Ball on 2008-12-28
I would plug it in and find out as mentioned in the last post. I would have figured USB is USB and IDE is IDE, regardless of the OS.

---

### Post by 73ckn797 on 2008-12-28
Using an add-on IDE card will work.

---

### Post by halitech on 2008-12-28
honestly, if it works with Mac OS 8.6 it should work just fine with linux even if the say its not supported. 

```
OS. Supports
Windows 98, ME, 2000, XP
Mac OS.8.6 or higher
```

---

### Post by BDNiner on 2008-12-28
So long as your computer can read the partitions on the drive it should auto mount like any other USB media when you plug it in. I guess manufactures of the device are saying that they will not help you troubleshoot the device if you are running Linux.

---

### Post by johntravis on 2008-12-28
If your laptop/desktop allows you to boot from usb you should be good to go. In bios set your boot order to boot from usb first.

---

### Post by richg on 2008-12-28
I bought a IDE to USB converter some months ago that works very well with an ancient 20gb drive and a not so ancient 80gb drive. It also works with a CD drive.

Rich

---

### Post by sqrooup on 2008-12-29
Update;

It does not work, and none of the drives are bootable!

---

### Post by logos34 on 2008-12-29
> **sqrooup said:**
> Update;

It does not work, and none of the drives are bootable!

I used one successfully about a year ago and remember having to set the hard disk jumper (on the back) to 'master'

---

### Post by cariboo on 2008-12-29
If the device is the one in the attached screenshot, I'd be really surprised if it work at all. You need more power than what the usb connector can provide. I have only seen a few external usb drives that are powered by USB ports, and they need two usb connectors to operate correctly, one for power and the other to transfer data. You would be far better of with [this]("http:///www.maplin.co.uk/Module.aspx?ModuleNo=45441"), even though it is twice the price, a seperate power supply will ensure you have enough power to run the drive.

Jim

---

### Post by Frak on 2008-12-29
If it works on OS 8, that implies it is using a standardized interface. It'll read under Linux with no problem.

@what was said above
He's right, there's not enough power there.

---

### Post by gn2 on 2008-12-29
> **cariboo907 said:**
> If the device is the one in the attached screenshot, I'd be really surprised if it work at all. You need more power than what the usb connector can provide. 

Which is easily achieved by using a molex extension.

But absolutely DO NOT connect or disconnect it while the PSU is on.

---

