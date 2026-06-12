---
title: "SCP speed is going down and CPU usage high with 18.04.3 LTS"
date: 2019-10-17
forum: Networking &amp; Wireless
---

### Post by dirk-weber on 2019-10-17
Hello,

I was running Ubuntu 16.04.6 LTS on an old notebook (Core i5-560M) as a "server" for many years.
Samba, FTP and SCP is working with full network speed about 10 MByte/s. (only 100Mbit NIC)

Then I was building a new low-energy serversystem with:
ASRock J4105-ITX 
Intel Quad-Core Celeron Processor J4105 (1,5 GHz, up to 2.5 GHz) 
8GB Memory SSD and NAS HDD

Fresh installed Ubuntu 18.04.3 LTS and the same network services like on the old one.

Samba and FTP are also working with max. available network speed.
But SCP is completly down with performance.

Many small files are copied with acceptable speed, but large files with 10-20 MByte and more the copy starts with about only 3 MByte/s and then after a few seconds the copyspeed goes down to 250-500kbyte/s.
While copying HTOP is showing high cpu usage of 100% of only one cpu core.
All other cores are idle with max 1-5% usage.

ssh_config and sshd_config is default and nothing changed on both systems.

Then for testing, where the problem is, I upgraded the old system from 16.04.6 to 18.04.3 and after this I have the same problem on this machine!
So the sshd of 18.04.3 must be buggy or what was changed, that this is a problem now?
Is there some changed with the encryption methods or whatever?

How can I solve the problem and get a performant SCP connection again?

Very interessting is, that copy from the server is affected, but NOT copy to the server!
Copy large files from other computer to the server with SCP is working with "good old" performance.

KR
Dirk

---

### Post by TheFu on 2019-10-17
Have you tried **rsync**?  I use rsync almost exclusively to copy files.
Have you tried sftp?
Have you tried using a different cipher for which a J4105 would have hardware encryption support?

---

### Post by dirk-weber on 2019-10-17
> **TheFu said:**
> Have you tried **rsync**?  I use rsync almost exclusively to copy files.
Have you tried sftp?
Have you tried using a different cipher for which a J4105 would have hardware encryption support?

Quick and dirty tried SFTP with WinSCP.
And what a wonder, transfer speed 10,8MByte/s. Full networkspeed used and all 4 cpu cores are used and no more than 5-10% cpu usage.

But what is the difference?
Both are using SSH as crypto protocol.
And why is this only since version 18.04.3?

---

### Post by TheFu on 2019-10-17
WinSCP?  Is Windows somehow involved here?

---

### Post by dirk-weber on 2019-10-17
Yes, I connect via WinSCP to the server using SCP, SFTP.

---

### Post by TheFu on 2019-10-17
Sorry, I can't help with testing Windows issues, no system to test with.  Perhaps someone else can.

There are a large number of complaints about winscp being slow over the years.  
[https://winscp.net/eng/docs/faq_slow](https://winscp.net/eng/docs/faq_slow)
[https://winscp.net/forum/viewtopic.php?t=25705](https://winscp.net/forum/viewtopic.php?t=25705)

I did a test from a 16.04 laptop to an 18.04 server running inside a VM (1 vCPU, 1GB RAM) over my GigE network:
```
$ scp -v  ./0526/3839-t.mkv test-1804:/tmp/
3839-t.mkv              100%  342MB 114.1MB/s   00:03
```
I can't see the performance being any faster between those systems.  912 Mbps is pretty much as fast as anyone should expect on GigE.

So, I'm back to thinking it is a WinSCP issue.  If you have putty on Windows, there is a pscp.exe program that might be worth trying?

---

