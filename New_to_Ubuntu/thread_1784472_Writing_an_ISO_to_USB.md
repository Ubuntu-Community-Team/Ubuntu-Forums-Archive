---
title: "Writing an ISO to USB"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by AlvitrValkyrie on 2011-06-17
Can someone help me install opensuse in virtualbox?
I don't have an optical drive, so using a disk is out of the question.
I want to know if there's a simple way to take the suse ISO and write it to my USB. So far, I've only found programs that help me write Ubuntu to a USB...

---

### Post by Paresh on 2011-06-17
Have you tried [PenDriveLinux]("http://www.pendrivelinux.com")?

They usually have a range of articles on various systems.

However, if you're installing on virtual box, you can simply add a CD drive to your virtual box guest and point it to the ISO file without mounting it on a USB, that's the way I do it.

---

### Post by beew on 2011-06-17
If you are running Ubuntu this tool is very handy.

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Website is in French but the program is in English (probably depending on where you download it)

BTW, does OpenSuse only offer DVD image for download? (4.7G!) Do you know if I can get a CD image?

---

### Post by mister_playboy on 2011-06-17
> **beew said:**
> If you are running Ubuntu this tool is very handy.

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Website is in French but the program is in English (probably depending on where you download it)

BTW, does OpenSuse only offer DVD image for download? (4.7G!) Do you know if I can get a CD image?

CDs are available right on the download page: [http://software.opensuse.org/114/en](http://software.opensuse.org/114/en)

None of this is necessary since he's just trying to install in VirtualBox... he just needs to mount the ISO on the virtual drive as already mentioned.

---

### Post by AlvitrValkyrie on 2011-06-17
> **beew said:**
> If you are running Ubuntu this tool is very handy.

[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Website is in French but the program is in English (probably depending on where you download it)

BTW, does OpenSuse only offer DVD image for download? (4.7G!) Do you know if I can get a CD image?

Yeah, you can. [http://software.opensuse.org/114/en](http://software.opensuse.org/114/en) Click on Live GNOME or KDE.

---

### Post by AlvitrValkyrie on 2011-06-17
> **mister_playboy said:**
> CDs are available right on the download page: [http://software.opensuse.org/114/en](http://software.opensuse.org/114/en)

None of this is necessary since he's just trying to install in VirtualBox... he just needs to mount the ISO on the virtual drive as already mentioned.

How would I mount it on the virtual drive?

---

### Post by mister_playboy on 2011-06-17
With VirtualBox open, just press F1 to access the help information.

Unlike most other Linux programs, the VB manual is extremely comprehensive and easy to use.  It will do a better job explaining than I could.

---

### Post by AlvitrValkyrie on 2011-06-17
And yooop. I've used pendrive linux a whole bunch of times...

---

### Post by AlvitrValkyrie on 2011-06-17
> **mister_playboy said:**
> With VirtualBox open, just press F1 to access the help information.

Unlike most other Linux programs, the VB manual is extremely comprehensive and easy to use.  It will do a better job explaining than I could.



Hmmmmm.

I downloaded the help file, and found the appropriate section. All it tells you is that there is an area to select the ISO....not when there is, so I'm confused which menu is the right one

---

### Post by AlvitrValkyrie on 2011-06-17
hah, I found it x.x
Thanks a lot!

-feels like a NUB-

---

### Post by mister_playboy on 2011-06-17
Assuming you have already created the virtual machine.  Click on Storage, the click on the word "Empty" next to the CD icon under "IDE Controller", then click on the CD icon over on the right side of the window and choose your OpenSUSE ISO.

---

### Post by SeePU on 2011-06-19
> **Paresh said:**
> Have you tried [PenDriveLinux]("http://www.pendrivelinux.com")?

They usually have a range of articles on various systems.

However, if you're installing on virtual box, you can simply add a CD drive to your virtual box guest and point it to the ISO file without mounting it on a USB, that's the way I do it.PendriveLinux is a POS.  I suspect a Windows user created that site to turn off Linux users.

I tried XBOOT which gives you a present of Malware.

YUMI doesn't work.  This glorious work of software can't detect the .iso files you downloaded already.  So, these are their highlighted USB flashdrive programs to boot distros, huh?  

NIIIIIIIIIIIIIICE....

Epic fail...

---

### Post by Paresh on 2011-06-19
> **SeePU said:**
> PendriveLinux is a POS.  I suspect a Windows user created that site to turn off Linux users.

I'm not sure why you think that, I have do evidence to support your view, but my own experience with that site has been mostly successful, and it hasn't turned me off Linux.

---

### Post by HermanAB on 2011-06-19
Uhmmm...  lots of misguided advice above.

Suse (as well as Redhat, Fedora, CentOS, Mandriva, Mageia and PCLinuxOS) ISO files are dual mode and can be written directly to a USB memory device.  You do not need special software to do it. (Basically, it is only Ubuntu that is behind the times - everybody else figured out how to do this many years ago).

Plug USB stick in.
$ dmesg
Look to see which device name comes up, for example /dev/sdc

Now simply write the ISO file to it:
$ sudo dd if=susefile.iso of=/dev/sdc

La voila!

---

