---
title: "Safely Remove Hardware"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-03-05
One thing I really miss from Windows is its Safely Remove Hardware option. Whenever I did this in Windows to a flashdrive, external hd, etc, the light on the device would go out, so I would then know the device was shut off.

This doesn't happen in Linux. When I right-click on my external hardrive, and hit Unmount Volume, all that happens is a little window will pop up saying it's ok for me to unplug the device or something(but this window doesn't pop up all the time), but...the light still remains on. So the device is still on.

When I go to sleep at night I like to turn off my external since it's not being used. But I always have to manually unplug the usb cable, since Linux doesn't properly turn the device off like Windows does.

I did a search, and I found [_this thread_](http://ubuntuforums.org/showthread.php?t=1085810&highlight=Safely+Remove+Hardware). And a member recommends to open Terminal and type this:

sudo fdisk -l

But that really doesn't do anything. Terminal shows my drives, but then that's about it. It doesn't shut anything off.

So my question is, is there any type of app or software for Ubuntu for that will properly turn off these devices when I hit Unmount Volume?

Thank you for an yhelp.

---

### Post by Andavane on 2009-03-05
I also really missed that function in Linux.
However, I also remember that in windows half the time when I went to "safely remove" I would get the message "Windows is unable remove this device at the moment. Please Try later" or something, and however much later I tried, it wouldn't remove, so I had to shut down the PC to do it that way.

But I agree that it would be good for it to be really "off" and the light removed. By the way my mate has Vista and the light doesn't go off there (although it does in XP).

If you are in doubt as to whether the device has been unmounted or not, go can go to "Places/Computer..." and navigate to where your device is.
Right click on  it and read the list which appears. If there is a "Mount" option, then the device is not mounted.

And vice versa.

Regards

John

---

### Post by lykwydchykyn on 2009-03-05
sudo fdisk -l isn't supposed to turn anything off; it's just a command to show the drives and partitions.  Probably the guy posting that was trying to get diagnostic info from the original poster (which he never got).

Unfortunately I don't know a way to get the light to turn off.  I do know you can ensure the data has been written by simply typing "sync" at a terminal -- though if you unmount the drive this is implicit anyway.

From what I've seen, sounds like this is a known issue and has been reported to developers (see this: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/90097](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/90097))

---

### Post by h8uthemost on 2009-03-05
Thank you for the relpy.

And yeah, I know the device is actually unmounted because it no longer shows up in the Places tab. So it's definitely unmounted, but the device isn't turned off. I did a little more searching, and a member said that Windows would actually unmount the volume *and* power the device off. Where Linux only unmounts it.

And I've been searching and searching for an app/software that will actually power it off for me without having to unplug it, and I just cannot come across any. So I'm guessing there's no way that you can make Linux do this.

EDIT: Thanks lykwydchykyn. Yeah, that's pretty much all that terminal command does, just shows the drives. I was hoping it would power a drive off. Oh well, hopefully in a future release of Ubuntu the OS will be able to do this.

Thanks.

---

### Post by Andavane on 2009-03-05
> **h8uthemost said:**
> Thank you for the relpy.

And yeah, I know the device is actually unmounted because it no longer shows up in the Places tab. So it's definitely unmounted, but the device isn't turned off. I did a little more searching, and a member said that Windows would actually unmount the volume *and* power the device off. Where Linux only unmounts it.

And I've been searching and searching for an app/software that will actually power it off for me without having to unplug it, and I just cannot come across any. So I'm guessing there's no way that you can make Linux do this.

EDIT: Thanks lykwydchykyn. Yeah, that's pretty much all that terminal command does, just shows the drives. I was hoping it would power a drive off. Oh well, hopefully in a future release of Ubuntu the OS will be able to do this.

Thanks.

which "windows" were you using?
XP physically turns it off - Vista doesn't.

Rgds

john

---

### Post by h8uthemost on 2009-03-05
It's Windows XP that I have on my computer(I dual boot). I never used Vista so I had no idea that this feature didn't work in it.

---

### Post by Andavane on 2009-03-05
> **h8uthemost said:**
> It's Windows XP that I have on my computer(I dual boot). I never used Vista so I had no idea that this feature didn't work in it.
I really liked that feature in XP... comforting knowing that it was unmounted and disconnected.

I'm sure that it is possible in Linux.

Somehow.

---

