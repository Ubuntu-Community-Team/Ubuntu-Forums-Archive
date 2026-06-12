---
title: "Samba och windows FTP"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by Mandorr on 2008-03-17
Hi

I'm using Ubunto server 7.10 for fileserver whit samba and it is working great. But I have a windows 2003 server whit a FTP program running on it and the problem is that the FTP server program does not work whit the samba share. So windows can speak to samba but the FTP program can not.

What’s bothering me is that I have hade it running about a year ago. :(

Please help!

/Mandorr

---

### Post by akudewan on 2008-03-17
Your question is not very clear to me. Why would FTP work with samba? They are different protocols...

---

### Post by Mandorr on 2008-03-17
What I know the FTP program uses the same UNC path that windows does
Therefore the FTP program should be able to use the samba share?

When I’m using the explorer I can easily access files on the samba share.
But when the FTP program is trying to go the same path it just stops.

I have tried whit a lot of different FTP programs but all whit the same error

When I connect whit a FTP client I get “Can’t list” “No such file or directory” 

/Mandorr

---

### Post by akudewan on 2008-03-17
Ok, tell me if I have this correct. You're trying to connect to samba from your windows box, using an ftp client, right?

Is there an ftp server involved in the picture ?

---

### Post by Mandorr on 2008-03-17
Not realy...

The windows 2003 machine is running the FTP program....
so... I has a user can use the samba share, but the FTP program can not.

But I think I found the problem...
the samba log file gave me this.

[2008/03/17 11:18:45, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!

Any ides of what is means?

---

### Post by akudewan on 2008-03-17
That error in the log file has something to do with printing and CUPS, not ftp.

Is your FTP "program" in windows a client or a server ?

---

### Post by Mandorr on 2008-03-17
It is a server program.

The FTP server program is running for an Windows 2003 machine and it is trying to use the samba share.

/Mandorr

---

### Post by akudewan on 2008-03-17
Oh, I think you'll need to map the samba share as a network drive then

---

### Post by Mandorr on 2008-03-17
Done that... not working

Someone whit the exact same problem...
[http://www.linuxquestions.org/questions/linux-software-2/samba-doesnt-allow-certain-connections-583671/](http://www.linuxquestions.org/questions/linux-software-2/samba-doesnt-allow-certain-connections-583671/)

/Mandorr

---

### Post by Eiríkr on 2008-03-17
Question for you --

The link you posted describes someone trying to serve via FTP a share at //SERVER/SHARE.  What Akudewan suggests is mapping //SERVER/SHARE as a network drive, so instead the FTP server should be serving up a directory such as F:\Share instead.  This way the FTP sever program has exactly *zero* to do with Samba authentication -- all of that should be handled by the OS (possibly Explorer?) when the share is mounted in Windows as a mapped drive.  

If you're already attempting to serve F:\Share and that's *still* drawing a blank, have a look at permissions on the mapped drive *from within Windows* and make sure that whatever username the FTP server process is running under has access.  

HTH,

Eiríkr

---

