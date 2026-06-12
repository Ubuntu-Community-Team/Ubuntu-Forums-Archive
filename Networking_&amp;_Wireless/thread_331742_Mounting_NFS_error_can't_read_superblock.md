---
title: "Mounting NFS error: can't read superblock"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by vikingth0r on 2007-01-05
Hello,

I have a problem with my home network using kubuntu as my server computer.

In the past I have successfully been able to export directories and mount them between Mac OS X and slackware, but after switching over to kubuntu I am experiencing some problems.](*,) 


This is my current network setup through a wireless D-link router:

Server amd 1.8ghz: Kubuntu 6.10
Clients: Apple Powerbook 

I followed this HowTo [http://www.ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://www.ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)

my export file on my server reads:
```
 /mnt/200GB/share 192.168.1.1/24(rw,insecure,async,all_squash,anonuid=1000,anongid=1000)
```

on my client I type ```
mount -t nfs 192.168.1.102:/mnt/200GB/share /mnt/server
```

mount hangs for about 2 minutes and then returns that it can't read the superblock

I did all that the howto said about portmap and installing nfs etc... along with making sure to restart the services and re-export the directories after making changes to the exports file. I made sure to not check the loopback option when configuring portmap.

I am hope some experienced Ubuntu/Kubuntu users can shed some light on this problem because I've been playing around with it for a few days in my free time and have not been able to figure it out.

---

### Post by vikingth0r on 2007-01-05
Anyone?

---

### Post by vikingth0r on 2007-01-05
What took the headache away and made everything work out was downloading NFS Manager on my Mac [http://www.bresink.de/products.html]("http://www.bresink.de/products.html") . I had used this tool in the past and just remembered to try and use it again and BAM! it worked...

---

