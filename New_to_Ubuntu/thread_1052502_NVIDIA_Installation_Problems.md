---
title: "NVIDIA Installation Problems"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by age99 on 2009-01-27
Hi,
I tried to upgrade my NVIDIA driver to version 180.22.  I got this to work temporarily and I had all the settings I wanted, but every time I rebooted, I was told that "Ubuntu is running in low-graphics mode" and for some reason, none of my settings remained.  It seems to be over-writing my xorg.conf file each time I reboot.  

How do I maintain my settings?

Should I be re-installing the NVIDIA driver?  

I downloaded the driver from [www.nvidia.com](www.nvidia.com), shut down the gdm, ran the installation program.

Any help will be appreciated.

---

### Post by mikewhatever on 2009-01-27
What driver did you use before 180.22? Did you black listed the modules?

---

### Post by XanderCrews on 2009-01-27
See if you have any packages along the lines of linux-restricted-modules, and if you do, completely remove them.  Then uninstall and re-install the 180.22 driver.

XC

---

### Post by age99 on 2009-01-27
The NVIDIA driver is a restricted driver.  How do I remove the driver?

---

### Post by XanderCrews on 2009-01-27
While I'm sure that 180.22 would be considered restricted if it were in the repositories (to my knowledge it isn't), for the moment I'm speaking of restricted modules in the repositories themselves.  You can check to see if you have any packages named linux-restricted-modules via synaptic:

System->Administration->Synaptic Package Management

when it comes up search for "linux-restricted-modules" (no quotes) and with the results, any name with a green square next to it is installed.  If you have any installed, right click on their name and choose "Mark for Complete Removal".  Do this for each instance of linux-restricted-modules you find.
Up in the tool bar is a button with a green check mark labeled "Apply".  Hit that and let Synaptic do its work.

Once that is done, uninstall and reinstall 180.22 by shutting down gdm and so on.  It should solve the problem.

XC

---

### Post by klein de usa on 2009-01-27
hi 
you might want to check this out helped me

[http://littlergirl.googlepages.com/NvidiaDriverHowTo.html]("http://littlergirl.googlepages.com/NvidiaDriverHowTo.html")

---

### Post by minsf on 2009-01-27
could you post here the output of ```
dpkg -l |grep nvidia
```

---

### Post by age99 on 2009-01-28
I had a look at the Synaptic Package Manager and there were a bunch of modules installed, none that appeared to have anything to do with NVIDIA.  I know that my Broadcom wireless card also has restricted drivers.
I followed the instructions as per Klein's link, but it still resulted in the same issues.  I re-start the X-server, but it doesn't pick up the NVIDIA driver.  If I try to use the NVIDIA-settings, it will not allow me to do anything because it says that I do not have an NVIDIA X server running.

Here is the output from dpkg -l |grep nvidia


ii  nvidia-173-modaliases                      173.14.12-1-0ubuntu4                    Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-177-kernel-source                   177.82-0ubuntu0.1                       NVIDIA binary kernel module source
ii  nvidia-177-modaliases                      177.82-0ubuntu0.1                       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-71-modaliases                       71.86.04-0ubuntu10                      Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                       96.43.09-0ubuntu1                       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                              0.2.4                                   Find obsolete NVIDIA drivers
rc  nvidia-glx                                 1:96.43.05+2.6.24.14-21.51              NVIDIA binary XFree86 4.x/X.Org driver
rc  nvidia-glx-173                             173.14.12-1-0ubuntu4                    NVIDIA binary Xorg driver
ii  nvidia-glx-177                             177.82-0ubuntu0.1                       NVIDIA binary Xorg driver
rc  nvidia-glx-new                             169.12+2.6.24.16-23.56                  NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1+nmu2ubuntu2                  NVIDIA binary kernel module common files
ii  nvidia-settings                            177.78-0ubuntu2.1                       Tool of configuring the NVIDIA graphics driv

---

### Post by minsf on 2009-01-28
according to the dpkg output, it seems that your system used to have some nvidia-glx packages, which has been removed, but not purged. the "rc" before them means that they have been r-emoved but they are still c-onfigured. i dont know if this is the reason for oyur problem, but i am pretty sure that it is healthy for oyur system to completely purge them, if you are installing the 180.22 driver directly from nvidia. 

also, if you are trying to install or already installed 180.22, i do not see why you should still have nvidia-glx-177 installed on your system, so i recommend purging it too.

bottom line, please run
```
sudo apt-get purge nvidia-glx nvidia-glx-173 nvidia-glx-177 nvidia-glx-new nvidia-177-kernel-source
```

---

### Post by minsf on 2009-01-28
rather than removing all the restricted modules (maybe your system needs some of them for broadcom) i suggest to just black list them in the file
/etc/default/linux-restricted-modules-common
you will have to edit this file with root permissions
```
sudo nano /etc/default/linux-restricted-modules-common
```
there should be a line like 
```
DISABLED_MODULES=""
```
to which you add nv or any other driver that you dont want, like this
```
DISABLED_MODULES="nv nvidia_new"
```

After you make these changes and, say, reboot, please post here the output of the "dpkg -l |grep nvidia" again and also the output of:
```
sudo lshw -C display
```
cheers :)

---

### Post by stchman on 2009-01-28
> **age99 said:**
> Hi,
I tried to upgrade my NVIDIA driver to version 180.22.  I got this to work temporarily and I had all the settings I wanted, but every time I rebooted, I was told that "Ubuntu is running in low-graphics mode" and for some reason, none of my settings remained.  It seems to be over-writing my xorg.conf file each time I reboot.  

How do I maintain my settings?

Should I be re-installing the NVIDIA driver?  

I downloaded the driver from [www.nvidia.com](www.nvidia.com), shut down the gdm, ran the installation program.

Any help will be appreciated.

What kind of nvidia card do you have?  The Hardware Driver section ususally makes the best choice.

---

### Post by age99 on 2009-01-28
Hi,
I have the GeForce 8400M GS NVIDIA driver, running on a dual-boot Dell XPS M1330.
I opened up the /etc/default/linux-restricted-modules-common file and it already had the nv and nvidia-new blacklisted.
The output from sudo lshw -C display:
>  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GeForce 8400M GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

I tried to uninstall all NVIDIA files, and re-install 180.22 driver, but now it is telling me that "CC version check failed" and my compiler versions are incompatible.  I tried to temporarily backtrack my compiler with:
```

CC=gcc-4.2
export CC

```
But that didn't seem to do anything.

---

### Post by age99 on 2009-01-28
I sorted out the compiler and kernel issues.  I was not running the lastest installed version.  I was able to re-install the 180.22 driver by CNTRL-ALT-F1, stop the gdm, and installing the downloaded driver.  The installation ran fine, and updated the xorg.conf file, but upon reboot, the same problem: Ubuntu is running in low-graphics mode

Any other suggestions?

---

### Post by minsf on 2009-01-28
i hate to ask you again for the output of "sudo lshw -C display", but last time you posted it was before you sorted out the compilation problems, and that output clearly show that the driver is not in use.
so just to verify that the installation indeed went fine and you are running with that driver, would you please post it again and not hate me?
LOL
also, i want to be sure that the nvidia-glx packages are not around. have you purged them? could you post the output of "dpkg -l|grep nvidia" after the purge?
one important thing to keep in mind that the compilation of that driver depends on the packages linux-headers-XXX gcc build-essential pkg-config and xserver-xorg-dev. at least, that's what the nvidia folks say on their forums. so if before a compiling the driver, one should run
```
sudo apt-get install linux-headers-$(uname-r) gcc pkg-config build-essential xserver-xorg-dev
```

also are you sure that the correct resolution is specified in the Screen section of /etc/X11/xorg.conf? i know it's trivial- just checking to be sure

---

### Post by age99 on 2009-01-30
Ok, I was able to sort out the installation, finally.  Part of my problem stemmed from the fact that I had not been using the updated Ubuntu kernels.  So, I updated the grub menu.lst, and started ubuntu properly, then uninstalled all NVIDIA components that I could find using Synaptic.  Then I CNTRL-ALT-F1 to the prompt, stopped the gdm, then ran
```
sudo sh Nvidia*.run
```
and followed the instructions.  After restarting the X server, it ran great.

Thanks everyone for your help.

---

### Post by minsf on 2009-01-30
glad to hear it finally worked.
enjoy!

---

### Post by emid on 2009-01-30
> **age99 said:**
> Ok, I was able to sort out the installation, finally.  Part of my problem stemmed from the fact that I had not been using the updated Ubuntu kernels.  So, I updated the grub menu.lst, and started ubuntu properly, then uninstalled all NVIDIA components that I could find using Synaptic.  Then I CNTRL-ALT-F1 to the prompt, stopped the gdm, then ran
```
sudo sh Nvidia*.run
```
and followed the instructions.  After restarting the X server, it ran great.

Thanks everyone for your help.

How do you update the grub menu.lst?  I have what seems to be the exact same problem with being stuck in low-graphics mode.  I just noticed that although I installed the latest kernel, it isn't available for seleciton when I reboot my system.

---

### Post by emid on 2009-01-30
Never mind I figured it out. I ended up doing it manually.  After booting up with the newest kernel and reinstalling the driver, everything works as it should. :D

---

