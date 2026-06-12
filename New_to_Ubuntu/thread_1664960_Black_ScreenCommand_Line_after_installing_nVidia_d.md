---
title: "Black Screen/Command Line after installing nVidia drivers on Ubuntu 10.10"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by Dolphin2011 on 2011-01-11
*Hi,*
 
*I am new to Linux and any help you can provide would be greatly appreciated. I have installed Ubuntu 10.10 Desktop Edition on my Toshiba Qosmio G40-10E. I am struggling with the nVidia graphics card. I have tried installing it using the 'Additional Drivers' and rebooting after the installation is complete and some time I get a black screen and I can't do anything and other times I get the command line. I have tired repeating the whole process a few times but the result is the same.*
 
*My graphics card details are:*
***manufacturer : NVIDIA® ***
***type : NVIDIA® GeForce® 8600M GT supporting TurboCache™ technology ***
***mmanufacturer : NVIDIA® ***
***type : NVIDIA® GeForce® 8600M GT supporting TurboCache™ technology ***
***memory : 512 MB dedicated VRAM (up to 2303 MB total available graphics memory using TurboCache™ technology with 4 GB system memory) ***
***memory type : DDR Video RAM (resp. DDR Video RAM and DDR system memory combined) ***
***connected bus : 16x PCI Express ***
***emory : 512 MB dedicated VRAM (up to 2303 MB total available graphics memory using TurboCache™ technology with 4 GB system memory) ***
***memory type : DDR Video RAM (resp. DDR Video RAM and DDR system memory combined) ***
***connected bus : 16x PCI Express ***
 
*Please can you help - I don't know what else to try!*
 
*Thanks*

---

### Post by dysentry on 2011-01-11
When you get the command line try this (It will enable debugging):

sudo vim /etc/X11/xorg.conf


Find the section called "Screen" and add the below line

```
Option         "ModeDebug" "true"
```

Mine looks like:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "GT210-CARD"
    Monitor        "MonitorVGA"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "ModeDebug" "true"
EndSection
```

save and exit by hitting the escape key and typing:
:wq!


Restart pc or type startx

It will log everything needed to /var/log/Xorg.0.log

It would be helpful to post that file so we can see what is happening.

---

### Post by amsterdamharu on 2011-01-11
10.10 comes with the latest nvidia drivers.

Could you post the output of:[FONT=monospace]
[/FONT]```
[FONT=monospace]sudo lshw -C video
```
and[/FONT]
```
dpkg-query -W | grep nvid
```

---

### Post by Dolphin2011 on 2011-01-13
> **amsterdamharu said:**
> 10.10 comes with the latest nvidia drivers.

Could you post the output of:[FONT=monospace]
[/FONT]```
[FONT=monospace]sudo lshw -C video[/FONT]
```[FONT=monospace]
and[/FONT]
```
dpkg-query -W | grep nvid
```

Sorry for the late response - I couldn't get into my laptop so I had to reinstall Unbuntu completely and I had various issues doing this, but it has finally installed successfullyand I have run the Update Manager, but I have not installed any of the nVidia drivers.

Below are the outputs for:
* sudo lshw -C video
                  *-display UNCLAIMED     
                  description: VGA compatible controller
                  product: G84 [GeForce 8600M GT]
                  vendor: nVidia Corporation
                  physical id: 0
                  bus info: pci@0000:01:00.0
                  version: a1
                  width: 64 bits
                  clock: 33MHz
                  capabilities: pm msi pciexpress vga_controller cap_list
                  configuration: latency=0
                  resources: memory:fd000000-fdffffff memory:e0000000-efffffff memory:fa000000-fbffffff   ioport:cf00(size=128) memory:fc000000-fc01ffff

*  dpkg-query -W | grep nvid
                  nvidia-173-modaliases    173.14.28-0ubuntu1
                  nvidia-96-modaliases    96.43.18-0ubuntu1
                  nvidia-common    0.2.24
                  nvidia-current-modaliases    260.19.06-0ubuntu1

Thanks.

---

### Post by amsterdamharu on 2011-01-13
The card is supported for what I can see.

If you installed the drivers and get a black screen try to press control + alt + F1 to get to a text only login screen. After logging in you can try these commands:

```
sudo nvidia-xconfig
startx
```

---

### Post by Dolphin2011 on 2011-01-14
> **amsterdamharu said:**
> The card is supported for what I can see.

If you installed the drivers and get a black screen try to press control + alt + F1 to get to a text only login screen. After logging in you can try these commands:

```
sudo nvidia-xconfig
startx
```


At the moment I haven't installed any of the nVidia drivers. Which driver should I install? Or doesn't it matter?

---

### Post by Dolphin2011 on 2011-01-14
> **amsterdamharu said:**
> The card is supported for what I can see.

If you installed the drivers and get a black screen try to press control + alt + F1 to get to a text only login screen. After logging in you can try these commands:

```
sudo nvidia-xconfig
startx
```


At the moment I haven't installed any of the nVidia drivers. Which driver should I install? Or doesn't it matter?

---

### Post by amsterdamharu on 2011-01-14
Oh, sorry. Yes I am missing nvidia-current. You can try the following command:
```
sudo jockey-text
```
If it finds anything I'd recommend nvidia-current.

That should find your nvidia card and install the driver but you need a cabled Internet connection to get the drivers. After it'll ask to reboot, you can try to reboot (press control + alt + delete) and see if that fixes anything.

---

### Post by Dolphin2011 on 2011-01-15
> **amsterdamharu said:**
> Oh, sorry. Yes I am missing nvidia-current. You can try the following command:
```
sudo jockey-text
```If it finds anything I'd recommend nvidia-current.

That should find your nvidia card and install the driver but you need a cabled Internet connection to get the drivers. After it'll ask to reboot, you can try to reboot (press control + alt + delete) and see if that fixes anything.

No drivers were found when I ran the 'Sudo jockey-text', so I run the 'Additional Drivers' and activated the recommended driver and then rebooted. I didn't get the GUI, but the black screen with a prompt. So I then ran 'sudo nvidia-xconfig' and 'startx' and got a lot of text and which included:
'Failed to load the NVIDIA kernal module. Please check your systems kernel log for additional error messages.
Failed to load module "nvidia" (module-specific error, 0)
No drivers available.
Fatal server error:
no screens found'

Hope this makes sense.

---

### Post by amsterdamharu on 2011-01-15
When you start your computer and press the key down arrow you should get a menu where there is an option Ubuntu recovery. Could you choose the recovery and try dpkg reconfigure?

If that didn't fix it than could you choose the normal Ubuntu menu entry (usually top one) and press e to edit then replace quiet splash with:
```
nouveau.modeset=0 rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1 nomodeset
```

This because sometimes loading the nouveau drivers for your card blocks loading the nvidia driver.

>  run the 'Additional Drivers' and activated the recommended driver and then rebooted.
What driver did you install? Did you take nvidia-current?

---

### Post by Dolphin2011 on 2011-01-16
> **amsterdamharu said:**
> When you start your computer and press the key down arrow you should get a menu where there is an option Ubuntu recovery. Could you choose the recovery and try dpkg reconfigure?

If that didn't fix it than could you choose the normal Ubuntu menu entry (usually top one) and press e to edit then replace quiet splash with:
```
nouveau.modeset=0 rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1 nomodeset
```This because sometimes loading the nouveau drivers for your card blocks loading the nvidia driver.


What driver did you install? Did you take nvidia-current?

I tried the dpkg reconfigure and nothing happened. Then I replaced the quiet flash as suggested, but it would not reboot once I had changed it and I kept getting a message saying the the kernel was needed. When I forced a restart adn went back to the GRUB menu the quite splash had not been changed at all and was still saying:
    'linux /boot/vmlinuz-2.6.35-24-generic root=UUID=dae3aa35-cc47-4ca6-9fc0-362db004ee93 ro quiet splash'

The nVidia driver I installed was the once that was recommended and it didn't have a number but just said it was the 'NVIDIA accelerated graphics driver (version current) [Recommended]'. The other driver that was found after the Additional Drivers' search was 'NVIDIA accelerated graphics driver (version 173)'.

---

### Post by amsterdamharu on 2011-01-16
Sorry, I meant replace the text "quiet nosplash" with [FONT=monospace]
[/FONT]```
[FONT=monospace]nouveau.modeset=0 rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1 nomodeset
```
Not the entire line.
[/FONT]

---

### Post by Dolphin2011 on 2011-01-17
> **amsterdamharu said:**
> Sorry, I meant replace the text "quiet nosplash" with [FONT=monospace]
[/FONT]```
[FONT=monospace]nouveau.modeset=0 rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1 nomodeset[/FONT]
```[FONT=monospace]
Not the entire line.
[/FONT]

Sorry my mistake. It didn't say 'quiet nosplash', but 'quiet spalsh'. I replaced it with 'quiet nosplash' and then when that didin't make a difference I replaced it with the text '[FONT=monospace]nouveau.modeset=0 rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1 nomodeset' but still getting the command prompt after reboot. I have found I am able to access the GUI in very low resolution if I select 'recovery'. 

Do you think it might be that both drivers that are found when searching in 'Additional Drivers' are not the right ones for the card?

Thanks again
[/FONT]

---

### Post by janoschhcsonaj on 2011-03-19
I face a similar problem and posted it on [http://ubuntuforums.org/showthread.php?p=10574045](http://ubuntuforums.org/showthread.php?p=10574045).

Thanks for any help.
Janosch

---

