---
title: "error on installing"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by kapi on 2008-12-31
Hi, wondered if anyone knew what the message below means:

E: msttcorefonts: subprocess post-installation script returned error exit status 1

many times when I try to use the synaptic package manager I get this message 

Is there something wrong with my initial install or is it easily fixed?

Thanks for your help

kapi

---

### Post by taurus on 2008-12-31
What happens when you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo dpkg --install -f 
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kapi on 2008-12-31
Hi Taurus,

thanks for replying. basically when I input the commands to the terminal the first command did not work and I got a menu of possible commands to use

second command tried to execute data from the iso cd rom but got this message

"W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs"

regards 

kapi

---

### Post by kapi on 2008-12-31
Also I don't know if it has any significance but the update manager seems to be knackered too its stuck at 165 days ago and when I try to update it says the reposistory is unavailable

kapi

---

### Post by taurus on 2008-12-31
So into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and remove the check mark for the Cdrom.  Click Close and shut down synaptic.  

Now, run these two commands from a terminal and see what happens.

```
sudo apt-get update
sudo apt-get upgrade
```
If there is an error message, post the whole message here.

---

### Post by kapi on 2009-01-01
Hi Taurus, 

right I uninstalled the cd rom as suggested and input the commands. the system appeared to dowload a few updates from a server, then I got this message at the end of the process:

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

