---
title: "ssh/sftp speed on local network"
date: 2016-04-06
forum: Networking &amp; Wireless
---

### Post by DGINSD on 2016-04-06
I just set up a media server on an old laptop and have been using sftp to transfer the files I create from my main computer to the new server. My SFTP speeds max out at 1.9mb a second on my local network ( usually more like 1.7) this seems really slow to me. I realize SSH carries some overhead with encryption, I've tested this with no other network demands, same result, I'm not running top of the line new hardware but I'm not using the worst either.

I'm my searching I've looked into encryption ciphers, HDD speed, suggestions of using FTP or samba instead, an SSH patch called hp-ssh, tpc/ip tuning, none of which offered any help. It just seems I should be able to get at least 4 MBS and that would be fine.

Hp-ssh seems very interesting but a bit above my skill level requiring recompiling  ssh.

TCP/IP tuning on modern Linux kernels (2.6+) is automatically implemented

FTP and samba seem like giving in to a less secure protocol rather than making the proper better one work correctly.

So where have I gone wrong and how can I diag and fix it.

---

### Post by nerdtron on 2016-04-07
Are you transferring via wifi? or via a 100mbps lan cable? are both destination linux?
SSH/sftp can be slow in terms of copying via network due to the increase overhead on encryption. Samba is a bit faster although less secure. 
That being said, you sacrifice a little speed for increased security.

---

### Post by DGINSD on 2016-04-07
The older and slower machine is on a 100mb LAN connection the the other on wifi. Again though I'm not asking for instantaneous transfer but it's taking me like 30 min to transfer a 2 gb file seems excessive.

Both machines are running Linux the older lubuntu 14.04.4, the newer Ubuntu 15.10 upgraded from original 14.04 install.

---

### Post by nerdtron on 2016-04-08
Mine is from a raspberry pi 300MB file takes about 5 mins. Samba share wifi to wifi transfer. If i use LAN to wifi, it gets a little faster. I guess 30 mins for 2GB file via wifi and with SSH encryption is the normal.

---

### Post by HermanAB on 2016-04-08
Howdy, 

You can speed things up by selecting a simpler encryption algorithm and possibly by compressing the headers:
scp -C -c blowfish filename user@computer:~/. 

The fastest encryption algorithm is arcfour, but it may not be installed.

Note that while intel procesors have special instructions to speed up encryption, simple processors like a RPi or other may not have it.  So then using a simple encryption algorithm can make a big difference.

---

### Post by slickymaster on 2016-04-08
*Moved to the ***Networking & Wireless*** sub-forum*

---

