---
title: "Ubuntu on USB Drive or VirtualBox?"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by bhakeman on 2009-03-02
Ok, here's the deal.  I have a PC with Vista Home Premium x64 (I'll wait until the laughter dies down).

OK, the problem is my scanner (Canon LIDE 20) doesn't have drivers for the 64 bit version of vista. (the last pc we used the scanner on was running windows 2000)

I'd like to know if I can run Ubuntu in VirtualBox and be able to use the scanner?  Virtual PC, from what I can see, doesn't support USB.

Or, would it be possible to run ubuntu from a USB drive so I don't have to install virtualbox and ubuntu on my pc?

I have some experience with Linux, having installed both DSL and Puppy Linux on a 12 year old laptop that ran windows 95, but detailed instructions would greatly be appreciated.

Thanks in advance.

---

### Post by TeoBigusGeekus on 2009-03-02
Why don't you dual boot?

---

### Post by carml on 2009-03-02
The solution IMHO is a dual boot,because any software for virtualization lies on the real machine support,so if Win?%&s Vista doesn't recognize your scanner not even Ubuntu over e.g. Virtualbox will do.
Me too I tried to use an "old" scanner under Vista,I couldn't use it,while WinXp or Ubuntu recognize the same scanner.:)

---

### Post by bhakeman on 2009-03-02
I'll have to think about it (Dual Boot).  I was hoping for a solution that wouldn't require digging into my HDD too much.

On a side note, if I were to create a LiveDVD for Ubuntu, would I need to partition the HDD just to try out Ubuntu?

Thanks

---

### Post by Ben Crisford on 2009-03-02
> **bhakeman said:**
> On a side note, if I were to create a LiveDVD for Ubuntu, would I need to partition the HDD just to try out Ubuntu?

Not at all, it would run entirely off the CD.

You do not set up partitions until installation.

TIP:  Before you partition an HDD you should *always* back up at least your main files.  It is normally okay, but its a bit risky if you have some important documents on there.

I dual boot vista and ubuntu 8.10 and I *love* it :D!  My installation was 100% fine and reasonably fast, and my HDD was un-damaged.  Did I mention that I love it? :D:D:D

---

### Post by bhakeman on 2009-03-02
Ok, new question then, can I dual boot with Ubuntu on an external HDD?  I have an external drive (USB).  

Just checking.

---

### Post by bhakeman on 2009-03-04
Well I tried a liveCD of Ubuntu 7 and was able to use xsane to scan images and save them onto the PC's Hard Drive.  I don't want to mess with the pc's hard drive too much, so I think I'll either stick with the LiveCD or create a bootable USB stick.  Does anyone have experience with UNetbootin?  Seems like the easiest way.

As far as my first attempt using Ubuntu, wow.  Very easy to use for the first time.  I liked that I could still access my pc's hard drive and go online without setting up anything.

---

### Post by anewguy on 2009-03-05
If you were able to use your scanner in a LiveCD version of Ubuntu, it should work with Ubuntu in a virtual machine.  Most likely it is USB connect, in which case you want to download/install the free but non-opensource version of virtualbox in order to get USB support.  You need to set up a filter in the virtual machine setup to get the device, but that is extremely easy.  While it is true that a virtual machine uses the base operating system, for USB it is almost a pass-through, but the trick is (I believe) that Windows must see the device.  Without a driver, I doubt Vista "knows" the device and therefore probably can't pass it through.  While I doubt it would work with the 64-bit version of Vista, you could try using the Windows 2000 driver for your scanner and see if Vista will recognize it.

If that fails, you definitely could use dual-boot.  I understand not wanting to mess with your existing Vista drive, so if you have a second drive it would be ideal.  You mention an external drive - what I don't know is if you can actually boot Ubuntu from an external drive or not.  You may want to try searching this forum for:

boot from external drive

and see if anything is returned to help you.

In addition, try a Yahoo! and/or Google search with:

ubuntu boot from external drive

and see what is returned there as well.

Someone following this thread may know already if you can boot from an external drive and might be able to guide you.  I think the biggest trick there is that the external disk would always have to be connected in order for you to boot, since GRUB will probably install on your Windows drive mbr, and GRUB will need access to the menu.lst, etc., things stored on the Ubuntu drive within /boot/grub.

Good luck!

dave :)

---

### Post by Wintersdark on 2009-03-05
not sure if this helps you or not, but... You absolutely can install ubuntu to and external USB HD.  In fact, just last night I did a full desktop installation to a 8gb USB pendrive. Kinda slow, but fully functional, and doesn't impact my HD at all.  

Another option is to install Ubuntu with Wubi. This let's you do a full installation within windows resulting in a dual boot setup WITHOUT partitioning - you can even use windows add/remove programs to delete the ubuntu installation after if you wish.

---

### Post by bhakeman on 2009-03-05
I'll have to look into that. (Wubi)  The main issue was trying to get my scanner to work (Canon Lide 20).  Canon doesn't have drivers for Vista-64bit.  I was impressed with the simplicity of xsane. Click, scan, done. 

I just downloaded the iso for ubuntu 8x so I'll play with that for a while from a live CD.

Thanks

---

### Post by dye01 on 2009-03-05
Fairly new to Ubuntu and love it, over Vista.. duh.
one qestion:

I installed Ubuntu intrepid on VirtualBox on Vista home. i.e. Vista=host machine, Ubuntu=guest machine. My question is, is there a way i can make an exact mirror of all my applications, themes, backgrounds, pictures, system settings, other settings, everything and save it to an iso disk image, then, use it to install Ubuntu with Wubi to make a dual boot? So basically i want to transfer Ubuntu from Virtual Box to a Wubi dual boot without losing one letter. Or perhaps zip my /root and /home folders and copy to the other (Wubi)Ubuntu and extract?

thanks for any help in advance, and again when answered.

---

### Post by bhakeman on 2009-03-07
Ok, question about Wubi, will I still have to reboot like you do to use a Live CD to get from Windows to Ubuntu?

Just wondering, thanks.

Edit:  After doing some searching here on the forum, I've learned that Wubi isn't a virtualization, but a 'safe' dual boot option.  I think I'll stick with Live CD's for now (having fun testing out releases - have Ubuntu 7, 8.04, 8.10 and Mint 6)  Mint looked interesting, quicker to load liveCD than ubuntu and it reminded me a little of Puppy, but with more features.

In any case, Linux saved us $ not having to buy a new scanner with Vista 64 drivers.

---

### Post by bhakeman on 2010-03-26
Since my last post on this subject, I had installed Ubuntu on Virtualbox with the Vista Host.  Since Virtualbox has usb support, I was able to run the scanner from the virtual Ubuntu computer.  I wasn't able to set up shared folders between the Vista side and the Ubuntu side.  I have since done a complete install of Ubuntu on a 'new to me' laptop and can run the scanner exclusively through the laptop without having to use the Vista hardware.  

Now my wife is happier since I now have a Linux 'mule' to test out Linux all I want and it doesn't mess with our main set-up.

---

