---
title: "how to upgrade graphics driver"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by elsea on 2011-03-24
Hi,

I have the "recommended driver" already installed NVidia 260.19.06 for GeForce GTS 450.  

I would like to upgrade to newer version.  Is there a way I can do that from the Synaptic Package Manager?  I tried re-installing nvidia-current, but that seems to have just reinstalled version 260.19.06.

I cannot upgrade from the package manager, how do I do it from the command line?  

Thanks.

---

### Post by PCNetSpec on 2011-03-24
260.19.44 are the latest, but will have to be downloaded from NVIDIA:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Make sure you get the right ones, ie. 32bit or 64bit.

---

### Post by elsea on 2011-03-24
Thanks, I just upgraded, to 260.19.44.

I used the information from other threads about how to install the downloaded drivers <[http://ubuntuforums.org/showthread.php?t=1699710](http://ubuntuforums.org/showthread.php?t=1699710)> and how to stop X server <[http://ubuntuforums.org/showthread.php?t=304325](http://ubuntuforums.org/showthread.php?t=304325)>.

By the way, I thought the latest version was already at 270.-- based on what I was looking for, but maybe that's for a different card than what I have.

---

### Post by PunkLV on 2011-03-24
I have 270.30. Downloaded from Nvidia's site. 
You sure the new drivers actually managed to install and are in use?

---

### Post by cariboo on 2011-03-24
Natty uses the latest driver 270.30, but it also uses a different version of Xorg-xserver, from earlier versions. If you download the driver from nVidia, make sure the driver still supports Xorg-xserver 1.9

---

### Post by PCNetSpec on 2011-03-24
I thought the 270.30 drivers were still in beta:

[http://www.nvnews.net/vbulletin/showthread.php?p=2399427](http://www.nvnews.net/vbulletin/showthread.php?p=2399427)

The ReadMe says nothing about dropping support for Xorg 1.9, but the posting mentions "added" support for 1.10

But use at your own risk ;)

---

### Post by elsea on 2011-03-24
Thanks everyone for the follow-up.  

When I use the link provided by PCNetSpec <[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)>, the 260.19.44 is the certified version resulting from the search with my system specs. 

The upgrade to 260.19.44 fixed the problem that prompted me to look into upgrading to 270.--.  I don't otherwise need a newer version, but I appreciate everyone's input.

---

### Post by beew on 2011-03-24
I got my upgrade through this ppa.
[URL="https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"]
https://launchpad.net/~ubuntu-x-swat/+archive/x-updates[/URL]

Installing manually from Nvidia's site can be tricky. Also I think the driver will be broken every time  you have kernel update based on what I read.

---

