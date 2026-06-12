---
title: "Can't enable wifi on Dell Inspirion 3521"
date: 2019-06-27
forum: Networking &amp; Wireless
---

### Post by antarmanu on 2019-06-27
I have been having huge problems with my Dell Inspirion 15 3521 laptop. Virtually none of the linux distros will have a working wi-fi out of the box. 

However, today I made a breakthrough with Ubuntu! Apparently, I have a Broadcom Corporation BCM43142 802.11b/g/n (rev 01) wi-fi adapter (it is listed when I use the lspci command from the terminal).

When I load Ubuntu 18.04.2 from an USB flash drive (without installing it, just in order to "try it"), and when I follow the instructions given in this thread on this forum:

[https://ubuntuforums.org/showthread.php?t=2232629](https://ubuntuforums.org/showthread.php?t=2232629)

Namely, when I just enter this command in the terminal:

```

sudo apt-get install bcmwl-kernel-source

```

the wi-fi gets enabled right away, even without a restart! Unfortunately, since Iam running Ubuntu from a Live USB drive, and it's still not installed on the hard disk, this cannot remain saved in my configuration.

When I try to run the above mentioned command from an already installed Ubuntu on my Laptop's hard drive, I get the error message that the package cannot be located. :(

I suppose that when I try to install bcmwl-kernel-source while I'm running Ubuntu from an USB drive it pulls that drive from USB installation files and installs it correctly, whereas when I try to do the same when Ubuntu is already installed on my laptop's hard drive, it doesn't know where to look for those files, and it (still) doesn't have internet access, so it reports the error that the package cannot be found.

Since it would be extremely complicated to enable any kind of wired internet to that Dell laptop, is there any way I can still install the bcmwl-kernel-source in Ubuntu (when it's already installed on the hard drive), for instance from an USB drive? Is there a way to tell it to look for that package in the USB drive that contains the complete Ubuntu installation? Or, is there a way to somehow just copy those files to a new USB flash drive and then to install them in the Ubuntu on the hard drive? I am willing to try anything that would enable me to use Wi-Fi on that Dell laptop providing I don't have to connect any wired internet to it. 

By the way, I tried to install this deb package when Ubuntu is already installed on the hard drive:

[https://pkgs.org/download/bcmwl-kernel-source](https://pkgs.org/download/bcmwl-kernel-source)

(I downloaded the version for Bionic Beaver because that's apparently what my Ubuntu is) but it says it needs some additional Gnome packages, which again is impossible to provide because I don't have internet access. :/


Does anyone have any idea how to solve this problem and enable wi-fi on the Ubuntu's hard drive installation as it is possible on the Live USB drive?

---

### Post by chili555 on 2019-06-27
Just substitute USB for SD in my answer here. As you surmise, the required driver and its prerequisites are all on the installation USB.

[https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949](https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949)

---

### Post by antarmanu on 2019-06-27
> **chili555 said:**
> Just substitute USB for SD in my answer here. As you surmise, the required driver and its prerequisites are all on the installation USB.

[https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949](https://askubuntu.com/questions/1069550/unable-to-use-wifi-card-16-04-macos-dual-boot/1069949#1069949)



Awesome! It worked very well, thanks!

Would the same files (taken from Ubuntu installation USB) work on Linux Mint (Mate) to enable Wi-Fi there as well? Or would it be necessary to select some other, specific files from Mint's installation USB (in a similar fashion as described here)?

---

### Post by chili555 on 2019-06-27
Awesome, glad it's working! Please use thread tools at the top to mark Solved. The serachers will appreciate it.> 
Would the same files (taken from Ubuntu installation USB) work on Linux Mint (Mate) to enable Wi-Fi there as well? Or would it be necessary to select some other, specific files from Mint's installation USB (in a similar fashion as described here)?
I don't know much about Mint. However, I suspect that you'll find the required deb files on Mint's USB installer. That's what I'd recommend trying.

---

