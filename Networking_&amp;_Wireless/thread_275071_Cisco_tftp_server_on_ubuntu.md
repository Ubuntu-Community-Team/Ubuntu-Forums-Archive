---
title: "Cisco tftp server on ubuntu"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by maxwas on 2006-10-10
Hi all,

I have set up a tftp server on my ubuntu box so i can play around with saving cisco router configs and ios's, and load them back up.

I have tftp running under inetd (along with telnet) with no problems and i am using gtkterm for the console.  

Now in order for me to save my router running config (called myconfig) to my box i need a folder in / called tftpboot with permissions 777, done that. i also need to create an empty file (touch) called myconfig in tftpboot with permissions 666, done that as well.

My router is pinging my box ok, when i try to copy over my config i keep getting 'permission denied' when trying to write to the empty file myconfig.

I dont know if anyone in the forum has tried this, but if so is there anything i am doing wrong? I have tried on another ubuntu box and get the same error, i have also tried on a slackware and freebsd boxes, but with success.

Any help would be greatly appreciated

M ](*,)

---

### Post by Mithrilhall on 2006-10-12
I had trouble getting tftpd-hpa and tftpd running using inetd or xinetd.

I ended up removing inetd, xinetd, tftpd, tftpd, and tftpd-hpa.

I then installed atftpd and edited "/etc/default/atftpd".

I changed the line

```

USE_INETD=true

```

to

```

USE_INETD=false

```


I didn't try keeping the original USE_INETD=true while I had inetd installed but I would think it would work.

---

### Post by t3rror on 2007-04-06
Make sure that the file you are touching (myconfig) is world readable and writeable (chmod 777).  I believe this would be a great place for the sticky bit!

---

### Post by jrogers360 on 2007-06-08
I've had a lot of difficulty with this.  I changed the config file as mentioned, and when trying to do a GET from a cisco switch:

```
Jun  8 09:18:10 rafiki atftpd[3110]: Advanced Trivial FTP server started (0.7)
Jun  8 09:18:20 rafiki atftpd[3111]: Serving c3750-ipbasek9-mz.122-37.SE.bin to 66.189.2.74:52273
Jun  8 09:18:24 rafiki atftpd[3111]: Serving c3750-ipbasek9-mz.122-37.SE.bin to 66.189.2.74:52273
Jun  8 09:18:25 rafiki atftpd[3111]: timeout: retrying...
Jun  8 09:18:29 rafiki atftpd[3111]: timeout: retrying...
Jun  8 09:18:29 rafiki atftpd[3111]: Serving c3750-ipbasek9-mz.122-37.SE.bin to 66.189.2.74:52273
Jun  8 09:18:30 rafiki atftpd[3111]: timeout: retrying...
Jun  8 09:18:40 rafiki last message repeated 6 times
Jun  8 09:18:42 rafiki atftpd[3111]: Serving c3750-ipbasek9-mz.122-37.SE.bin to 66.189.2.74:52273
Jun  8 09:18:44 rafiki atftpd[3111]: timeout: retrying...
Jun  8 09:18:49 rafiki last message repeated 5 times
Jun  8 09:18:50 rafiki atftpd[3111]: Serving c3750-ipbasek9-mz.122-37.SE.bin to 66.189.2.74:52273
Jun  8 09:18:52 rafiki atftpd[3111]: timeout: retrying...
Jun  8 09:19:22 rafiki last message repeated 8 times
Jun  8 09:19:50 rafiki last message repeated 5 times

```

Server and switch are in the same subnet and I can telnet to the switch from the server.   I tried turning up the verbosity:

```
Jun  8 09:29:11 rafiki atftpd[3430]: Advanced Trivial FTP server started (0.7)
Jun  8 09:29:11 rafiki atftpd[3431]:   running in daemon mode on port 69
Jun  8 09:29:11 rafiki atftpd[3431]:   logging level: 9
Jun  8 09:29:11 rafiki atftpd[3431]:   directory: /tftpboot/
Jun  8 09:29:11 rafiki atftpd[3431]:   user: nobody.nogroup
Jun  8 09:29:11 rafiki atftpd[3431]:   log file: syslog
Jun  8 09:29:11 rafiki atftpd[3431]:   server timeout: Not used
Jun  8 09:29:11 rafiki atftpd[3431]:   tftp retry timeout: 5
Jun  8 09:29:11 rafiki atftpd[3431]:   maximum number of thread: 100
Jun  8 09:29:11 rafiki atftpd[3431]:   option timeout:   enabled
Jun  8 09:29:11 rafiki atftpd[3431]:   option tzise:     enabled
Jun  8 09:29:11 rafiki atftpd[3431]:   option blksize:   enabled
Jun  8 09:29:11 rafiki atftpd[3431]:   option multicast: enabled
Jun  8 09:29:11 rafiki atftpd[3431]:      address range: 239.239.239.0-255
Jun  8 09:29:11 rafiki atftpd[3431]:      port range:    1758
Jun  8 09:29:35 rafiki atftpd[3431]: Creating new socket: 66.189.2.75:33042
Jun  8 09:29:35 rafiki atftpd[3431]: Serving c3750-ipbasek9-mz.122-37.SE.bin to 66.189.2.74:52254
Jun  8 09:29:39 rafiki atftpd[3431]: Creating new socket: 66.189.2.75:33043
Jun  8 09:29:39 rafiki atftpd[3431]: Serving c3750-ipbasek9-mz.122-37.SE.bin to 66.189.2.74:52254
Jun  8 09:29:40 rafiki atftpd[3431]: timeout: retrying...
Jun  8 09:29:44 rafiki atftpd[3431]: Creating new socket: 66.189.2.75:33044
Jun  8 09:29:44 rafiki atftpd[3431]: Serving c3750-ipbasek9-mz.122-37.SE.bin to 66.189.2.74:52254
Jun  8 09:29:44 rafiki atftpd[3431]: timeout: retrying...
Jun  8 09:29:50 rafiki last message repeated 4 times
Jun  8 09:29:50 rafiki atftpd[3431]: Creating new socket: 66.189.2.75:33045
Jun  8 09:29:50 rafiki atftpd[3431]: Serving c3750-ipbasek9-mz.122-37.SE.bin to 66.189.2.74:52254
Jun  8 09:29:54 rafiki atftpd[3431]: timeout: retrying...

```

Any ideas?

---

### Post by marmus on 2008-04-11
Hi, if you use iptables-like fw, then you have to install modules:
**ip_conntrack_tftp, ip_conntrack_ftp, ip_nat_ftp** and **ip_nat_tftp**
yourcomp# modprobe ip_conntrack....
yourcomp# echo ip_conntrack... >> /etc/modules

---

