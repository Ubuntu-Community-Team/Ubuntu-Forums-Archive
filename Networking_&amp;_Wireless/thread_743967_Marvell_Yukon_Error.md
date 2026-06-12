---
title: "Marvell Yukon Error"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by Ladkipz on 2008-04-03
Hey,
On my Gigabyte GA-965P-S3 I have been unable to get my onboard networking to work at all. I have lurked through many posts and help pages and I know its because of the lack of support for the Marvell Yukon drivers on ubuntu or something... But as i only got linux last week i have no idea what most of the stuff they are talking about in those guides.

If someone could give me a simple guide to tell me how i can connect to networks through that networking card then i would be most grateful. Cheers
Michael

---

### Post by chili555 on 2008-04-03
Evidently, your Yukon doesn't work with the *sky2* module (or driver, as it's called in the Windows world) and it is reported to work with the *sk98lin* module. Let's find out which one is loading. Open a terminal (Applications -> Accessories -> Terminal) and type in:```
lsmod | grep sk
```That vertical line, or pipe, is on the same key with \. The terminal will return either some verbage including either  *sky2* or *sk98lin.* 

If it returns *sky2*, as I suspect it will, let's first try the *sk98lin* module built in to the kernel. We will first stop the *sky2* from loading. Open a terminal and do:```
gksudo gedit /etc/modprobe.d/blacklist
```Add a separate line:```
blacklist sky2
```Save and close the file. Now we will load *sk98lin*. In the terminal, do:```
gksudo gedit /etc/modules
```Add a separate line:```
sk98lin
```Save and close. Then in the terminal, do:```
sudo ifdown eth0
sudo rmmod sky2
sudo modprobe sk98lin
sudo ifup eth0
```Please let us know the result. Did your ethernet interface get an IP address?

---

