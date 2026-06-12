---
title: "Failure to boot"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by Iceman692 on 2010-04-12
Today is just going to be a wonderful day, isn't it?

Got home with my new HDMI cable to hook up to my Mythbuntu machine. Adjusted the resolution to 1080p and my screen was wobbly and quality was bad. It was probably my TV. I decided to downgrade it to 720p. Did that and quality was great, but there seemed to be an overscan problem. half of my screen was cut off! So I decided to disable my NVIDIA driver because I read on another forum that it was a newer driver problem. Decided to reboot after that and now everything boots properly until I get to where my desktop should be. Instead it asks for my login info in a terminal-type setting and the entire thing is flashing and quirky, but the funny thing is that it only types when its not flashing. And I'm talking about fast flashing, so its rather hard to even type anything. I'm not able to get my password in correctly because its flashing so much. I'm assuming this is because my dumb butt disabled the NVIDIA driver. If this is indeed the problem, then how can I fix it?

As always, I appreciate any help!

---

### Post by WinterRain on 2010-04-12
Hit Esc as ubuntu is booting up to get to grub. Then choose "recovery mode". Then after logging in, do:
```
sudo apt-get install nvidia-glx-185
```
then ```
sudo reboot
```

---

### Post by Iceman692 on 2010-04-15
> **WinterRain said:**
> Hit Esc as ubuntu is booting up to get to grub. Then choose "recovery mode". Then after logging in, do:
```
sudo apt-get install nvidia-glx-185
```
then ```
sudo reboot
```
 
I tried that. Looked like it worked, but then I rebooted and had the same problem. I went back into safe mode a bit more frustrated and when it said that it installed packages for me and I no longer need to install it and gave me the option to "safe uninstall optional packages" (or something similar). I selected that and it removed things like "gnome-desktop" and "python". I knew that was a mistake right away. However, it did boot up. when I got into Mythbuntu the title bar text was huge and things were very disproportioned. 720 was big. 600*800 was rediculously huge. Only part of the desktop was on screen. I looked under the app menu (which I had to guess where it was since it was off of the screen) and MythTV was gone. Next I tried to boot up my Windows installation (I had been dual booting). That worked, and it ran updates. I restarted to install the updates and once that was done, I was never able to get back into Windows 7. It gave me a blue screen with some error I don't recall. I decided I needed to start from scratch. I inserted my Mythbuntu live USB drive to reformat the HDD. I got all the way to the desktop and it froze. I got that far twice (having several unsuccessful attempts of getting it to even boot up from the boot menu) and then it started only going as far as the TV loading icon. Then I tried using UNetbootin to creating another MythTV live USB drive with the same result. Next, I tried a regular Ubuntu Drive and it locked up on the Ubuntu logo loading screen. Finally, I tried my Ubuntu live CD. I got to the loading icon here too and it froze like the others. I tried that twice to no avail. Now, after booting from the CD, the NVIDIA boot agent loads and eventually tells me DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER (even though there is no disk).
 
I've been having tons of problems while booting to these devices. Every time I'd boot from an external device and it would freeze, I would have to hard shut down the machine, remove the media and then the computer hardware would start next time and have nothing on the screen. Not even the motherboard splash, bios, or cursor. Nothing. No signal. Then, I'd have to hard shut down again, and it would finally start up. I'm running a 1TB drive and a 160 GB drive. The 160 has my OSes and the 1TB is just a little bit of storage. My next plan of action is to remove the drive, connect it to a PC via SATA>USB cable, reformat, and attempt to start from scratch again. Will this in fact solve my problems?
 
The PC hardware is mostly new. I just installed everything about a week ago and have been setting everything up the way I like it, so hardware failure seems like a long shot.

---

