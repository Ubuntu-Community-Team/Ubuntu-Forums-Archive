---
title: "How to install NVIDIA-Linux-x86_64-185.18.36-pkg2.run (video driver)"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by chris1950 on 2009-09-08
Could not get Screen Effects to work UE 2.3 installs the 180 verion so I downloaded the latest driver from NVIDIA 185 version. When download finished I had two files.

/home/chris/Downloads/NVIDIA-Linux-x86_64-185.18.36-pkg2.run
/home/chris/Downloads/NVIDIA-Linux-x86_64-185.18.36-pkg2.run:Zone.Identifier

Tried various commands but could not get it to install.:confused:

Help please, Thanks in advance

---

### Post by 3rdalbum on 2009-09-08
The 180 version should definitely work with your card. Did you restart after installing the driver and before trying to activate Desktop Effects?

This is the summary of installation instructions from the Nvidia website (the page where you download the driver):

> Installation instructions: Once you have downloaded the driver, change to the directory containing the driver package and install the driver by running, as root, sh /home/chris/Downloads/NVIDIA-Linux-x86_64-185.18.36-pkg2.run

(I added in your full directory path).

You first need to install the kernel headers package for your kernel (the "linux-headers-generic" package from the repositories, if your system is up-to-date) and a build environment ("build-essential"). Before running that command as well, you need to quit X; logout, press Control-Alt-F1, log into that text terminal and run these commands:

```
sudo killall gdm
sudo /home/chris/Downloads/NVIDIA-Linux-x86_64-185.18.36-pkg2.run
(the installer will run, and when it's finished)
sudo gdm
```

---

### Post by chris1950 on 2009-09-08
> **3rdalbum said:**
> The 180 version should definitely work with your card. Did you restart after installing the driver and before trying to activate Desktop Effects?

This is the summary of installation instructions from the Nvidia website (the page where you download the driver):



(I added in your full directory path).

You first need to install the kernel headers package for your kernel (the "linux-headers-generic" package from the repositories, if your system is up-to-date) and a build environment ("build-essential"). Before running that command as well, you need to quit X; logout, press Control-Alt-F1, log into that text terminal and run these commands:

```
sudo killall gdm
sudo /home/chris/Downloads/NVIDIA-Linux-x86_64-185.18.36-pkg2.run
(the installer will run, and when it's finished)
sudo gdm
```


The 180 driver worked with desktop effects when I had Jaunty installed but the effects do not work in UE 2.3. As far as I know my system has had all the updates completed after the install (about 180+ files)

Sorry I missed the instructions on Nvidia's site as I was only looking for the driver download button:(, will be more careful in the future.

Thanks for the info, will do the code shortly so will be off line, will let you know how it when when I get back.

---

### Post by chris1950 on 2009-09-08
Sorry, not work. First I closed all open windows, then ctrl+alt+F1. In the terminal cd / to get root level, then sudo killall gdm (this worked), then sudo /home...... (error- file not found), then sudo sh /home...... (error - can not open NVIDA.......),  then cd to Downloads and tried both commands again got nsame errors, finally sudo gdm to exit.

---

### Post by oldos2er on 2009-09-08
There's a ppa for Nvidia 185 video drivers. Howto: [http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

---

### Post by cookie9001 on 2009-09-08
Hi, Im having the same problems, Ive tried all that you have and also tried the ppa and nothing works, I am completely new to Linux and have very little computer experience other than using microsoft. can anyone offer any further advice?

---

### Post by PunkLV on 2009-09-08
Try this, or wait for the next post which points out mistakes I've made.

System -> Administration -> Hardware Drivers
Select [Recomended]
Apply
Reboot

CTRL+ALT+F1
login
```
sudo apt-get install gcc
sudo nano /etc/default/linux-restricted-modules-common
```
change DISABLED_MODULES="" to DISABLED_MODULES="nv"
```
sudo apt-get remove --purge nvidia
```
```
sudo /etc/init.d/gdm stop
sudo sh /home/chris/Downloads/NVIDIA-Linux-x86_64-185.18.36-pkg2.run
```
Follow instructions
```
sudo nvidia-xconfig
```
Reboot

---

### Post by chris1950 on 2009-09-09
> **PunkLV said:**
> Try this, or wait for the next post which points out mistakes I've made.

System -> Administration -> Hardware Drivers
Select [Recomended]
Apply
Reboot

CTRL+ALT+F1
login
```
sudo apt-get install gcc
sudo nano /etc/default/linux-restricted-modules-common
```change DISABLED_MODULES="" to DISABLED_MODULES="nv"
```
sudo apt-get remove --purge nvidia
``````
sudo /etc/init.d/gdm stop
sudo sh /home/chris/Downloads/NVIDIA-Linux-x86_64-185.18.36-pkg2.run
```Follow instructions


```
sudo nvidia-xconfig
```Reboot

Not work see errors-
DISABLED_MODULES=nv --file not found
sudo apt-get remove --purge nvidia (NVIDIA) tried both - package not found
sudo sh /etc/....... can not open

---

### Post by Perfect Storm on 2009-09-09
I don't think it's needed to disable the nv driver, and it's good to have as a backup driver if the nvidia fails.


Instead of reboot do a 

```
sudo /etc/init.d/gdm start
```
No need for reboot here.


Note when you manually install the the driver; when the kernel get patched or upgraded you need to install the nvidia driver again.

---

### Post by shae on 2009-09-09
Follow the following site's instructions to run Compiz Check.  This will help tell us why your effects will not run.  Please post its output.  [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by PunkLV on 2009-09-09
> I don't think it's needed to disable the nv driver, and it's good to have as a backup driver if the nvidia fails.

Well, that is true, however, since I've had some really terrifying experience in the past with nvidia drivers, w/o any access to Internet and being completely new to linux; now I disable "nv" module, to be sure that the Nvidia driver works and everything is fine, enabling it later on, usually, lol.

---

### Post by chris1950 on 2009-09-11
After trying so many things with no luck I reinstalled, updated everything, activated the 180 driver, rebooted, then enabled effects , it worked fine. Don't know what happened the first time causing it not to work as I did everything the same way????

---

### Post by Gregz on 2009-09-11
I have installed seems to work fine except:

I cannot save xconfig file, I have to reset display setting's(starts in 800x600) every reboot.

It say's cannot remove back-up config file....

Also not really important is I get no splash screen on boot...

---

### Post by NoaHall on 2009-09-11
You have to run it as "gksudo nvidia-settings"

---

