---
title: "Install 1.1.0 VLC"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2011-06-09
The laptop I want to install VLC 1.1.0 on is a ThinkPad X200 with Intel X4500HD. Ubuntu Software Center has VLC but it's the 1.0.6 version. How do I install from a PPA so that my VLC gets updated along with Update Manager???

---

### Post by petronell on 2011-06-09
This page explains what to do...

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

daveR

---

### Post by petronell on 2011-06-09
Or even more simply install the getdeb package at getdeb.net they have packaged vlc v1.1.7.

---

### Post by emeraldgirl08 on 2011-06-09
That VLC webpage you linked only has instruction for 1.0.6.

---

### Post by Gone fishing on 2011-06-09
I just installed through the repositories and my version of vlc is 1.1.9

---

### Post by emeraldgirl08 on 2011-06-09
How do I install through the repositories?

TIA.

---

### Post by wojox on 2011-06-09
Here's the ppa:

```
sudo add-apt-repository ppa:ferramroberto/vlc
sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc
```

---

### Post by Paqman on 2011-06-09
If you read the page petronell posted, it has instructions ofr enabling a PPA that will allow you to get a later version of VLC through Software Centre.

---

### Post by emeraldgirl08 on 2011-06-09
> **wojox said:**
> Here's the ppa:

```
sudo add-apt-repository ppa:ferramroberto/vlc
sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc
```

This got me 1.0.6

Is it even worth it to upgrade? I did notice on the VLC website that it suggests using a newer version than 1.0.6. I want to try this b/c when I play MKV on the packaged media player it will stop after a couple of minutes of viewing. Not sure why but I have to reboot and use windows to watch my videos.

---

### Post by wojox on 2011-06-09
> **emeraldgirl08 said:**
> This got me 1.0.6

Is it even worth it to upgrade? I did notice on the VLC website that it suggests using a newer version than 1.0.6. I want to try this b/c when I play MKV on the packaged media player it will stop after a couple of minutes of viewing. Not sure why but I have to reboot and use windows to watch my videos.

Sorry, that is the ppa for 11.04

Go back to the link for the VLC site and the ppa for 10.04 is there.

---

### Post by emeraldgirl08 on 2011-06-09
It's been awhile since I've used term commands but is

```
sudo apt-get purge VLC
```

the easy way to uninstall VLC so that I can try the VLC webpage PPA??? Do I even need to uninstall the 1.0.6 version first or will the PPA update it?

---

### Post by Paqman on 2011-06-09
> **emeraldgirl08 said:**
> will the PPA update it?

Yep.

You can purge something through Synaptic, incidentally. Right click and "uninstall completely".

---

### Post by emeraldgirl08 on 2011-06-09
Okay thanks :D

as for the terminal command is this the right one?

```
 sudo add-apt-repository ppa:lucid-bleed/ppa
 sudo apt-get update
 sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

```

---

### Post by Paqman on 2011-06-09
Indeed, fire away.

---

### Post by emeraldgirl08 on 2011-06-09
It downloaded and installed 1.1.9 which seems to work fine so far :)

Thanks!!!  

:D:D:D

---

