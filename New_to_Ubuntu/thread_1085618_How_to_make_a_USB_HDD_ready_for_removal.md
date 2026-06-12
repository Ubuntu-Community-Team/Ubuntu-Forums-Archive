---
title: "How to make a USB HDD ready for removal?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by tnek on 2009-03-03
Hi,

I have an external HDD with a capacity of 640GB (it's not a flash memory stick) which I connect using USB. It's formatted with ext2 and it works well.

When I remove it I first do: (It's mounted as /media/external640)
```
$ umount /media/external640
```

And then I wait a couple of seconds and unplug it. The fact that I unmount it doesn't seem to affect the spin of the HDD. It still spins when I unplug it (I think it takes around 10 minutes before it spins down of itself if there is no access to it).

Am I doing something wrong? Should I want until it has spun down even if it takes a long time? (10 minutes is a long time if you want to take your laptop and leave.)

If I right click on it and choose to Eject it I get an error message. It might only work on flash sticks, I don't know.

---

### Post by opscure on 2009-03-03
After you do the umount command do you get your prompt back or are you just unplugging it after a few seconds and then the prompt appears?  

The reason I'm asking is because depending on how much data you copied over to the HD, the unmount command is usually writing that data when the drive is to be removed.  So if you are doing a backup of your laptop HD then maybe the 10 minute wait time is necessary.  On the other hand if you are copying a 10kb text file there should be little or no wait time to unmount the drive.  The fact that it's still spinning; however, leads me to believe it's the former.

---

### Post by sydbat on 2009-03-03
I wonder the same thing. Perhaps test with a large file (10MB?), copy it over, do the unmount, unplug as you normally would. Then, after it has stopped spinning, plug the USB drive back in and see if the entire file has been copied. If it has, then the spindown might just be internal workings of the USB drive shutting itself down because there is no input. If it hasn't, then you might need to wait that 10 minutes.

Test several scenarios to determine if you need to wait to unplug it or not. Maybe after waiting that 10 minutes, with the USB plugged in, the drive will still be spinning.

---

### Post by mikechant on 2009-03-03
If you unmount it by right-clicking on the desktop icon (If there is one) then if there is data to write you will get a 'writing data, do not remove' message, and then you will get the 'safe to remove' message.

---

