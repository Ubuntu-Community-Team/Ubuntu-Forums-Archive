---
title: "USB WantTV DBV-T Digital"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by Segofam on 2011-04-02
Hi,

I have a WandTV DVB-T Digital Terrestrial TV Stick that I used to use with Windows.

If it is possible...

Would someone instruct me in how to get it to work with Ubuntu please?

Sincerely,

Scott

...I posted this in the Multimedia section to no avail.

---

### Post by TopEnder on 2011-04-02
> **Segofam said:**
> Hi,

I have a WandTV DVB-T Digital Terrestrial TV Stick that I used to use with Windows.

If it is possible...

Would someone instruct me in how to get it to work with Ubuntu please?

Sincerely,

Scott

...I posted this in the Multimedia section to no avail.
Scott, Connect the stick then check to see if there is any drivers for the stick by going to: System/Adminstration/Hardware Drivers, just follow any screen instructions.

---

### Post by Segofam on 2011-04-02
> **TopEnder said:**
> Scott, Connect the stick then check to see if there is any drivers for the stick by going to: System/Adminstration/Hardware Drivers, just follow any screen instructions.

Hi TopEnder,

The box came up with no proprietry drivers are in use on this computer!
Also, the Wand does not light up when I plug it in, but it does if I use Windows!

Any thoughts?

Regards,

Scott

---

### Post by TopEnder on 2011-04-02
As I stated in my previous post check for Drivers in System/Adminstration/Hardware Drivers (Top Panel), to see if there is any Ubuntu/Linux drivers for your USB Stick, follow on screen instructions (if any) to install.

---

### Post by Segofam on 2011-04-02
> **TopEnder said:**
> As I stated...
[IMG]file:///tmp/moz-screenshot-2.png[/IMG]
I attached a screen shot of the Hardware Driver pop up box...there are no choices!

Any suggestions!

---

### Post by TopEnder on 2011-04-02
Sorry to hear that, could you post the output for stick using a terminal command lsusb. ( my output for a Gadget Geek stick is : Bus 001 Device 003: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0), if its an Afatech chip then there is a lot of posts on that chip.

Hopefully someone in this forum can help, also do a search on Google for your stick chip and maybe on other Debian base Forums someone must have installed or tried to install that stick.

---

### Post by TopEnder on 2011-04-02
Sorry to hear that, could you post the output for stick using a terminal command lsusb. ( my output for a Gadget Geek stick is : Bus 001 Device 003: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0), if its an Afatech chip then there is a lot of posts on that chip.

Hopefully someone in this forum can help, also do a search on Google for your stick chip and maybe on other Debian base Forums someone must have installed or tried to install that stick.

---

### Post by Segofam on 2011-04-02
> **TopEnder said:**
> ...could you post the output for stick using a terminal command lsusb....

All this is Alien to me:

scott@scott-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 18b4:1001 e3C Technologies DUTV007
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1e4e:0803  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
scott@scott-laptop:~$ ^C
scott@scott-laptop:~$ 

Does appear as though it would have no recognition or drivers!?

---

### Post by jmszr on 2011-04-02
Segofam,

This thread looks like it might be of help: [http://ubuntuforums.org/archive/index.php/t-1233308.html](http://ubuntuforums.org/archive/index.php/t-1233308.html) .

---

