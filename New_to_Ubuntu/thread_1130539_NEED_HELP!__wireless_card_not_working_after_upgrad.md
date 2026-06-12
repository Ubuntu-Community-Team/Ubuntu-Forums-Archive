---
title: "NEED HELP!  wireless card not working after upgrade to hardy heron"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by xfearxnxloathing on 2009-04-19
[COLOR="Red"]**[SOLVED]**[/COLOR] thnx [COLOR="Red"]ugm6hr[/COLOR]!!!


i was using this card under gutsy gibbon aka 7.10 just minutes before updating to hardy heron aka 8.04. the real deal is i was wanting to update to intrepid ibex aka 8.10 and they (ubuntu site) said not to skip any upgrades or you may have problems later so i didn't and just as hardy heron finished and rebooted my card no longer worked and i cannot access the internet to find a fix. so i'm at my parents eating dinner hoping someone can help me fix this small problem.

INFO: Netgear WPN311 RangeMax Wireless-G MIMO PCI 


Envy

---

### Post by ptn107 on 2009-04-19
You can try using the backported modules package for Ubuntu 8.04.

_[linux-backports-modules-2.6.24-23-generic (32-bit)]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb")_
_[linux-backports-modules-2.6.24-23-generic (64-bit)]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_amd64.deb")_

After you install the package, restart, and confirm that it works, you should then install the respective dependent metapackages:
```
sudo apt-get install linux-backports-modules-hardy -y
```
which will install 'linux-backports-modules-hardy' and 'linux-backports-modules-hardy-generic' which are empty dummy packages but needed for upgrades.

---

### Post by xfearxnxloathing on 2009-04-20
> **ptn107 said:**
> You can try using the backported modules package for Ubuntu 8.04.

_[linux-backports-modules-2.6.24-23-generic (32-bit)]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb")_
_[linux-backports-modules-2.6.24-23-generic (64-bit)]("http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_amd64.deb")_

After you install the package, restart, and confirm that it works, you should then install the respective dependent metapackages:
```
sudo apt-get install linux-backports-modules-hardy -y
```
which will install 'linux-backports-modules-hardy' and 'linux-backports-modules-hardy-generic' which are empty dummy packages but needed for upgrades.

i will try this tomorrow.  as of rightnow i'm using the gutsy 7.10 live distro cd that is limiting me from going to the link you posted.  probably because i only have 512 mb of memory lol.

---

### Post by ptn107 on 2009-04-20
If you can pop open a terminal (Accessories -> Terminal) on the Live CD you can download it via 'wget' using the following command:
```

wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb
```

---

### Post by xfearxnxloathing on 2009-04-20
> **ptn107 said:**
> If you can pop open a terminal (Accessories -> Terminal) on the Live CD you can download it via 'wget' using the following command:
```

wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb
```

i did the command output is : > To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ wget [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb)
--06:47:16--  [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-backports-modules-2.6.24/linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb)
           => `linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb'
Resolving mirrors.kernel.org... 204.152.191.39, 149.20.20.135
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,515,188 (1.4M) [text/plain]

100%[====================================>] 1,515,188    159.01K/s    ETA 00:00

06:47:24 (193.65 KB/s) - `linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb' saved [1515188/1515188]


now what?  please be specific and thank you so much for helping out!  

i should also mention the live disc isn't 8.04, it's 7.10 if that even matters.

---

### Post by ptn107 on 2009-04-20
The live disk your using doesn't matter it's just a means for getting on the web at this point.  The file you just downloaded with wget is going to be in the home folder on the Live CD (Places -> Home Folder).  You should copy it to your home folder on your actual 8.04 system, and reboot into 8.04.  After you reboot into to your actual system you can open a terminal (Applications -> Accessories -> Terminal) and type the following to install it (just make sure the file is in your 8.04 home folder first):
```
sudo dpkg -i linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb
```
A restart may then be required.

---

### Post by xfearxnxloathing on 2009-04-20
> **ptn107 said:**
> The live disk your using doesn't matter it's just a means for getting on the web at this point.  The file you just downloaded with wget is going to be in the home folder on the Live CD (Places -> Home Folder).  You should copy it to your home folder on your actual 8.04 system, and reboot into 8.04.  After you reboot into to your actual system you can open a terminal (Applications -> Accessories -> Terminal) and type the following to install it (just make sure the file is in your 8.04 home folder first):
```
sudo dpkg -i linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb
```
A restart may then be required.

it didn't work for me.  i did put the package into my home folder and typed in exactly what you said and i got this: > envy@Elemented:~$ sudo dpkg -i linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb
[sudo] password for envy: 
Selecting previously deselected package linux-backports-modules-2.6.24-23-generic.
(Reading database ... 114282 files and directories currently installed.)
Unpacking linux-backports-modules-2.6.24-23-generic (from linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb) ...
dpkg: dependency problems prevent configuration of linux-backports-modules-2.6.24-23-generic:
 linux-backports-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not installed.
dpkg: error processing linux-backports-modules-2.6.24-23-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-backports-modules-2.6.24-23-generic
envy@Elemented:~$ sudo dpkg -i linux-backports-modules-2.6.24-23-generic_2.6.24-23.30_i386.deb

---

### Post by ugm6hr on 2009-04-20
Looks like this is a AR5215 card.

I can't find much about its drivers, but have no reason to suspect the standard madwifi drivers dont work.  Do you remember how you installed it on Gutsy?

Plug the computer in with wired ethernet, and then use the Hardware Drivers in System -> Admin menu to enable the madwifi drivers.

The reason the restricted-modules doesn't install is because the upgrade probably didn't install the latest kernel image.  You can check with:

```
uname -a
```

---

### Post by xfearxnxloathing on 2009-04-20
> **ugm6hr said:**
> Looks like this is a AR5215 card.

I can't find much about its drivers, but have no reason to suspect the standard madwifi drivers dont work.  Do you remember how you installed it on Gutsy?

Plug the computer in with wired ethernet, and then use the Hardware Drivers in System -> Admin menu to enable the madwifi drivers.

The reason the restricted-modules doesn't install is because the upgrade probably didn't install the latest kernel image.  You can check with:

```
uname -a
```


i dont have internet i backtracked my way into someone elses of which i'm using now with the live cd.  gutsy gibbon just recognized it on its own using the restricted drivers i believe (i could be wrong).

here's what i got after typing: ```
uname -a
``` > Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by ugm6hr on 2009-04-20
I need the output from uname -a when using the Hardy install, not the Live Gutsy CD.

---

### Post by xfearxnxloathing on 2009-04-21
> **ugm6hr said:**
> I need the output from uname -a when using the Hardy install, not the Live Gutsy CD.

here's what i got > Linux Elemented 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by ugm6hr on 2009-04-21
Try this one instead: [http://mirrors.kernel.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb)

---

### Post by xfearxnxloathing on 2009-04-21
> **ugm6hr said:**
> Try this one instead: [http://mirrors.kernel.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb)


can you give me a wget version?

---

### Post by ugm6hr on 2009-04-21
> **xfearxnxloathing said:**
> can you give me a wget version?

Sure.  Just add wget in front of the url:

```
wget http://mirrors.kernel.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb
```

Then (if copied to Hardy Home folder):

```
sudo dpkg -i linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb
```

Or just double-click on it.

---

### Post by xfearxnxloathing on 2009-04-21
> **ugm6hr said:**
> Sure.  Just add wget in front of the url:

```
wget http://mirrors.kernel.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb
```

Then (if copied to Hardy Home folder):

```
sudo dpkg -i linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb
```

Or just double-click on it.

this is what i got: > envy@Elemented:~$ sudo dpkg -i linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb
[sudo] password for envy: 
Selecting previously deselected package linux-restricted-modules-2.6.24-16-generic.
(Reading database ... 114343 files and directories currently installed.)
Unpacking linux-restricted-modules-2.6.24-16-generic (from linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb) ...
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-16-generic:
 linux-restricted-modules-2.6.24-16-generic depends on linux-restricted-modules-common (>= 2.6.24); however:
  Version of linux-restricted-modules-common on system is 2.6.22.4-14.9.
dpkg: error processing linux-restricted-modules-2.6.24-16-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.24-16-generic

---

### Post by ugm6hr on 2009-04-21
```
wget http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-common_2.6.24.16-23.56_all.deb
```

Then same again (copy to Home etc):

```
sudo dpkg -i linux-restricted-modules-common_2.6.24.16-23.56_all.deb
```

It appears your upgrade did not complete successfully.  Your linux-restricted-modules file (2.6.22.4-14.9) is the Gutsy file, but your kernel is Hardy.  You may find that this is impossible to resolve without wired internet, but it is worth giving this a try.

---

### Post by xfearxnxloathing on 2009-04-21
> **ugm6hr said:**
> ```
wget http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-common_2.6.24.16-23.56_all.deb
```

Then same again (copy to Home etc):

```
sudo dpkg -i linux-restricted-modules-common_2.6.24.16-23.56_all.deb
```

It appears your upgrade did not complete successfully.  Your linux-restricted-modules file (2.6.22.4-14.9) is the Gutsy file, but your kernel is Hardy.  You may find that this is impossible to resolve without wired internet, but it is worth giving this a try.

ok this time it gave me: > envy@Elemented:~$ sudo dpkg -i linux-restricted-modules-common_2.6.24.16-23.56_all.deb
[sudo] password for envy: 
(Reading database ... 114577 files and directories currently installed.)
Preparing to replace linux-restricted-modules-common 2.6.22.4-14.9 (using linux-restricted-modules-common_2.6.24.16-23.56_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Setting up linux-restricted-modules-common (2.6.24.16-23.56) ...

---

### Post by ugm6hr on 2009-04-21
Back to part 1:

```
sudo dpkg -i linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb
```

---

### Post by xfearxnxloathing on 2009-04-21
> **ugm6hr said:**
> Back to part 1:

```
sudo dpkg -i linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb
```

i wake up a 2pm est and go to bed between 5-6am est.
plus i just wanted to tell how slow and long this process is due to the fact of having to swap in and out the live distro and rebooting before and after lol.  

for this round, this is what i got: > envy@Elemented:~$ sudo dpkg -i linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb
[sudo] password for envy: 
(Reading database ... 114577 files and directories currently installed.)
Preparing to replace linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34 (using linux-restricted-modules-2.6.24-16-generic_2.6.24.12-16.34_i386.deb) ...
Unpacking replacement linux-restricted-modules-2.6.24-16-generic ...
Setting up linux-restricted-modules-2.6.24-16-generic (2.6.24.12-16.34) ...


did a reboot and restricted drivers found my atheros card!!!

**[COLOR="Red"][SOLVED][/COLOR]** thnx [COLOR="Red"]ugm6hr[/COLOR]!!!

---

