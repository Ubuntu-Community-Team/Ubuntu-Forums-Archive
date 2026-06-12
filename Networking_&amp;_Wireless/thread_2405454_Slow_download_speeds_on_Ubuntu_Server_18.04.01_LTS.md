---
title: "Slow download speeds on Ubuntu Server 18.04.01 LTS"
date: 2018-11-06
forum: Networking &amp; Wireless
---

### Post by tunkio on 2018-11-06
Copy pasting my problem from here: [https://askubuntu.com/questions/1090155/slow-download-speeds-on-ubuntu-server-18-04-01-lts](https://askubuntu.com/questions/1090155/slow-download-speeds-on-ubuntu-server-18-04-01-lts)

I have home server setup with old Packard Bell laptop that I've been  running years without much of a problem. I recently ugraded my home  internet connection from 4G LTE to much faster VSDL2 (75/10). Every  other device on my networks seemed to have benefitted from the upgrade  but my server is unable to achieve faster speeds.

  What I've tried is to download exactly same file ([ftp://ftp.funet.fi/dev/1Gnull](ftp://ftp.funet.fi/dev/1Gnull))  using wget with my server and with home desktop Windows 7. Average  speed with Windows is 9.20MB/s which seems fine. Homewer downloading  same file with Ubuntu gets average speed of about 1.00MB/s. Both machines have been wired same way, straight to the router.

  What is interesting is that I've tried to also download torrents  (Ubuntu Server iso) with my server and while downloading it gets to same  maximum speeds as Windows. Also running speed test gives maximum speed  results (using [https://www.speedtest.net/](https://www.speedtest.net/) apis).

  Information from my machine: [URL="https://privatebin.net/?1a147e5c2a2129a0#OXhy5FGXJ6c0zB0JrSz75K+L8a62Kk9w7gtTH+Q0gGI="]https://privatebin.net/?1a147e5c2a2129a0#OXhy5FGXJ6c0zB0JrSz75K+L8a62Kk9w7gtTH+Q0gGI=
[/URL]
  What could I do to try to improve my download speeds?

---

### Post by TheFu on 2018-11-06
The server can throttle different clients however they like.  If you use wget in Windows, is it slower?  wget is a well-know batch downloader and many sites will throttle it.

That's my only guess.

---

### Post by tunkio on 2018-11-07
Yes, I use wget also in Windows and it downloads with max speed. I've also tried different clients on Ubuntu side, for example aria2 and JDownloader. Results are same as with wget.

---

### Post by TheFu on 2018-11-07
Only other thing I can think of is that FTP is using a passive connection in Linux, but not in Windows.  This would happen if the firewall was enabled on Linux.  I pulled that file with wget and saw on average about 1.2MB/s.  Without doing any more research, I would assume it was throttled on the other side.  

The speeds ranged from 0.5 MB/s to 1.8 MB/s.  I'm on a commercial ISP without any connection issues.
Using a browser to get the FTP file, I saw similar speeds as wget.
I also tried modifying some network stack parameters which claimed to solve this issue previously. For me, those changes reduced the download speeds about 40%. The settings were net.ipv4.tcp_rmem and net.core.rmem_max, if you'd like to look them up.

I'll keep watching for solutions.  Generally, if I'm using FTP, I kick off the task in a different window and don't worry about it.

---

### Post by tunkio on 2018-11-08
Good theory, but this problem unfortunately is not limited to FTP. I also noticed same kind of behavior with HTTP(S) too. It is not also limited to that that current host as I've noticed this behavior with others too.

I also tried tinkering with those parameters but did not notice any difference in speed by doing that (quick googling gave me this: [https://wwwx.cs.unc.edu/~sparkst/howto/network_tuning.php](https://wwwx.cs.unc.edu/~sparkst/howto/network_tuning.php)).

---

