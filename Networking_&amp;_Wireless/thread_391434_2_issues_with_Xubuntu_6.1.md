---
title: "2 issues with Xubuntu 6.1"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by drumkitcat on 2007-03-23
Hi,

I've installed Xubuntu 6.10 on my daughter's desktop computer, and it installed perfectly fine.

her computer spec's are as follows:
AMD K6-2/450 Mhz with 392Mb Ram, 40Gb Hard drive, Atheros AR5212 wireless PCI adapter

Here are my two issues, that I need help with:

1. Atheros AR5212 adapter - when I do "lspci" it shows up as exactly that with the rev number etc... however when I do a "iwconfig" all that shows up is "lo" and no "ath0" or "wifi0" listings... why?  how do I get it to show up.. the software knows there's an Atheros wireless pci adapter present, but how do I get it to create that as ath0 - in the networking section, all that is listed is the modem, no wireless adapters at all..  help please!?

2. Second issue - installing Madwifi.  I have downloaded the latest Madwifi, tarball file, and tried to install it.  The error I get is something to the effect of "cannot determine kernel type..." or "kernel path not found/set" - It does have the latest kernel (sorry not at computer now) - how do I correct that?

If anyone can offer help, I'd really appreciate it.  thanks

---

### Post by drumkitcat on 2007-03-23
any ideas from anyone?

---

### Post by josephus on 2007-03-23
I don't know if I'm pointing you in the right direction, but have you downloaded the linux kernel header files before trying to compile the madwifi sources?

---

### Post by josephus on 2007-03-23
Also check if the driver is properly loaded onto your system.

```
lsmod
```

On my system I see ath_pci, I'm not what is needed for wireless to work properly.  If it's not loaded you can use modprobe to add new modules.

---

### Post by drumkitcat on 2007-03-28
thanks... I did try modprobe with no luck.. it comes back saying command not found.

ath_pci results in a message saying something like device does not exist.

currently when I do the lspci, it does show the Atheros wireless adapter, but when I do the iwconfig, all that shows up is "lo" - no ath0, no wifi0, no eth0 (of course, there's no ethernet card installed, only the Atheros wireless one".

It looks like I will have to connect the box to the internet using an ethernet card to get the Linux Kernel Headers installed as I have no other way of doing that - I have a cd of the operating system, but when I try and install the Linux headers, it attempts to go online to get them and not to the cd.

Hope that makes sense... if you or anyone can offer any other suggestions, I'd appreciate it.

thanks very much!
Paul

---

### Post by maxamillion on 2007-03-28
> **drumkitcat said:**
> Hi,

I've installed Xubuntu 6.10 on my daughter's desktop computer, and it installed perfectly fine.

her computer spec's are as follows:
AMD K6-2/450 Mhz with 392Mb Ram, 40Gb Hard drive, Atheros AR5212 wireless PCI adapter

Here are my two issues, that I need help with:

1. Atheros AR5212 adapter - when I do "lspci" it shows up as exactly that with the rev number etc... however when I do a "iwconfig" all that shows up is "lo" and no "ath0" or "wifi0" listings... why?  how do I get it to show up.. the software knows there's an Atheros wireless pci adapter present, but how do I get it to create that as ath0 - in the networking section, all that is listed is the modem, no wireless adapters at all..  help please!?

2. Second issue - installing Madwifi.  I have downloaded the latest Madwifi, tarball file, and tried to install it.  The error I get is something to the effect of "cannot determine kernel type..." or "kernel path not found/set" - It does have the latest kernel (sorry not at computer now) - how do I correct that?

If anyone can offer help, I'd really appreciate it.  thanks


1) check the modules and make sure you are using "sudo" when trying to modprobe

Also, do "ifconfig -a" and see if the networking device is seen and just not up/configured and if so do ```
sudo ifup <interface_name>
```

2) you might need to install the kernel headers which are available in the package "linux-kernel-headers" otherwise its possible that you just don't have a path set to your kernel directory


.... hope this helps

---

### Post by drumkitcat on 2007-03-28
> **maxamillion said:**
> 1) check the modules and make sure you are using "sudo" when trying to modprobe

Also, do "ifconfig -a" and see if the networking device is seen and just not up/configured and if so do ```
sudo ifup <interface_name>
```

2) you might need to install the kernel headers which are available in the package "linux-kernel-headers" otherwise its possible that you just don't have a path set to your kernel directory


.... hope this helps


Thanks, I will try that -  I do know however that there is an issue with the path to the kernel directory (which I checked and does exist currently) - I'm hoping that by installing the headers again that will fix it.. I hope.

---

### Post by josephus on 2007-03-28
is there a particular reason why you are downloading madwifi from source?  have you tried installing the linux-restricted-modules from the repository? they include a relatively recent set of madwifi drivers.

---

### Post by drumkitcat on 2007-03-29
> **josephus said:**
> is there a particular reason why you are downloading madwifi from source?  have you tried installing the linux-restricted-modules from the repository? they include a relatively recent set of madwifi drivers.

Oh, really?  I didn't know that!  
Then again, I don't know what the repository is either... unless that's what I get when I am able to get online with a wired ethernet card and do an update (which I haven't had a chance to do yet)

It would be nice if those files were available on the cd.... it would be i-deal if when I entered the "sudo apt-get update" command it would first look for the cd before just attempting to go to the website.

I really had no idea.

---

### Post by josephus on 2007-03-29
if you are able to get online through a wired connection you should either use the command line apt-get ... or use synaptic to get the needed module.  I find that synaptic is much easier to use than the command line, as I don't have remember the exact names of different modules and can just search for them.

You have to make sure that the restricted repository is included.  In synaptic there is an option to add/remove repositories that it looks through.  I can't remember if there is a check box for the restricted libraries on a fresh install of edgy, but if not just add:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted

It would be nice if this was included on the live cd, and I think that in the Feisty it actually is included.

---

### Post by drumkitcat on 2007-03-29
> **josephus said:**
> if you are able to get online through a wired connection you should either use the command line apt-get ... or use synaptic to get the needed module.  I find that synaptic is much easier to use than the command line, as I don't have remember the exact names of different modules and can just search for them.

You have to make sure that the restricted repository is included.  In synaptic there is an option to add/remove repositories that it looks through.  I can't remember if there is a check box for the restricted libraries on a fresh install of edgy, but if not just add:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted

It would be nice if this was included on the live cd, and I think that in the Feisty it actually is included.

Ok, thanks very much! I'll try that out!  

I also prefer using Synaptic Package Manager as it works very well for doing the downloading and installation immediately whereas on the command line I find it's easy to mess up commands and not have things installed properly or at all....

---

