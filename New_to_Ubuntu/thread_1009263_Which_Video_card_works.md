---
title: "Which Video card works"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Brutus2006 on 2008-12-12
I have a Nvidia 5500FX and am using Ubuntu 8.10 I cant get this to work at all with proper screen resolution, only have 2 settings. Im pretty green with Linux and wondering if there is a hassle free video card that works great with Ubuntu. no fussing around with config files. Im totally confused on how to make this work right.
Any help or answers would be greatly appreciated

---

### Post by wolfen69 on 2008-12-12
open a terminal and: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then reboot or restart x.

---

### Post by Brutus2006 on 2008-12-12
ok i did that but highest screen resolution is 800x600

---

### Post by Brutus2006 on 2008-12-12
I really would like it higher like around 1024x768

---

### Post by Drakkor on 2008-12-12
Did you install the propietary hardware drivers ?

---

### Post by Locke_99GS on 2008-12-12
That card ought to work just fine.

Are you using the proprietary driver?

You can force that resolution by adding that mode (or modeline) to your /etc/X11/xorg.conf file.

---

### Post by Drakkor on 2008-12-12
Try System>Administration>Hardware Drivers

---

### Post by stchman on 2008-12-12
Go to System--->Administration--->Restricted Driver Manager and enable the Nvidia driver is you have not done that.

---

### Post by Brutus2006 on 2008-12-12
I think so how do I tell like I say Im pretty new here

---

### Post by Brutus2006 on 2008-12-12
ok I enabled my driver and restarted highest my resoultion goes is 640x480

---

### Post by JKBurton on 2008-12-12
I've seen 8400GS cards as low as $25 recently, and with the restricted drivers installed, they love Ubuntu. I have them in two systems. 

Don't try an ATI card. I like their hardware, but their Linux drivers are a year or two behind Nvidia's and it makes a huge difference.

I think the last time I used a 5500FX I had to use the "173" restricted driver instead of the "177" one. If you want to try that, FIRST uninstall the existing driver and reboot before installing the new one. Otherwise it wouldn't work right for me.

---

### Post by Brutus2006 on 2008-12-12
I have the 173 restricted driver installed but only get 640x480

---

### Post by JACook on 2008-12-12
I had the same problem that you are describing.  Ubuntu also does not recognize my monitor, and cannot detect it when you click the Detect Monitor button.  I am wondering if it is related to this...  My monitor is not a plug-and-play monitor.  It is fairly old, a Viewsonic A70 CRT.  Windows does not recognize it either; just calls it "Default".

I'm using a PNY 5200FX AGP graphics card.  Same driver you are.

---

### Post by Drakkor on 2008-12-13
I also have an "unknown" monitor,but after the proprietary hardware drivers were installed , I get anywhere from

---

