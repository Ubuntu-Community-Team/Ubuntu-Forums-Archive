---
title: "No more Windows"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by steve423 on 2007-06-20
I want to only use Windows when I have to but I have to, so I was thinking of running Windows in  VMware player in Umbuntu.  I downloaded the tar but it seems like alot of work so I downloaded the RPM but it wouldn't extract, something about it wasn't supported.  I'm guessing that the RPM was not design to run on Ubuntu  

Does anyone know of a better way of doing this.  How easy is it to setup remote destop in Linux to Windows?

Thanks,
Steve

---

### Post by ukripper on 2007-06-20
> **steve423 said:**
> I want to only use Windows when I have to but I have to, so I was thinking of running Windows in  VMware player in Umbuntu.  I downloaded the tar but it seems like alot of work so I downloaded the RPM but it wouldn't extract, something about it wasn't supported.  I'm guessing that the RPM was not design to run on Ubuntu  

Does anyone know of a better way of doing this.  How easy is it to setup remote destop in Linux to Windows?

Thanks,
Steve

Ok mate, first thing first, are you looking for Vmplayer which is a virtual app or are you looking for remote desktop app? 

Secondly, RPM is not designed for ubuntu but there are ways you can convert them but hold on a minute why you want RPM anyways as you can get vmplayer within repo. just open up synaptic manager and search for vmplayer 

or 

type folowing in terminal:

```
sudo apt-get install vmplayer
```


PS: Just for your knowledge -Alien can convert RPM to DEB packages.

---

### Post by steve423 on 2007-06-20
I'm trying both ways.  Right now I'm running open SUSE 10.2 in VMware player in Windows XP and on the same machine I used the Wubi installer to install Ubuntu.  Ideally I want to start in Linux and run Windows either through remote desktop or in a VMplayer player.  

Do you have any experiance with either of these methods?  

I've installed NOMACHINE on my SUSE VMplayer installation but can't seem to get it to connect.  I'm not sure if it can connect to itself, since the machine I'm trying to connect to is the machine I'm running it on.  I did try another computer running VNC and remote desktop is enabled, no luck.  NOmachine ask for a Windows Terminal server I'm not sure if were running one on this network but VNC is not working either.


If there is an easier way please do share.


Thanks,
Steve

---

### Post by ukripper on 2007-06-21
1. Try using VirtualBox instead of Vmplayer.

2. To connect remotely you can use Remote Desktop, location ---->    system>Preferences>Remote Desktop

---

