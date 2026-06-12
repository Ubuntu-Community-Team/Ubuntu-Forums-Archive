---
title: "Linux distro with no plymouth"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by jaycee23 on 2010-11-07
For some reason my laptop will not play ball with Plymouth. I have managed to get it to work with 9.10 but without any graphics driver. If I install a driver all I get is vertical lines all over the display making it unusable. I can hear the OS in the background and if I guess where to click I can hear it working away so it is purely a display / graphics issue.

I can get 10.10 to install messing with the boot options but if I try to install the driver the lines reappear and with 9.10 I don't need to adjust settings at boot. I have tried all sorts but nothing works except the above setup.

I also tried other Linux distros inc PCLinuxOS and openSUSE but I didn't get past the boot page going blank!

The system is a Windows 7 dual boot and Windows works absolutely fine and will even play games such as Crysis so I know the hardware is fine.

So my final thought is to try a distro which does not use Plymouth (such as 9.10) before I completely give up.

My laptop specs are in my sig. 

Any thoughts welcome!

---

### Post by bioterror on 2010-11-07
If you want something Easy, go with the Salix OS.
If you want to go the hard way, Arch Linux or Gentoo or normal Debian.

---

### Post by theozzlives on 2010-11-07
> **bioterror said:**
> If you want something Easy, go with the Salix OS.
If you want to go the hard way, Arch Linux or Gentoo or normal Debian.

Also Knoppix.

---

### Post by coffeecat on 2010-11-07
> **jaycee23 said:**
> Any thoughts welcome!

Remove 'quiet splash' from the kernel boot options. Instead of the Plymouth splash, you'll get scrolling text which is not pretty, but prettier than the artifacts you're seeing. 

But...

> **jaycee23 said:**
> I have managed to get it to work with 9.10 but without any graphics driver.

I think you mean without the proprietary driver. If you had no graphics driver at all, you wouldn't see anything! All of this, and this:

> **jaycee23 said:**
> I also tried other Linux distros inc PCLinuxOS and openSUSE but I didn't get past the boot page going blank!

... certainly sounds like a graphics card issue. Perhaps if you post details of the graphics card and what boot options you've already tried someone might be able to help you.

---

### Post by jaycee23 on 2010-11-07
> **coffeecat said:**
> Remove 'quiet splash' from the kernel boot options. Instead of the Plymouth splash, you'll get scrolling text which is not pretty, but prettier than the artifacts you're seeing. 

But...



I think you mean without the proprietary driver. If you had no graphics driver at all, you wouldn't see anything! All of this, and this:



... certainly sounds like a graphics card issue. Perhaps if you post details of the graphics card and what boot options you've already tried someone might be able to help you.

Very happy to take any help.

Yes - boots with nomodeset and quiet splash but then get pushed into low graphics mode when reboot.

Graphics card is Nvidia GeForce 8600M GT

---

### Post by coffeecat on 2010-11-07
Curious. Are you using the default nouveau video driver or have you installed the proprietary nvidia one?

---

### Post by jaycee23 on 2010-11-07
> **coffeecat said:**
> Curious. Are you using the default nouveau video driver or have you installed the proprietary nvidia one?

Default nouveau driver and even that doesn't work on versions after 9.10!

---

### Post by JustinR on 2010-11-07
> **jaycee23 said:**
> 
Graphics card is Nvidia GeForce 8600M GT

I have the same card in my laptop - and it works fine.

Have you tried this guide?
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

(Works for 10.10 too)

---

### Post by jaycee23 on 2010-11-07
> **JustinR said:**
> I have the same card in my laptop - and it works fine.

Have you tried this guide?
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

(Works for 10.10 too)

Odd thing about this problem is that initially when I installed 10.04 all worked well until one day when it didn't and I have no idea why.

Now I can't even see the login page I just get flashing vertical lines distorting the whole screen.

---

