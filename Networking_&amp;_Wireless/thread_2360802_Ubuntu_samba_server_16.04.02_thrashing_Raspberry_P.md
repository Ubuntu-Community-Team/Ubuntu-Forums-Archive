---
title: "Ubuntu samba server 16.04.02 thrashing Raspberry Pi"
date: 2017-05-08
forum: Networking &amp; Wireless
---

### Post by l-dvve-7 on 2017-05-08
Hi, This one has got me foxed.  I have a Ubuntu Server 16.04.02 running Samba.  Separately I have a Raspberry Pi 2 running Jessie Lite.  Recently I noticed there was a lot of network activity, and long story short I discovered that the Samba server is launching loads of what appears to be port scans at the Pi, only the Pi, nothing else on the network.  Here is a sample from the Pi running tcpdump -

22:19:11.365714 IP goliath.microsoft-ds > 192.168.1.101.47254: Flags [.], ack 43, win 227, options [nop,nop,TS val 1157820 ecr 18708376], length 0
22:19:11.370514 IP goliath.microsoft-ds > 192.168.1.101.47254: Flags [F.], seq 1, ack 43, win 227, options [nop,nop,TS val 1157821 ecr 18708376], length 0
22:19:11.370785 IP 192.168.1.101.47254 > goliath.microsoft-ds: Flags [F.], seq 43, ack 2, win 229, options [nop,nop,TS val 18708377 ecr 1157821], length 0
22:19:11.371112 IP 192.168.1.101.47256 > goliath.microsoft-ds: Flags [S], seq 2414012073, win 29200, options [mss 1460,sackOK,TS val 18708377 ecr 0,nop,wscale 7], length 0
22:19:11.371403 IP goliath.microsoft-ds > 192.168.1.101.47254: Flags [.], ack 44, win 227, options [nop,nop,TS val 1157821 ecr 18708377], length 0
22:19:11.371737 IP goliath.microsoft-ds > 192.168.1.101.47256: Flags [S.], seq 3876534122, ack 2414012074, win 28960, options [mss 1460,sackOK,TS val 1157821 ecr 18708377,nop,wscale 7], length 0
22:19:11.372057 IP 192.168.1.101.47256 > goliath.microsoft-ds: Flags [.], ack 1, win 229, options [nop,nop,TS val 18708377 ecr 1157821], length 0
22:19:11.372386 IP 192.168.1.101.47256 > goliath.microsoft-ds: Flags [P.], seq 1:43, ack 1, win 229, options [nop,nop,TS val 18708377 ecr 1157821], length 42 SMB PACKET: SMBecho (REQUEST)

I ran netstat on the server and got a whole load of this -

tcp        0      0 192.168.1.5:445         192.168.1.101:52328     TIME_WAIT   timewait (44.08/0/0)
tcp        0      0 192.168.1.5:445         192.168.1.101:49224     TIME_WAIT   timewait (34.47/0/0)
tcp        0      0 192.168.1.5:445         192.168.1.101:55974     TIME_WAIT   timewait (55.32/0/0)
tcp        0      0 192.168.1.5:445         192.168.1.101:50008     TIME_WAIT   timewait (36.89/0/0)
tcp        0      0 192.168.1.5:445         192.168.1.101:51368     TIME_WAIT   timewait (41.12/0/0)
tcp        0      0 192.168.1.5:445         192.168.1.101:40492     TIME_WAIT   timewait (7.48/0/0)
tcp        0      0 192.168.1.5:445         192.168.1.101:43446     TIME_WAIT   timewait (16.62/0/0)

If I stop Samba on the server with a "sudo service smbd stop" then the network goes quiet, so its definitely the problem.

Has anyone any idea what is causing this and what I need to do to stop it?

Many thanks, Dave

---

### Post by l-dvve-7 on 2017-05-09
Ok, solved but probably useful info for others that come across this.  The reason was that the RPi is in a 24/7 role, but the server is only powered when needed.  A couple of days back I backed up the data on the RPi by creating a CIFS mount point to the server.  Once complete I forgot to umount again.  The server was then shutdown but the RPi left running.  Now, when the server is powered up it seems to get in a right hissy fit with the RPi, until I umounted the share.  Once that was done, normality resumed.

---

