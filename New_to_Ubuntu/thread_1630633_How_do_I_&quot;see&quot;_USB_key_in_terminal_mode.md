---
title: "How do I &quot;see&quot; USB key in terminal mode?"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by bthomson100 on 2010-11-25
I need to back up files from the windows D: partition (/media/sda3) of my hard drive onto a USB key without going out of Ubuntu 10.4 terminal/console mode. However, when I plug a USB key into the computer, I can't "see" it. It should probably be /media/sdbx, and there is a /media/sdb1 showing but ls -a shows an empty drive, which the USB is not.

I also have a backup drive called "FreeAgent Drive" which appears with ls but which I can't access, possibly because the name has a space between FreeAgent and Drive.

I'm pretty new to this so would appreciate clear tips that don't assume I know much about Linux.
 
Thanks

Bob Thomson
Ottawa Canada

---

### Post by ptn107 on 2010-11-25
Show us your mtab with the usb drive plugged in:

```
cat /etc/mtab
```

---

### Post by Hippytaff on 2010-11-25
also it might need to be mounted...what does 
```

mount

```
return with the key plugged in?

nothing wrong with seeing
```

lsusb

```
also :-)

---

### Post by bthomson100 on 2010-11-25
I can't put the output from the "mount" or "cat /etc/mtab" files here that easily because I would have to send them to the Windows D: partition, leave Ubuntu and start Windows Vista in order to "see" the result and copy/paste it into a message. It takes 10 minutes to load Windows and 10 minutes to shut it down, making it absolutely horrible to use for this sort of thing. Which is why I want to be able to "see" and access a USB key. I'm writing this from a separate netbook running Ubuntu 10.10 which is causing it's own problems!

---

### Post by matt_symes on 2010-11-25
Hi

I>  also have a backup drive called "FreeAgent Drive" which appears with  ls but which I can't access, possibly because the name has a space  between FreeAgent and Drive.

Try

ls -al FreeAgent\ Drive

to view the drive.

Does the USB stick have a label?

Also, we could really do with the output from the commands already suggested.

Kind regards

---

### Post by Hippytaff on 2010-11-25
Can't you get online with the ubuntu that's having trouble seeing the usb?

---

### Post by bthomson100 on 2010-11-25
Ok. A friend of a friend came over and helped me mount the USB key and I've been able to backup the contents of /home/bobt from my Acer Aspire 3104 laptop running Ubuntu 10.4.

So this particular problem is solved.

I wish I could make a nice synthesis here but I still don't understand exactly how one mounts a USB device to a virtual place called /mnt/sdb1 so I can't do that.

My main problem was that the Ubuntu root drive appears to be full and Ubuntu couldn't boot. This thread was a separate sub-issue that I needed to solve and wasn't getting any response on the other thread which is "Help: Computer locked up - seems Power Management"

I've solved that one now too.

Thanks to all for your efforts and help. I'm further along the learning curve now.

Bob

---

### Post by Locke_99GS on 2010-11-26
If the USB drive was mounted by gnome, then it would be found in ~/.gvfs/
It only mounts to /media if you explicitly mount it.

---

### Post by Hippytaff on 2010-11-26
> **Locke_99GS said:**
> If the USB drive was mounted by gnome, then it would be found in ~/.gvfs/
It only mounts to /media if you explicitly mount it.
 
My usb mounts to /media automatically :-)

---

### Post by djmac on 2010-11-26
> **Hippytaff said:**
> My usb mounts to /media automatically :-)

As does mine ..

This is useful for determining which disk are present (including usb) over terminal:
```
sudo fdisk -l

```

As is:
```
lsusb
```

 . . .but I think someone already mentioned that.

---

