---
title: "[SOLVED] No internet after ubuntu desktop install"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by webdirectsites on 2008-11-11
I have internet in the ubuntu shell before and during the download of ubuntu-desktop but after it installs and I restart and boot into the desktop it gives me no internet also when I log into the shell after installing the desktop there is no internet! Please Help. I am running Ubuntu Server 8.10.

---

### Post by superprash2003 on 2008-11-11
please post output of ifconfig.. you should be getting an ip for internet..

---

### Post by webdirectsites on 2008-11-11
I found out after troubleshooting that it is the updates that are causing the internet loss. ifconfig is as follows: 


eth0      Link encap:Ethernet  HWaddr 00:04:4b:17:7b:f5  
          inet addr:65.40.129.14  Bcast:65.40.129.127  Mask:255.255.255.128
          inet6 addr: fe80::204:4bff:fe17:7bf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:510 (510.0 B)  TX bytes:3845 (3.8 KB)
          Interrupt:252 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:17:7b:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16148 (16.1 KB)  TX bytes:16148 (16.1 KB)

---

### Post by webdirectsites on 2008-11-11
I also just found out that I am serving pages to the web.

---

### Post by Iowan on 2008-11-11
Is there supposed to be a machine between the server and the web (router, modem, etc)?

---

### Post by webdirectsites on 2008-11-11
Yes it is a router but it is bridged. I could connect to the internet before the update.

---

### Post by webdirectsites on 2008-11-11
Can someone please help me?

---

### Post by Jayock on 2008-11-11
What does 'ip r' give you for output?

Have you verified that you cannot get any activity, by name, by IP, via various protocols out?

---

### Post by webdirectsites on 2008-11-11
65.40.129.0/25 dev eth0  proto kernel  scope link  src 65.40.129.14 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 65.40.129.1 dev eth0  metric 100

---

### Post by Jayock on 2008-11-11
So it thinks your default gateway is 65.40.129.1.  Can you get a ping response from it?

Also, is this the setup from Network Manager.  Your metrics look different from what Network Manager usually sets up.

---

### Post by webdirectsites on 2008-11-11
This is the output when I do sudo apt-get update:

Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by Jayock on 2008-11-11
Ok, so how about the ping to your gateway?

---

### Post by webdirectsites on 2008-11-11
That works.

Also I am serving pages to the internet.

---

### Post by Jayock on 2008-11-11
Ok, so try the following three commands, and let me see their outputs.

ping 4.2.2.2

dig google.com

dig @67.138.54.100 google.com

---

### Post by Jayock on 2008-11-11
Also, just for fun, try to ping google.com

---

### Post by webdirectsites on 2008-11-11
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=248 time=49.2 ms
64 bytes from 4.2.2.2: icmp_seq=2 ttl=248 time=48.4 ms
64 bytes from 4.2.2.2: icmp_seq=3 ttl=248 time=48.1 ms
64 bytes from 4.2.2.2: icmp_seq=4 ttl=248 time=48.8 ms
64 bytes from 4.2.2.2: icmp_seq=5 ttl=248 time=48.5 ms
64 bytes from 4.2.2.2: icmp_seq=6 ttl=248 time=48.6 ms
64 bytes from 4.2.2.2: icmp_seq=7 ttl=248 time=48.6 ms
64 bytes from 4.2.2.2: icmp_seq=8 ttl=248 time=48.3 ms
64 bytes from 4.2.2.2: icmp_seq=9 ttl=248 time=48.0 ms
64 bytes from 4.2.2.2: icmp_seq=10 ttl=248 time=48.9 ms
64 bytes from 4.2.2.2: icmp_seq=11 ttl=248 time=48.6 ms
64 bytes from 4.2.2.2: icmp_seq=12 ttl=248 time=48.0 ms
64 bytes from 4.2.2.2: icmp_seq=13 ttl=248 time=48.5 ms
64 bytes from 4.2.2.2: icmp_seq=14 ttl=248 time=48.4 ms
64 bytes from 4.2.2.2: icmp_seq=15 ttl=248 time=48.8 ms
64 bytes from 4.2.2.2: icmp_seq=16 ttl=248 time=48.5 ms










root@ns1:/home/codi# dig google.com

; <<>> DiG 9.5.0-P2 <<>> google.com
;; global options:  printcmd
;; connection timed out; no servers could be reached

















root@ns1:/home/codi# dig @67.138.54.100 google.com

; <<>> DiG 9.5.0-P2 <<>> @67.138.54.100 google.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18304
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: Messages has 436 extra bytes at end

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		108	IN	A	72.14.207.99
google.com.		108	IN	A	209.85.171.99
google.com.		108	IN	A	64.233.187.99

;; Query time: 132 msec
;; SERVER: 67.138.54.100#53(67.138.54.100)
;; WHEN: Tue Nov 11 17:14:53 2008
;; MSG SIZE  rcvd: 512

---

### Post by webdirectsites on 2008-11-11
root@ns1:/home/codi# ping google.com
ping: unknown host google.com

---

### Post by webdirectsites on 2008-11-11
All of this happened after I did apt-get update.

---

### Post by Jayock on 2008-11-11
Ok, so the first command tells me you can get out to internet.

Second tells me your default DNS servers are unresponsive.

Thrid tells me you can get DNS from the server IP specified (a free DNS server), so it isnt a resolving problem.

Check your DNS servers in /etc/resolv.conf.  Make sure they are good.  You can use the IP in that second dig command if necessary, as it is a free public DNS server.

---

### Post by Jayock on 2008-11-11
Also, you can probably set the DNS in network manager if you prefer, it will make the resolv.conf changes for you.

---

### Post by webdirectsites on 2008-11-11
All that is in there is 

# Generated by NetworkManager

---

### Post by webdirectsites on 2008-11-11
How do I get to Network Manager?

---

### Post by Jayock on 2008-11-11
It should be up in the tray by the clock.  right click it and choose `Edit Connections`

You can also get to it System->Preferences->Network Configuration

Otherwise, start it with `nm-applet &` from the command line

Alternatively, at the end of resolv.conf list your DNS server IPs one per line, and nothing else.  It will do the same thing.

---

### Post by webdirectsites on 2008-11-11
Like this?

# Generated by NetworkManager

205.244.194.36

207.14.188.36

---

### Post by Jayock on 2008-11-11
oops.  No.  I don't know what I was talking about at first.  needs nameserver prepended


Like this 

> 
# Generated by NetworkManager
nameserver 205.244.194.36
nameserver 207.14.188.36 


---

### Post by Jayock on 2008-11-11
Then restart your networking:

 sudo /etc/init.d/networking restart

and try again

---

### Post by webdirectsites on 2008-11-11
That did it!!!!!


To bad I can't hit the thank you 1000 times!!:)

---

### Post by Jayock on 2008-11-11
Only thing that worries me... is that if Network Manager isn't configured correctly, it may overwrite that change if it is used at a later date.  I am a RedHat/Fedora Server guy who recently converted to Ubuntu, so Im not entirely sure how Network Manager is going to handle this if you make changes later.

---

### Post by Jayock on 2008-11-11
Basically, just remember how to fix this if it comes up again.  :)

---

### Post by webdirectsites on 2008-11-11
For anyone else with this problem:

vi /etc/resolv.cnf

Then add your DNS like so 


nameserver 11.111.111.111
nameserver 11.111.111.111

Replacing 11.111.111.111 with your nameservers

---

### Post by webdirectsites on 2008-11-11
Can I remove Network Manager? 
I think this is an update problem.

---

### Post by Iowan on 2008-11-11
Removing Network Manager has been mentioned as a solution before:
[http://ubuntuforums.org/showthread.php?p=6119911]("http://ubuntuforums.org/showthread.php?p=6119911")

---

### Post by Swanbot on 2008-12-03
Okay so I am getting the same errors from post #11, then I try the advice from post #14 and for ping 4.2.2.2 I get "connect: Network is unreachable" then dig google.com "connection times out; no servers could be reached" any ideas?

---

