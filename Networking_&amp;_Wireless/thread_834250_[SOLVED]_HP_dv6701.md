---
title: "[SOLVED] HP dv6701"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by thejem on 2008-06-19
Yesterday I did a fresh install of Hardy and used ndiswrapper with R174291.exe to make my 4315 wireless card work. I was connected to my wpa protected wireless fine and surfing the web. In the afternoon I let Hardy download and install 17? updates and after rebooting my wireless cards light wont even come on and no wireless found. I hate to do another install anybody have an idea what happened?

---

### Post by Ayuthia on 2008-06-19
> **thejem said:**
> Yesterday I did a fresh install of Hardy and used ndiswrapper with R174291.exe to make my 4315 wireless card work. I was connected to my wpa protected wireless fine and surfing the web. In the afternoon I let Hardy download and install 17? updates and after rebooting my wireless cards light wont even come on and no wireless found. I hate to do another install anybody have an idea what happened?

Did you compile ndiswrapper?  If so, there might have been a kernel update that requires you to recompile ndiswrapper.  If you are not sure if you compiled ndiswrapper or not, open a Terminal and please post the results of:
```
ndiswrapper -l
```
Or if the results have a version of 1.53, then you will need recompile ndiswrapper.

EDIT: I just saw that you have a 4315 card.  If there was a kernel update and you have linux-restricted-modules installed, a new driver was introduced called wl.  Check lshw -C network and see if ndiswrapper or wl is showing up for your wireless driver.  If it is wl and you are happy with ndiswrapper, try the following:
[code]echo blacklist wl|sudo tee -a /etc/modprobe.d/blacklist

---

### Post by thejem on 2008-06-19
> **Ayuthia said:**
> Did you compile ndiswrapper?  If so, there might have been a kernel update that requires you to recompile ndiswrapper.  If you are not sure if you compiled ndiswrapper or not, open a Terminal and please post the results of:
```
ndiswrapper -l
```
Or if the results have a version of 1.53, then you will need recompile ndiswrapper.

EDIT: I just saw that you have a 4315 card.  If there was a kernel update and you have linux-restricted-modules installed, a new driver was introduced called wl.  Check lshw -C network and see if ndiswrapper or wl is showing up for your wireless driver.  If it is wl and you are happy with ndiswrapper, try the following:
[code]echo blacklist wl|sudo tee -a /etc/modprobe.d/blacklist
bob@laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4315) present (alternate driver: wl)
bob@laptop:~$ 
After having this problem I did remove ndiswrapper and downloaded lhe latest version and compiled it

---

### Post by cdtech on 2008-06-19
Be sure you have the ndiswrapper module listed in your /etc/modules list so that it gets loaded during boot.

You could type sudo modprobe ndiswrapper to install the module to see if it works without rebooting.

Hope this helps......

[B]P.S.
Never mind, beat me to it......[/B]

---

### Post by cdtech on 2008-06-19
I had to blacklist these:

```
# everything to do with wireless
blacklist b44
blacklist ipv6
blacklist b43
blacklist b43legacy
blacklist ssb
```

And then reload the ndiswrapper without rebooting:

```
sudo modprobe -r b44
sudo modprobe -r b43
sudo modprobe -r b43legacy
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

If that works then you should be ok on your next reboot with the blacklist.

---

### Post by thejem on 2008-06-19
I did notic tho that my cards logical name used to be wlan0 and now it is eth1, but that may have been before the frsh install.

---

### Post by thejem on 2008-06-19
Ok did all the blacklisting and still no wireless connection

---

### Post by Ayuthia on 2008-06-19
> **thejem said:**
> bob@laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4315) present (alternate driver: wl)
bob@laptop:~$ 
After having this problem I did remove ndiswrapper and downloaded lhe latest version and compiled it
Try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo depmod -ae
sudo modprobe ndiswrapper
```
If that works, then you need to blacklist the wl driver.

---

### Post by cdtech on 2008-06-19
Do you have your ndiswrapper file in the /etc/modprobe.d/ ?

cat:
alias wlan0 ndiswrapper

And what do you get with iwconfig and ifconfig.

---

### Post by thejem on 2008-06-19
Hey success!!!! I need to blacklist wl....
Thank you thank you thank you!

---

### Post by cdtech on 2008-06-19
> **Ayuthia said:**
> Try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo depmod -ae
sudo modprobe ndiswrapper
```
If that works, then you need to blacklist the wl driver.

Thanks Ayuthia, I forgot about the wl module.

---

