---
title: "Video Card Driver"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by perito on 2008-12-30
My game Warcraft 3 keeps crashing on ubuntu, I cant start it. So I'm guessing its the Video Card Driver. My question is:
How do I find out what is my video card driver and how do i get it updated ? :)

---

### Post by perito on 2008-12-30
My game Warcraft 3 keeps crashing on ubuntu, I cant start it. So I'm guessing its the Video Card Driver. My question is:
How do I find out what is my video card driver and how do i get it updated ?

---

### Post by perito on 2008-12-30
I just did lspci -nn and got this

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)

how do I get latest version of this?

---

### Post by PmDematagoda on 2008-12-30
I don't think Warcraft 3 has a native Linux client, are you running this on Wine? If so, what version of Wine do you have?

---

### Post by perito on 2008-12-30
ubuntu@ubuntu-laptop:~$ wine --version
wine-1.0.1

---

### Post by Sealbhach on 2008-12-30
This should reveal it:

```
lshw -C display
```

Paste the output of that here.


.

---

### Post by perito on 2008-12-30
ubuntu@ubuntu-laptop:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
ubuntu@ubuntu-laptop:~$

---

### Post by Sealbhach on 2008-12-30
Oh, that didn't show the driver. You can look in your xorg.conf file:

```
cat /etc/X11/xorg.conf
```

It will list the driver there. A more convenient way to look through it is to put a copy of it on your desktop:

[HTML]cat /etc/X11/xorg.conf > ~/Desktop[/HTML]


.

---

### Post by perito on 2008-12-30
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by overdrank on 2008-12-30
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by Sealbhach on 2008-12-30
Doesn't say what it is. :confused:

Suggest start a new thread asking what the driver is for "Mobile 945GM/GMS, 943/940GML graphics card".

.

---

