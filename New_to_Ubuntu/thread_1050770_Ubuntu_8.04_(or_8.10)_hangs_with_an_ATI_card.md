---
title: "Ubuntu 8.04 (or 8.10) hangs with an ATI card"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by futuroimperfetto on 2009-01-26
Hello,

 I've got an Asus Z96J with an ATI X1600 and Ubuntu 7.10 Gutsy mounted on it (full specs at the bottom of this post). Compiz is not working on these system (it says that the "composite extension is not available"), but the system works very well.

I would like to upgrade to 8.04 or 8.10, but all the times I tried, I had issues.

The problem is that with both 8.04 and 8.10 my computer freezes completely after about 15 minutes that I use it and nothing works (not even CTRL+ALT+BACKSPACE), save for the mouse. I have to do a hard reboot. I fully installed 8.04 when it came out and tinkered a bit with it. I tried 8.10 through the LiveCD option and I got the same issue after about 20 minutes that I'm using it.

I have to notice that both in 8.04 and 8.10 compiz works, while it doesn't on my current situation. I'm seeing this with or without the restricted ATI driver, with Compiz on or off, always about 15 to 30 minutes after I boot it. 

From my ignorant standpoint, it looks like I'm having the problem reported in this entry of Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/195051]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/195051")

I can see some suggestions in the comments there, but I don't want to start poking my nose around the system as I might not be able to invert the changes. Where should I be looking and what data can I provide to help troubleshoot this?

Thanks

---

### Post by blueridgedog on 2009-01-26
Are you using the restricted drivers for the ATI card?

System -> administration -> hardware drivers

---

### Post by futuroimperfetto on 2009-01-26
Hi blueridgedog,

 Thanks for your reply. I've had the same problem both with and without the restricted ATI drivers on 8.04 which I installed about 6 months ago (then I had to go back to 7.10).

Two days ago I decided to give 8.10 a spin through LiveCD and I had exactly the same behavior without restricted ATI drivers (if I'm not wrong, I can't have them installed on LiveCD, because it would force me to reboot).

I'm afraid that the problems would persist unless I do something about it, even if I install 8.10 and enable the restricted drivers.

Do you know of any tricks or things related to this issue?

Cheers

---

### Post by blueridgedog on 2009-01-26
Try booting off of the live CD and then disabling desktop effects.

System -> Preferences -> Appearance -> Visual Effects set to "None".

---

### Post by futuroimperfetto on 2009-01-26
> **blueridgedog said:**
> Try booting off of the live CD and then disabling desktop effects.

System -> Preferences -> Appearance -> Visual Effects set to "None".

I did this when I was using 8.04 and it hanged anyway.

Still, this is a simple test which I was forgetting to try and it may encourage me on whether or not there is hope. I hope to be able to do it tomorrow night (unfortunately, I can't do it immediately). At worst, in a couple of days.

Thanks for the suggestions

Cheers

---

