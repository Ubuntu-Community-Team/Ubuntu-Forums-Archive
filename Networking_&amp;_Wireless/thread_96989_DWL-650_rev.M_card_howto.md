---
title: "DWL-650 rev.M card howto"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by carlosqueso on 2005-11-30
I had a lot of trouble with getting my DWL-650 card working under linux.  I went through 3 distros and it took me almost a month to get it working under Ubuntu.  Since it now works \\:D/, I thought I'd share how I did it so that others may be able to.

WARNING: I'm a n00b, so I put no warranty on this advice, and probably won't be able to help you if you blow up your system!

1). Download the drivers attached on this post (thanks to orbinick for the driver) DO NOT use the dlink drivers, they messed up my system when wrapped
2). Unzip the .zip archive
3).  Install ndiswrapper if you haven't already with
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils
``` 
4). open a terminal and navigate to the directory to which you unzipped the windows drivers
5). type
```
sudo ndiswrapper -i NET8180.INF
```
6). to get your wireless working, you have to type ```
sudo modprobe ndiswrapper
```
if you want it to work at startup, you must also type ```
sudo ndiswrapper -m
```

One more note...I also had the network-manager package installed and it would disconnect the wireless whenever X loaded....so you'll probably have to remove that if you have it.

---

