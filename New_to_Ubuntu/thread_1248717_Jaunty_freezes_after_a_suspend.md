---
title: "Jaunty freezes after a suspend"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by confused_person on 2009-08-24
I've had ubuntu for a few weeks and have been able to get it in and out of suspend mode just fine until about a few days ago. Now, whenever I wake it up from suspend mode, the computer turns back on (i.e. i can hear the fan running and my usb mouse lights up) but the screen stays black. All I can do is hold down the power button and totally shut down/turn back on the computer, but of course I'd like to just be able to suspend it normally like I used to. I don't really understand why this is happening. Any advice? Thanks!

---

### Post by jbrown96 on 2009-08-24
What type of video card do you have and which drivers have you installed. 

If you don't know you can check with ```
lspci | grep VGA
```

---

### Post by Garyhans on 2009-08-24
I also get random freezes after suspend. I have an Nvidia card..6600gt didn't get the freezes before. I just reboot and say the hell with it..  today.. I had to do the Alt Sys Req.. Reisub watching a video on Youtube.  So for now on I just reboot instead of suspend.

---

### Post by sandyd on 2009-08-24
> **Garyhans said:**
> I also get random freezes after suspend. I have an Nvidia card..6600gt didn't get the freezes before. I just reboot and say the hell with it..  today.. I had to do the Alt Sys Req.. Reisub watching a video on Youtube.  So for now on I just reboot instead of suspend.

install any updates recently?

---

### Post by jbrown96 on 2009-08-24
Garyhans. What version of the nvidia drivers are you using (180.xx or 173.xx)? I've found that the 180.xx drivers have everything configured properly for suspend (at least with a quadro 570m). I think the problem that you have is driver related. Perhaps the drivers are deactivated. This is likely due to a problem with dkms. Dkms automatically rebuilds kernel modules when a new kernel is installed. If it didn't work properly, your system could be loading a generic driver, which won't support suspend. 

Solution: System--->Administration-->hardware drivers. Try to reinstall your drivers (180.xx if available) and reboot.

---

### Post by confused_person on 2009-08-26
> **jbrown96 said:**
> What type of video card do you have and which drivers have you installed. 

If you don't know you can check with ```
lspci | grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

---

