---
title: "Ubuntu 11.04 not working with Compiz"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by jhinxed on 2011-08-18
Hi again,

Just wondering if anyone can help me with setting up compiz for ubuntu 11.04? I wanted to resize my icons on the launchbar but it's not really working as well as other plugins. I saw some posts which say that unity 2d does not work well with compiz but I'm not really sure which is supposed to work. Thanks!

---

### Post by androssofer on 2011-08-18
> **jhinxed said:**
> Hi again,

Just wondering if anyone can help me with setting up compiz for ubuntu 11.04? I wanted to resize my icons on the launchbar but it's not really working as well as other plugins. I saw some posts which say that unity 2d does not work well with compiz but I'm not really sure which is supposed to work. Thanks!

so compiz is in by default... then i assume u installed "CompizConfig settings manager" and then did u select the unity plugin and change the launcher size within tht? is tht wer its not working right?

---

### Post by adeklipse on 2011-08-18
> **jhinxed said:**
>  I saw some posts which say that unity 2d does not work well with compiz but I'm not really sure which is supposed to work. Thanks!

It's not that Unity 2D doesn't work well with Compiz, but Unity 2D actually does not work with Compiz at all.

If I'm not mistaken, Unity 2D on Ubuntu 11.04 uses the Metacity Window Manager, and not Compiz (although in the next release, it will use Compiz)

I've been looking for an easy Unity 2D settings manager too (at least on par with CCSM for Unity 3D), but I'm not having the best luck. :(

---

### Post by jhinxed on 2011-08-18
> **androssofer said:**
> so compiz is in by default... then i assume u installed "CompizConfig settings manager" and then did u select the unity plugin and change the launcher size within tht? is tht wer its not working right?

Yes, that's where I'm currently stuck at. I've tried reinstalling the CompizConfig Settings Manager and still no changes. still not working

---

### Post by jhinxed on 2011-08-18
> **adeklipse said:**
> It's not that Unity 2D doesn't work well with Compiz, but Unity 2D actually does not work with Compiz at all.

If I'm not mistaken, Unity 2D on Ubuntu 11.04 uses the Metacity Window Manager, and not Compiz (although in the next release, it will use Compiz)

I've been looking for an easy Unity 2D settings manager too (at least on par with CCSM for Unity 3D), but I'm not having the best luck. :(

Oh, I see. Hope there's a workaround for that. On that note, would unity 3d support it if that was enabled instead of 2d?

---

### Post by coffeecat on 2011-08-18
> **jhinxed said:**
>  On that note, would unity 3d support it if that was enabled instead of 2d?

If your hardware can run Unity 3d, then it can run compizconfig-settings-manager. But what hasn't been determined is whether your system can run Unity 3d. What graphics hardware do you have and what driver? If you do not know, post the terminal output of:

```
sudo lshw -C display
```

---

### Post by jhinxed on 2011-08-18
> **coffeecat said:**
> If your hardware can run Unity 3d, then it can run compizconfig-settings-manager. But what hasn't been determined is whether your system can run Unity 3d. What graphics hardware do you have and what driver? If you do not know, post the terminal output of:

```
sudo lshw -C display
```

Here's the details:

  *-display               
       description: VGA compatible controller
       product: C73 [GeForce 7100 / nForce 630i]
       vendor: nVidia Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:23 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff memory:fe9c0000-fe9dffff

---

### Post by adeklipse on 2011-08-18
> **jhinxed said:**
> Oh, I see. Hope there's a workaround for that. On that note, would unity 3d support it if that was enabled instead of 2d?

Just like coffeecat answered, it *should* work.

And judging by the output, so long as you have the driver installed, compositing Compiz should work.

---

### Post by jhinxed on 2011-08-18
> **adeklipse said:**
> Just like coffeecat answered, it *should* work.

And judging by the output, so long as you have the driver installed, compositing Compiz should work.

Hmm.. Thanks for the help :D I'll try to figure this out and post what I did if I get it to work :P By the way, how do i uninstall unity2d from my system?

---

### Post by coffeecat on 2011-08-18
I'm not quite clear whether you are actually able to log into the Unity 3d desktop or not, but I'll assume that you can only run Unity 2d. Your graphics card is:

> **jhinxed said:**
> product: C73 [GeForce 7100 / nForce 630i]
       vendor: nVidia Corporation

And you have one of the versions of the proprietary nvidia driver enabled. There have been reports of problems with some of the Geforce 7*** series in 11.04, but I can't remember the details. Open Additional Drivers and see which nvidia driver is installed. It will probably say something like "the driver is activated but not in use".  The "not in use" message is a bug and can be ignored. If it's activated, it's in use!

If you have the "current" nvidia driver activated, activate the 173 driver, reboot and see if that gets you Unity 3d. If it doesn't, then I suggest you search the forum for your graphics hardware ("GeForce 7100") and see if any fixes have been posted.

If you are not sure whether you are getting Unity 3d or 2d, the quickest test I know is to open a terminal and place the terminal window half over another app window or a pattern on your wallpaper. The 3d terminal is slightly transparent - the 3d terminal is entirely opaque.

---

