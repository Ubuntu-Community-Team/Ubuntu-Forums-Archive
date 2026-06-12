---
title: "New to ubuntu. Uninstalled OS and now have a problem &quot;Grub rescue&gt;&quot;"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by carovegas on 2010-09-06
Hi everbody!
I'm really really new to ubuntu, a total beginner.
A week ago I installed xubuntu on my Toshiba Satellite Laptop so that it was'nt so slow and to get to know ubuntu. Before I install it, I made paritions for windows, linux, linux-swap and data and installed form a live USB, cause my CD-room is not working. As doing that, I uninstalled my windows too, but I didn't matter cause I had ubuntu.

I worked with ubuntu for like a week and I really liked it, but my disk space flew away really fast because (I find out later) at the moment of installation it made another linux, and linux-swap partitions. I started gparted and try to resize the disks, but it woudn't let my, so I decided to eliminate the partitions (REALLY STUPID, I KNOW!!!!! ](*,  ). I thought that I would be able to boot with the live USB again, but I couldn't.

When I try to start the computer a message showing
error: no such partition.
grub rescue>

I have been looking on google about grub and how to restart it, but I have not been able. I could only start the computer with sysresccd, but I can't setup grub so that it boots the USB. I even got to mount the USB in wich I have the Xubuntu live, but, can I installet or boot it?, how?

- I already have set the BIOS to start from USB, and sysresccd run this way.
- Xubuntu live USB does not run, but before I format it did.
- I run super grub disk as well, but I coudn't set up de grub thing.

I'm really new in to this so I may be doing somting wrong, but I want to know if I can fix it or if I blew it forever.

I also have an idea, but I don't know if it will damage the disk. If I create another partition table, ¿does de MRB resets?, is it possible that by doing that i eliminate grub and it would read my xubuntu USB live againt?

Sorry if I say stupid things, but I am really new and really desperated.
I liked XUbuntu, so I would like to install it againt.

I don't know what else to do...

---

### Post by candtalan on 2010-09-06
> **carovegas said:**
> I thought that I would be able to boot with the live USB again, but I couldn't.
This is important. You should be able to use the live usb stick just as you did the first time. If you cannot then there are problems, possibly with the usb stick or your bios settings or your computer. consider to try the live usb in another computer?

>  When I try to start the computer a message showing
error: no such partition.
grub rescue> 

This sounds like you trying to start the computer from the hard drive, not from the usb stick. You have removed partitions I think you said, so even if the grub boot loader is still in  place, it will not find the operating system to be able to work.

It will be important to use a working method to boot up the pc. 
A live CD or a live usb should be ok. Make sure you check them after you create them to be sure they are good and are fully self checked. Maybe in another computer.

When you can boot your problem pc you can then see what the problem is. Take your time, do not rush. and ask questions here, as early as you can one question at a time if possible.

---

### Post by coffeecat on 2010-09-06
> **candtalan said:**
> Take your time, do not rush. and ask questions here, as early as you can one question at a time if possible.

+1

Even though you set the BIOS to boot from USB when you first installed, the BIOS may have reset itself when you booted from a HD and there was no USB drive to detect. My netbook does this.

Recheck the BIOS. Re-enable booting from USB and make sure the boot order shows the USB drive as no 1. You may have to have the USB drive plugged in before the BIOS lets you do this. Then you should be able to boot from the USB drive. Grub is easily repaired once you can boot with a USB stick or a live CD.

---

### Post by carovegas on 2010-09-06
Hi there.

Yes, there was a problem with the USB. I used another one and it works.
Thank you very much for your atention.

I'll take your advices and will not rush.

Regards.:D

And one more, how do I mark "solved" this thread?

---

### Post by coffeecat on 2010-09-06
At the top of the thread > Thread Tools. Drop down the menu and click on 'mark this thread as solved'.

Good luck!

---

### Post by carovegas on 2010-09-06
Thank you!

---

