---
title: "dev sys and proc not found on reboot"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by JohnGalt on 2010-09-30
I have Ubuntu 10.04.1 on my dad's laptop as he had a tendency to get viruses in Windows. It was a recent fresh install, couple of weeks old. Well I showed up and tried to do a system update for it. The update box popped up but stayed blank. Everything else on the system did the same thing so I do a restart. Upon boot up I get a message

mount: mounting /dev on /root/dev failed: No such file or directory

Then said the same for /sys and /proc. It ends with BusyBox v1.13.3 with (initramfs) and blinking prompt. I'm not sure what happened or what to do other than full reformat and start over.

In either case any advice on what possibly happened and what to do to keep it from happening again?

Thanks

---

### Post by andrewthomas on 2010-09-30
Purge and reinstall grub2.  Follow the instructions here:

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by JohnGalt on 2010-09-30
I'll give it a shot when I go get my usb live disk.

So are those grub files that are missing and not the OS files? I had assumed OS since they were in root and not a boot section but I don't know that much about it all. Just trying to learn, Thank you

---

### Post by andrewthomas on 2010-09-30
There seems to be a lot of corrupted grub's lately.

---

### Post by JohnGalt on 2010-09-30
What would cause the system to mess up while running? Couldn't bookmark in firefox. No system settings windows would start up properly.

I'm going to try grub in the morning when I go back to the shop.

Thank you

---

### Post by andrewthomas on 2010-09-30
> **JohnGalt said:**
> What would cause the system to mess up while running?  
Thank you
 I don't know.  Maybe there is a problem with the hard drive.

---

### Post by jtarin on 2010-09-30
Is it possible that some updates were donewithout your knowledge? From the GRUB boot screen _how many kernels are listed_ and what are the numbers if diferent. Have you already tried recovery moce?

---

### Post by JohnGalt on 2010-10-01
I didn't see any kernals listed. I just booted up from a live usb to back up all the files before trying anything.

He could of started updates and managed to shut it down in the middle of them. He keeps claiming he didn't do anything so I don't know. This is the third time he has ruined a ubuntu install. I'm not sure what to do as Windows didn't work for him either.

I'm afraid it could be a hard drive problem. The laptop already quit charging the battery some time ago and it's only a year an half old I think, bought it refurb and was just out of warranty when it quit.

Using USB to live boot.

/init: line 7: can't open /dev/sr0: No medium found

Then it reads the usb drive as sdb

Then it says:
unable to open '/dev/sda'

It just hangs here not continuing on. The gui load page just shows the circles going across the screen. I let it sit for a while and nothing.

---

### Post by jtarin on 2010-10-01
Whatever you decide to do to get up and running....next time make two accounts.No one else has access to.
> Using USB to live boot.

/init: line 7: can't open /dev/sr0: No medium found

Then it reads the usb drive as sdb

Then it says:
unable to open '/dev/sda'
sr0 is your CD drive it is probably configured first boot. /dev/sdb is common designation for a USB external or second drive./dev/sda is the drive you need to boot. Can you run the Live version and get to the desktop? If you can then you can CHROOT into your Ubuntu install and move things elsewhere then re-install or run a grub update to /dev/sda.

---

### Post by JohnGalt on 2010-10-03
I haven't tried booting from a linux cd as I no longer have access to an iso and burner on the same pc. I have tried booting from live cd usb. It gets into the errors above with unable to open sda. I could never get it to boot into live either.

I went to Fry's and picked up another drive and popped it in. Booted up with the usb linux drive just fine and I told it to install Ubuntu to hard drive and let it go. It got to 85% and was still at 85% an hour later so I canceled it. I checked it in gparted and couldn't see the hard drive so I restarted the computer. It would not boot up and gave me a media error message.

I popped out the hard drive and put it in a sata to usb adaptor onto another pc and formatted it to ntfs. It works as an external drive just fine. I put it back into the laptop and media error and won't boot live usb.

I'm not sure what's going on but since the battery hasn't charged in months, I believe the motherboard is dying out. Does that sound about right? It's an HP 550

---

### Post by jtarin on 2010-10-03
> media error and won't boot live usbThat usually pops up when your media is not readable by the ....whether on USB,CD or DVD.

What is likely happening at the 85% the installation will attempt to connect to the internet to download updates.....it does seem like it's stuck and depending on your version Of Ubuntu and your connection speed it could take some time. Try again and when it gets to that point as soon as you can click on the "cancel/skip" button if you do not have a connection....or let it run if you do.

---

