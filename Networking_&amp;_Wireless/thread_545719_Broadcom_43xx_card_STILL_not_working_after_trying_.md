---
title: "Broadcom 43xx card STILL not working after trying the &quot;EASY&quot; way - please help!"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by peterv6 on 2007-09-07
I tried using the offline procedure in the post titled "[COLOR="Blue"]**HOWTO: Broadcom 43xx based wireless cards the EASY way**[/COLOR]", but I'm having trouble with the sudo aptitude upgrade. I ran the update, then when I run the upgrade, after a few minutes, I get the following question:

112 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 140MB of archives. After unpacking 3891kB will be used.
Do you want to continue? [Y/n/?] y

I answered yes, and messages scroll by for a few more minutes before getting the following error messages, then it hangs:

Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main mesa-utils 6.5.2-3ubuntu8 [45.0kB]
[COLOR="Red"][B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main openoffice.org-core 2.2.0-1ubuntu4
Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main openoffice.org-common 2.2.0-1ubuntu4
Bad header line [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim-tiny 1:7.0-164+1ubuntu7.2
Bad header line [IP: 91.189.88.31 80]
Get:61 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim-common 1:7.0-164+1ubuntu7.2 [186kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main vim-common 1:7.0-164+1ubuntu7.2
Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libisc11 1:9.3.4-2ubuntu2.1
Bad header line [IP: 82.211.81.138 80]
Get:62 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libdns22 1:9.3.4-2ubuntu2.1 [499kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libdns22 1:9.3.4-2ubuntu2.1
Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80]
Get:63 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libisccc0 1:9.3.4-2ubuntu2.1 [95.7kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libisccc0 1:9.3.4-2ubuntu2.1
Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libisccfg1 1:9.3.4-2ubuntu2.1
Bad header line [IP: 91.189.88.31 80]
Get:64 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libbind9-0 1:9.3.4-2ubuntu2.1 [95.4kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libbind9-0 1:9.3.4-2ubuntu2.1
Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]
Get:65 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main liblwres9 1:9.3.4-2ubuntu2.1 [112kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main liblwres9 1:9.3.4-2ubuntu2.1
Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80]
Get:66 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main bind9-host 1:9.3.4-2ubuntu2.1 [115kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main bind9-host 1:9.3.4-2ubuntu2.1
Error writing to output file - write (28 No space left on device) [IP: 91.189.88.31 80]
Get:67 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main dnsutils 1:9.3.4-2ubuntu2.1 [184kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main dnsutils 1:9.3.4-2ubuntu2.1
Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main file 4.19-1ubuntu2.1
Bad header line [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libmagic1 4.19-1ubuntu2.1
Connection timed out [IP: 82.211.81.138 80]
Get:68 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main rsync 2.6.9-3ubuntu1.1 [262kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main rsync 2.6.9-3ubuntu1.1
Error writing to output file - write (28 No space left on device) [IP: 82.211.81.138 80][/B][/COLOR]

Then it hangs here:

**[COLOR="Blue"]42% [Waiting for headers][/COLOR]**

I would really appreciate it if anyone can help me out! I have no idea how it's getting a write error, I know my drive has space, and the ip address isn't for my machine.
__________________

---

