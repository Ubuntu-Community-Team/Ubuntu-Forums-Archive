---
title: "Audio problems!"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by dvaldes21 on 2010-08-10
Hey y'all....
So I'm running a fresh install of Ubuntu 10.4 via the [Wubi installer.]("http://wubi-installer.org/") Everything went great except for some audio problems I'm having specifically in Ubuntu (audio works fine in Windows.)

Basically whenever I try to adjust the volume through the panel or keyboard shortcuts, I immediately hear what can only be described as a mix of swarming bees and static. The only way to get regular sound going is to change the Profile for my sound device in the Sound Settings menu. That gets it back to normal, but doesn't solve the static problem. It happens on every Profile setting. I also often hear faint static when playing music.

A run of the lspci command show this as my sound card: ```
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
``` Are there known issues with this card and Ubuntu? Is it a simple driver problem? Any help would be appreciated!

Thanks,
-D.

PS.,
I installed the GNOME ALSA mixer and that allows me to lower and raise the volume without static, but I can still hear static in the background sometimes and it'd be nice to have it work from the panel....

---

