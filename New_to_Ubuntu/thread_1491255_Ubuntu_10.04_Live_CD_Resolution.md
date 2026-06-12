---
title: "Ubuntu 10.04 Live CD Resolution"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by linuxnovice on 2010-05-23
Hello,

I am trying to install Ubuntu 10.04 on my Gateway PC using the LiveCD. However, when I first boot into the live CD, the desktop took only 1/4 of my 22" screen. I checked online and set the graphics options to nomodeset for nvidia graphic card. Now, it takes up the entire screen, however its resolution is only 800x600 and the only other option that is available is 640x480. I really don't want to proceed with the installation without fixing (or atleast have a way to fix) this. 

Any suggestions?

Thanks.

---

### Post by oldfred on 2010-05-23
Have you tried running the liveCD and download the nvidia driver. On my PC after about a minute it offered the nvidia driver as a hardware choice. If that works then I would not worry about the install.

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

---

### Post by mbzn on 2010-05-23
The nvidia driver should fix this.. go to System>administration>Hardware drivers.

---

### Post by linuxnovice on 2010-05-23
> **oldfred said:**
> Have you tried running the liveCD and download the nvidia driver. On my PC after about a minute it offered the nvidia driver as a hardware choice. If that works then I would not worry about the install.

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

Thanks. Well it is offering restricted drivers options in the LiveCD version. I haven't chosen it yet since I don't have the operating system installed. 

But I'll give it a shot and see what happens.

---

### Post by linuxnovice on 2010-05-23
Hi,

I restarted the PC and rebooted into the live CD version again. I pressed F6 and choose nomodeset option and then clicked "Try without installing". Now all I get is a the new Ubuntu logo and 5 red dots below it. The screen is frozen at this.

Any ideas?

---

### Post by themusicalduck on 2010-05-23
If you want to test the Nvidia driver before installing, install them while in the liveCD environment. It'll tell you you have to restart which obviously wouldn't work, but you can do it another way.

When they are installed, press ctrl+alt+f1. Then type this command into the prompt ```
sudo service gdm restart
``` It'll take you back to your dekstop with the video drivers working and still in the liveCD boot. Then you could try running nvidia-settings from a terminal to see what settings there are available.

---

### Post by linuxnovice on 2010-05-23
> **themusicalduck said:**
> If you want to test the Nvidia driver before installing, install them while in the liveCD environment. It'll tell you you have to restart which obviously wouldn't work, but you can do it another way.

When they are installed, press ctrl+alt+f1. Then type this command into the prompt ```
sudo service gdm restart
``` It'll take you back to your dekstop with the video drivers working and still in the liveCD boot. Then you could try running nvidia-settings from a terminal to see what settings there are available.

Worked like a charm! Thanks.

---

