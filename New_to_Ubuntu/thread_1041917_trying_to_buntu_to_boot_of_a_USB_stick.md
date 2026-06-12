---
title: "trying to buntu to boot of a USB stick"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by UKDave on 2009-01-17
hi
i want to have Ubuntu on a memory stick so i can run it via a USB 2.0 boot. having followed the instuctions for creating a USB Boot disk, all i get when trying to boot of said usb Stick is 'operating system not present.. what did i do wrong?


Dave

---

### Post by cdtech on 2009-01-17
Did you use "System > Administration > Create a USB startup disk"

---

### Post by UKDave on 2009-01-17
yes i did

Dave

---

### Post by cdtech on 2009-01-17
You have to set the BIOS to use the USB device as the first bootable drive.

**UPDATED::.**
Never mind I seen the "no operating system".

---

### Post by theozzlives on 2009-01-17
Boot off the Live CD, go to terminal and type:
```
wget pendrivelinux.com/downloads/u810/u810.sh
```
```
chmod +x u810.sh && sh u810.sh
```
assuming you have the 8.10 live CD.

---

### Post by UKDave on 2009-01-17
i realise that the usb has to be the first device to boot from in the BIOS, thanks though...

do i have to type the two pieces of code idividually with return between them?

thanks 
Dave

---

### Post by theozzlives on 2009-01-17
> **UKDave said:**
> i realise that the usb has to be the first device to boot from in the BIOS, thanks though...

do i have to type the two pieces of code idividually with return between them?

thanks 
Dave

If you're talking to me, the wget line and chmod line are seperate.

---

### Post by UKDave on 2009-01-17
ty TheOzzlives..i was..(sorry for not being clear...too early and still on my first coffee)

will try it now

Thanks again

Dave

---

### Post by lemmy999 on 2009-01-17
@UKDave

Best way of installing Ubuntu (or indeed any Linux distro) to flash memory is via Unetbootin. Format the card/key to FAT32 , fire up Unetbootin, follow a few very simple instructions and you are "good to go"

---

### Post by sugi007 on 2009-01-20
I have just written a [post ]("http://codesingh.blogspot.com/2009/01/ubuntu-on-stick-with-persistence.html")about this problem on my blog as I struggled with it myself for a few days.

Looks like everything is ok with the stick except it isn't set to boot

Used the following code fixed the problem.

```
install-mbr /dev/sdX
```

where /dev/sdX is the location of your USB stick

Hope this helps

[Code Singh]("http://codesingh.blogspot.com")

---

