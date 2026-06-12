---
title: "NVIDIA on X-Server"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2009-09-18
this is the second time i'm trying to install nvidia driver on my ubuntu...

last time did it, it worked well...

first i stopped the s server...
i got the prompt and i ran the package
then i started the x server again...

but this time when i stop the x server i'm not getting  command prompt...

so i went to command prompt and stopped s server from there and then i couldnt find my package to install...

i put my package in my home folder...

i put it in desktop too...

what could be wrong??? last time my swap size was 2.5G, now its only 1G, could that be the problem???

and yes, i tried as root too... there i couldnt find my installation package...

can anyone help me please...

---

### Post by Conzo on 2009-09-18
[http://ubuntuforums.org/showthread.php?t=1216691](http://ubuntuforums.org/showthread.php?t=1216691)
Old post .. Might be helpful
 
 
Conzo

---

### Post by randolf_ambrose on 2009-09-18
> **Conzo said:**
> [http://ubuntuforums.org/showthread.php?t=1216691](http://ubuntuforums.org/showthread.php?t=1216691)
Old post .. Might be helpful
 
 
Conzo

no dude... it doesnt...

thanks anyways... :-)

---

### Post by fooman on 2009-09-18
there is a launchpad repository for nvidia.  you can add it to your /etc/apt/sources.list and then install the driver through synaptic....makes it pretty easy.

to add the repo,  open a terminal (appilcations > accessories > terminal) and type or copy/paste the following into it to open the sources.list file for editing:

```
gksudo gedit /etc/apt/sources.list
```when it opens....copy/paste the following lines to the bottom of the file:

```
## nvidia vdpau
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
```then save and close the file.

back in the terminal...run the following to update the repos:

```
sudo apt-get update
```when it completes....open synaptic (system > administration > synaptic package manager) and search for nvidia.  when the search is complete,  find and install the nvidia-glx-*** driver (*** = whichever version you choose).  it will grab a few other dependencies along with it.  when its done, logout and back in again to complete.

hope that helps.

---

### Post by randolf_ambrose on 2009-09-18
> **fooman said:**
> there is a launchpad repository for nvidia.  you can add it to your /etc/apt/sources.list and then install the driver through synaptic....makes it pretty easy.

to add the repo,  open a terminal (appilcations > accessories > terminal) and type or copy/paste the following into it to open the sources.list file for editing:

```
gksudo gedit /etc/apt/sources.list
```when it opens....copy/paste the following lines to the bottom of the file:

```
## nvidia vdpau
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
```then save and close the file.

back in the terminal...run the following to update the repos:

```
sudo apt-get update
```when it completes....open synaptic (system > administration > synaptic package manager) and search for nvidia.  when the search is complete,  find and install the nvidia-glx-*** driver (*** = whichever version you choose).  it will grab a few other dependencies along with it.  when its done, logout and back in again to complete.

hope that helps.

i've seen this method...

i wanted to install the version 185... in synaptic package manager, till 180 is available... this 180, i could install it in my hardware drivers like you said...

---

### Post by randolf_ambrose on 2009-09-18
this seems to be working...

i'm downloading the driver now...

[http://www.ubuntugeek.com/howto-install-nvidia-190-25-beta-drivers-in-ubuntu-jauntyintrepidhardy.html](http://www.ubuntugeek.com/howto-install-nvidia-190-25-beta-drivers-in-ubuntu-jauntyintrepidhardy.html)

---

