---
title: "Slow ftp upload"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by Goliash on 2006-10-30
I have desktop and server, on both proftpd server.
When I upload to ftp server in my 100Mb network, speed is about only 200KB/s. I can download from ftp server 11MB/s and when I had WinXP, I could down/upload up to 11MB/s both directions.
There is Kubuntu on my desktop, proftpd, gftp. I tried different ftp clients: KBear, Krusader, gFTP, mc but still the same results. On my server there is Debian, proftpd. When I download from desktop ftp, it is up to 11MB/s. 

Don't you know why I can upload to ftp only 200KB/s?

---

### Post by Goliash on 2007-02-28
New hardware (notebook), installed Kubuntu, still the same slow upload on ftp server on LAN. Where is a mistake? Don't anybody know?

---

### Post by utnubu1 on 2007-03-20
I have the same problem, any solutions?

---

### Post by frostiebek on 2007-03-24
+1
I also have that problem of slow upload for ftp and ssh transfers between Windows and Linux (~1500ko/s instead of 10000 on XP) ... I don't know why :(
But this is not particular to Ubuntu series, I had the same on Debian too.
Gentoo is faster, I remember having about 6000ko/s on it with pureftpd.

I had very bad experiences with proftpd running Edgy or Feisty, it was damn slow on directory listing. But removing it and installing vsftpd instead resolved this problem. I really recommand it for small networks, it's fast and really easy to configure.

If somebody knows a trick for full-bandwidth transfer on Ubuntu, it might interest a lot of geeks (including me :) )

---

### Post by Goliash on 2007-04-08
It works now, I had Edgy, it worked lately and now I have Feisty and I also upload full speed to Debian proftpd server. I don't exactly know what upgrade helped, but I am glad it works.

---

