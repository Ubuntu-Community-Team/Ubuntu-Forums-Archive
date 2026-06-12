---
title: "nvidia has me crying (8.10; gforce go)"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-04-07
I have an Nvidia card that should be compatible with the newest version of the nvidia driver...

Yet I have installed the 180 version of the nvidia driver, and nothing works. I'm in low graphics mode...

I uninstalled everything related to nvidia; then reinstalled it... Nothing. 
I get the following errors in my boot up:
nouveau... failed
nvidia 180... failed

Someone please help me - I'm frustrated with myself...

---

### Post by Crafty Kisses on 2009-04-07
Here try this, once you have downloaded the proper NVIDIA driver you need to stop your X server, so press Cntrl-Alt-F2. Once you have done that you need to run the following:
```
sudo /etc/init.d/gdm stop
```
Then once you've done that you need to run the following, remember I'm just guessing the file is called NVIDIA-Linux and it's saved to your desktop, so remember substitute your information:
```
cd ~/Desktop
chmod +x NVIDIA-Linux.run
sudo ./NVIDIA-Linux.run

```
Once the installation is done, restart the X server with:
```
sudo /etc/init.d/gdm start

```

---

### Post by chilimac02 on 2009-04-07
I have tried that, found a tutorial suggesting the same thing. When I ran the file it gave me an error message.

---

### Post by chilimac02 on 2009-04-08
more specifically, the error is:

unable to find kernel source tree... it says to make sure the source files are installed... ???

-Justin

---

### Post by ibuclaw on 2009-04-08
Get the build-essential and linux-header packages.
```
sudo apt-get install build-essential linux-headers-`uname-r`
```

First though, before setting up nvidia:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then logout and log back in again.

You are now on the default VESA drivers, so Compiz+Other Composite features will be disabled.

First things first, to ensure that you get no conflicts, **completely remove all installed NVIDIA** packages listed in Synaptic, as New drivers/Old drivers will cause API conflicts that will prevent X from starting.
(Or, CLI way):
```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```

Next, if you are on **32bit Ubuntu**, download these drivers:
```
wget ftp://download.nvidia.com/XFree86/Linux-x86/185.19/NVIDIA-Linux-x86-185.19-pkg1.run
```
**64bit Ubuntu**, get these instead:
```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/185.19/NVIDIA-Linux-x86_64-185.19-pkg2.run
```
And move it to a place you can retrieve later:
```
sudo install NVIDIA-Linux-*185.19*.run /usr/src
```
Next, logout and switch to another tty console ( **Ctrl+Alt+F1** ).

Login to the shell, and kill gdm:
```
sudo /etc/init.d/gdm stop
```
This will take a while. Afterwards, install the drivers.
```
sudo sh /usr/src/NVIDIA-Linux*.run
```
Follow the instructions, and everything should be fine (don't worry about pre-compiled binaries, just let the script compile the drivers itself).

Once finished, reboot:
```
sudo reboot
```

Hopefully, that should resolve your issue, albeit, with a brand new Logo that you can remove by issuing:
```
sudo sed -i '/Driver\s*.nvidia./a\    Option         "NoLogo" "True"' /etc/X11/xorg.conf
```

Although, now with custom compiled nvidia modules, you'll have to ensure that you keep up-to-date whenever a new kernel gets released.
Follow this thread to set it up: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Regards
Iain

---

### Post by ftabor on 2009-04-08
I just did the auto upgrade to the version 180 driver and it killed my video.  It booted into a black screen.  I had to boot into recovery, run fix x and then reboot and reinstall the version 173 driver.  

Will the above work here also?  HP Pavillion GeForce 7150M / nForce 630M on Ubunto 8.10.

Thanks

---

### Post by Nepherte on 2009-04-08
Note that 185.19 are beta drivers. The latest stable version is 180.44

---

### Post by starcannon on 2009-04-08
> **ftabor said:**
> I just did the auto upgrade to the version 180 driver and it killed my video.  It booted into a black screen.  I had to boot into recovery, run fix x and then reboot and reinstall the version 173 driver.  

Will the above work here also?  HP Pavillion GeForce 7150M / nForce 630M on Ubunto 8.10.

Thanks

I had the same result with a clean install of 8.10 on twin Nvidia 7950gt's using the 177 and 180 drivers. My solution was to revert to 8.04 with the 177 drivers, even in 8.04 the 180 drivers were a no go.

My wife's and my mom's laptops with the Nvidia 8400m gs gpu have had no issues in Ubuntu 8.10.

I think this is in part the new xserver, and in part the 180 drivers; combined with 7xxx cards, and it needs fixed. I can not keep buying the latest nvidia cards, it gets to expensive, they (Nvidia) is simply going to have to be more careful with their backwards compatability in the future.

---

### Post by Jakey_TheSnake on 2009-04-08
I'm pretty sure with nVidia you need the Catalyst Control Center to do anything somewhat advanced...

EDIT: This is ATI, my bad, ignore me.

---

### Post by ibuclaw on 2009-04-08
> **starcannon said:**
> I had the same result with a clean install of 8.10 on twin Nvidia 7950gt's using the 177 and 180 drivers. My solution was to revert to 8.04 with the 177 drivers, even in 8.04 the 180 drivers were a no go.

My wife's and my mom's laptops with the Nvidia 8400m gs gpu have had no issues in Ubuntu 8.10.

I think this is in part the new xserver, and in part the 180 drivers; combined with 7xxx cards, and it needs fixed. I can not keep buying the latest nvidia cards, it gets to expensive, they (Nvidia) is simply going to have to be more careful with their backwards compatability in the future.
You situation is far greater than a simple "it works" or "it doesn't work".
Taking that small bit of effort into finding out why X won't start and working around it using what utils you have at your dispense so you can work around it can go a long way, even if there is a small learning curve or eye training involved.

In the event that it doesn't work, switch to a tty console, login, and:
**1)**
```
grep "^(EE)" /var/log/Xorg.0.log"
```
This will tell you if there are any errors with your **/etc/X11/xorg.conf** file.

If there is an error emitted, for example:
> (EE) Failed to load module "type1" (module does not exist, 0)
The module **type1** doesn't exist on your system, to fix, ensure that you have removed any previous driver if you've upgraded, and re-install/reboot your computer.
If the problem still persists, open up your xorg.conf file and remove the line which references it.

**2)**
```
grep -i "nvidia\|NVRM" /var/log/syslog.0
```
If the Xorg.log errors are vague, this will tell you exactly what the problem is:

Another example of a typical error:
> 
Apr  7 23:03:57 intrepid kernel: [79531.760530] NVRM: API mismatch: the client has the version 185.19, but
Apr  7 23:03:57 intrepid kernel: [79531.760531] NVRM: this kernel module has the version 177.82.  Please
Apr  7 23:03:57 intrepid kernel: [79531.760532] NVRM: make sure that this kernel module and all NVIDIA driver
Apr  7 23:03:57 intrepid kernel: [79531.760534] NVRM: components have the same version.

We have 2 versions of the same driver in conflict!
Usually this is because the old one is still in cache, or hasn't been rmmod'd yet. But in most cases, if a reboot doesn't solve it, then again, make sure you have removed all installed nvidia references with "--purge"
```
sudo apt-get --purge remove **package-name**
```
and then reinstall the driver again.


Don't like working with a GUI?
```
sudo dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm start
```
And your desktop will load with the defaulted failsafe drivers.

Regards
Iain

---

### Post by chilimac02 on 2009-04-08
in response to tinivole's first command:
I got this error
E: Couldn't find package linux-headers-uname-r

Did I miss something?

This is what happens:
justin@justin-laptop:~$ sudo apt-get install build-essential linux-headers-`uname-r`
bash: uname-r: command not found
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
Package linux-headers is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nouveau-kernel-source (0.0.11+git20090404-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: nouveau-0.0.11+git20090404
You cannot add the same module/version combo more than once.
dpkg: error processing nouveau-kernel-source (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 nouveau-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)


thanks for caring enough about ubuntu to help us noobs...

---

### Post by hovzio on 2009-04-08
> **chilimac02 said:**
> in response to tinivole's first command:
I got this error
E: Couldn't find package linux-headers-uname-r

Did I miss something?

This is what happens:
justin@justin-laptop:~$ sudo apt-get install build-essential linux-headers-`uname-r`
bash: uname-r: command not found
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
Package linux-headers is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nouveau-kernel-source (0.0.11+git20090404-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: nouveau-0.0.11+git20090404
You cannot add the same module/version combo more than once.
dpkg: error processing nouveau-kernel-source (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 nouveau-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)


thanks for caring enough about ubuntu to help us noobs...

little typo I assume :) Try this:


```
sudo apt-get install build-essential linux-headers-`uname -r`
```

EDIT: I highly recommend thoroughly following tinivole's instructions. This procedure worked well for me, just go through the steps one by one. Remember to shut off gdm when you install the drivers.

---

### Post by chilimac02 on 2009-04-08
E: Couldn't find package linux-headers-2.6.27-14-generic

is what I got from inputing the above command...

Anyone have advice on how to fix that error?

---

### Post by chilimac02 on 2009-04-08
So then, is clean install my best option? Nobody seems to want to further instruct me. I've followed all of the recommended steps, but receive errors whenever installing the nvidia driver. It ALWAYS says that it failed to find the source tree...

-Justin

---

### Post by ibuclaw on 2009-04-09
> **chilimac02 said:**
> E: Couldn't find package linux-headers-2.6.27-14-generic

is what I got from inputing the above command...

Anyone have advice on how to fix that error?

Hmm, looks to me that you are running a rather obtuse version of the Ubuntu kernel, I cannot find any reference to 2.6.27-14 anywhere, not even on my system packages list. Maybe you have hardy-backports enabled? :confused:

Try explicitly installing the **2.6.27-11** version, as that appears to be the most recent.
```
sudo apt-get install linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic linux-headers-2.6.27-11-generic
```
Then reboot install that kernel version, and remove all packages linked with the **2.6.27-14** version.

Regards
Iain

---

### Post by chilimac02 on 2009-04-09
justin@justin-laptop:~$ sudo apt-get install linux-image-2.6.27-11-generic linux-restricted-modules-2.6.27-11-generic linux-headers-2.6.27-11-generic
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
justin@justin-laptop:~$

---

### Post by hovzio on 2009-04-10
Sounds like your package manager was busy while you were trying to use it. There may only be one instance of a package manager running at one time. Were you doing updates? Otherwise it sounds (*respectfully said) like your your package manager may need a little help. Are you able to install other software?

---

### Post by ibuclaw on 2009-04-10
Run:
```
ps -el | grep "aptitude\|apt-get\|dpkg"
```
If you get any output, post what you get.

If you don't, run:
```
sudo rm /var/lib/dpkg/lock
```

Then try installing again.

Regards
Iain

---

### Post by Thorny3 on 2009-04-12
Thanks, tinivole, for pointing me in the right direction. I was able to solve my problems on GeForce 9200M GS with the latest stable drivers from nvidia.

Thor.-

---

### Post by SIlvio77 on 2009-04-16
Hi,

I've been trying to install two NVIDIA 9600GT cards for the last two days, on 8.10.
I have followed the instruction above. The drivers seem to install them self fine.
Only problem is when I reboot Ubuntu it won't go further then "Checking battery".
It's done that a couple of times and each I have reinstalled Ubuntu.
I have also gone into a tty console and tried to check but nothing comes up.

Please help I feel like throwing my machine thru the window...

---

### Post by zeex on 2009-04-16
Hi! 

[check this out]("http://stringofthoughts.wordpress.com/2009/04/03/installing-nvidia-drivers-in-ubuntu/") ...it might help
it worked on Ubuntu 8.04 may be it'll work on 8.10. 

Black screen comes because of driver conflict. nVIDIA driver and Xorg driver. Removing Xorg diver (which is installed by deafult) and then installing nVIDIA driver works.

good luck !!!

---

