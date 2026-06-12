---
title: "How to restart sound?"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by P235 on 2010-02-27
I use UNR 9.10 on my Acer Aspire One A0751H netbook.  At this point, everything is okay save for sound.  I had this problem before with other laptops and would restart if I really wanted the sound back.  

Is there another way to restart sound without restarting my netbook?

**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by bikeboy on 2010-02-27
Try this:
```
sudo invoke-rc.d alsa-utils restart
```

Beyond that, you might need to remove and re-add the sound modules using *rmmod* and *modprobe*, but that's a fair bit trickier as you would need to know which modules to play with.

---

### Post by P235 on 2010-02-28
Thanks for the reply.  Unfortunately it did not work out for me.

---

### Post by Jared Norris on 2010-03-01
Just a couple of quick links to help you out,

If you are using the default PulseAudio check out: [http://ubuntuforums.org/showthread.php?t=816159]("http://ubuntuforums.org/showthread.php?t=816159")

Or if you have reverted to Alsa you should look at [http://ubuntuforums.org/showthread.php?t=301640]("http://ubuntuforums.org/showthread.php?t=301640")

Hope that helps.

---

### Post by P235 on 2010-03-02
Thanks for the links.  I do seem to be using PulseAudio, but killing it and starting it again didn't work either.   :(

---

### Post by Jared Norris on 2010-03-02
Ok well to troubleshoot any further you will need to provide a little more information. I'm no guru on sound issues but if you can answer questions like the following it will give us something to work with:

Do you get any sound at all ever? 
If you do does rebooting the laptop make it work again?
What applications cause it to stop?

Also try looking at [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578") to see if that can give you any pointers

---

