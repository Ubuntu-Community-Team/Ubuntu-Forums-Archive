---
title: "Do I have Dove or i.MX51 board?"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by jimhoff on 2009-10-25
I'm trying to download the desktop image of 9.10 from this website_ _[http://releases.ubuntu.com/releases/9.10/](http://releases.ubuntu.com/releases/9.10/) so I can install ubuntu through the use of a flash drive. But i'm not sure if I need to marvel dove or Freescale i.MX51 image. Haven't been to successful finding out information on what exactly the differences are or how I can figure out which one I have.

I need the image to install onto a Dell Latitude d4340.

Thanks!

---

### Post by Hospadar on 2009-10-25
you probably want the cd version (not the image).  You can install this from a usb stick with the proper setup.

In ubuntu use usb-creator

in windows you can use: [http://www.ubuntugeek.com/usbuntu-live-creator-create-liveusbs-from-windows-using-a-gui.html](http://www.ubuntugeek.com/usbuntu-live-creator-create-liveusbs-from-windows-using-a-gui.html)

---

### Post by halitech on 2009-10-25
Both of them are ARM type boards and the Dell is either x86 or 64bit so you don't want either of them. You want the plain Desktop PC download which will give you an .iso file to burn directly to cd without extracting.


Marvel dove
[https://wiki.edubuntu.org/ARM/MarvellDoveKarmicInstall](https://wiki.edubuntu.org/ARM/MarvellDoveKarmicInstall)

Freescale i.mx51
[http://www.freescale.com/webapp/sps/site/prod_summary.jsp?code=i.MX515](http://www.freescale.com/webapp/sps/site/prod_summary.jsp?code=i.MX515)

---

### Post by jimhoff on 2009-10-25
awesome thanks

---

### Post by cong06 on 2010-04-30
Ok... I'm trying to figure this out too, and the links (while helpful) didn't really answer the question.

What's the difference? and why is there absolutely no information online?

I have a Eee PC 701SD. To download and install Netbook Edition 10.04, I have to choose between :
ubuntu-10.04-netbook-armel+dove.img
ubuntu-10.04-netbook-armel+imx51.img
(I'm also curious what armel is, there's no information about that either)

So, which one do I want? Isn't this just the processor architecture?

---

### Post by halitech on 2010-04-30
> **cong06 said:**
> Ok... I'm trying to figure this out too, and the links (while helpful) didn't really answer the question.

What's the difference? and why is there absolutely no information online?

I have a Eee PC 701SD. To download and install Netbook Edition 10.04, I have to choose between :
ubuntu-10.04-netbook-armel+dove.img
ubuntu-10.04-netbook-armel+imx51.img
(I'm also curious what armel is, there's no information about that either)

So, which one do I want? Isn't this just the processor architecture?

same as Jim, you don't want either one. The Eeepc uses an Intel® Celeron M 353 so you want the x86 version. Go here for instructions and download.

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

---

### Post by cong06 on 2010-04-30
Well, the Asus does say Intel on the outside, so I was a bit confused.

Actually, I just found that the mirror I used, I didn't scroll down far enough:
```

[   ] ubuntu-10.04-netbook-armel+dove.img.torrent  29-Apr-2010 18:19   21K  
[   ] ubuntu-10.04-netbook-armel+dove.img.zsync    29-Apr-2010 18:18  1.0M  
[TXT] ubuntu-10.04-netbook-armel+dove.list         27-Apr-2010 16:16  3.0K  
[   ] ubuntu-10.04-netbook-armel+dove.manifest     27-Apr-2010 15:28   35K  
[   ] ubuntu-10.04-netbook-armel+dove.metalink     29-Apr-2010 18:22  7.6K  
[   ] ubuntu-10.04-netbook-armel+imx51.img         27-Apr-2010 16:16  554M  
[   ] ubuntu-10.04-netbook-armel+imx51.img.torrent 29-Apr-2010 18:19   22K  
[   ] ubuntu-10.04-netbook-armel+imx51.img.zsync   29-Apr-2010 18:19  1.1M  
[TXT] ubuntu-10.04-netbook-armel+imx51.list        27-Apr-2010 16:16  3.0K  
[   ] ubuntu-10.04-netbook-armel+imx51.manifest    27-Apr-2010 13:33   35K  
[   ] ubuntu-10.04-netbook-armel+imx51.metalink    29-Apr-2010 18:22  7.6K  
[   ] ubuntu-10.04-netbook-i386.iso                29-Apr-2010 14:12  700M  
[   ] ubuntu-10.04-netbook-i386.iso.torrent        29-Apr-2010 18:19   28K  
[   ] ubuntu-10.04-netbook-i386.iso.zsync          29-Apr-2010 18:17  1.4M  
[TXT] ubuntu-10.04-netbook-i386.list               29-Apr-2010 14:13  4.5K  
[   ] ubuntu-10.04-netbook-i386.manifest           29-Apr-2010 13:39   38K  
[   ] ubuntu-10.04-netbook-i386.metalink           29-Apr-2010 18:22  7.2K  

```



So sweet...

---

