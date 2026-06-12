---
title: "Boot Screen (plymouth). Can I get rid of it?"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by maryalesia on 2010-12-05
This ... is a weird question. I don't have an issue with the ubuntu logo that is the boot screen. I don't really mind the bug that makes it all ugly once you install proprietary graphics drivers, or the fact that in maverick there isn't even a graphic, just terminal-type text that says "Ubuntu 10.10" with little white dots beneath it. 

But I wanna know if I can get rid of that. 

Like, when you just see a bunch of text attacking your screen as stuff boots? I'm not even sure if that makes sense or is even related to the boot screen.

Just out of curiosity.

---

### Post by maryalesia on 2010-12-05
okay i did a quick google and from what I understand getting rid of plymouth entirely will royally screw stuff up. However something was mentioned about disabling the visuals by changing something to "nosplash"? Or something?

IMPORTANT SIDE NOTE: I'm bash illiterate; I once accidentally deleted GRUB (in the n00b move of the century). Messing around in the terminal with anything remotely related to grub gives me, like, PTSD level flashbacks.

---

### Post by Megaptera on 2010-12-05
If it's booting & working OK, perhaps leave it alone? I'm not sure how many times per day you boot, but do the boot graphics really matter as long as Ubuntu flies when running?

Just a thought ...

---

### Post by Silent Warrior on 2010-12-05
maryalesia: Megaptera's suggestion is really the best one. However, if you really must: If you enter Synaptic, see how many Plymouth-themes you can uninstall without taking anything else with it. As Plymouth seems to have to be integrated with the main distribution, you're not going to get rid of it completely (unless you roll your own distribution, or take Arch for a spin), but there is a text-plugin for Plymouth in the repositories. If no theme is available or set, I think Plymouth defaults to normal text-output.
To disable Plymouth on boot, either open your GRUB-configuration (/boot/grub/menu.lst?) and remove 'splash' from the kernel-line. You can also do this through the GRUB-menu when you boot, though I'm not sure it's persistent: Highlight your kernel, press 'e', navigate the cursor with the arrow-keys and delete 'splash' from the kernel-line. You won't see splash anywhere BUT on the kernel-line, so don't worry too much. Then just hit Ctrl+X and you're good.

---

### Post by maryalesia on 2010-12-05
> **Megaptera said:**
> If it's booting & working OK, perhaps leave it alone? I'm not sure how many times per day you boot, but do the boot graphics really matter as long as Ubuntu flies when running?

Just a thought ...

> **Silent Warrior said:**
> maryalesia: Megaptera's suggestion is really the best one.

Oh I fully plan on leaving it as it is. I was just curious if it was possible. 

I began wondering because I ran a script through a link posted in another thread that was supposed to fix the pixelated ubuntu boot screen. I think it works in 10.04, but in 10.10, as I said, you basically get the text-load in purple. It doesn't REALLY bother me, however since I ran the script I've notice two things:
1. boot up is the same, but tinier and in the upper left corner of the screen.
2. When I shut down, for my viewing pleasure I get: a boot screen. Like, how the boot screen at load up SHOULD look: nice graphics, no pixelation.

Those two things don't bother me so much as make me scratch my head. What worries me is the fact that since I ran the script, I can't use the "restart computer" option. When I use it, x.org shuts down but my computer stays running, never to re-boot. I have to hold down the power button to get out of it. 

At this point I can easily work around such a problem, but I'm afraid that it might be a symptom of something that could potentially get worse. 

As I said I have in the past deleted grub, but I've also had a few months of x.org fail that also kind of scarred me. 

I don't know how to work the reverse-script for the script that I ran (bash illiterate ... probably should've thought of that before I ran the script in the first place) so I tried purging and reinstalling grub, but I guess plymouth is something different because it didn't do anything. 

sorry for the long post!

---

### Post by Silent Warrior on 2010-12-05
Long posts are good, as long as they have content in 'em. :)
I sort of recognise those two symptoms, but I don't really know what to do about them. Having the splash in the upper left is a natural consequence of manually increasing Grub's resolution, but I don't have that issue myself - I think I did with LMDE, and I randomly see it even now, but for me it's a rare sight.
First try running
```
sudo update-initramfs -u
```
(This will regenerate the scripts read and run during boot - has to be done when you change Plymouth-themes, btw.)
If that doesn't work, it might be time to make use of dpkg-reconfigure. It would be nice to know what script you used, though. Can you post the contents of it, or a link to where you found it?

---

### Post by maryalesia on 2010-12-05
> **Silent Warrior said:**
>  It would be nice to know what script you used, though. Can you post the contents of it, or a link to where you found it?

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)
 
^That is the blog post with the script I ran. At the bottom is a link to download the revert script, but I'm not sure how to use it. I don't totally understand how the color-coding works. I'm more copy-paste when it comes 10to the terminal.

---

### Post by maryalesia on 2010-12-05
assuming that I attached this file correctly ... this is the revert script.

---

### Post by maryalesia on 2010-12-06
ps I tried

sudo update-initramfs -u

with no luck.

Thanks for all the help, though. I really appreciate it. :D

---

### Post by Silent Warrior on 2010-12-07
Ah, that fix. Well, it shouldn't be difficult to salvage. You should probably run the script - it looks like it's just a matter of running it, and that should take care of things.

An explanation of what the revert-script does:
```
sudo apt-get purge v86d
```
The -y in the script-file tells apt-get to assume yes to all questions (AKA non-interactive mode). I recommend you don't use it yourself until you know why you'd want to, really, so I don't show the invocation with -y included. Uh, well, this removes a virtual framebuffer device that the fixer-script installed for you. :) I think I tried it in Arch - I now use FBSplash on my Arch-machine.
```
sed 's/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\ nomodeset\ video\=uvesafb\:mode\_option\=1280x1024-24\,mtrr\=3\,scroll\=ywrap\"/GRUB\_CMDLINE\_LINUX\_DEFAULT\=\"quiet\ splash\"/g' /etc/default/grub > ./temp
sudo mv -f ./temp /etc/default/grub
```
This opens /etc/default/grub, finds the line containing 'GRUB_CMDLINE_LINUX_DEFAULT=[whatever]', removes what's already there and replaces it with the normally preinstalled string - GRUB_CMDLINE_LINUX_DEFAULT="quiet splash". (Which is what I'm running, and several others.) Consider manually editing this file and remove splash:
```
gksu gedit /etc/default/grub #Find GRUB_CMDLINE_LINUX_DEFAULT and set its value to "quiet"
```
```
sed 's/GRUB\_GFXMODE\=1280x1024/\#GRUB\_GFXMODE\=640x480/g' /etc/default/grub > ./temp
sudo mv -f ./temp /etc/default/grub
```
This opens the same file, and comments out the GRUB_GFXMODE-line, as well as setting it back to the default value, which was set to 1280x1024 by the script. This affects what resolution GRUB is shown in - I don't think it affects Plymouth in any way, but don't quote me on it. If you have a laptop, or an up-to 19" non-4:3 monitor, chances are it doesn't support 1280x1024 (should try 1024x768 or 1280x800). Commenting this string makes GRUB2 use the default, failsafe, resolution 640x480.
```
sed 's/uvesafb\ mode\_option\=1280x1024-24\ mtrr\=3\ scroll\=ywrap//g' /etc/initramfs-tools/modules > ./temp
sudo mv -f ./temp /etc/initramfs-tools/modules
```
I'm not sure of this line, but I think you could either edit /etc/initramfs-tools/modules as root (gksu gedit) and comment out the uvesafb-line or remove it altogether. Commenting (adding # followed by a space in front of it) is of course the safer option - then, if it works fine with the # in place, you can remove the line. Or you could just run the command and see what happens. :D My guess is that setting this line in the first place is what caused the problem.
```
sed 's/FRAMEBUFFER\=y//g' /etc/initramfs-tools/conf.d/splash > ./temp
sudo mv -f ./temp /etc/initramfs-tools/conf.d/splash
```
And here we move into /etc/initramfs-tools/conf.d/splash and remove the FRAMEBUFFER=y line.
```
sudo update-grub2
sudo update-initramfs -u
```
These should be self-explanatory, more or less. Run these to make your changes take effect, reboot. If that doesn't fix it, crawl under your bed and squeal.

---

### Post by maryalesia on 2010-12-07
> **Silent Warrior said:**
> Ah, that fix. Well, it shouldn't be difficult to salvage. You should probably run the script - it looks like it's just a matter of running it, and that should take care of things.

These should be self-explanatory, more or less. Run these to make your changes take effect, reboot. If that doesn't fix it, crawl under your bed and squeal.

You. ROCK. :D:D:D

---

