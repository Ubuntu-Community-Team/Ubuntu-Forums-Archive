---
title: "black screen on iso boot"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by jacknet52 on 2011-09-02
I downloaded ubuntu 11.04 using Pendrivelinux to a thumbdrive. made sure in bios it was usb enabled and drive was first in boot order. 
Alls I got was black screen with a tiny cursor blinking in the upper left corner. Am I doing some thing wrong? Thanks, jack

---

### Post by anewguy on 2011-09-02
Does it do anything before you get to the screen with the blinking cursor - like try to boot, etc.?

What are the specs on your computer and video adapter?

---

### Post by jacknet52 on 2011-09-02
yes it posts and splashes the motherboard page where it says to hit delete key for bios at the bottom. I'm using a pentium celeron 2.66Ghz, 2g memory, azus motherboard with onboard video card. I also downloaded unetbootun and reloaded my thumbdrive using that. Still the same.
Thanks for responding and any help.
Jack

---

### Post by anewguy on 2011-09-02
I assume you put the USB as the first boot device, or selected it from a boot menu?

Do you know what chipset is on the motherboard, and in particular for the video?  It's possible you may need to try the alternate CD and see if it can do any better - it may be a video driver problem, but I don't know.  The alternate CD will let you detect and configure your video.

Dave ;)

---

### Post by jacknet52 on 2011-09-02
So I guess what you are saying Dave is that I should run unetbootr and burn the iso file on to a cd. I think the video is fine as witnessed by the motherboard flash screen coming in fine from the bios but what I see happening is the bios isn't seeing the bootlogger in the iso files. It's not even getting to the video driver as far as I can tell. Does that make sense?

---

### Post by anewguy on 2011-09-03
I'm honestly not sure.  However, if you have the ability to boot from a CD, then I would just take the ISO image you downloaded (it's of the LiveCD, correct?) and just burn that image to disk.  Remember, it's an image, so you don't burn it as a file.  Most burning software has an option to create a data disk from an ISO.  I think I would try that and then see what happens.

Dave ;)

---

### Post by jacknet52 on 2011-09-03
Dave - Thanks for your endeavor to try and help me. I burnt the image to cd using imageiso or some software and it worked. For you out there using an older computer don´t even mess with USb. Take care dude. Jack

---

### Post by anewguy on 2011-09-04
Just glad it's working for you!

Good luck!

Dave ;)

BTW - please see "Thread Tools" above the thread and click to open, then select the thread solved option.  This will let others know that for you a solution was found.

---

