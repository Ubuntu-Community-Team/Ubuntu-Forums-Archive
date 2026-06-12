---
title: "Error installing nomachine (error parsing archive)"
date: 2019-08-31
forum: Networking &amp; Wireless
---

### Post by steve234 on 2019-08-31
Hi there,

I'm trying nomachine as TV doesn't work for my application. 

I am following the tutorial here:
[https://websiteforstudents.com/install-nomacine-on-ubuntu-16-04-17-10-18-04/](https://websiteforstudents.com/install-nomacine-on-ubuntu-16-04-17-10-18-04/)

Having downloaded the package I get the following error:

```
sudo dpkg -i nomachine_6.7.6_11_amd64.deb(Reading database ... 234212 files and directories currently installed.)
Preparing to unpack nomachine_6.7.6_11_amd64.deb ...
dpkg: error processing archive nomachine_6.7.6_11_amd64.deb (--install):
 new nomachine package pre-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 nomachine_6.7.6_11_amd64.deb



```

Anyone know what went wrong?

---

### Post by TheFu on 2019-08-31
If your TV doesn't work, I don't get why a remote desktop will be helpful. Where will you display it? Do you have a different monitor?

---

### Post by steve234 on 2019-08-31
Lol - you know TV= teamviewer;

Solved it anyway - had an /etc/NX folder from previous faffing which was messing it up - rm'd that and the install worked. Am all happy remoting in (on my phone)

---

