---
title: "DVD Playback Without Internet"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by inkpoisoningandpapercuts on 2010-10-22
I am currently downloading Ubuntu 10.10. Prior to that I was running 9.10.
With 9.10 I was unable to play commercial DVDs on my computer and I have read that the same is true with 10.10 without downloading something.
I do not have internet on the computer that will be running Ubuntu 10.10 but would like to be able to watch DVDs on it. Is it possible to download software on another computer then transfer it to the computer without internet via flashdrive and install it? Everything I've read has to be done on the computer running Ubuntu.

Thanks so much!

---

### Post by ubudog on 2010-10-22
This should make it possible:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by ArgusVision on 2010-10-22
You can download .deb files on another computer and install them locally.
What may work better is get APTonCD on your PC and one with internet.
You could get it as a .deb file. 
APTonCD allows you to pull your cached apt-get files and load them on the non-connected PC. This is actually a very good way to keep a non-connected PC updated.

 On the connected PC, go to [www.medibuntu.org](www.medibuntu.org) and follow the steps to add the repos and download all the needed codecs using apt. Then use APTonCD to transfer them to the non-connected PC.

---

### Post by ubudog on 2010-10-23
AptonCD is great.

---

### Post by ArgusVision on 2010-10-23
Here's a link to the sourceforge page for APTonCD. Just download the .deb and install it on the 2 pc's.

[http://aptoncd.sourceforge.net/download.html](http://aptoncd.sourceforge.net/download.html)

---

### Post by ArgusVision on 2010-10-23
Something I wasn't thinking about... Does the connected PC have Ubuntu on it or another Debian based Linux? or Windows?

---

### Post by inkpoisoningandpapercuts on 2010-10-23
The connected computer is actually a school-issued MacBook with a bunch of parental controls but I may be able to gain access to a PC to use if absolutely necessary. I can download to the Macbook but I can not install anything. (Limited I know)

---

### Post by ArgusVision on 2010-10-23
Well, that is limiting, but many files are available as .deb. 

Updates are generally via apt in Ubuntu though. A bootable usb drive might be a viable option. You could boot a mac and/or pc connected to the net booted to ubuntu to download updates and again use APTonCD to transfer.

---

### Post by inkpoisoningandpapercuts on 2010-10-23
Tell me if this is stupid, but would one of you be able and/or willing to email me the files with instructions (written for someone new to this) so that I can set it up? :confused:

If so I would be eternally grateful!

---

### Post by ArgusVision on 2010-10-24
It's not stupid at all, and I'd be glad to. Which part do you need the instructions for?  APTonCD, installing .deb files, and/or creating a bootable usb?

---

### Post by ubudog on 2010-10-24
On the computer with Internet, download the restricted-extras from here.

[http://archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/](http://archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/)

And copy the .deb file (it doesn't matter if it's on windows) to a flash drive.  Copy the .deb from the flash drive to the Ubuntu computer, double click it, install, and that should be it.  That's really all you need to do I think.

---

### Post by perspectoff on 2010-10-24
You also need (in addition to ubuntu-restricted-extras or kubuntu-restricted-extras) the libdvdcss2 module in order to watch commercial DVDs.

* You can install libdvdcss2 as a 64-bit .deb package without installing the Medibuntu repositories: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb

    or a 32-bit .deb package: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb


So, on a computer that has Internet access, download the correct 32-bit (i386) or 64-bit (amd64) version (whichever is appropriate for your computer) of the libdvdcss .deb:

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)

or

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)

Copy whichever .deb file you have downloaded to your USB drive, and then copy it from there to the (K)Ubuntu computer without Internet access. Then run the appropriate command (from the command-line interface Terminal or Konsole) to install it:

sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb

or

sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb

---

### Post by inkpoisoningandpapercuts on 2010-11-05
I was able to install the libdvdcss2_1.2.10-0.2medibuntu1_1386.deb without a problem.

However.. When I tried to install the restricted extras

> **ubudog said:**
> On the computer with Internet, download the restricted-extras from here.

[url]http://archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/[/url

And copy the .deb file (it doesn't matter if it's on windows) to a flash drive.  Copy the .deb from the flash drive to the Ubuntu computer, double click it, install, and that should be it.  That's really all you need to do I think.

This is what happened: [URL="http://oi54.tinypic.com/28jy04j.jpg"]http://oi54.tinypic.com/28jy04j.jpg
[/URL]
Any suggestions?
Am I using the correct .deb file?

---

### Post by inkpoisoningandpapercuts on 2010-11-06
> **inkpoisoningandpapercuts said:**
> I was able to install the libdvdcss2_1.2.10-0.2medibuntu1_1386.deb without a problem.

However.. When I tried to install the restricted extras



This is what happened: [URL="http://oi54.tinypic.com/28jy04j.jpg"]http://oi54.tinypic.com/28jy04j.jpg
[/URL]
Any suggestions?
Am I using the correct .deb file?

Nevermind, I figured that part out.
Now when I try to play a commercial DVD I get this: [http://i52.tinypic.com/211j7dc.png](http://i52.tinypic.com/211j7dc.png)
Any suggestions?

---

