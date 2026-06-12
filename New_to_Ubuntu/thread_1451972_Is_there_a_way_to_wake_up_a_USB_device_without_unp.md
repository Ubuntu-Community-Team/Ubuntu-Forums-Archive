---
title: "Is there a way to wake up a USB device without unplugging and plugging in the USB..."
date: 2010-04-11
forum: New to Ubuntu
---

### Post by giddyup306 on 2010-04-11
I have an external HD that I use only for backup.  When I'm done backing up I don't like having the drive on since it doesn't need to be.  But I do have the drive turned on sometimes two or three times a day to backup data or retrieve data.  Basically it is kind of annoying unplugging and the plugging the USB back in.  Is there a way to wake the device up from the computer?

Thanks,

M.

---

### Post by Don1500 on 2010-04-11
What kind of drive is it? I have two 120 gig Solid State drives connected and they are always on, no problem for the last two years. 

If your drive is connected and powered up it should be as easy as going to  "Places" and mounting the drive. If you turn it off all you should have to do is turn it on and it will show up in "Places". You can also unmount from "Places".

---

### Post by HermanAB on 2010-04-11
You can try restarting the HAL daemon.

---

### Post by mellort on 2010-04-11
Hey giddyup306,

It looks like [scsi-spin]("http://manpages.ubuntu.com/manpages/hardy/man8/scsi-spin.8.html") can do what you want. Figure out what the device name of the drive is, possibly using
```
sudo fdisk -l
```
and then run
```
scsi-spin --up **devicename**
```
where **devicename** is the name of your disk. You can similarly use "--down" instead of "--up" to spin down the disk. Note, you may have to run the scsi-spin command as super-user (sudo) depending on the permissions of the drive.

Cheers

Edit: In hindsight, I'm not sure that I answered your question. It isn't clear if you drive is just spun-down or if you have it completely powered off. If it is completely powered off, then I don't think that this solution will work. Regardless, I'll leave my answer here for posterity.

---

