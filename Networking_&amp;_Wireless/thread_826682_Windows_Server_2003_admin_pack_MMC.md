---
title: "Windows Server 2003 admin pack/ MMC"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by flaps on 2008-06-12
Hey guys,

I'm trying to access my servers at work using the TS client. Unfortunately I'm getting an error message saying that there is no license available.

I have also tried installing the windows server 2003 admin pack using 

*msiexec /i adminpak.msi*

this gets the installer going, but it comes accross an error whenever i try to install it.

so 2 questions really... is there anyway of installing the admin pack??
and is there a way of getting a MMC for ubuntu (or anything like that, that is able to open MMC files)?

Any help would be much appreciated.

Regards

Flaps

---

### Post by shairozan on 2009-12-09
Hey there, 

I know this thread is kind of old, but I figured I'd post what I could in case anyone ever comes across it. 

First off, one of the primary reasons your server might not be responding to terminal server connections is that you might not have configured a licensing mode on it yet. Until it is setup, it will deny terminal service connections. It might also be that you have only 1 concurrent connection available and it's already in use. We see it a great deal where I currently work. 

Regarding the MMC, I have yet to get it to install currently under WINE, but if I find anything out, I'll update the post. 

Thanks
DJ

---

