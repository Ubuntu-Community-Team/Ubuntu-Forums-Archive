---
title: "Ubuntu will not boot after removing ATI driver"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by coolcatco888 on 2009-11-11
Hi,

I recently upgraded from 9.04 to 9.10.  The problem was when I upgraded, my ATI graphics card proprietary driver was disabled.  It was kinda annoying since compiz did not work and general scrolling was really really slow.

I was unable to activate it and after searching around, I found out that apparently ATI does not have a driver that is compatible with the latest Ubuntu.

So I decided to try to revert to the open source ATI driver.  I read this:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

And I ran:
```
$ sudo apt-get remove --purge xorg-driver-fglrx
```
which removed my driver.  When I rebooted.  It would not boot up.

I would see a screen that said:
Setting up Restricted Drivers...
Starting up Apache.. and so on.

The screen started flickering and it just hangs there.

What do I do?  I tried recovering but that does nothing and I tried installing the open source driver from the terminal but that does not help either.

Need help!

- Thanks

---

### Post by asuastrophysics on 2009-11-11
if you're at the shell prompt, type
```
aptitude
```

you should be able to search for any remaining proprietary ATI drivers in there.

---

### Post by coolcatco888 on 2009-11-11
thanks, actually it had something to do with firestarter hanging, so I removed it.  I got it to now.

However Catalyst 9.10 does not seem to install on Ubuntu 9.10. I downloaded the driver from the ATI site and installed it.

Here is my install log:
```
Errors during DKMS module removal
Errors during DKMS module removal
[Error] Kernel Module : Failed to add fglrx-8.661 to DKMS
```

I look under hardware drivers and the fglrx driver is disabled.  I click activate, put in my admin password and it downloads and installs (I guess from the repository) the driver but does not activate it.  I noticed that the latest version of the driver on synaptic is 8.660 (the one I am trying to install is 8.661)

My computer does not seem to use any hardware gfx acceleration right now.  Compiz does not work at the moment as well as any games under wine.

is fglrx supported in 9.10?

is there an open source alternative that works just as good as the proprietary driver and would let me use compiz and play wine games again?

- Thanks!

---

### Post by halitech on 2009-11-11
what ati video card do you have?

---

### Post by alphacrucis2 on 2009-11-11
> **coolcatco888 said:**
> thanks, actually it had something to do with firestarter hanging, so I removed it.  I got it to now.

However Catalyst 9.10 does not seem to install on Ubuntu 9.10. I downloaded the driver from the ATI site and installed it.


The fglrx driver in Karmic repos is already Catalyst 9.10. It was prereleased to Ubuntu by ATI when Karmic was still in beta. 



> I look under hardware drivers and the fglrx driver is disabled.  I click activate, put in my admin password and it downloads and installs (I guess from the repository) the driver but does not activate it.  I noticed that the latest version of the driver on synaptic is 8.660 (the one I am trying to install is 8.661)

What is you specific card? 

> My computer does not seem to use any hardware gfx acceleration right now.  Compiz does not work at the moment as well as any games under wine.

is fglrx supported in 9.10?

Yes. I am running it.

---

### Post by SlugSlug on 2009-11-11
try install envyng, run it as root with a -t flag
```
sudo envyng -t
```

and let that do the work of removing old driver and installing new...

---

### Post by coolcatco888 on 2009-11-14
Hi,
I have a Radeon HD 2600 Pro.

I checked synaptic, the latest version available to me is:

2:8660-0ubuntu4, which does not work.

envyng -t does not work either.

It keeps giving me:

"envyng has detected that the headers for your kernel are missing and cannot be installed"

Installing it through Hardware Drivers fails.

What should I do?

---

### Post by halitech on 2009-11-14
Grab the drivers here: 
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English)

Read the installer instructions and make sure you follow it *Exactly*

---

### Post by coolcatco888 on 2009-11-14
> **halitech said:**
> Grab the drivers here: 
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English)

Read the installer instructions and make sure you follow it *Exactly*


I have tried installing that driver many times, ati catalyst 9.10 still does not work.  I even used that installer to build .deb installer packages. After building the .deb packages for Ubuntu/karmic I placed them all in one folder and ran:

```
sudo dpkg -i *.deb
```

it seemed to run fine but I got this in the output:

```
Setting up fglrx-kernel-source (2:8.661-0ubuntu1) ...
Loading new fglrx-8.661 DKMS files...
Building initial module for 2.6.28-11-generic, architecture -a i686

Error! Your kernel source for kernel 2.6.28-11-generic cannot be found at
/lib/modules/2.6.28-11-generic/build or /lib/modules/2.6.28-11-generic/source.
Done.

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.28-11-generic (i686) first.

```

Which is pretty much the same thing as I got before when I ran the .sh installer.

**Can anyone give me any insight as to what the DKMS errors are and how to fix them?**

Someone else mentioned that the latest drivers are in the repository, I checked synaptic, the driver version (on synaptic 8.660) is older than the one on the ATI site (8.661, which I have been trying to install).  

**How did you guys get the fglrx driver working in Ubuntu 9.10?**

The Hardware Drivers app still does not let me activate the driver so that I can use it.

- Thanks,

---

### Post by halitech on 2009-11-14
Did you follow the instructions as per page 4?
> 
To install the ATI Proprietary Linux driver using the Automatic option, follow these
steps:
1   Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux
    driver download.
2   Enter the command sh ./ati-driver-installer-9-10-x86.x86_64.run to launch the ATI
    Proprietary Linux driver installer.
    The ATI Proprietary Linux Driver Setup dialog box is displayed.


---

### Post by coolcatco888 on 2009-11-14
Yes many times, it seems to install and ATI Catalyst Control Center shows up under applications.

I notice that this is displayed in the Terminal Window after install:

```
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details

```

When I try to open the Catalyst Control Center an error window pops up:

```
There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following:

No ATI driver is installed, or the ATI driver is not functioning properly.
Please reinstall the ATI driver appropriate for your ATI hardware, or configure using aticonfig.
```

I try to configure by entering the following command:

```
sudo aticonfig --initial -f
```

But after trying to open the Catalyst Control Center it still gives me the same error message window as above.

Then I check the log under:
/usr/share/ati/fglrx-install.log

```
Errors during DKMS module removal
Errors during DKMS module removal
[Error] Kernel Module : Failed to add fglrx-8.661 to DKMS
```

Believe me, I know how to install the driver, but it does not seem to be working for me.

---

### Post by halitech on 2009-11-14
you need to run the sudo aticonfig --initial as soon as the installer is finished and then reboot. At least thats the only way it worked for me.

try running this and then reinstall the drivers
```
apt-get install build-essential module-assistant fglrx-driver fglrx-kernel-src
```

---

### Post by asuastrophysics on 2009-11-14
> **coolcatco888 said:**
> I have tried installing that driver many times, ati catalyst 9.10 still does not work.  I even used that installer to build .deb installer packages. After building the .deb packages for Ubuntu/karmic I placed them all in one folder and ran:

```
sudo dpkg -i *.deb
```

it seemed to run fine but I got this in the output:

```
Setting up fglrx-kernel-source (2:8.661-0ubuntu1) ...
Loading new fglrx-8.661 DKMS files...
Building initial module for 2.6.28-11-generic, architecture -a i686

Error! Your kernel source for kernel 2.6.28-11-generic cannot be found at
/lib/modules/2.6.28-11-generic/build or /lib/modules/2.6.28-11-generic/source.
Done. 

Sounds like all you might need to do is install the linux-headers.
[CODE]sudo apt-get install linux-headers-(version number)-generic
```

To find the (version number), run this in terminal:
```
uname -r
```

That should fix the issue of the driver not being able to find the linux headers.

---

### Post by coolcatco888 on 2009-11-15
I have:

linux-headers-2.6.31-14-generic installed.

I cannot install the package it wants.

```
cley@cley-desktop:~$ uname -r
2.6.28-11-generic
cley@cley-desktop:~$ sudo apt-get install linux-headers-2.6.28-11-generic
[sudo] password for cley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.28-11-generic
cley@cley-desktop:~$ sudo apt-get install linux-headers-2.6.28-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.28-11-generic

```

---

### Post by coolcatco888 on 2009-11-15
Ok, I'm an idiot.

When I updated to 9.10, Grub was not updated to include a boot option for the new kernel.

I kept booting into the 9.04 kernel without knowing it.

"uname -r" kept giving me the previous kernel's name even though I had already upgraded my kernel.  It was only when I removed the 9.04 kernel from synaptic and restarted, did I realize this was the case (since I had to edit grub's menu.lst from Windows to boot into the new kernel).

I reinstalled the driver no problem and now it works.  I have compiz working again and everything was as fast as it was before.

- Thanks for all your help guys!

Sorry for the confusion :S

---

