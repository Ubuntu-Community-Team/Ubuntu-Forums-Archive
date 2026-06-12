---
title: "Ubuntu 9.04 jaunty ASUS cm5570 need help!"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Biomed1985 on 2009-07-14
Hello linux users! Brand new to linux and learning quickly. I just got a new computer and decided that windows just would not deliver, so here I am with ubuntu 9.04 jaunty with a gnome interface and I like what I see concerning OS functionality.

I am having some problems with 
-no audio (flash player works/no audio however)
-dual monitor configuration
- transparent windows and menus?

My system specs are as follows:
I am using an Asus CM 5570 Desktop 
With and nvidia graphics card (there are two graphics cards in this tower one of which supparting dual monitor configuration, not sure if that is the nvidia though)
and also an intel soundcard

                                 

 

 

 andy@andy-blackpearl:~$ lspci 
 00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03) 
 00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) 
 00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 
 00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 
 00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 
 00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 
 00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller 
 00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1 
 00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6 
 00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 
 00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 
 00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 
 00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) 
 00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller 
 00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller 
 00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller 
 00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller 
 01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1) 
 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01) 
 03:00.0 Network controller: RaLink RT2860 
 andy@andy-blackpearl:~$  
 

 help with these issues would be greately appreicated


thank you

---

### Post by LewRockwell on 2009-07-14
all updates installed?

all restricted drivers enabled and installed?

.

---

### Post by Biomed1985 on 2009-07-14
yep all updated and set

---

### Post by drang007 on 2009-08-30
Im having the same problem same model what was the fix.

The audio works in fedora 11 and mandriva 2009

they have the alsa drivers 1.0.20 with the alsa-plugins-pulseaudio 1.0.20

for the video card
In Kubuntu i downloaded the driver and compiled it myself

NVIDIA-Linux-x86_64-180.29-pkg2.run  works on this machine for the G100 card

i had to get compiling tools

sudo aptitude update
sudo aptitude install build-essential
i then had to get out of xserver to install

I wrote down all future commands and directorys then hit  Ctrl+Alt+F1 to get into tty1
i logged in then su to root agian

to stop xserver 

sudo /etc/init.d/gdm stop      "for gnome Ubuntu"
sudo /etc/init.d/kdm stop      "for Kde Kubuntu"

i then cd to driver dir
cd /home/download/drivers
sh Nvidia-Linux-x86_64-180.29-pkg2.run


reboot and all worked great 3d desktop and everything
if you update the kernel youll need to redo this

---

### Post by drang007 on 2009-08-30
Found this link for ppl searching this model

[http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html)

I followed this 100% restarted and sound worked

---

### Post by NoaHall on 2009-08-30
To set up dual screen - run "gksudo nvidia-settings" and enable your other moniter, and then save to the config file

---

