---
title: "xorg.conf file missing?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by michael.wayne on 2010-01-22
Hi all,
I am having trouble with my monitor using Ubuntu for the first time. I have a laptop and the resolution of the screen is stuck at 800x600 (Monitor: Unknown).

I have been searching the forums and have come across a bit of code (I think it's code anyways) and it says it has to be added into the monitor section of the xorg.conf file. Thing is I cannot find the damn file!

I tried to 'locate' it, here are the results:
```

mike@mike-laptop:~$ sudo dpkg-reconfigure xserver-xorg
mike@mike-laptop:~$ locate xorg.conf
/usr/share/man/man5/xorg.conf.5.gz

```

If anybody may be able to help that would be great!



Thanks,
Mike :confused:

---

### Post by philinux on 2010-01-22
> **michael.wayne said:**
> Hi all,
I am having trouble with my monitor using Ubuntu for the first time. I have a laptop and the resolution of the screen is stuck at 800x600 (Monitor: Unknown).

I have been searching the forums and have come across a bit of code (I think it's code anyways) and it says it has to be added into the monitor section of the xorg.conf file. Thing is I cannot find the damn file!

I tried to 'locate' it, here are the results:
```

mike@mike-laptop:~$ sudo dpkg-reconfigure xserver-xorg
mike@mike-laptop:~$ locate xorg.conf
/usr/share/man/man5/xorg.conf.5.gz

```

If anybody may be able to help that would be great!



Thanks,
Mike :confused:

The latest versions of ubuntu dont need that file per se. I have one as I have an nvidia card so the install of the driver created one.

What graphics card have you got. Any driver offered under System>admin>hardware drivers

---

### Post by michael.wayne on 2010-01-22
Hi,

I need to add custom resolution options to the display prefs. There are no drivers offered up to me. :(
Where can I find the 'manage hardware' equivalent on Ubuntu to Windows? :)

---

### Post by philinux on 2010-01-22
> **michael.wayne said:**
> Hi,

I need to add custom resolution options to the display prefs. There are no drivers offered up to me. :(
Where can I find the 'manage hardware' equivalent on Ubuntu to Windows? :)

You can create the file xorg.conf using

```
gksu nautilus
```

This gives you a root enabled file browser so be careful.

Create the file in /etc/X11 where it should live.

when you say manage hardware do you mean system info. If so install this app [hardinfo]("apt:hardinfo"). It ends up in Apps>SystemTools>System profiler and Benchmark

---

### Post by warfacegod on 2010-01-22
> **philinux said:**
> You can create the file xorg.conf using

```
gksu nautilus
```

This gives you a root enabled file browser so be careful.

Create the file in /etc/X11 where it should live.

when you say manage hardware do you mean system info. If so install this app [hardinfo]("apt:hardinfo"). It ends up in Apps>SystemTools>System profiler and Benchmark

The xorg.conf file should already be there. Ubuntu still installs with it, it's just blank now.

---

### Post by philinux on 2010-01-22
> **warfacegod said:**
> The xorg.conf file should already be there. Ubuntu still installs with it, it's just blank now.

Some do not get one at all.

If you look at post #1 he did locate xorg.conf. :P

---

### Post by halitech on 2010-01-22
> **philinux said:**
> Some do not get one at all.

If you look at post #1 he did locate xorg.conf. :P

are you referring to the OP locating this file?

/usr/share/man/man5/xorg.conf.5.gz

thats not the xorg.conf file, just the man file for xorg.

@OP - an easy way to create it is to open a terminal and type the following
```
sudo touch /etc/X11/xorg.conf
```
then to add the settings you need, Press ALT + F2 and run
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by warfacegod on 2010-01-22
> **philinux said:**
> Some do not get one at all.

If you look at post #1 he did locate xorg.conf. :P

If he found it then why, in post one, does he specifically ask for help finding it, and why are you telling him where to find it?

---

### Post by philinux on 2010-01-22
> **warfacegod said:**
> If he found it then why, in post one, does he specifically ask for help finding it, and why are you telling him where to find it?

He shows in post 1 that he has not got the file. I merely showed him how to create the file.

I think it depends on graphics card. With nvidia for instance you will end up with an xorg.conf. Since I dont have any other card I cant comment as to which ones result in no xorg.conf being on the system.

---

