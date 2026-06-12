---
title: "Nothing recognizing my harddrive"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by DieHards77 on 2009-04-01
I run ubuntu 8.1 and everything was working perfect.  I have an iomegga 1tb external hard drive that was mounted and working perfectly on my dell latitude d830.  I unplugged my laptop to take to a class and when I come back and try to hook everything back up on my desk my harddrive stopped working completly.  Im talking doesn't get recognised what so ever.  I plug it in and absolutly nothing happens.

I tried plugging it into my room-mates windows powered laptop, tried switching cables and multiple usb ports any still it doesn't even give a hint that it realizes it is plugged in.

Ive had the hard drive for about 9 months, never had any problems and keep it only sitting on my desk never dropped or shacked it what so ever that might cause it to break.

Any ideas of a fix? Or does it sound like its completely fried? Thanks a lot for the help

---

### Post by kanikilu on 2009-04-01
I guess the first question to ask would be, are you sure it's getting power? Do you hear it spin up or see any lights?

If so, plug it in, and then in Ubuntu, go to Applications > Accessories > Terminal and type ```
dmesg | tail
``` and also ```
sudo fdisk -l
``` Copy and paste the output of those commands here.

---

### Post by DieHards77 on 2009-04-01
Yea its getting power the power light is on and I hear it spinning so everything seems to be a go.

for the first command i get 

> jayloewy@jayloewy-laptop:~$ dmesg | tail
[ 6043.665148] CE: hpet increasing min_delta_ns to 33750 nsec
[ 6071.960968] CE: hpet increasing min_delta_ns to 50624 nsec
[ 6258.026271] CPU0: Temperature/speed normal
[ 6258.026276] CPU1: Temperature/speed normal
[ 6526.805030] Machine check events logged
[ 6559.252329] CPU1: Temperature/speed normal
[ 6559.252346] CPU0: Temperature/speed normal
[ 6865.092261] CPU0: Temperature/speed normal
[ 6865.092270] CPU1: Temperature/speed normal
[ 6901.805055] Machine check events logged


second command i get
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris


thanks again for the help

---

### Post by kanikilu on 2009-04-01
Hmm, neither of those are showing anything related to the 1TB drive. Maybe try plugging it into another USB port and then try those commands again.

---

### Post by DieHards77 on 2009-04-01
Sure i did that but it seems the same 

> jayloewy@jayloewy-laptop:~$ dmesg | tail
[ 7616.417139] CE: hpet increasing min_delta_ns to 75936 nsec
[ 7643.609622] CPU1: Temperature/speed normal
[ 7643.609624] CPU0: Temperature/speed normal
[ 7663.726946] usb 6-1.2: reset full speed USB device using uhci_hcd and address 3
[ 7876.805084] Machine check events logged
[ 7961.736561] CPU1: Temperature/speed normal
[ 7961.736582] CPU0: Temperature/speed normal
[ 8128.354979] usb 6-1.2: reset full speed USB device using uhci_hcd and address 3
[ 8266.226465] CPU1: Temperature/speed normal
[ 8266.226484] CPU0: Temperature/speed normal
jayloewy@jayloewy-laptop:~$ sudo fdisk -l
[sudo] password for jayloewy: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
jayloewy@jayloewy-laptop:~$ 


as i said i tried plugging it into my friends windows power laptop and got absolutely no usb response also which is making me think the thing is fried?

---

### Post by kanikilu on 2009-04-01
No it's definitely different:```
[ 8128.354979] usb 6-1.2: reset full speed USB device using uhci_hcd and address 3
``` Although, I'm not sure what that means, when I plug a USB HDD into my computer, I get "new high speed USB device...", not "reset full speed..."

Perhaps someone else can shed some light?

Are you plugging the drive into a USB hub or directly to the computer? If so, try it without going through the hub.

Are you by any chance using a USB extension cable? If so, try it without it. If not, do you have another USB cable you can try?

Do you hear any clicking or unusual sounds coming from the drive? If so, that could be a sign of disk failure.

Sorry, I'm not really sure what else to try...if it's not being seen in 2 operating systems and computers, and you can rule out the hardware (cables, usb ports), it might not be accessible.

---

### Post by DieHards77 on 2009-04-01
im not exactly sure how i would go about plugging it directly into the computer because as of now it is being plugged into a usb hub.  As for the other options its not using a usb extention or anything else.  This is so wierd because it was working fine before i unplugged it and then when i went to plug it all back in this happened.  Theres no clicing or wier dnoises at all just sounds completely regular/

If anyone could shed some more light on this it would be greatly appreciated

---

### Post by newbee70 on 2009-04-01
have you tried to run gparted with the check option on it?

---

### Post by primaxx on 2009-04-01
-Or have you tried other usb-devices you might have? 
Perhaps it's not your disk, but your usb-ports that are fried... (This happend to me)

---

### Post by kanikilu on 2009-04-01
> **DieHards77 said:**
> im not exactly sure how i would go about plugging it directly into the computer because as of now it is being plugged into a usb hub. Try it without going through the hub. Use one of the ports on your computer. Basically, you want to rule out as many variables as possible.

---

### Post by DieHards77 on 2009-04-01
> **newbee70 said:**
> have you tried to run gparted with the check option on it?

what do you mean by that? Im sorry ive just never heard of that before

As for the other replies ive tried other usb devices they work fine and ive plugged it directly into the computer and still nothing.  Thanks for all the help guys i really appreciate it anything else anyone else might have to say would be great

---

