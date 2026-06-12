---
title: "Running FreeBSD on Linux"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-01-15
Hi!

Question:
I need to test some software I wrote for FreeBSD.
Thus I want to run FreeBSD, but on my Linux partition.
I want to whipe the FreeBSD installation afterwards.

Now three questions:
Which is the
1. Easiest to setup VM
2. Fastest VM
3. most functional VM

for that purpose?

And I need USB support (memory stick).

---

### Post by albinootje on 2009-01-15
> **WitchCraft said:**
>  I need to test some software I wrote for FreeBSD.
Thus I want to run FreeBSD, but on my Linux partition.


Do you need a GUI in FreeBSD or not ?

You could use a live cd like this :
[http://www.rofreesbie.org/](http://www.rofreesbie.org/)

About VM's : Qemu and qemu-launcher is interesting, but slower than VirtualBox.

I've used FreeBSD on the desktop in the past, and I still use it on a few machines (non desktop) at work, but it's a while when I played with the few FreeBSD live cdroms there are.

And concerning the usb-support, if that's difficult, then you have another option.
In both Qemu and VirtualBox, when using NAT networking in the guest VM, you can run a web-server or ssh-server on 10.0.2.2, which is your host ip-address by default in the VM NAT setup, and then download your software from the host into the guest VM.

---

### Post by WitchCraft on 2009-01-15
> **albinootje said:**
> 
Do you need a GUI in FreeBSD or not ?

You could use a live cd like this :
[http://www.rofreesbie.org/](http://www.rofreesbie.org/)


yes I need a GUI. 
No I don't want a live cd.

> **albinootje said:**
> 
About VM's : Qemu and qemu-launcher is interesting, but slower than VirtualBox.


good, that answers 2.
qemu is more functional than VirtualBox?


> **albinootje said:**
> 
And concerning the usb-support, if that's difficult, then you have another option.
In both Qemu and VirtualBox, when using NAT networking in the guest VM, you can run a web-server or ssh-server on 10.0.2.2, which is your host ip-address by default in the VM NAT setup, and then download your software from the host into the guest VM.
Interesting.
I'll try that one, just for fun ;-)

---

### Post by WitchCraft on 2009-01-16
New question:

I'm trying to run freebsd xorg in the VirtualBox VM.
So far I installed the command line version and figured out that the updatedb command is  /usr/libexec/locate.updatedb

and I did 
pkg_add -r xorg


Now I should run Xorg -configure but this only shows a black screen...
Any ideas?

---

### Post by albinootje on 2009-01-16
> **WitchCraft said:**
>  pkg_add -r xorg

Hmm :( [http://www.virtualbox.org/ticket/1517](http://www.virtualbox.org/ticket/1517)

And you can try "startx" right away.
[http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)

---

### Post by WitchCraft on 2009-01-16
> **albinootje said:**
> 
Hmm :( [http://www.virtualbox.org/ticket/1517](http://www.virtualbox.org/ticket/1517)


F***!
Thanks for the info - That sux - ...

> **albinootje said:**
> 
And you can try "startx" right away.
[http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)


Anybody knows whether copy-pasteing the Linux xorg.conf works?

---

### Post by albinootje on 2009-01-16
> **WitchCraft said:**
> F***!
Thanks for the info - That sux - ...


I've just tried VirtualBox 2.1 (PUEL) with FreeBSD 7.1 as guest VM choosing X-user during the installation.
I had to boot with ACPI disabled, but then "startx" gave me a nice desktop! :)

I will still have to sort out the networking though, see here :
[http://www.wzdftpd.net/blog/index.php?2008/02/22/10-freebsd-7-installation-in-virtualbox](http://www.wzdftpd.net/blog/index.php?2008/02/22/10-freebsd-7-installation-in-virtualbox)

---

### Post by albinootje on 2009-01-16
> **albinootje said:**
> I've just tried VirtualBox 2.1 (PUEL) with FreeBSD 7.1 as guest VM choosing X-user during the installation.


After figuring out the network, I tried compiling something, and it bailed out. After giving the guest VM more RAM (300Mb instead of 192Mb) it still bailed out.
Because I was curious (As a Linux *and* FreeBSD advocate), I just installed qemu-launcher, and, even without the qemu kernel module enabled, the installation starts much faster (and disabling ACPI is not needed)..
Looks promising so far.

---

### Post by albinootje on 2009-01-16
> **albinootje said:**
> I just installed qemu-launcher, and, even without the qemu kernel module enabled, the installation starts much faster (and disabling ACPI is not needed)..
Looks promising so far.

It's a bit weird, with FreeBSD 7.1 as guest VM, Qemu (without the kernel module) is much faster than VirtualBox with *some* things, but on the whole it is slow :|
Of course you can also use VMware server (closed source but free-of-charge) to run FreeBSD as guest VM.

[http://ivoras.sharanet.org/freebsd/vmware.html](http://ivoras.sharanet.org/freebsd/vmware.html)
[http://blog.sourcehosting.net/2008/03/10/vmware-tools-installation-problem-under-freebsd-70/](http://blog.sourcehosting.net/2008/03/10/vmware-tools-installation-problem-under-freebsd-70/)

here's an image :
[http://blog.sourcehosting.net/2008/03/18/freebsd-70-vmware-image/](http://blog.sourcehosting.net/2008/03/18/freebsd-70-vmware-image/)

---

### Post by WitchCraft on 2009-01-17
> **albinootje said:**
> It's a bit weird, with FreeBSD 7.1 as guest VM, Qemu (without the kernel module) is much faster than VirtualBox with *some* things, but on the whole it is slow :|
Of course you can also use VMware server (closed source but free-of-charge) to run FreeBSD as guest VM.

[http://ivoras.sharanet.org/freebsd/vmware.html](http://ivoras.sharanet.org/freebsd/vmware.html)
[http://blog.sourcehosting.net/2008/03/10/vmware-tools-installation-problem-under-freebsd-70/](http://blog.sourcehosting.net/2008/03/10/vmware-tools-installation-problem-under-freebsd-70/)

here's an image :
[http://blog.sourcehosting.net/2008/03/18/freebsd-70-vmware-image/](http://blog.sourcehosting.net/2008/03/18/freebsd-70-vmware-image/)

Well it just doesn't seem to work... 
First the installation crashed (not enough ram allocated)
then the hard disk needs fscking
then xorg config doesn't work
I change the shell to bash in /etc/passwd, but that does not seem to have any effect
then xorg crashes, and the hard disk needs another fsck
Now xorg works, but the mouse doesn't...

Now I want to export my xorg.conf.new file from the vm to outside, but it doesn't work...

---

### Post by WitchCraft on 2009-01-17
Problem solved:
```

apt-get --purge remove `dpkg --search `which VirtualBox` | cut -d ":" -f1`

```

Previously I thought just Java and OpenOffice suck.
Now I have to correct myself:
Don't install anything made by Sun Mircosystems.

---

### Post by WitchCraft on 2009-01-17
OK, last question:

apt-get --purge remove

removes the programs, kernel modules and gnome-menus


But it doesn't remove
~/.VirtualBox

where some 3 GB of data are burried...

Which apt command would automagically remove ~/.VirtualBox ?

---

### Post by albinootje on 2009-01-17
> **WitchCraft said:**
> Problem solved:
```

apt-get --purge remove `dpkg --search `which VirtualBox` | cut -d ":" -f1`

```

Previously I thought just Java and OpenOffice suck.
Now I have to correct myself:
Don't install anything made by Sun Mircosystems.

You have very black and white opinions.
Since many years Solaris was a better product for the Enterprise than Linux was. 
OpenSolaris is a very promising product with ZFS and other goodies.
And personally I find VirtualBox a great product.

---

### Post by albinootje on 2009-01-17
> **WitchCraft said:**
>  Which apt command would automagically remove ~/.VirtualBox ?
Afaik apt-get will never remove personal settings.

---

### Post by WitchCraft on 2009-01-17
> **albinootje said:**
> 
You have very black and white opinions.


Yea, I know. 

For me, when it comes to software, something is either good and usable, or it is not.
There is no "in-between".

You know, my problem is not that there is a bug, which is something that can happen, and that in many cases could happen to anyone.

My problem is that buggy products are in most cases the result of an overall mental attitude that quality just is not important. Good marketing, much money spent on it, but no quality test.

And I have a (big) (acceptance) problem with this attitude.
That and with the attitude that you can just leave a bug open for a year or so - again, the same attitude problem...

If RELEASE VERSIONS are buggy once, then they are (most likely) buggy forever. They/you eliminate a bug, but you get another two for free.

Microsoft Windows is a good example for this, and so is OpenOffice and Java.

> **albinootje said:**
> 
Since many years Solaris was a better product for the Enterprise than Linux was. 


Solaris was built for another processor. 
Solaris was a long time not available for x86, and when I wanted to try it (that was appx. in 2002), it couldn't even correctly install to my harddisk (and that was NOT my fault). 
Linux (Debian), FreeBSD, Windows and even OpenBSD all installed fault-free at that time...

Diagnose: The company is unable to plagiarize (because it doesn't want the GPL in its product...)

And as a teacher of mine once said: 
You never have a second chance to make the first impression...

> **albinootje said:**
> 
with ZFS and other goodies.

And what do I profit of ZFS if the system does not recognize my hard-drive ? 
Sorry, but in my opinion, there seems to be a "tiny" priority problem...

> **albinootje said:**
> 
OpenSolaris is a very promising product

Sorry, I completely disagree. Solaris was made OpenSource for just the same reason as Mac made its operating system "OpenSource".
I never quite buyed it, and now Mac has closed the source for Darwin. I just wanna see how long it takes 'till Sun does the same.

It's their try to prevent their Software from becoming obsolete.
You work on it (for free) - they get the profit of it (your work) - later.
Sorry, again an attitude that I have a problem with.

> **albinootje said:**
> 
And personally I find VirtualBox a great product.


Your opinon - I disagree.
I personally am going to try installing FreeBSD via qemu, and if that doesn't work, I'm gonna install FreeBSD natively and move my Linux box to an USB drive - since FreeBSD is unable to support my USB drive for installation...

---

### Post by Mr-Biscuit on 2009-03-14
okay
install the kqemu kernel module and build it
then as root/sudo do a
#rmmod vboxdrv 
then a 
#modprobe kqemu

make a qcow2 image with
$qemu-img create -f <image name>.img <image size in mega/gigabytes, I suggest at least 8 for development and desktop use>

$ qemu -cdrom /path/to/cdrom-or-iso  -hda /path/to/image/file.img -m (you'll need 256 for a standard system with X and all, double that for development. I suggest 374m as a good number) -soundhw (I use sb16 here) -boot d

Follow the install instructions.

After install, close the vm during the simulated reboot.

Do the reboot from the command line with

$ qemu -hda /path/to/image -m (memory amount use above suggestion) -soundhw (look in the man page for other options) -boot c

Make this a bash script with
#!/bin/bash
/path/to/qemu -hda /path/to/image -m (memory amount use above suggestion) -soundhw (look in the man page for other options) -boot c

All paths must be exact.

As far as virtualbox goes. It really doesn't work on freebsd and freebsd doesn't exactly work on it.

---

