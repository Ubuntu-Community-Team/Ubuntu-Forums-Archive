---
title: "Server Virtulization"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by alexsmith_12 on 2009-10-26
I currently have Windows XP installed on my PC. I have come accross a 100 GB HDD and want to start making websites in drupal. SO this is my proposal. I want to vertulize Ubuntu Server in windows XP. I have VMware installed though i might have it installed wrong or somthing. The version is VMware-server-2.0.0. I got it from work. Along with drupal and other things to run on the server. 
 
Is it possible to virtulize Ubuntu Server through Windows XP? If yes, how?

---

### Post by cariboo on 2009-10-26
Yes you can, but if you are going to run a server, why run it on top of an old and unreliable OS like XP. Servers are noted for reliability and up time, I personally don't believe you can get the same thing from XP. 

Ubuntu servers don't need a lot of hardware, as they don't come with a gui installed. I ran my server on a discarded 1Ghz 64-bit AMD with 512Mb ram and 1.2Tb of hard drive space, the only thing I paid for was the hard drives. The server ran perfectly for 3 years until a defective power supply also took out the motherboard. If you can find a computer that someone has discarded, as being to old, but has decent specs, I would suggest using that.

---

### Post by Radioman991 on 2009-10-26
+1

I have recently set up an old P III with a gig of RAM and added a 500 GB HDD for my server.  Have it set up serving an internal web page, FTP and with SSH I can administer it from anywhere.

Its just a personal server for storage in my home network, and other than a little operator-caused issues, it wasn't too tough to set up.  Webmin and DynDNS are WONDERFUL.

The only dragon I have not slain is automatic backups of the /home folder.  Eventually I will, but for now, a weekly manual backup does the trick.

---

