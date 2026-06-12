---
title: "nvidia problem fixed, but I don't know why!"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by threetwoone on 2009-06-20
I kept getting an error whenever I tried to install the nvidia drivers for my 9500m gs (on my asus G1Sn-B1).
(Original post of my problem: [http://ubuntuforums.org/showthread.php?p=7487842#post7487842](http://ubuntuforums.org/showthread.php?p=7487842#post7487842))

The error was always the same:
Ubuntu is running in low graphics mode. The following error was encountered:
  (EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
  (EE) Failed to load module "nvidia" (loader failed, 7)
  (EE) No drivers available

but then I installed "nvidia-glx-180_185.19.1~really185.18.14-0ubuntu0_amd64.deb             (15.4 MiB)" from: [https://edge.launchpad.net/~thefirstm/+archive/ppa/+build/1048133]("https://edge.launchpad.net/%7Ethefirstm/+archive/ppa/+build/1048133").  Then I just went through System > Administration > Hardware Drivers and installed the recommended driver (I tried this prior to installing the package and I got the aformentioned error).  As far as I can tell it only changed the following packages in Synaptic:
nvidia-glx-180-dev
nvidia-glx-180-libvdpau
nvidia-glx-180modaliases
nvidia-glx-180
These are all now marked as upgradeable.
1. Did I just roll back these packages?  And if so is there a way to do this with non-thrid-party packages?
2. If I do the recommended upgrade is it possible that my problem will come back?
3. Why did this work in the first place

---

### Post by prvteprts on 2009-06-21
I have had that problem before too. Are you familiar with /etc/X11/xorg.conf? In my case with nvidia cards, I had to tweak it a bit to get it to work.

Ok, the first the you did was install the recommended drivers from Preferences> Hardware Drivers, which didn't work. Then you installed from the .deb you downloaded, and then installed the recommended drivers again on top of that.

Probably what happened was during the first install of the recommended drivers, the error message kept showing because xorg.conf wasn't edited in the proper way automatically. After you installed the downloaded .deb driver, that package was able to correctly configure xorg.conf for you. Then when you reinstalled the recommended drivers again, it worked because xorg.conf was already configured. 

I noticed that the packages downloaded externally tend to configure xorg.conf in a different way compared to the recommend driver packages. So I checked the different xorg.conf files from my other systems that worked, and I was able to figure out the lines which were missing from my problematic installation to get it to work. I did a few reinstallations and basically it boiled down to using the recommended drivers and editing the xorg.conf.

Hope this helps. This is just from my experience.

---

