---
title: "Merge two ext3 partitions"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Johan-Steyn on 2009-06-04
Hi All,

I have finally got Virtualbox 2.2.4. (non-ose) running properly with usb support in Jaunty and now operate the few remaining Windoze client programs (which could not run under Linux) in the emulator.

This is GREAT as I no longer have to reboot to Windoze three or four time per day!

So, I took the final leap and used gparted to delete the Windoze XP partition /dev/sda1/ altogether and formatted it to ext 3.

I also ran:

nano /boot/grub/menu.lst
and deleted the Windows XP entry from grub.

Now I have a extra 5 Gig ext3 media partition.

My question basically is this: How do I merge the two partitions (sda1 & sda5) into one contiguous partition?

I have already tried booting up with livecd and running gparted from there (as was suggested in some posts) but the partition could not be resized using the "slider" function of the gparted graphical interface.

Any suggestions? 

Thanks,

JS

---

### Post by ubername on 2009-06-04
> **Johan-Steyn said:**
> Hi All,

I have finally got Virtualbox 2.2.4. (non-ose) running properly with usb support in Jaunty and now operate the few remaining Windoze client programs (which could not run under Linux) in the emulator.

This is GREAT as I no longer have to reboot to Windoze three or four time per day!

So, I took the final leap and used gparted to delete the Windoze XP partition /dev/sda1/ altogether and formatted it to ext 3.

I also ran:

nano /boot/grub/menu.lst
and deleted the Windows XP entry from grub.

Now I have a extra 5 Gig ext3 media partition.

My question basically is this: How do I merge the two partitions (sda1 & sda5) into one contiguous partition?

I have already tried booting up with livecd and running gparted from there (as was suggested in some posts) but the partition could not be resized using the "slider" function of the gparted graphical interface.

Any suggestions? 

Thanks,

JS

Rather than create a new partition, wny don't you extend the existing one? (use gparted to delete your new, empty partition and then re-size the existing one.)

---

### Post by dca on 2009-06-04
Don't think it can be done.  sda1 is a primary partition & sda5 is a logical partition...  
 
look here:
 
[http://ubuntuforums.org/showthread.php?t=313651](http://ubuntuforums.org/showthread.php?t=313651)
 
...now you may be able to set up an LVM.
 
[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
 

...as mentioned in one of those posts, LVM takes a lot of research.

---

### Post by Johan-Steyn on 2009-06-04
Hi Guys,

Thanks for the quick reply.

Ubername:

I tired resizing using gparted, after booting from live-cd. Although I could delete the sda1 partition it still did not want to resize. I subsequently recreated and reformatted it to ext3.

dac:

Thanks, LVM looks promising! I have never heard of it before toady. I'll download it and give it a go.

I will post back with the outcome.

Thanks Again,

JS

---

### Post by michy99 on 2009-06-04
A screenshot of Gparted would help us to see what your situation is. To expand a logical partition, you have to expand the extended partition which contains it first.

---

### Post by Johan-Steyn on 2009-06-04
Hi michy99,

Herewith the screenshot.

[IMG]http:///home/johansteyn/Documents/Screenshot.jpg[/IMG]


Regards,

JS

---

### Post by Johan-Steyn on 2009-06-04
Sorry the .jpg screenshot did not come out.

/home/johansteyn/Documents/Screenshot.jpg

How do you insert a jpeg picture?

Regards, 

JS

---

### Post by ibuclaw on 2009-06-04
> **Johan-Steyn said:**
> Hi michy99,

Herewith the screenshot.

[IMG]http:///home/johansteyn/Documents/Screenshot.jpg[/IMG]


Regards,

JS

Add your image as an attachment. 

When you post a new message, look for "Manage Attachments" below the text input box.

Regards
Iain

---

### Post by Johan-Steyn on 2009-06-04
Hi All,

Herewith the screenshot as requested.

Regards,

JS

---

### Post by Johan-Steyn on 2009-06-04
Hi tinivole,

Thanks for the tip Iain!

Kind regards,

JS

---

### Post by ibuclaw on 2009-06-04
> **Johan-Steyn said:**
> Hi tinivole,

Thanks for the tip Iain!

Kind regards,

JS

Had to squint to see it :P

OK, do you have your Ubuntu LiveCD on you? You are going to have to boot into it to do what you want to do. (Insert it into your disc tray and reboot).

When the LiveCD environment loads, go to **System->Administration->Partition Editor** to start Gparted, and you can run the following operations from there:
[LIST]
[*]Delete sda1 (which used to house your Windows installation).
[*]Click on the [COLOR="Cyan"]Cyan Rectangle[/COLOR], this should select the extended partition. Click "Resize", and a new window will open, where you can click and drag the left arrow to grow it.
[*]Click on your Ubuntu Partition. Click "Resize", and do the exact same thing again.
[*]Ensure that everything looks fine, then click "Apply", and wait for about an 30 minutes to an hour while the partition manager reorganises your filesystems.
[/LIST]

If you are unsure about any step in the procedure, you are more than welcome to ask.

Regards
Iain

---

### Post by Johan-Steyn on 2009-06-05
Hi Tinivole,

Solved! Thanks for the help.

Regards,


JS

---

