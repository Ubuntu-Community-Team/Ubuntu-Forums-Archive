---
title: "Upgrade of ubuntu - nvidia legacy drivers"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by drowner on 2009-04-10
Hi all

I am running 8.04 LTS. I wanted to upgrade to 8.10 before 9.04 comes out. I went to do it, and I got informed that my nvidia card is using the restricted drivers which are not compatible with the new kernel, and therefore they would revert to an older version, nv (or something)

Anyhoo, I was wondering:

1. Are new legacy drivers available that are compatible with 8.10?
2. What can i expect to happen if I do revert to nv? Will X start? Will I lose 3d acceleration? Can I get it back?

Cheers

---

### Post by drowner on 2009-04-10
More info:

```
lspci |grep VGA

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)

```

---

### Post by 3rdalbum on 2009-04-10
2. If you revert to nv, you'll get some measure of 2D acceleration (it won't be as slow as "vesa" mode) but no 3D. Yes, X will start, but Compiz won't.

Back when I was having trouble with the Nvidia driver, I used nv for about a month. There's nothing wrong with it if you don't play games or use Compiz.

Your other question, I don't know the answer to sorry.

---

### Post by Abhinavhardikar on 2009-04-10
> **drowner said:**
> Hi all

I am running 8.04 LTS. I wanted to upgrade to 8.10 before 9.04 comes out. I went to do it, and I got informed that my nvidia card is using the restricted drivers which are not compatible with the new kernel, and therefore they would revert to an older version, nv (or something)

Anyhoo, I was wondering:

1. Are new legacy drivers available that are compatible with 8.10?
2. What can i expect to happen if I do revert to nv? Will X start? Will I lose 3d acceleration? Can I get it back?

Cheers

Download this file:
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.11/NVIDIA-Linux-x86-96.43.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.11/NVIDIA-Linux-x86-96.43.11-pkg1.run)

restart in recovery mode from grub
when the menu come select 'root'
now go to the place where you downloaded the file 
run "./NVIDIA-Linux-x86-96.43.11-pkg1.run" Without ""

then the setup will start and will tell you that you are running in 'init 1' but still continue the setup.

do not panic if the setup stops. Restart it and select the other option where the setup had got cancelled.

Hope this helps. If you get any problem you can report here or [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Abhinav:p

---

### Post by mcurtiss1970 on 2009-04-23
I'm running the old Riva nvidia card/.71 driver in 8.04 as well.  

Can I safely assume this is not compatible with the xorg in 9.04 as was the case in 8.10?

---

