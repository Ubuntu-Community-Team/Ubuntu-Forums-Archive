---
title: "How can I save LiveDVD configuration?"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Drake1132 on 2009-06-06
OK, so I'm trying to check out Ubuntu, and I'm booting from the Live disc rather than installing because I don't know for sure yet if I want to keep Ubuntu or go with something else.  I'm mostly happy with it so far, but I want to test out my hardware and such and I'm having issues with my nVidia graphics card...

I want to test out 3d acceleration stuff and see how well OpenGL programs work with my hardware.  So I told the running system (running from the Live disc) to download and install the recommended nVidia graphics drivers from System->Administration->Hardware Drivers and it's telling me that I have to reboot the system.  In the past though, when I've rebooted the system I've lost custom configuration stuff such as desktop theme colors and background images and such, so I suspect that rebooting will do nothing for me because it will undo the download/install that the reboot is supposed to complete anyway.

So this brings us back to my initial question (see subject)...  How can I save such configurations in order to test this stuff out?  Is it even possible to do this from a LiveDVD system rather than an installed system?

Thanks,
Drake

---

### Post by Tibuda on 2009-06-06
You can't. You can also install Ubuntu in a Live USB, which will be able to save settings.

---

### Post by lindsay7 on 2009-06-06
If you have windows you can inastall with wubi. Go to that web site. It will put Ubuntu on your computer under windows and you can try everything and save the configuration. If you are happy you can uninstall from the control panel and then reinstall Ubuntu with a full dual boot installation.

---

### Post by Drake1132 on 2009-06-06
> **danielrmt said:**
> You can't. You can also install Ubuntu in a Live USB, which will be able to save settings.

Where do I download a LiveUSB version to try that out?  The only one I saw on the main download page was the netbook remix version.  Are there others or other ways to put together a LiveUSB?

Thanks,
Drake

---

### Post by Drake1132 on 2009-06-06
> **lindsay7 said:**
> If you have windows you can inastall with wubi. Go to that web site. It will put Ubuntu on your computer under windows and you can try everything and save the configuration. If you are happy you can uninstall from the control panel and then reinstall Ubuntu with a full dual boot installation.

That would have been great a week ago when my windows system would still boot up, but not any more.  Right now I'm trying to decide if I want to install Ubuntu, or some other version of Linux, or do a system restore thing and put Vista back on in working condition...  I hate vista, so I'm more interested in finding a version of Linux that will work for me, and Ubuntu looks very promising.  At this point, all I'm really concerned about is whether or not 3d acceleration will work properly with my hardware under Ubuntu... if it does, then I'll install Ubuntu.

Thanks for the suggestion though,
Drake

---

### Post by lindsay7 on 2009-06-06
Here is where you can download it,

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Do you want to get Vista back and bootable? If so use the vista install disk and go to the repair option and type Bootrec.exe in the  command line. Then choose an option like bootrec /FixBoot

Here is the info.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Drake1132 on 2009-06-06
> **lindsay7 said:**
> Here is where you can download it,

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Do you want to get Vista back and bootable? If so use the vista install disk and go to the repair option and type Bootrec.exe in the  command line. Then choose an option like bootrec /FixBoot

Here is the info.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)



Well, I really hate vista, so I want to get rid of it and use either Linux or XP or both anyway, but I wouldn't mind getting Vista to work again long enough to back up my files that haven't been backed up yet.  the problem there is that I'm not sure I can actually do that... I don't have full installation discs for Vista, all I have are the recovery discs I got from HP (I hate that they do that).  Assuming the recovery discs can still run the Bootrec.exe the same way, I'll try that, but I'd be surprised if they have that capability.  I did manage to move some of my files to my external drive, but for some reason my LiveDVD of Ubuntu isn't finding any files in my Documents and Settings forlder on my Windows partition, so I still haven't been able to back those up (assuming they haven't been destroyed or something).

In the meantime I downloaded the netbook version and will try to run a LiveUSB to test out the 3d acceleration stuff.

Thanks,
Drake

---

### Post by tea for one on 2009-06-06
> **Drake1132 said:**
> 

So this brings us back to my initial question (see subject)...  How can I save such configurations in order to test this stuff out?  Is it even possible to do this from a LiveDVD system rather than an installed system?

Thanks,
Drake

Good evening

Pop the live CD into your drive and boot up the CD
When you have arrived at the desktop, navigate to:-
System > Administration > USB Startup Disk Creator

This utility will guide you through the process of installing a "live" image onto a USB stick.

During this process, you will be able to create a "persistent" storage area. This will allow you to save data and applications.

When the USB image is created, you can set your BIOS to boot from a USB device (hopefully) and then you can save data and new applications to your USB device.

Good luck

---

### Post by Tibuda on 2009-06-06
Just remember that not every computer allows to boot from USB.

---

### Post by lindsay7 on 2009-06-06
You can get a vista recovery disk here and fix you mbr problem.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by tea for one on 2009-06-06
> **danielrmt said:**
> Just remember that not every computer allows to boot from USB.

Yes, indeed, this is one of the irritations that are often perplexing.

The following website has a plethora of information about operating systems installed on USB sticks:-

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Kind regards

---

