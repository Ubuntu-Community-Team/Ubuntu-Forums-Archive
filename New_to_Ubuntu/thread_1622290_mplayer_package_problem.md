---
title: "mplayer package problem"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by kekearif on 2010-11-15
hey, I am trying to install mplayer in the software centre and I get a message saying it requires installation of untrusted packages     gnome-mplayer libsvga1 libvdpau1, how can I get it to install the packages?

Thanks

---

### Post by Hippytaff on 2010-11-15
You can try doing it from the Terminal (CTRL+ALT+T to open a terminal)
```

sudo apt-get install {Packagename}

```
where {Packagename} is the name of the package :-)

---

### Post by venicequeen7706 on 2010-11-15
Do you know which ones are untrusted? I didn't get any issues like that when i tried it just now. you might have to enable other repositories in synaptic. I'm not the best with this stuff but to enable another repository open synaptic go to settings then repositories. Unless you are in love with mplayer I would go with VLC, i think it has everything you could need

---

### Post by kekearif on 2010-11-15
hey I use the terminal and I get this error :(


keke@keke-R510-P510:~$ sudo apt-get install gnome-mplayer
[sudo] password for keke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libopenjpeg2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsvga1 libvdpau1 mplayer
Suggested packages:
  gecko-mediaplayer nvidia-vdpau-driver vdpau-driver mplayer-doc
The following NEW packages will be installed:
  gnome-mplayer libsvga1 libvdpau1 mplayer
0 upgraded, 4 newly installed, 0 to remove and 6 not upgraded.
Need to get 710kB/3,613kB of archives.
After this operation, 7,922kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libsvga1 libvdpau1 gnome-mplayer
Install these packages without verification [y/N]? y
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/universe libsvga1 i386 1:1.4.3-29
  Something wicked happened resolving 'tw.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) maverick/main libvdpau1 i386 0.4-5ubuntu1
  Something wicked happened resolving 'tw.archive.ubuntu.com:http' (-5 - No address associated with hostname)
0% [Connecting to tw.archive.ubuntu.com]


any ideas why? Thanks

---

### Post by Hippytaff on 2010-11-16
I think it's something to do with authentication keys and keyrings? though I'll need to read up a bit more...should still be safe to install though, but you might want to read up on thisw a bit more and set it up so you have the correct authentication keys etc to avoid the error messgae

---

