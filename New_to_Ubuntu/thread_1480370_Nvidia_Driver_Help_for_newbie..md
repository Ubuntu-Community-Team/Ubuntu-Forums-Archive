---
title: "Nvidia Driver Help for newbie."
date: 2010-05-11
forum: New to Ubuntu
---

### Post by kornfan on 2010-05-11
Hello, 

I need some help installing drivers for an Nvidia 210 graphics card. I know absolutely nothing about Linux. I have already downloaded the drivers however i get the following error when trying to install them.

Could not open the file /home/linuxuser/Desktop/…ux-x86-195.36.24-pkg1.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

The Nvidia website gave some instructions on how to go about doing this but they are geared toward someone with more experience than i have.

Any help would be greatly appreciated.

System info:
Ubuntu Linux (unknown version)
Gnome Interface (Version 2.26.1)

If you need more info plz ask and if possible give directions on how to find it.
Thank you and have a great day.

---

### Post by dv3500ea on 2010-05-11
Go to System -> Administration -> Hardware Drivers
It will automatically locate the correct driver to download and install.

If that doesn't work, you can go to System -> Administration -> Synaptic Package Manager and search for [nvidia-current]("apt:nvidia-current") which you can install.

---

### Post by quadproc on 2010-05-11
> **kornfan said:**
> Hello, 

I need some help installing drivers for an Nvidia 210 graphics card. I know absolutely nothing about Linux. I have already downloaded the drivers however i get the following error when trying to install them.

Could not open the file /home/linuxuser/Desktop/…ux-x86-195.36.24-pkg1.run.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

It appears that you selected (perhaps implicilty) the editor _gedit_ when you tried to do something with the .run file.  If that .run file is typical of a driver installation file then it contains an initial script followed by lots of compressed data.  The editor saw the compressed data and did not know what to do with it so it produced an error message.

The usual way to install a downloaded .run file for a driver is: make a directory for the driver installation process, move the downloaded file to that directory, change your working directory to that one, set the execute permission bit on the file, then find out which shell the file needs.  To do that, try head -n 20 <the_name_of_the_downloaded_file>.  If the file was written well then you should find a line that says something like "Use /bin/sh to unpack this file".

Assuming that the file expects sh (as opposed to bash) then enter "sudo sh <the_name_of_the_downloaded_file> otherwise substitute bash for sh in the command.

This will start the default installation procedure.  After it finishes then you will need to restart the X server before the new driver will be used; a reboot will work.  If it fails to boot then you will probably need to use the recovery version of the operating system to uninstall the driver.

quadproc

---

### Post by kornfan on 2010-05-12
To dv3500ea: I opened the Synaptic Package Manager and searched for Nvidia-current. It brought up a long list of possible options. Do i need to list all possibilities here or is there a specific one im looking for?

To quadproc: i appreciate your information but i didn't understand anything u were talking about. As i stated, i know nothing about Linux. The only reason i am on this forum is because my friend needed a new graphics card for his computer which is running linux.

Thank you both for taking the time to respond. I really do appreciate the help.

---

### Post by IndyGunFreak on 2010-05-12
What version of Ubuntu are you using?  I know you said you didn't know, but it's near impossible to really help you without knowing.

Open a terminal and type or copy/paste this, then hit enter.

lsb_release -a

IGF

---

### Post by kornfan on 2010-05-12
I am using Ubuntu 9.04

---

### Post by IndyGunFreak on 2010-05-12
OK... Did you try the suggestion earlier, of going to System/Admin/Hardware Drivers ?  It might have been called "Restricted Driver Manager" in 9.04(which by the way, support will expire for in about 5mo).

What happened when you tried to activate the Driver?

IGF

---

### Post by kornfan on 2010-05-12
I did try that suggestion and it searched for drivers then popped up a window that says No proprietary drivers are in use on this system.

I tried the second suggestion of using the Synaptic package manager and got many choices.

---

### Post by IndyGunFreak on 2010-05-12
> **kornfan said:**
> I did try that suggestion and it searched for drivers then popped up a window that says No proprietary drivers are in use on this system.

I tried the second suggestion of using the Synaptic package manager and got many choices.

How new is this video card?  

Open a terminal and type "lspci" no quotes and hit enter, and post the output.  

If I were you, I'd try downloading the Ubuntu 10.04 live CD, and see if it does a better job of recognizing the device.

---

### Post by kornfan on 2010-05-12
I bought it brand new a few days ago. It is a geforce 210. Didn't need anything fancy just needed a working card as there is no onboard graphics. The output is as follows.

00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a65 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)

---

### Post by SpongeBob SquarePants on 2010-05-12
[QUOTE=kornfan;9285468]I did try that suggestion and it searched for drivers then popped up a window that says No proprietary drivers are in use on this system./QUOTE]

It always says "No proprietary drivers are in use on this system". That's because you haven't enabled any yet. Look at the list in "Hardware Drivers" and choose the one with "recommended" after it. Then press activate. It will then download the driver and install it automatically.

---

### Post by IndyGunFreak on 2010-05-12
> **SpongeBob SquarePants said:**
> [QUOTE=kornfan;9285468]I did try that suggestion and it searched for drivers then popped up a window that says No proprietary drivers are in use on this system./QUOTE]

It always says "No proprietary drivers are in use on this system". That's because you haven't enabled any yet. Look at the list in "Hardware Drivers" and choose the one with "recommended" after it. Then press activate. It will then download the driver and install it automatically.

Most likely there's no driver to enable.  Otherwise, he would have saw suggestions to enable a driver..

---

### Post by kornfan on 2010-05-12
There was nothing else. Just what i put in my reply.

---

### Post by lkraemer on 2010-05-12
The Nvidia Drivers Version:
195.36.24 Certified
Release Date:  2010.04.28
Operating System: Linux

Support the following 2xx series:

GeForce 200 series:
GT 240, GTX 285, GT 220, GTX 275, 210, GTX 260, GTX 295, GT 230, G210, GTS 240, GTX 280, GTS 250, 205

GeForce 200M series:
GT 240M, GTX 280M, GT 230M, GT 220M, G210M, GTS 260M, GTX 260M, GTX 285M

Ref:
[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

Information for the install:
Installation instructions: Once you have downloaded the driver, change to the directory containing the driver package and install the driver by running, as root, sh ./NVIDIA-Linux-x86-195.36.24-pkg1.run

One of the last installation steps will offer to update your X configuration file. Either accept that offer, edit your X configuration file manually so that the NVIDIA X driver will be used, or run nvidia-xconfig

See the README for more detailed instructions.

lk

---

### Post by Kosimo on 2010-05-12
I've written an easy how-to that seems to work well for many users, you can have a look here:

**How to Install nvidia drivers in Ubuntu**
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by 3rdalbum on 2010-05-12
The Geforce GT210 came out well after Ubuntu 9.04, so in this case you must use the download from the Nvidia website.

First, use Synaptic Package Manager to install the 'build-essential' and 'linux-headers-generic' packages. Make sure the Nvidia driver installer is **directly** in your home directory (NOT on your desktop or any subfolders).

Second, log out. When you are at the login screen, press Control-Alt-F1. This brings up a text terminal.

Log into this terminal using your normal login details and type these commands:

```
sudo killall gdm
sudo chmod a+x NVID<press Tab to autocomplete this>
sudo ./NVID<press Tab to autocomplete this>
```

When the installation is done, type:

```
sudo reboot
```

Note that you'll need to do all these steps each time you update your kernel - sorry, but the Linux community has been asking Nvidia to improve its driver.

---

### Post by kornfan on 2010-05-12
The home directory is just the folder that says is called Home correct?

---

### Post by 3rdalbum on 2010-05-12
> **kornfan said:**
> The home directory is just the folder that says is called Home correct?

Yes.

---

