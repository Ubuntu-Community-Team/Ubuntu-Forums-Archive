---
title: "tftp"
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by ipguru99 on 2005-07-07
Am I missing something with Ubuntu as far as atftpd or in.tfptd and permissions?  I remember doing this with SuSE 9.?.. but I didn't think it was that difficult.  I am trying to push some images from a some routers and NOTHING is working.  

Try to go through this here...
Using atftpd, I have
```
username@ubuntu:/etc$ sudo find / -name atftpd
/etc/default/atftpd
/etc/init.d/atftpd
/usr/share/doc/atftpd
/usr/sbin/atftpd
``` 
 
My /etc/default/atftpd looks like this
```
USE_INETD=true
OPTIONS="--daemon --port 69 --tftpd-timeout 300 --retry-timeout 5     --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5  /tftpboot"
``` 
I tried it with /home/username/tftp... but that didn't seem to work, so I went back to what I found on google and the man pages and stuck with /tftpboot

I get this
```
username@ubuntu:/etc$ netstat -an|grep \:69
udp        0      0 0.0.0.0:69              0.0.0.0:*
``` 
... so I know it is listening.  

Most of the time I am getting Authorization errors (cisco routers... but it shouldn't make a difference, isn't this supposed to be "auth-free".

I figure this has something to do with me having to
```
username@ubuntu:/etc$ sudo mkdir /tftpboot
``` 

I had to do this from a windows box today because I couldn't figure this out!! Please don't make me have to keep this bloated OS on the other side of my hard drive for this!!

---

### Post by ipguru99 on 2005-07-07
I am an idiot....  Out of frustration, I just went to the console and typed in 'in.tftpd' to see if it was still there... the last part of the 'quick' help says that the /tftpboot directory must be world readable and writeable... duh!.. it works as advertised.

Love this distro by the way, I am converting everyone in sight!

---

