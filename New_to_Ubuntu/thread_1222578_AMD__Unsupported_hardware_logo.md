---
title: "AMD  Unsupported hardware logo"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by loseby on 2009-07-25
have an amd unsupported hardware icon/message/logo appearing in the bottom right of my monitor. I have just replaced a 4870 with a 4890


Are 4890 supported ?

btw: went to system/admin/hardware drivers but it says the driver is activated and in use

---

### Post by keplerspeed on 2009-07-25
Are you talking about ATI graphics cards? What version of ubuntu are you using?

Enter this to find out:
```

uname -r

```

---

### Post by loseby on 2009-07-25
using 9.04 ( pretty sure but am in Win7 mode atm )

And yes, I am using a AMD graphics card. I had a AMD 4870 and it workedbut when I upgraded to the 4890 I got that message about unsupported hardware

---

### Post by markbuntu on 2009-07-25
That is a very new card so I doubt the driver you have suports it.
You need to get the latest driver from ati. Be sure to read the release ntes and installer instructions.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by lestatius on 2009-07-27
I have the same problem. I have the same card (Radeon HD4890). Why does it show the AMD logo. I have an intel mobo and cpu? And I activated the radeon driver through administration-->hardware drivers too.

this is my what I get when I run

```
uname -r
```

2.6.28-13-generic

---

### Post by lestatius on 2009-07-27
I got it to work :D thanks

---

### Post by CrinkElite on 2009-07-31
> **lestatius said:**
> I got it to work :D thanks

hi I'm having the same problem 
can you let me know how you fixed it. i can't access the display options in the admin tab as the computer hangs. 

nice one

ps. i have a 4890 i just haven't updated my signature

---

### Post by lestatius on 2009-08-01
> **CrinkElite said:**
> hi I'm having the same problem 
can you let me know how you fixed it. i can't access the display options in the admin tab as the computer hangs. 

nice one

ps. i have a 4890 i just haven't updated my signature


download the driver and instructions of how to install here:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

that should work :D if you have any questions just let me know.

---

### Post by 3rdalbum on 2009-08-01
> **lestatius said:**
> Why does it show the AMD logo. I have an intel mobo and cpu?

Your graphics card is an ATI, which is made by AMD. The "unsupported hardware" is the graphics card, which is not officially supported by the graphics driver you are using.

---

