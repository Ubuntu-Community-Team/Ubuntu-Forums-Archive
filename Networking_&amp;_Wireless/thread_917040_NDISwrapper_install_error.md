---
title: "NDISwrapper install error"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by Morhas on 2008-09-11
Well once again it seems I'm having issues installing ndiswrapper :(. I've been trying to install it on my compaq desktop running 7.04 with a crappy usb trendnet adapter. I keep getting the following error. 
-
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/morhas/Desktop/ndiswrapper-1.53/utils'
make: *** [install] Error 2

Can anyone point me in the right direction?

---

### Post by caljohnsmith on 2008-09-11
Unless you've all ready tried the ndiswrapper version in the repositories and have problems with it, then there really isn't any reason you need to compile ndiswrapper yourself at this point. Just install it with:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
Let us know how it goes or if you have more problems.

---

### Post by Morhas on 2008-09-11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  ndiswrapper-utils-1.9: Depends: libc6 (>= 2.6.1-1) but 2.5-0ubuntu14 is to be installed
E: Broken packages

---

### Post by caljohnsmith on 2008-09-11
So what version of Ubuntu are you running? And what kernel are you using? Post the output of:
```

lsb_release -a
uname -r
```

---

### Post by Morhas on 2008-09-11
morhas@morhas-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
morhas@morhas-desktop:~$ uname -r
2.6.20-17-generic
morhas@morhas-desktop:~$

Thanks for the post.

---

### Post by caljohnsmith on 2008-09-11
It looks like ndiswrapper is complaining because your "libc6" installed package is out-of-date. Is there any reason why you haven't upgraded your system to Hardy? If you really want to use ndiswrapper in feisty, I suppose you could download ndiswrapper-utils-1.9 and ndiswrapper-common for Feisty from packages.ubuntu.com and install those files. If you decide to do that, just download them to your desktop, and install them with:
```
cd ~/Desktop
sudo dpkg -i ndis*
```
That might work or it might give you the same error.

---

### Post by Morhas on 2008-09-11
Well I tried to boot from the live cd, and it was unable to get any farther than the login screen. It would go through the countdown, then go to a black screen, then go back to the login page and repeat the countdown. When I went to shut down from the login page it failed to do that as well. I checked the dics for errors, and nothing came up. I ran the install, and the same problem persisted. :confused:

Just tried the same disc in my laptop and it worked fine. So something about my desktop hates it I guess.

---

### Post by Crafty Kisses on 2008-09-11
What are your system specs?

---

### Post by Morhas on 2008-09-11
Amd althlon64 
1gb DDR
Crappy ati radeon xpress 200
200gb hdd

---

### Post by Crafty Kisses on 2008-09-11
Have you tried installing Ubuntu using the alternate CD installer?

---

### Post by Morhas on 2008-09-11
I have not. I assume this would mean I would need to order a new cd?

---

### Post by Crafty Kisses on 2008-09-11
Yes, or you could burn a new one.

---

### Post by Morhas on 2008-09-11
I'm going to try and download it. We'll see how it goes. Thanks.

---

