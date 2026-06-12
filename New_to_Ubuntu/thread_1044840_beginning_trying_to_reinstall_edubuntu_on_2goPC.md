---
title: "beginning trying to reinstall edubuntu on 2goPC"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by jennwesxc on 2009-01-19
Hi, 

I need to reinstall edubuntu on my 2goPC and I'm trying to figure out how to do that. I want to use my flash drive, (getting the edubuntu image onto my flash drive using a different computer that runs on windows) because my 2goPC doesn't have a CD drive. I've checked out the edubuntu website, but I'm having trouble understanding the directions I found there. Here's what they say:

"to install one of the images below to a Classmate PC you need a 1G (or bigger) USB key.
Write the image to this device with the dd or rawrite tools.
Example for dd (if your usb key is detected as /dev/sdd and the image hardy-classmate-20080311.img was downloaded to /tmp):
dd if=/tmp/hardy-classmate-20080311.img of=/dev/sdd
Plug the USB key in one of the Classmate PCs USB ports, hit F11 during boot and select the key with the image from your boot menu to start the installation."

What I've done so far is download the image that I believe is the correct one directly onto my flash drive (is that an okay thing to do?). I googled dd/rawrite to learn what that was, and learned that it's a way to do direct dumps from one device to another, but that said, I really don't understand what to do next. For example, I'm having trouble figuring out when (and on what computer--my working computer with windows, or my laptop that I'm trying to reinstall edubuntu back on) to type in dd if=/tmp/hardy-classmate-20080311.img of=/dev/sdd 
I'm also not sure if /dev/sdd was just an example of what a device might be called, or if that's what I'd actually type in. 

If anyone can help me better understand this process, I'd really appreciate it. 

Thanks a lot,
Jenn

---

### Post by yeats on 2009-01-19
/dev/sdd, dd, rawrite, etc. is for Linux, not Windows, and I know that just copying the disk image onto the USB drive won't work.  I've never done this, but it's probably helpful to know what *won't* work. :-)

I'm sure someone will speak up who has more experience with this.

Good luck.

---

### Post by jennwesxc on 2009-01-19
> **chrissharp123 said:**
> /dev/sdd, dd, rawrite, etc. is for Linux, not Windows, and I know that just copying the disk image onto the USB drive won't work.  I've never done this, but it's probably helpful to know what *won't* work. :-)

I'm sure someone will speak up who has more experience with this.

Good luck.

Do you know if downloading the image right onto the USB drive works (or is that just the same as copying it?)

Thanks, 

Jenn

---

### Post by rstack on 2009-02-05
Hi Jenn. Did you get this working? I am in the same boat as you.

Robert

---

### Post by niteshifter on 2009-02-05
Hi,

UNetbootin is what you need. See [this page]("http://unetbootin.sourceforge.net/"). This [page]("http://linuxondesktop.blogspot.com/2008/08/install-ubuntuand-other-linux-distros.html") may also be useful.

---

### Post by rstack on 2009-02-05
How do you use UNetbootin to create a bootable USB drive with a img file? I can do it with an ISO but not a img. Is there a way to change the img to a iso?

---

