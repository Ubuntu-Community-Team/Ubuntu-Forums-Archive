---
title: "Should I install ALL possible drivers?"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-12-31
I run Ubuntu from an external HDD connected by USB cable. It was installed on my current machine, spec is in my sig.

I would like to run my Ubuntu set up on other machines that I come across from time to time, such as those belonging to friends and business acquaintances. Of course, I've no idea at this point what hardware specs those machines might be, other than they're likely to be i686 based.

So, what I want is an Ubuntu set-up that can be ported to various other hardware configurations seamlessly, where if the boot procedure finds that the machine has (say) an nVidia card instead of my Intel on-board graphics card, it'll know what to do.

To provide me with the most robust system possible for the use I'd like to make of it as described above, should I just install **every** driver in the Ubuntu repositories, even though they are not appropriate to my current configuration?

Is there anything that could go wrong with installing drivers for hardware that, as far as my current machine is concerned, doesn't exist?

---

### Post by TenPlus1 on 2009-12-31
Ubuntu will automatyically detect whichever gfx card yoiu are using on that particulat system anyhow during boot, the download drivers are only needed if you wish to use 3d for ati/nvidia...

---

### Post by komputes on 2009-12-31
Modules will not be loaded if the hardware is not detected at boot, so this should be relatively safe. I had the same question as you (concerning binary drivers for computers that do not have internet access) and listed all the packages needed here:

[http://ubuntuforums.org/showthread.php?t=1329514](http://ubuntuforums.org/showthread.php?t=1329514)

Keep in mind that once you have them installed they are sitting there, you may still have to go to System > Administration > Hardware Drivers to activate/enable them.

---

### Post by Roger Allott on 2009-12-31
> **TenPlus1 said:**
> Ubuntu will automatyically detect whichever gfx card yoiu are using on that particulat system anyhow during boot, the download drivers are only needed if you wish to use 3d for ati/nvidia...

Thanks, but what then will happen if I boot my Ubuntu on a friend's PC that has an ati/nvidia card, and so I then install the driver for 3D when it's running on that machine?

Would my Ubuntu be compromised when I then revert to booting my Ubuntu from my PC that doesn't have ati/nvidia?

Sorry, but as you might be able to tell, I'm not entirely up to speed with what drivers in general do and don't do!

---

### Post by Martje_001 on 2009-12-31
Well, it wouldn't crash I suppose, but it wouldn't work either ;). The Nvidia driver sets the following line in xorg.conf:
```
Driver "nvidia"
```
So when you boot up *without* a nVidia videocard, you will get a fancy recovery mode of X.

Btw: You can't install both fgrlx (prop. driver ATi) and nvidia (prop. driver nVidia) on the same system.

---

### Post by Roger Allott on 2009-12-31
> **komputes said:**
> Modules will not be loaded if the hardware is not detected at boot, so this should be relatively safe. I had the same question as you (concerning binary drivers for computers that do not have internet access) and listed all the packages needed here:

[http://ubuntuforums.org/showthread.php?t=1329514](http://ubuntuforums.org/showthread.php?t=1329514)

Keep in mind that once you have them installed they are sitting there, you may still have to go to System > Administration > Hardware Drivers to activate/enable them.

AHA!! We seem to be of the same mindset. What I suppose I want is for the drivers to be downloaded and put in the correct place on my system for the boot process to find them as and when necessary, but not to be actually installed yet.

But I also want them to be upgradable (but still not installed) when Update Manager notices that a new version is available.

---

### Post by Paqman on 2009-12-31
The simple solution would be to not use proprietary graphics drivers at all. If you just stick to the basic open source drivers that come on the LiveCD then you'll be able to boot up on any system. You won't get fancy 3D or high resolutions, but you will get compatibility, which sounds like it'd be more useful to you.

---

### Post by Roger Allott on 2009-12-31
> **Paqman said:**
> The simple solution would be to not use proprietary graphics drivers at all. If you just stick to the basic open source drivers that come on the LiveCD then you'll be able to boot up on any system. You won't get fancy 3D or high resolutions, but you will get compatibility, which sounds like it'd be more useful to you.

OK, that's a reasonable compromise, but whilst the open source drivers might be on the LiveCD, they are not on my USB-connected HDD because they were deemed unnecessary when I did the initial install. (Or am I mistaken on that point?)

I definitely do not want to fanny around with carrying a LiveCD with me. I want to have as close to a plug'n'play operating system as possible.

---

### Post by Martje_001 on 2009-12-31
No, all drivers which are available on the live-cd are also installed on your hdd. For example, search in Synaptic for 'xserver-xorg-video': you'll see a whole bunch of videocard-drivers installed (on both the live-cd and hdd-install).

---

### Post by Roger Allott on 2009-12-31
> **Martje_001 said:**
> No, all drivers which are available on the live-cd are also installed on your hdd. For example, search in Synaptic for 'xserver-xorg-video': you'll see a whole bunch of videocard-drivers installed (on both the live-cd and hdd-install).

Ah, thanks for that. What I see is that all of those from the main repository are showing as installed (except the debugging packages), but those from the universe and multiverse repositories are not installed.

The obvious, but perhaps stupid, question is should I install the ones from the universe and multiverse repositories?

---

### Post by Martje_001 on 2009-12-31
The drivers which are not installed are mostly very very old. I don't think you'll ever need them, but it wouldn't harm to install them, though.

---

### Post by JimInLakeland on 2009-12-31
Why not just burn a 9.10 CD/DVD and boot to it?

---

### Post by Martje_001 on 2009-12-31
[LIST=1]
[*]It's slow
[*]Settings don't servive a reboot
[*]You don't have your personal files
[/LIST]
I think.

---

### Post by Roger Allott on 2009-12-31
> **JimInLakeland said:**
> Why not just burn a 9.10 CD/DVD and boot to it?

> **Martje_001 said:**
> [LIST=1]
[*]It's slow
[*]Settings don't servive a reboot
[*]You don't have your personal files
[/LIST]
I think.

Correct.

---

