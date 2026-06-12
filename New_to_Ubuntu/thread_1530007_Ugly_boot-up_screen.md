---
title: "Ugly boot-up screen"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by DeadSpace on 2010-07-13
Hello everyone! :)

I am a new user to Ubuntu and Linux and thus far I am thoroughly enjoying my time here. However, I have noticed a very minor problem on bootup after installing Hardware Drivers, where the purple Ubuntu screen is at a very low resolution. Is there a simple, plain English way to fix this?

Thanks very much in advance for your time and assistance :)

---

### Post by jerenept on 2010-07-13
The startup splash screen does not work well with proprietary graphics drivers. There is not much you can do.

---

### Post by stevek123 on 2010-07-13
Not sure I can be alot of help but I see you've not gotten any answers yet. I'm kind of a noob but have run ubuntu for a cpl of yrs now and am working on my third installation...

your msg implies that the screen WAS OK but after hardware drivers it no longer is... Generally hardware drivers means video drivers. 

If you are running an ATI vid card you may find all kinds of problems/issues (I am right NOW and so is my neighbor) so I cannot help much. ATI cards are not very compatible to Linux = poor support I think...I've found that the xserver.org drivers slightly better than the ATI fxgl ones.

If you are running Nvidia, there may be issues but better drivers available. If you added proprietary drivers they should be listed under System->Admin->Hardware Drivers. Go there and make sure that they have been enabled and configured properly. 

And then basics...display settings are generally found Sys->Preferences->Display

Not sure if this helps but it may point you in the right direction.

---

### Post by DeadSpace on 2010-07-13
Sorry, I should have specified.

Currently using an Nvidia 9800 GT.

Linux Mint 9 has a very easy method of solving this problem via startup manager, so I just assumed that Ubuntu would have something similar?

---

### Post by uRock on 2010-07-13
You can find startupmanager in Synaptic Package Manager or just open a terminal and run ```
sudo apt-get install startupmanager
```then StartUp-Manager will be listed in the System> Administration menu. It offers the same capabilities for Ubuntu as it does for Mint.

Let us know how it goes,
uRock

---

### Post by clhsharky on 2010-07-13
DeadSpace

> Linux Mint 9 has a very easy method of solving this problem via startup manager, so I just assumed that Ubuntu would have something similar?

StartUp-Manager is in repository.

Sharky

---

### Post by uRock on 2010-07-13
I just gave startupmanager a shot and it made the boot screen even uglier. You can't even read the text on it. Not even after putting the settings back where they were. It was nice to get a decent resolution for the grub menu though.

Cheers,
uRock

---

