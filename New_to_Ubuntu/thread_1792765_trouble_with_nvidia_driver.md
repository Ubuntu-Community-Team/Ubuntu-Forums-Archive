---
title: "trouble with nvidia driver"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by 007casper on 2011-06-28
I am having a trouble with nvidia card.

what is the equivalent of System -> Administration -> Third-Party Drivers and install the Nvidia driver on kde?

---

### Post by climhazzard36 on 2011-06-28
apt-get install restricted-manager

Hope this helps :)

---

### Post by wolfen69 on 2011-06-28
```
sudo apt-get install nvidia-current
```

---

### Post by 007casper on 2011-06-28
thank you.

I did
> sudo apt-get install nvidia-current

how do I check it has the latest driver.  I have also downloaded the driver from nvidia to the download folder.  I want to make sure that it has the latest driver as the nvidia site.

---

### Post by 007casper on 2011-06-28
> apt-get install restricted-manager

couldnt find package restricted-manager

---

### Post by 007casper on 2011-06-28
I saw the nvidia panel.  It wanted me to run nvidia-xconfig as root.  I did
sudo nvidia-xconfig.  It didnt work.  Then, I did nvidia-xconfig as root.

restart the system.

now, I get 
> 
Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE)NVIDIA: Failed to load the nvidia kernel module.
Please, check your 
(EE)NVIDIA: system kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error,0)
(EE) No drivers available

---

### Post by wolfen69 on 2011-06-28
> **007casper said:**
> thank you.

I did


how do I check it has the latest driver.  I have also downloaded the driver from nvidia to the download folder.  I want to make sure that it has the latest driver as the nvidia site.

Getting the latest from the nvidia site probably won't make your card run any better. The latest driver will help those that have the absolute newest card available. Plus, if you install from the nvidia website and install it, you will have to reinstall it every time you update the kernel. Not ideal. Better to just use the one offered by ubuntu which is fairly recent version.

---

### Post by 007casper on 2011-06-28
I have dq45ek intel board.  It cant handle my cinema apple display.  

So, I got Zotac ion graphics card. A few days ago, when I installed the card, the computer stop working.  It didnt even give me a chance to load the new drivers. I uninstalled the card.  I figured I should load the drivers first. 

The dq45ek has horrible old bios, and it is highly recommended to update the bios.  So, I updated the most current bios without any problem.

Zotac's site, and nvidia shows the same latest driver 275.09.07
I have download it to my 'download folder'  I didnt load/run it yet.

@wolfen69 - however, I did sudo apt-get install nvidia-current as suggested.

then, looked around on kubuntu.  When I looked at hardware drivers, it says the system doesnt use any proprietary drivers.

Then, I saw nvidia interface.  I clicked on it, and I got a window pop up saying to run nvidia-xconfig as root.

I did.  However, it is not booting properly.  It gives me a console that says ubuntu is running in low graphics mode.

I am wondering if I should turn the computer off, and install the video card.

---

### Post by 007casper on 2011-06-28
I just installed the video card again and reboot. It worked. :)

thank you so much for your help.

---

### Post by 007casper on 2011-07-25
I was able to use the graphics card without a problem for three weeks.  

I loved it.

Last night, I have updated the computer.  And then, I started to have graphics card problems.  Actually, the computer wont boot with graphics card installed at all.  I cant even get an error screen, or an option to restart x server etc with the card installed. 

I decided to troubleshoot, I used lower resolution monitor that is borrowed from a friend without the video card. If I take the video card, and use on board, then it boots.

I did exactly as wolfen69 suggested.  sudo apt-get install nvidia-current

> Plus, if you install from the nvidia website and install it, you will have to reinstall it every time you update the kernel.

If I am not mistaken, the update had to the with kernel. It is strange though.  I did do apt-get install nvidia-current, and didnt load the driver in any other way.

Now, I am stuck for hours, trying to make this work.  I uninstalled, reinstall etc.  I just cant make it work.

What is the best place to look to see what the problem is?  Is there a specific log I should check.

Thank you.

---

### Post by wildmanne39 on 2011-07-25
Hi, this link should get you into ubuntu so you can fix your driver.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

It most cases it is best to use the nvidia driver in additional drivers unless you had a good reason not too.

Believe my I know from experience that the latest drivers can have issues with natty and if you install from additional drivers you do not have to worry about reinstalling every time the kernel gets updated.

---

### Post by 007casper on 2011-07-25
I am using kubuntu 10.04 LTS.  However, I am going to check the link out.  I hope it will work.  Thank you so much.

---

### Post by wildmanne39 on 2011-07-25
Hi, your welcome! if you need more help post back here and say what you have tried and the results.

---

### Post by 007casper on 2011-07-25
I took out the graphic card.  

Reboot, it gave me an error screen, and gave me options. :)

I chose Run Ubuntu in low graphics mode for just one session

then, on console, I went to etc/default/grub and tried to add nomodeset via vim.  After I added nomodeset esc :wq! - it just wont write to the file.  It is freaking out, and stating it is read only.

Should I change permissions, or write to file as root?

---

### Post by 007casper on 2011-07-25
I saw that grub is writable as root.  So, I went in as root and added nomodeset.  Then, sudo update-grub

I am going to add one at a time to make sure I dont hit a wall.

---

### Post by 007casper on 2011-07-25
I installed the video card.  Reboot.  I still have the nvidia driver installed.

A message comes up and disappears.

Where can I locate that message on the computer?  Is it written to a log?

This time it passed the white bars, and went to a black screen.  Time to add more to the grub.

I also found a little write up about my card.  Does that make any sense?  It seems as they misspelled nomodeset...

> I installed this on my AMD Opteron workstation (which only has PCIe x1 and x4 slots). To install 

you must do this:

load grub at boot and edit your kernel boot line, preferably one of the single user mode lines.
add: "vga=ask nomodetest nouveau.blacklist=yes" to the kernel parameters

Choose F00 (eff zero zero) as the video mode. When it boots, I chose 'netboot'.
I then did this:
sudo apt-get purge remove xserver-xorg-video-nouveau

I also edited /etc/modprobe.d/blacklist.conf and added:

blacklist nouveau

When I rebooted I found that I needed to boot with special parameters still. This time use a 

normal boot mode (full multiuser graphical boot) but add this to the kernel boot line:
vga=ask nouveaublacklist=yes

I again chose F00 as the mode but Ubuntu booted graphically anyway. From here I could go to 

System -> Administration -> Third-Party Drivers and install the Nvidia driver.

It's unfortunate that nouveau crashes on this card, but the card can be made to work

At the moment, I am only going to follow 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by 007casper on 2011-07-25
it doesnt work.  I followed this thread
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

cd /etc/default/
sudo su
vi grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""
:wq
exit
sudo update-grub

nothing 

it passed the white bars.  However, I have the black blank screen.

Any ideas?

I really appreciate it.

---

### Post by wildmanne39 on 2011-07-25
Hi, try this in recovery mode it should reset xserver which is your config file for video card and many other things, make sure you have networking when you do this.

This is if you are using natty.

```
sudo rm /etc/X11/xorg.conf
```
```
 sudo dpkg-reconfigure xserver-xorg
```

The nomodeset options you only needed to use it once to fix the driver problem, you did not need to run update-grub unless you had to make it perminent.

When you get into ubuntu go into synaptic and remove all nvidia drivers then open additional drivers and activate one of the drivers for your card.

As in my experience I had to activate the older driver because the new one did not get along with natty.

---

### Post by 007casper on 2011-07-25
thank you wildmanne39

nomodeset didnt work for me. I was to busy troubleshooting. I didnt see your post till now, when I came here to post the solution that worked for me. 

So, I didnt try 
sudo rm /etc/X11/xorg.conf
sudo dpkg-reconfigure xserver-xorg

After, this line wasnt working
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""

I tried this thread 
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

```

GRUB> echo $linux_gfx_mode
echo $gfxmode
 set gfxmode=2560x1600
load_video (this line didnt work for me)
insmod gfxterm
 GRUB> vbeinfo

```
append/adding a vga=xxx, where xxx is the mode.

It boots slow.  But it works so far.  I am happy to get my needed resolution.  Thank you so much for your help.

---

### Post by wildmanne39 on 2011-07-25
Hi, your welcome!

---

