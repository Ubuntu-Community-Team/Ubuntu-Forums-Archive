---
title: "Gutsy 7.10 &amp; Netgear WG311 PCI"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by CJ_Hudson on 2008-07-23
Hi Everyone,
Have just tried the normal method for getting this working and after a bit of tweaking and reading-up discovered it all works until I get to the last step.

1) I go to Source forge and get the compatible v.1.53
2) I sudo su and apt-get away
3) I unpackage the tar with xvvf and make install
4) I get the latest (windows) driver for the WG311v3
5) I ndiswrap-per it in /Windows 2000/WG311v3.inf
6) depmod -a whatever that does
7) modprobe ndiswrapper (?!)
8) then, cutting closer to the chase: ndiswrapper -m
9) Now here's where it seems to go wrong for me: when I

  gedit /etc/modules

I am informed that the following modules require loading at the boot-time:

fuse
Ip
sbpz

Any assistance would be gratefully recieved. I feel it is almost there but then I've been trying umpteen times without freshly installing Gutsy again so could well be a cumulative problem. Please advise me.
Thankyou already!

---

