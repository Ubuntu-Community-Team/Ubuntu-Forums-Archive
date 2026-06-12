---
title: "cant install restricted nvidia driver, stuck at 0%"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by WinterMadness on 2009-10-10
anyone know why?

I goto system>admin>hardware drivers and my video card shows up, and i goto activate it and its stuck at zero.

---

### Post by cariboo on 2009-10-10
You didn't sav what version you where using, but Jaunty doesn't indicate that it is downloading the needed packages. The repositories have been kind of slow since the Karmic beta came out, so it may take a while to download the drivers. The progress bar doesn't start moving until the drivers have been downloaded. Be patient, it just may take a while.

---

### Post by WinterMadness on 2009-10-10
yeah its jaunty, thanks for the info ill leave it go for a bit

---

### Post by WinterMadness on 2009-10-10
"sorry the jockey backend crashed"

happens every time, is there a way to do this via the command line or something?

im trying to install the nvidia accelerated graphics driver version 180

---

### Post by WinterMadness on 2009-10-10
anyone?

---

### Post by mick55 on 2009-10-10
hi

Try installing through the terminal.

Install nvidia drivers

```
sudo apt-get install nvidia-glx-180
```Run nvidia config

```
sudo nvidia-xconfig
```After a reboot you should be running the Nvidia driver.

Let me know how it works out.

cheers
mick

---

### Post by WinterMadness on 2009-10-10
```

joe@joe-laptop:~$ sudo apt-get install nvidia-glx-180
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libscrollkeeper0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dkms fakeroot nvidia-180-kernel-source nvidia-180-libvdpau nvidia-settings
  patch
Suggested packages:
  diff-doc
The following NEW packages will be installed:
  dkms fakeroot nvidia-180-kernel-source nvidia-180-libvdpau nvidia-glx-180
  nvidia-settings patch
0 upgraded, 7 newly installed, 0 to remove and 153 not upgraded.
Need to get 0B/13.5MB of archives.
After this operation, 39.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)'
in the drive '/cdrom/' and press enter

```

very odd, i dont have the disc anymore and why would i need it

---

### Post by ConXtionS on 2009-10-10
I noticed it took mine ALONG TIME to download today

---

### Post by WinterMadness on 2009-10-10
ok I got it to work. I just tried it in KPackageKit and the first time it failed, the second time it worked.

Even synaptic asked me for a disc. thats really weird.

---

### Post by mick55 on 2009-10-10
Glad it worked.

Check your software sources to make sure the "install from  
cd-rom" is not checked as a choice.

in Ubuntu the path is

system->administration->software sources

I am not familiar with the Kubuntu desktop, hopefully
you can find it:)

cheers
mick

---

### Post by jobsworth on 2009-10-25
mick55 you are great.
I have been stuck for a long time on this one.

Your solution System>Adminstration>Software Sources
uncheck "Installable from CD ROM/DVD"
seems so obvious when you know how.

I guess an install from cd could work
only the cd is mounted in /media and not in /cdrom,
where it expects to find it.

There must be a way to tell ubuntu where is the the cd
'cos the download for something which may already be on the cd
takes forever.

---

