---
title: "New user, having problems booting."
date: 2010-04-13
forum: New to Ubuntu
---

### Post by Streyker on 2010-04-13
Hello, I am a new user of Ubuntu, and I recently switched after frustrations with windows 7. I am a pretty inexperienced linux user in general.

My problem is this. After formatting my hard drive and installing ubuntu (via 9.10 cd rom) I am unable to boot to ubuntu directly from the hard drive. It gets to a file verification screen (black screen with white ubuntu logo in the middle) and gets to 1% and then stops, no further progress. So I have to do a hard reset, and boot from cd rom. I am currently using my computer directly from the cd rom and ubuntu is working fine however it tells me that my hard disk has "many bad sectors".

Is there anything I can do to work around this for now? Or is this simply caused by a poor hard drive and I should just replace immediately? Kind of annoying since I just bought this laptop 3 months ago and it has been sitting at a desk the whole time (not bouncing around in a backpack or anything that would harm the hard drive).

Alternatively, would it be possible until a new drive arrives to install ubuntu to my 1tb external drive and how well would this operate through USB?

Sorry, alot of questions. I really appreciate the help though. Thanks!

---

### Post by egalvan on 2010-04-13
First, check the CD to be sure it's OK...

Boot with the CD, and on the boot menu, look for the option to "check media" (or words to that effect)

This will run a checksum on all the files, and if it runs OK,
you at least know you have a good LiveCD.

Next, run the "memory test" option...
try to let it run through at least 7 passes.

Again, this will raise the confidence level on the hardware.


Third, realize that 10.4  Lucid Lynx will ship in 17 days...
This is a Long Term Support release, which is usually much more stable...
Take the time to experiment with 9.10, but I would recommend a complete re-install of Lucid a few days after it's release...
In the long run, you will be happier.

---

### Post by Sin@Sin-Sacrifice on 2010-04-13
While booted into the live cd open a terminal and type ```
sudo fsck
``` then reboot and see if the OS loads. fsck should fix those bad sectors.

---

### Post by readycarpenter on 2010-04-13
boot the live cd, there is an option to check cd for errors, after you discover the disc is fine, boot live cd.

then goto system>administration>disk utility
this will then tell you you have bad sectors, 

I believe this is you problem, your hd is on its way out, since you are booting the live cd fine.

hds are cheap under $100 get you plenty large enough drive 

cheers

---

### Post by Streyker on 2010-04-13
Thank you all for these helpful responses! I am going to try some of this advice and see what results I can get. I thought my hard drive might be going out also, but I am going to make the manufacturer replace it rather than buy new, on principal alone. No 3 month old hard drive should be going out, especially not one that has been sitting safely on a desk the whole time.

---

### Post by Streyker on 2010-04-13
Just thought I would mention, I tried "sudo fsck" in terminal and it produced "fsck from util-linux-ng 2.16" and nothing else happens.

---

### Post by Sin@Sin-Sacrifice on 2010-04-20
I'm sorry. ```
sudo fsck /dev/drive
``` where drive is the hdd you want to check.

---

### Post by themusicalduck on 2010-04-20
To find out what you need to put in /dev/drive you need to run ```
sudo fdisk -l
``` in a terminal first and see which is your drive (probably /dev/sda). But to be honest there's a much better way. If you open Disk Utility on the live CD under System > Administration and highlight your disk, you can click Check Filesystem at the bottom which will do the same thing. Hopefully it might fix some of the bad sectors on the drive and let you boot back in to the install. Certainly a drive shouldn't completely fail after 3 months!

As to running Ubuntu off a usb drive. It is possible, but bear in mind that usb is not that fast compared to an internal drive, so it will run somewhat slower.

---

