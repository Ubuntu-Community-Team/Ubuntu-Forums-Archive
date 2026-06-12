---
title: "External Drive"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by szaqlon on 2009-10-08
Is there any way to get the files from an external drive that was not properly unmounted?

---

### Post by macabrem on 2009-10-08
Was the data actually "lost" or does the drive not re-mount?

---

### Post by szaqlon on 2009-10-08
the drive will not remount.

---

### Post by macabrem on 2009-10-08
I'm wondering if the computer still thinks the drive is mounted? 

I'm not sure without searching, but there should be a way to see with the command line if the drive still looks mounted, then just unmount it, replug it in and power it up to remount.

---

### Post by macabrem on 2009-10-08
What shows up in you /dev/ directory if you open a terminal and cd into it?

I'm not sure how the drive will show up, but the software may think the drive is still mounted somewhere in the /dev directory.   When you figure out the drive, try to open a terminal and type:

  unmount "device name"

or

  sudo unmount "device name"

Also, just leaving the drive unplugged and restarting the computer may unmount it...

---

### Post by szaqlon on 2009-10-08
The problem is I got the drive when I was visiting my brother. I put a bunch of files on it and unplugged it without unmounting it. He lives 1500 miles away and I'm trying to get to the files from another computer.

---

### Post by Anarci on 2009-10-08
If its a windows file system like ntfs you can try mounting it in windows and then mounting it in linux again

---

### Post by szaqlon on 2009-10-08
No it's ext3, and the laptop I'm trying to mount it to is ext4.

---

### Post by macabrem on 2009-10-08
Sorry, I didn't understand I guess.  

I didn't realize that not unmounting correctly would cause a glitch in the drive.  I assumed it would only cause the computer it was mounted to to think it was still mounted.

---

### Post by szaqlon on 2009-10-08
No idea. When I plug it in though nothing happens and I can't find it anywhere.

---

### Post by macabrem on 2009-10-08
I found this - it is a google cached page, for some reason I can't find the current page:

[http://74.125.93.132/search?q=cache:uEE8NRVt2PwJ:www.ehow.com/how_2208480_mount-ntfs-drive-ubuntu.html+drive+not+unmounted+ubuntu&cd=25&hl=en&ct=clnk&gl=us&client=firefox-a](http://74.125.93.132/search?q=cache:uEE8NRVt2PwJ:www.ehow.com/how_2208480_mount-ntfs-drive-ubuntu.html+drive+not+unmounted+ubuntu&cd=25&hl=en&ct=clnk&gl=us&client=firefox-a)

I know this applies to NTFS - but I'm wondering if this helps...

---

### Post by DGortze380 on 2009-10-08
plug the drive in and post the output of 

```

sudo df -l

```

---

### Post by szaqlon on 2009-10-08
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              6728280   2736268   3650232  43% /
tmpfs                   900952         0    900952   0% /lib/init/rw
varrun                  900952       328    900624   1% /var/run
varlock                 900952         0    900952   0% /var/lock
udev                    900952       156    900796   1% /dev
tmpfs                   900952       528    900424   1% /dev/shm
lrm                     900952      2392    898560   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1               101086     19672     76195  21% /boot
/dev/sda7            230647028   1022420 217908408   1% /home

---

