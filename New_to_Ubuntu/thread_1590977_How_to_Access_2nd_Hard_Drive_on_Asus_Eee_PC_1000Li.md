---
title: "How to Access 2nd Hard Drive on Asus Eee PC 1000/Linux"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by lhb1142 on 2010-10-08
I own a 2008-model [Asus Eee PC 1000/Linux netbook]("http://www.amazon.com/10-Inch-Netbook-Processor-Storage-Battery/dp/B001BYD16E/ref=cm_cr-mr-title"). It originally came with an Asus-modified-Xandros OS but, as that system is no longer supported, I 'wiped' the netbook and installed Ubuntu 'Lucid Lynx' v.10.04.

This computer has TWO installed SSDs; the 'main' one is 8 GiB (non-removeable) and the other one is 32 GiB.

(See Attachment 1 below)

When I installed the new OS I specified that the main site for installing the system was to be the first hard drive (which, inexplicably, was named /dev/sda2). I created a 'swap' file, specifying 386 MB (shows as 367 MB); that is labeled /dev/sda5. (Is that sufficient?)

(See Attachment 2)

The second, larger, hard drive is labeled /dev/sdb1. When asked for a mounting point, I chose /boot.

(See Attachment 3)

As you can see, both of the hard drives are formatted as ext4. And they are both present and accounted for!

The problem I am having is that I can find NO WAY to actually access that second hard drive (/dev/sdb1)! Obviously I cannot copy any folders or files to it and I am thus limited to what that first 8 GiB hard drive will hold (and you can see that I'm almost out of room!).

Can anyone help me access that second installed hard drive? (Can you tell if I did something wrong during the installation? If it is necessary for me to reinstall Ubuntu, that is not a problem.) Thanks very much for any help.

---

### Post by lbrty on 2010-10-08
How have you tried to access the SSD drive? What is the feedback once you click on it when you go to Places and click the drive (if it is mounted)?

What is status of the drive under System>Administration>Disk Utility? Is it mounted? Do you have data on the drive? Have you formatted the drive? What is the partition type?

Please post output for the following:
```
sudo fdisk -l
```

---

### Post by lhb1142 on 2010-10-11
> **lbrty said:**
> How have you tried to access the SSD drive? What is the feedback once you click on it when you go to Places and click the drive (if it is mounted)?

What is status of the drive under System>Administration>Disk Utility? Is it mounted? Do you have data on the drive? Have you formatted the drive? What is the partition type?

Please post output for the following:
```
sudo fdisk -l
```

Dear 'lbrty,'

First let me apologize for this delayed response; we were away this weekend.

This morning, after reading your questions, I went into the Disk Utility to check the status of the drives. BOTH were mounted but the second volume (the 32 GiB SSD) had no name. Perhaps that's why I could not access it.

I fiddled around with it, within the Terminal (by unmounting it) and in the Disk Utility by naming it; I named it '32-Gib-SSD' and then I was 
able to access it. I had very little information on this computer but I transferred all my Documents, Music, Pictures, and Videos files to the 32 GiB drive and I was able to open them up normally.

Unfortunately, during the process of 'fiddling,' I must have done something to corrupt GRUB for, when I attempted to reboot, I could not do so, receiving only a Grub Rescue prompt with which I could do nothing.

I tried a bit of correcting the Grub from instructions on the web but to no avail.

So the easiest and quickest thing for me to do was to reinstall Ubuntu. I specified the installation to go to the whole disk (which meant the 8.1 GiB drive only) and, when I was finished, there was a correct installation of Ubuntu on that 8.1 GiB drive and the data which I had put onto the 32 GiB drive was still there and easily accessed.

Now all I have to do is to reconfigure Ubuntu the way I like it.

I want to thank you for mentioning the Disk Utility function. I hadn't even thought of that and your message 'turned a few wheels' for me.

I now have a fully functioning Asus Eee PC 1000/Linux model and I can easily access BOTH of its two SSDs.

Thank you again!

Regards,

Lawrence H. Bulk

---

