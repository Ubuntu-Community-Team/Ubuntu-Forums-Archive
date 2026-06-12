---
title: "Debian 5 vs Ubuntu 9.04 (Server)"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by SuperMiguel on 2009-05-26
For a home server. Regular LAMP with file sharing. Is there any difference between Debian 4 and Ubuntu Server 9.04??? Thanks :)

---

### Post by SuperMiguel on 2009-05-26
bump

---

### Post by aktiwers on 2009-05-26
I don't think there will be much difference, Though Ubuntu can be easier to use in some areas, if you are a beginner.

---

### Post by halitech on 2009-05-26
I would suggest Debian 5 (Lenny) over Debian 4 (Etch - old stable)

Ubuntu server may have more drivers installed but if you are going with a true server install (no gui) then both should work about the same with no noticable difference.

also, you shouldn't bump a thread anymore often then once in a 24 hour period

---

### Post by growled on 2009-05-26
I think it comes down to individual choice. Either will do just fine.

---

### Post by wizard10000 on 2009-05-26
> **SuperMiguel said:**
> For a home server. Regular LAMP with file sharing. Is there any difference between Debian 4 and Ubuntu Server 9.04??? Thanks :)

Just my opinion but one should only use LTS releases for production server duty.  If you're gonna use Ubuntu you should probably be using 8.04 server instead of the latest and greatest.

---

### Post by albinootje on 2009-05-26
> **SuperMiguel said:**
> For a home server. Regular LAMP with file sharing.

Ubuntu 9.04 will have newer software than Debian Lenny (5).

Ubuntu uses sudo by default, whereas Debian will prompt you to for a root password during installation.

Ubuntu has this new LandScape thing on the server edition, I haven't looked into that.

I'm using Debian and Ubuntu within several VPS-es, and I tend to go for Debian Etch or Debian Lenny, because I usually prefer the "stable" product on my servers.

---

### Post by SuperMiguel on 2009-05-26
also do u guys recommend using ISPConfig 3?

---

### Post by albinootje on 2009-05-26
> **SuperMiguel said:**
> also do u guys recommend using ISPConfig 3?

I've tried several of those ISP panels in the past, and there was not one that I really liked. I also don't see why you would want that on your home server.

I prefer using OpenVZ to have VPS-es, and use those to separate different setups, very pleasant to work with imho.

---

### Post by halitech on 2009-05-26
> **albinootje said:**
> Ubuntu 9.04 will have newer software than Debian Lenny (5).

Ubuntu uses sudo by default, whereas Debian will prompt you to for a root password during installation.

Ubuntu has this new LandScape thing on the server edition, I haven't looked into that.

I'm using Debian and Ubuntu within several VPS-es, and I tend to go for Debian Etch or Debian Lenny, because I usually prefer the "stable" product on my servers.

if you are using it for a server, are you necessarily looking for newer software or stable, proven software?

Debian can also be setup to use sudo

I use Debian Lenny on everything as I prefer stable to newer so I don't have to worry about things working and not crashing on me.

---

### Post by SuperMiguel on 2009-05-26
whats the point of using VPS-es? Also this is a p4 3.4Ghz 1gb of ram 2tb of HD. And i wanted to install ISPConfig 3 as a monitor tool.. i dont know any other.

---

### Post by albinootje on 2009-05-26
> **halitech said:**
> if you are using it for a server, are you necessarily looking for newer software or stable, proven software?

A few times in the past I needed newer software, like perl related packages (I prefer deb packages instead of using CPAN), and then you'll notice the slow Debian development cycle, I solved it by compiling backports.
> 
Debian can also be setup to use sudo

Yes, that's what I do, as I like sudo.

---

### Post by halitech on 2009-05-26
> **albinootje said:**
> A few times in the past I needed newer software, like perl related packages (I prefer deb packages instead of using CPAN), and then you'll notice the slow Debian development cycle, I solved it by compiling backports.

Yes, that's what I do, as I like sudo.

so far I haven't run across that since changing from Ubuntu to Debian but I'm also pretty easy to please as long as it works :)

so do I, find it easier for my purposes plus I'm the only one using this computer

---

### Post by albinootje on 2009-05-26
> **SuperMiguel said:**
> whats the point of using VPS-es? 

One thing that I like is that I can have only ssh running on the host system, and then have VPS-es on top of that.
Whenever there's some tweaking or a change, then it's a matter of restarting the VPS. It's also fairly easy to do a new install, or restore from a backup.
This is totally different from having all services running on the same machine in old fashioned style.
> 
Also this is a p4 3.4Ghz 1gb of ram 2tb of HD. And i wanted to install ISPConfig 3 as a monitor tool.. i dont know any other.

A monitor tool ? Can you clarify what you want with that ?
There's phpsysconfig, and nagios.

[http://phpsysinfo.sourceforge.net/](http://phpsysinfo.sourceforge.net/)

---

### Post by SuperMiguel on 2009-05-26
> **albinootje said:**
> One thing that I like is that I can have only ssh running on the host system, and then have VPS-es on top of that.
Whenever there's some tweaking or a change, then it's a matter of restarting the VPS. It's also fairly easy to do a new install, or restore from a backup.
This is totally different from having all services running on the same machine in old fashioned style.


A monitor tool ? Can you clarify what you want with that ?
There's phpsysconfig, and nagios.

[http://phpsysinfo.sourceforge.net/](http://phpsysinfo.sourceforge.net/)

sorry i meant to say monitoring. Like to monitor the server, yes i think phpsysinfo will do the trick. Also to use VPN do i need a faster computer or i can just use my p4 with 1gb of ram. Or i will need to pay a company to host it?

---

### Post by albinootje on 2009-05-26
> **SuperMiguel said:**
> or i can just use my p4 with 1gb of ram.

If you would like to use OpenVZ to use a VPS or more, there's easy interfaces for it (I don't use it, a friend of mine does), for example here : [http://webvz.sourceforge.net/](http://webvz.sourceforge.net/)

You will need to use a kernel with OpenVZ support :
[http://packages.debian.org/search?suite=default&section=all&arch=any&searchon=names&keywords=openvz+image](http://packages.debian.org/search?suite=default&section=all&arch=any&searchon=names&keywords=openvz+image)
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=openvz+linux-image](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=openvz+linux-image)

I'm using OpenVZ also on an old Celeron with 512 Mb of RAM as a mail- and web-server, it depends on what you use it for, and how much load it will have.

Per VPS container you can limit the maximum resources it can take.

See also :
[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)
[http://en.wikipedia.org/wiki/OpenVZ](http://en.wikipedia.org/wiki/OpenVZ)

---

### Post by SuperMiguel on 2009-05-26
> **albinootje said:**
> If you would like to use OpenVZ to use a VPS or more, there's easy interfaces for it (I don't use it, a friend of mine does), for example here : [http://webvz.sourceforge.net/](http://webvz.sourceforge.net/)

You will need to use a kernel with OpenVZ support :
[http://packages.debian.org/search?suite=default&section=all&arch=any&searchon=names&keywords=openvz+image](http://packages.debian.org/search?suite=default&section=all&arch=any&searchon=names&keywords=openvz+image)
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=openvz+linux-image](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=openvz+linux-image)

I'm using OpenVZ also on an old Celeron with 512 Mb of RAM as a mail- and web-server, it depends on what you use it for, and how much load it will have.

Per VPS container you can limit the maximum resources it can take.

See also :
[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)
[http://en.wikipedia.org/wiki/OpenVZ](http://en.wikipedia.org/wiki/OpenVZ)

umm so OpenVZ is the same as KVM?? if yes i tought u were only able to use virtualization if u had a 64bit cpu

---

### Post by albinootje on 2009-05-26
> **SuperMiguel said:**
> umm so OpenVZ is the same as KVM?? if yes i tought u were only able to use virtualization if u had a 64bit cpu

KVM needs the hardware virtulization support in the machine itself, something which things like XEN, UserModeLinux, Linux VirtualServer, and OpenVZ don't need.

All of this, except KVM will run on a 32bit machine.

---

### Post by SuperMiguel on 2009-05-26
ohh ok. So if i just want this server as file server and music server (gnump3d) is there any use for OpenVZ?

---

### Post by albinootje on 2009-05-26
> **SuperMiguel said:**
> ohh ok. So if i just want this server as file server and music server (gnump3d) is there any use for OpenVZ?

No, it is probably much easier to do without, to start with.

But if you're gonna give other people access over the internet, then I personally find it very handy to use VPS-es.

---

### Post by SuperMiguel on 2009-05-26
> **albinootje said:**
> No, it is probably much easier to do without, to start with.

But if you're gonna give other people access over the internet, then I personally find it very handy to use VPS-es.

I do have a 64 bit desktop that i have ubuntu installed on it and i want to put this desktop on a DMZ to share some files. I was going to install virtulbox and use the virtualization option that they have there, and installed an FTP server on it to share few files over the internet. So do u recommend using OpenVZ or KVM instead of virtualbox.???

---

### Post by albinootje on 2009-05-26
> **SuperMiguel said:**
> So do u recommend using OpenVZ or KVM instead of virtualbox.???

I am running VirtualBox (headless) on a server since 1 month or so, it consumes a bit more resources than OpenVZ is my impression, but it sounds like a much easier option in your setup, to install and to maintain.

---

### Post by SuperMiguel on 2009-05-26
> **albinootje said:**
> I am running VirtualBox (headless) on a server since 1 month or so, it consumes a bit more resources than OpenVZ is my impression, but it sounds like a much easier option in your setup, to install and to maintain.

k thanks :)

---

