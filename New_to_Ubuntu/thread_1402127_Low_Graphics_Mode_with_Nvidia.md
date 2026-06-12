---
title: "Low Graphics Mode with Nvidia"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Stubbs3 on 2010-02-08
I did a kernel update and after reboot, it came to low graphics mode.
Ive tried to uninstall the nvidia drivers and reinstall accordingly to the instructions provided at [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+drivers](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+drivers)

Im still very new to Ubuntu let alone typing in commands, so let me know what other info is needed.
I have a Nvidia 8600GT (yes i know its old, but it works), Ubuntu 9.10, Hauppauge HVR-1600
I had insta

Any help or guidence would be greatly appreciated.

---

### Post by wojox on 2010-02-08
Scroll down to **Important note:** you need to install that bash script to keep from the having troubles when the kernel gets upgraded.

---

### Post by Stubbs3 on 2010-02-08
Yes i understand that i will need to perform this step. But shouldn't i wait to perform this step until AFTER i get the xserver to work correctly? All that the bash script says it's good for is automatically updating the drivers once the new kernel is updated.
The problem is, is that right now I'm getting the "low graphics mode" screen at startup. How do i correct this issue?

---

### Post by Pelgar on 2010-02-08
Hi Stubbs, I had similar problems with my old nvidia MX-4000 drivers after the kernel update. I believe you need to uninstall the nvidia drivers, even though they are not working, then reinstall. I believe you need the following command to uninstall.
```
sudo nvidia-installer --uninstall
```I followed ibuclaw's instructions at [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
when I installed the 96.43.14 drivers. I had to modify the commands where driver versions were used but otherwise everything worked well. 
About midway down my post at [http://ubuntuforums.org/showthread.php?t=1400177](http://ubuntuforums.org/showthread.php?t=1400177) I've listed out the exact steps I used. You could compare my modified steps to the original if need be.

I'm pretty new to Ubuntu and Linux myself and the only reason I had the Nvidia proprietary drivers installed was because I didn't know any better. After the fiasco with the latest kernel update I ended up installing my drivers via Synaptic Package Manger. If you want to try that read on down in the post at [http://ubuntuforums.org/showthread.php?t=1400177](http://ubuntuforums.org/showthread.php?t=1400177)

Hope this is at least a little helpful

---

### Post by Stubbs3 on 2010-02-10
Found out the problem was that it was all due to my grub menu.lst. I must have updated grub causing it to wipe out the vmalloc=[I]256MB
[/I]I tried numerous times to Un-install and re-install the drivers, But it kept on going into low graphics mode. I went over my logs and found that it wasn't able to initialize the nvidia card. After some research I stumbled across having to change the grub menu.lst if using  nvidia card with a hauppauge card. Remembering that I have done this change previously I checked it and it was gone.

[I]Thanks for everyone's input and help!

Stubbs
[/I]

---

