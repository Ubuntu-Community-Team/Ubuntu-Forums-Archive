---
title: "update several computer, but with one time downloading"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by legolas_w on 2008-12-04
Hi
Thank you for reading my post.
Is there any way to ensure that we just download the update once instead of downloading the updates several times for several workstations?

Thanks.

---

### Post by jken146 on 2008-12-04
The package files that apt downloads are stored in /var/cache/apt/archives/ and can be copied from that directory on one machine to the same place on other machines (with the same version of Ubuntu -- 8.10, 8.04, 7.10, ...).

---

### Post by linux_tech on 2008-12-04
apt-cacher or apt-mirror are probably the closest thing to sus.
[http://www.nick-andrew.net/projects/apt-cacher/](http://www.nick-andrew.net/projects/apt-cacher/)
[http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)

In most cases its best if clients can download updates from a local intranet server(s) that had been set up to run software update services over the internet.  
That way the client updates will be much faster especially for a larger 
network because it is time consuming to update each client using cmd line tools or GUI update manager and there is too much traffic over the wan link.

---

### Post by mapes12 on 2008-12-04
You can update one workstation then copy the updates to a CD using an application called aptoncd. Do a search in Synaptic Package Manager for it. Here's the home page: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by sdowney717 on 2008-12-04
aptoncd looks interesting. How big are these repos?

---

### Post by handydan918 on 2008-12-04
Depending on how many hosts you are maintaining, aptoncd may still be a lot of "sneakernet"work. Setting up a [local mirror]("http://www.debian.org/mirror/ftpmirror.en.html") of the Debian or Ubu repos is straightforward.

---

### Post by akshay.sulakhe on 2008-12-04
sudo apt-get install aptoncd            aptoncd is in ubuntu repos and some 1 mb program...not more..generate a meta package..and there u go...

---

### Post by Archmage on 2008-12-04
> **linux_tech said:**
> apt-cacher or apt-mirror are probably the closest thing to sus.
[http://www.nick-andrew.net/projects/apt-cacher/](http://www.nick-andrew.net/projects/apt-cacher/)
[http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)

Please don't be so crazy and download EVEYRTHING (over 10 GB) to do have a local mirror, because of the updates you might end download 100 GB a month, although you need only 100 MB.

Only download what you need and use apt-proxy.

---

### Post by billgoldberg on 2008-12-04
Just let one machine download the updates and have the other machines get their machines over the network from that machine.

---

### Post by mapes12 on 2008-12-04
handydan918 said> Depending on how many hosts you are maintaining, aptoncd may still be a lot of "sneakernet"work. Setting up a local mirror of the Debian or Ubu repos is straightforward.But the local mirror Howto says > Do I have the resources to host a mirror? Mirrors take up considerable disk space and bandwidth, one has to be able to commit to the cost.It would be reasonable to assume the OP only wants to download once because of the bandwidth issue and avoid extra cost. 

billgoldberg said> Just let one machine download the updates and have the other machines get their machines over the network from that machine.but this does not give the OP any idea of how to accomplish this task.
> aptoncd looks interesting. How big are these repos?aptoncd only has the packages you want on your machine(s). Therefore,the size will be governed by how many packages/applications you need. My guess is that we are talking SMALL size.

---

### Post by handydan918 on 2008-12-04
> **mapes12 said:**
> handydan918 saidBut the local mirror Howto says It would be reasonable to assume the OP only wants to download once because of the bandwidth issue and avoid extra cost. 


Please. The comment you quote clearly states "hosting a mirror", not just having one on your LAN. How in the world could it use MORE bandwidth to download something ONCE for redistribution on the LAN than to download it multiple times?

:confused:

---

### Post by mapes12 on 2008-12-04
> **handydan918 said:**
> Please. The comment you quote clearly states "hosting a mirror", not just having one on your LAN. How in the world could it use MORE bandwidth to download something ONCE for redistribution on the LAN than to download it multiple times?My post is simply a cut and paste from the resource recommended. It makes no reference to> "hosting a mirror"

Even if you have a mirror on your LAN that will mean downloading an entire distro package environment onto your server, most of which you will not need.

---

### Post by handydan918 on 2008-12-04
> **mapes12 said:**
> My post is simply a cut and paste from the resource recommended. It makes no reference to

Even if you have a mirror on your LAN that will mean downloading an entire distro package environment onto your server, most of which you will not need.

Here is a cut and paste of your cut and paste.

> Do I have the resources to host a mirror?

Note the terms "host" and "mirror".

Read what you posted. I did.


Have a nice day.

):P

---

### Post by aqk on 2009-01-24
OK, here's the NEXT question-
  Is there any way we can get the updates and put 'em on a CD or preferably a thumb-drive,*** under Windows?*** 

Reason:
 I have a coupla Ubuntu systems at home, but I do NOT have access to hi0speed-  I must use dialup.

 But a friend a few miles away does have hispeed, but alas, only Windows on his PC.
I suppose I could offer to add Ubuntu to a partition on his PC, but I ummm... don't think he's ready yet..  

  And doing a couple of 130Meg Ubuntu updates on a 40K modem takes a lonnng time!

---

