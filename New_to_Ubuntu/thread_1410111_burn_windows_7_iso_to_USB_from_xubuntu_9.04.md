---
title: "burn windows 7 iso to USB from xubuntu 9.04"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Redmage913 on 2010-02-18
Hey there,

I messed up the MBR in my netbook, which only has USB input (no optical drive).  To fix this, I need to take my iso image of Win7 Pro and burn it to a USB drive so I can boot the Recovery Console.

Any ideas how I should do this?  I have to do all of this from Ubuntu, so any responses that require Windows programs can't be used...sorry.

Thanks,

--Red

---

### Post by emeraldgirl08 on 2010-02-18
Try using Brasero. Use 1:1 copy and direct the ISO to be placed in your USB drive. That's a method I used for a program I needed for a science course. It runs fine.

---

### Post by Redmage913 on 2010-02-18
Brasero doesn't seem to be letting me choose a USB drive. It just says that it doesn't have a disc to burn to.

---

### Post by emeraldgirl08 on 2010-02-18
I'm not sure what you mean. I'm not on Linux right now (ugh school related stuff) and am wondering if you can see your USB drive? Is your USB Icon on the desktop? What about directing the ISO to be placed on your desktop and then dragging that into your USB?

---

### Post by Redmage913 on 2010-02-18
I'm not trying to copy the iso file over. I'm trying to make a bootable USB drive using the Win7 ISO.  I can't use unetbootin since it's linux-based. Think of it like burning the CD - it's not that I'm simply burning the iso file, I'm trying to burn the *contents* of the iso file, including its bootable characteristics, into the USB drive.

Windows has a DVD USB tool, but of course it's for Windows.

---

### Post by emeraldgirl08 on 2010-02-18
Oh okay. I'm sorry. I'm not sure how that would work out! I'm pretty new at this. You have a good question though so I'm subscribing to this thread in case I need to do that one day... or get bored :)

---

### Post by Julita on 2010-02-18
Hi! Are you able to install usb-creator?

---

### Post by Redmage913 on 2010-02-18
USB creator is Ubuntu's ISO burner for Ubuntu's ISO images, isn't it? Does it work with non-Ubuntu iso files?

---

### Post by Julita on 2010-02-18
Actually, it is supposed to work with any .iso Try it!

---

### Post by nikhilbhardwaj on 2010-02-18
no brasero wont work

here's what you need to do

find out what your usb drive is called

```

sudo fdisk -l 

```
will help.

lets say that it is /dev/sdc

now we need to write the windows 7 image to the usb
by dd
```

sudo dd if=/PathToWindowsISO.iso of=/dev/sdc

```

wait for sometime
and you should be good to go
you can now boot from the usb


it must be noted that dd is a dangerous command
if you use it to the wrong drive /dev/sda ie your hard disk
you'll loose all your data
so it is imperative that you use the correct device name.

replace /PathToWindowsISO.iso
with the actual path to your windows iso

ask here if you dont know what that is

best of luck

---

### Post by Mark Phelps on 2010-02-18
I've attached a link showing the steps needed to create what you want -- so you can understand it's NOT a simple matter of copying an ISO file to a USB stick.

Perhaps others, who have machines that can boot from USB (I don't) can then provide feedback on how you can accomplish these steps from Xubuntu:

[http://geekswithblogs.net/cicorias/archive/2009/05/04/making-a-win7-bootable-usb-device.aspx]("http://geekswithblogs.net/cicorias/archive/2009/05/04/making-a-win7-bootable-usb-device.aspx")

---

### Post by wilee-nilee on 2010-02-18
OP go to a library or anywhere you can use a windows computer and use the MS USB W7 loader this is a quick process about 5 min and you will be set. Trying to load this with Linux is not a good idea, you want to have a confirmed backup install bootable thumb or DVD to get things done.
Windows 7 USB/DVD Download Tool

Installing this does need administrative access so a library will not work probably but anybody with admin rights can install the usb loader and your set.

---

