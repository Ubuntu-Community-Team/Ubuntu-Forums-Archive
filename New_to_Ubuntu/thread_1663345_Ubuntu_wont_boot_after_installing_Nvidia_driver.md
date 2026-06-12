---
title: "Ubuntu wont boot after installing Nvidia driver"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by jennkhutch on 2011-01-09
Hello, I installed the Nvidia accelerated driver and rebooted. Now Ubuntu wont  boot to the log in screen. The Dell logo appears then the boot menu then when I choose Ubuntu, the screen goes blank and gets stuck there.  Any help appreciated.

I have a partitioned install of 10.04.1 with Win7 on a Dell XPS laptop.

---

### Post by cariboo on 2011-01-09
Stat in recovery mode, and once at the menu, use the arrow keys to select netprompt and press enter, once at the prompt type:

```
nvidia-xconfig
```

Once the command has finished running, type reboot at the prompt to reboot your system, it should now take you to the login screen.

---

### Post by jennkhutch on 2011-01-09
Recovery mode leads me to the same blank screen.

---

### Post by jennkhutch on 2011-01-09
Is there something I can do from the install cd?

---

### Post by jennkhutch on 2011-01-09
Edited my original post for clarity. Help?

---

### Post by bradenmast on 2011-01-09
sounds similiar to my problem i had just a couple of hours ago :l 

[http://ubuntuforums.org/showthread.php?t=1663339](http://ubuntuforums.org/showthread.php?t=1663339)

This was my thread id give it a quick skim to the end and read what was posted and hopefully it will have some helpful info. 

Good luck man!

---

### Post by jennkhutch on 2011-01-09
I had been looking at your post but unfortunately none of the suggested solutions will work for me since I only have a completely  blank screen, no where to input any info at all.

---

### Post by lbarnes on 2011-01-09
Try ctrl-alt-f7

---

### Post by jennkhutch on 2011-01-09
> **lbarnes said:**
> Try ctrl-alt-f7

Nothing :(

The only way to get into Ubuntu and access my files is with the live cd (thank goodness for that so I could get school papers I'd have lost otherwise).  I know it is possible to fix issues from the live cd but how in this case?  I don't even know where to look for information about that outside of these forums.  I can't be the only person this has happened to and posted about it online but my google-fu is failing me big time. It has been 12 hours trying to figure this out and I'm about ready to just reinstall ubuntu 32-bit if I can figure out how to do that and overwrite the 64-bit version installed.  Or just try another Linux distro altogether that won't cause so many headaches, arggh.

---

### Post by TechWiz2100 on 2011-01-09
Also try Ctrl + Alt + F1-7 not just F7 because F7 is default for gnome so that shouldn't get you very far...

From LiveCD I think you can open terminal, mount your Ubuntu partition and chroot into the Ubuntu Partition then run nvidia-xconfig

---

### Post by amsterdamharu on 2011-01-09
If control + alt + F1 doesn't work I suggest booting from live CD and post the following files:
```
(ubuntu on harddisk)var/log/kern.log
(ubuntu on harddisk)var/log/Xorg.0.log

```


Then when you mounted your ubuntu partition try to rename xorg.conf you have to be root for that so the command should be like. (after mounting the partition in nautilus by double clicking on it)
```
cd /media/(press tab)/etc/X11/
sudo mv xorg.conf xorg.old
```

You can reboot after this but if you get a blanc screen in recovery renaming xorg should not do much since recovery only uses console.

---

### Post by lbarnes on 2011-01-10
Did you ever try running "startx" ??

---

### Post by TechWiz2100 on 2011-01-10
> **lbarnes said:**
> Did you ever try running "startx" ??

The OP can't get a prompt in which to run startx

---

### Post by jennkhutch on 2011-01-11
I finally got to the command line. From there I tried dkpg config and startx suggestions I found on various forums and neither worked. Another suggestion I found that did work was to edit the xorg file and replace nvidia with vesa and edit the boot from "quiet splash" to "nomodeset" and pressing ctrl x. At that point I got warnings that I am running in low graphics mode with a bunch of options to reconfigure, continue in low graphics mode or exit to command line. I tried to reconfigure to the default generic as well as creating a new one. All that did was leave me with so many xorg backup files in the X11 folder with nothing changed that I uninstalled/deactivated the Nvidia accelerated driver and removed all of the xorg files from the folder and am back at square one.

Is it best to just reinstall?  If so, how  do I do that on a dual boot without affecting windows?

---

### Post by amsterdamharu on 2011-01-11
How did you get to the command line? By pressing control + alt + F1?

Anyway the vesa option was is fine (just start in low graphics not try to reconfigure), you should be able to copy and paste some commands in a terminal.

Like what kind of card you have (model of your nvidia):
```
sudo lshw -C video
```


What drivers are installed for nvidia.
```
dpkg-query -W | grep nvidia
```

I would not suggest re install because after you install the drivers you might get the same problems again since your hardware hasn't changed.

Could you tell me again what version of Ubuntu you have installed?
```
cat /etc/issue
```

---

### Post by jennkhutch on 2011-01-11
Thank you for your response.  I got to the command line 2 ways, one by realizing that my laptop keyboard is set so that the function keys don't default to f1-f12, I actually have to press a "Fn" key first. This was after going into my files with the live CD and changing the xorg to vesa and logging in with the "nomodeset" change into low res mode.

sudo lshw -C video brings up this:

*-display UNCLAIMED     
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:a8000000-a9ffffff memory:b0000000-bfffffff(prefetchable) memory:ac000000-afffffff(prefetchable) ioport:2000(size=128) memory:aa000000-aa07ffff(prefetchable)
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f03fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)

dpkg query brings up

nvidia-173-modaliases	173.14.27-0ubuntu1
nvidia-96-modaliases	96.43.18-0ubuntu1
nvidia-common	0.2.23
nvidia-current	260.19.29-0ubuntu1~xup1~lucid
nvidia-current-modaliases	260.19.29-0ubuntu1~xup1~lucid


Version Ubuntu 10.04.1 LTS \n \l



> **amsterdamharu said:**
> How did you get to the command line? By pressing control + alt + F1?

Anyway the vesa option was is fine (just start in low graphics not try to reconfigure), you should be able to copy and paste some commands in a terminal.

Like what kind of card you have (model of your nvidia):
```
sudo lshw -C video
```


What drivers are installed for nvidia.
```
dpkg-query -W | grep nvidia
```

I would not suggest re install because after you install the drivers you might get the same problems again since your hardware hasn't changed.

Could you tell me again what version of Ubuntu you have installed?
```
cat /etc/issue
```

---

### Post by theozzlives on 2011-01-11
Did you download the driver or did you install it via System > Administration > Additional Drivers?

---

### Post by jennkhutch on 2011-01-11
> **theozzlives said:**
> Did you download the driver or did you install it via System > Administration > Additional Drivers?

Additional drivers through system admin. I have since deactivated it though.

---

### Post by amsterdamharu on 2011-01-11
Strange that the model is not given on the lshw, I got:
product: C68 [GeForce 7025 / nForce 630a]

Ok, you can uninstall the nvidia drivers by copy and pasting the following commands in low graphics mode:

```
sudo aptitude purge nvidia-173-modaliases
sudo aptitude purge nvidia-96-modaliases
sudo aptitude purge nvidia-common
sudo aptitude purge nvidia-current
sudo aptitude purge nvidia-current-modaliases
sudo mv /etc/X11/xorg.conf  xorg.old
```Now when you reboot you should boot in the nouveau driver and get a message that you're in low graphics mode. This is fine, don't fix just restart x (I think it's somewhere in the menu.)

After you log in Ubuntu should have found a driver and alert you to it, if not you can press alt + F2, type jockey-gtk and click run. 

When the driver is installed (if the above didn't give you a driver please post here) it will ask you to reboot, don't do that yet.

Open a terminal and paste the following command:
```
sudo nvidia-xconfig 
```Now maybe post your /etc/X11/xorg.conf that has just been created and execute:
```
lshw -C video
```To see if you get the model of your nvidia card this time.

Now reboot and see what happens.

---

### Post by jennkhutch on 2011-01-11
> **amsterdamharu said:**
> Strange that the model is not given on the lshw, I got:
product: C68 [GeForce 7025 / nForce 630a]

Ok, you can uninstall the nvidia drivers by copy and pasting the following commands in low graphics mode:

```

sudo mv /etc/X11/xorg.conf  xorg.old
```



jenn@jenn-laptop:~$ sudo mv /etc/X11/xorg.conf  xorg.old
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory

---

### Post by amsterdamharu on 2011-01-11
That's fine, I just added that to make sure the vesa driver isn't loaded and would load nouveau.

jockey should after a reboot recognize your videocard and offer to install it.

---

### Post by jennkhutch on 2011-01-11
Jockey didn't find any drivers.  Perhaps it isn't recognizing my card now?

---

### Post by amsterdamharu on 2011-01-11
What does the lshw -C video say? Do you get the exact model of your card?

Is it under system -> hardware drivers?

If it's not then try to install the following package again:

```
sudo apt-get install nvidia-current-modaliases
```

---

### Post by jennkhutch on 2011-01-11
It is still not finding any available drivers. I ran that code again then searched again for drivers with no change.

From my Laptop's specs, I have 1024 (MB) NVIDIA GT435M GeForce installed.

(for reference, this is my laptop [http://www.dell.com/us/p/xps-17/pd?oc=dndojx1&model_id=xps-17](http://www.dell.com/us/p/xps-17/pd?oc=dndojx1&model_id=xps-17))

---

### Post by amsterdamharu on 2011-01-11
When you installed the nvidia-current-modaliases there were no errors? That package is needed to recognize the make and model of your videocard.

When you do the lshw -C video the model doesn't show so that's a bit strange and suggesting there is something wrong.

You could try to reboot in recovery and try dpkg reconfigure option, you need cable internet and some time because it might take a while.

---

### Post by jennkhutch on 2011-01-11
I think it is just time for a reinstall :/  I've only had the laptop for a month and had been using ubuntu for a few weeks so I won't be missing much.  I will just remember to not enable the recommended Nvidia Accelerated Driver and get through all my linux books and guides online before I make changes again. 

If I could be pointed in the direction of the best way to reinstall on a dual boot, it would be greatly appreciated.

---

### Post by amsterdamharu on 2011-01-11
> I think it is just time for a reinstall

I don't see the point of that, it will get you exactly where you are right now. No drivers for nvidia, no xorg.conf so nouveau would be loaded.
What exactly did you have before you installed the driver that you don't have now?

The nvidia-current package I have on lucid does not have your model listed as being supported by the driver.
/usr/share/doc/nvidia-current/README.txt.gz

Now checking the nvidia website:
[http://www.nvidia.com/object/product-geforce-gt-435m-us.html](http://www.nvidia.com/object/product-geforce-gt-435m-us.html)

---

### Post by amsterdamharu on 2011-01-11
And their website of course does not allow me to download just a file, I have to run some java app to detect my driver and then install it.
One big problem "Available for Windows Vista*, Windows XP*, Windows 2000*, and Windows 7*."

If the nvidia-current is the only driver available at this point then your card is not supported (it is not in the list). The best it could do is vesa or nouveau.

You could try asking nvidia support for help on this and I might have a look at it later.

---

### Post by amsterdamharu on 2011-01-11
By the way we still don't know:
1. what version of ubuntu you are using.
2. if lshw -C video gave you the make and model of your card.

You answered "it didn't work" but did that mean jocky didn't give you an option to install a driver or the card's make and model still isn't listed?

---

### Post by realzippy on 2011-01-11
Folks,
the problem seems to be that OP has kind of dual graphics/optimus technology.Means NVIDIA chip **and** Intel.

[I]product: Core Processor Integrated Graphics Controller
vendor: Intel Corporation
[/I]
To verify open terminal:
```
lspci | grep VGA
```

..if this shows 2 devices,then there is no existing NVIDIA driver to install 
although jockey offers the "current";NVIDIA offers no driver and probably never will.
Bad luck,also the nvidia graphics sucks battery power,if you do not have a VGA switch Intel/NVIDIA in your laptops BIOS,the laptop will be nearly useless in any Linux OS without connected to power supply.


[More...]("http://www.nvnews.net/vbulletin/showthread.php?p=2291824#post2291824")

---

### Post by amsterdamharu on 2011-01-11
I guess that solves it, you were probably using the intel but I didn't see it in lshw. Sorry it was there but overlooked it.

By the way the latest nvidia driver supports  "GeForce GT 435M" 
[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run)

I have an Intel graphics card on my laptop and enabled xorg-edgers to get 3d on it.

---

### Post by realzippy on 2011-01-11
> **amsterdamharu said:**
> I guess that solves it, you were probably using the intel but I didn't see it in lshw. Sorry it was there but overlooked it.

By the way the latest nvidia driver supports  "GeForce GT 435M" 
[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run)

I have an Intel graphics card on my laptop and enabled xorg-edgers to get 3d on it.

...the driver will not work without BIOS switch to "kill" the intel graphics.If [I]lspci | grep VGA
[/I]returns something similar to :
*VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)*
then 3D/direct rendering (MESA) should work out-of-the-box (at least in 10.10;dunno if also in 10.04 OP uses),no need for xorg-edgers PPA.

---

### Post by amsterdamharu on 2011-01-11
Oh sorry, I forgot to mention that I have to go with zippy on this one. Best just keep using the Intel if it gives you longer batery life.

I mentioned the drivers for people who would see this thread and think their card is not supported as it is with the latest nvidia drivers (not in repository for Lucid yet).

I remember not having 3D on mint 9 (is lucid 10.04) on my laptop and fixing it with xorg-edgers, as for the op; no need to fix stuff if it isn't broken so maybe ask advice on it if you don't have 3d support.

---

### Post by Dolphin2011 on 2011-01-11
Hi,
 
I am new to Linux and have just recently installed Ubuntu 10.10 Desktop Edition and everything appears to be working fine on my laptop except for the monitor which has very low resolution and it makes it difficult to use. I check the 'Monitor' settings and thesr isn't much to change to for the screen resolution (just an even lower screen resolution) and I can't enable any of the desktop effects. 
 
I have a Toshiba Qosimo G40-10E and I think my graphics card is a nVidia GT 8600. I have installed the nVidia drivers that come up when I initially log in, but after rebooting I can't get into the GUI and sometimes it just displays a blank screen and other times it displays only command prompt.
 
I have tired re-installing Ubuntu and different nVidia drivers but always with the same result.
 
Have you seen this problem before with the graphics card I have? I have looked at a lot of threads and tried a lot of different things I don't understnd but nothing seems to work. I really want to stick with ubuntu, but perhaps it wouldn't work on my laptop, so if you can suggest another Linux OS I could try that would also be great.
 
Any help/advice would be greatly appreciaited.
 
Thanks.

---

### Post by realzippy on 2011-01-11
[I]Best just keep using the Intel if it gives you longer batery life.
[/I]
...unfortunately it is impossible (for a few models ugly hacks exist) to "switch off" the nvidia via software;
it sucks power although you cannot use it,some laptops have a switch in their BIOS,most don't.Bought such a laptop for my GF (because of the nvidia
card),now she is lost without power supply....and I am the idiot.
Thanks,NVIDIA!

---

### Post by realzippy on 2011-01-11
> **Dolphin2011 said:**
> Hi,
 
I am new to Linux and have just recently installed Ubuntu 10.10 Desktop Edition and everything appears to be working fine on my laptop except for the monitor which has very low resolution and it makes it difficult to use. I check the 'Monitor' settings and thesr isn't much to change to for the screen resolution (just an even lower screen resolution) and I can't enable any of the desktop effects. 
 
I have a Toshiba Qosimo G40-10E and I think my graphics card is a nVidia GT 8600. I have installed the nVidia drivers that come up when I initially log in, but after rebooting I can't get into the GUI and sometimes it just displays a blank screen and other times it displays only command prompt.
 
I have tired re-installing Ubuntu and different nVidia drivers but always with the same result.
 
Have you seen this problem before with the graphics card I have? I have looked at a lot of threads and tried a lot of different things I don't understnd but nothing seems to work. I really want to stick with ubuntu, but perhaps it wouldn't work on my laptop, so if you can suggest another Linux OS I could try that would also be great.
 
Any help/advice would be greatly appreciaited.
 
Thanks.

...see and run the command given in post #30 of this thread.If you have not 2 graphic devices,then your problem differs.In this case
I suggest to make an own thread;will come over for help.Threadnapping makes things complicated...

---

### Post by Dolphin2011 on 2011-01-11
Thanks for your quick reponse and suggestiion. I am acutally at work and don't have my laptop, but I will try it whan I get home this evening. 
 
I am sorry to just add on an exisiting thread (I just didn't want to start a new thread if it is the same issue), but if it doesn't work I will start a new theard and thanks for your offer of help.

---

### Post by jennkhutch on 2011-01-11
> **amsterdamharu said:**
> By the way we still don't know:
1. what version of ubuntu you are using.
2. if lshw -C video gave you the make and model of your card.

You answered "it didn't work" but did that mean jocky didn't give you an option to install a driver or the card's make and model still isn't listed?

1. 64-bit 10.04.1

2. I meant that jockey didn't find any suggested drivers and the lshw -c video gave the same result as before that I c&p'd earlier.


Before I enabled the nvidia accelerated driver, mostly everything was working fine. My windows were wobbly, games could be played with the exception of not being able to full screen on facebook and you tube which a solution for that was to enable recommended drivers thus causing this clusterf*ck.

---

### Post by jennkhutch on 2011-01-11
> **amsterdamharu said:**
>  as for the op; no need to fix stuff if it isn't broken 

Except that I still can't get into my GUI unless I go into Bios and change "quiet splash" to "nomodeset" every time and it only runs in low graphics mode.

---

### Post by amsterdamharu on 2011-01-11
```
... change "quiet splash" to "nomodeset"
```
Thats the grub menu not the BIOS. 
Have you checked the bios to see if you can disable the nvidia card (or the Intel whichever you prefer)?

If you run with one card disabled it makes sense to install drivers for the other.

---

