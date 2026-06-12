---
title: "Question about drivers."
date: 2010-08-11
forum: New to Ubuntu
---

### Post by myrtle001 on 2010-08-11
I just have a question about how installing drivers in Ubuntu (Wubi) will affect Windows.

I ask this because today while watching a video (on Windows), the screen went blank but the sound kept going. Eventually the Blue Screen of Death came up, but I didn't get a chance to read what it said. I booted up Windows and everything seemed fine. The error report's solution was that maybe my NVIDIA graphic card needed updating, but I could find no driver updates for it.

This morning, I installed the "**NVIDIA accelerated graphics driver (version 173) **" from System-->Administration-->Hardware Drivers after first installing the [FONT="Courier New"]bcmwl-kernel-source[/FONT] package and second the "**Broadcom B43 wireless driver**" to get my wireless working (see [http://ubuntuforums.org/showthread.php?t=1541915](http://ubuntuforums.org/showthread.php?t=1541915)). I am concerned that maybe this interfered with Windows. Because of that I've already uninstalled the graphics driver from System-->Administration-->Hardware Drivers.

I'm not sure, but the BSoD _*might*_ have come up before (like a few months ago before I even knew what a Linux Distro was ;)), but I am not positive about that.

I had a virus scan going, but it only got about halfway (no viruses detected) before I had to restart to install Windows updates.

I want to know if this is something serious or something to not even worry about before I boot back into Windows. I also want to know if it is safe to install new programs, save files, install drivers, etc in Wubi-installed Ubuntu 10.04 LTS.

Here are some of my Computer stats:
- Dell XPS M1530 Laptop
- Apx. 320GB harddrive (according to Ubuntu, Windows says 285GB)
- 32-bit Windows Vista Home Premium Edition
- Wubi-installed 32-bit Ubuntu 10.04 LTS "Lucid Lynx"
- Some sort of NVIDIA video card.

Thanks in advance!:D

---

### Post by sandyd on 2010-08-11
> **myrtle001 said:**
> I just have a question about how installing drivers in Ubuntu (Wubi) will affect Windows.

I ask this because today while watching a video (on Windows), the screen went blank but the sound kept going. Eventually the Blue Screen of Death came up, but I didn't get a chance to read what it said. I booted up Windows and everything seemed fine. The error report's solution was that maybe my NVIDIA graphic card needed updating, but I could find no driver updates for it.

This morning, I installed the "**NVIDIA accelerated graphics driver (version 173) **" from System-->Administration-->Hardware Drivers after first installing the [FONT=Courier New]bcmwl-kernel-source[/FONT] package and second the "**Broadcom B43 wireless driver**" to get my wireless working (see [http://ubuntuforums.org/showthread.php?t=1541915](http://ubuntuforums.org/showthread.php?t=1541915)). I am concerned that maybe this interfered with Windows. Because of that I've already uninstalled the graphics driver from System-->Administration-->Hardware Drivers.

I'm not sure, but the BSoD _*might*_ have come up before (like a few months ago before I even knew what a Linux Distro was ;)), but I am not positive about that.

I had a virus scan going, but it only got about halfway (no viruses detected) before I had to restart to install Windows updates.

I want to know if this is something serious or something to not even worry about before I boot back into Windows. I also want to know if it is safe to install new programs, save files, install drivers, etc in Wubi-installed Ubuntu 10.04 LTS.

Here are some of my Computer stats:
- Dell XPS M1530 Laptop
- Apx. 320GB harddrive (according to Ubuntu, Windows says 285GB)
- 32-bit Windows Vista Home Premium Edition
- Wubi-installed 32-bit Ubuntu 10.04 LTS "Lucid Lynx"
- Some sort of NVIDIA video card.

Thanks in advance!:D
ubuntu doesn't change/affect anything in windows when installing drivers. probably just a freak occurance BSOD

---

### Post by Res2216firestar on 2010-08-11
As far as I know, installing drivers in wubi should not affect Windows at all. Check with nvidia from windows to make sure it has the latest drivers: [http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us").

---

### Post by myrtle001 on 2010-08-11
Alright, glad to know it's nothing serious! I'll get to go on enjoying Lucid via Wubi!

Thanks!:D

---

