---
title: "Server 8.04.1 network help"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by Kingsley8891 on 2008-09-09
Hey guys!

I've been using Ubuntu Server since it was 6.10 and I've loved fiddling around with it all this time.
However lately when I threw in a new Gigabit network card, I can't seem to use wget or apt-get, even though I can ping domains, and other people can connect to my server through it.

Wget or apt-get return saying timeout, but ping returns normally.

Its really weird behavior, I can't make sense of it, there's no ISP proxy in place, (I've trawled the net), or any IPTable configurations.

Thanks in advance for any help!

---

### Post by amo-ej1 on 2008-09-09
And if you try to ping /  traceroute the source apt tries to fetch things from ? It could be that your mirror has died or has some problems. It seems very unlikely that it has anything to do with your NIC. 

could you paste some output of say 

sudo traceroute [www.google.com](www.google.com)

and 

wget --debug [www.google.com](www.google.com) 

?

---

### Post by Kingsley8891 on 2008-09-09
I haven't installed Traceroute, I'll find my 7.10 CD and try to install it off that. 

WGet:
DEBUG output created by Wget 1.10.2 on linux-gnu.

--16:24:50--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 74.125.19.104, 74.125.19.147, 74.125.19.99, ...
Caching [www.google.com](www.google.com) => 74.125.19.104 74.125.19.147 74.125.19.99 74.125.19.103
Connecting to [www.google.com|74.125.19.104|:80](www.google.com|74.125.19.104|:80)... Closed fd 3
failed: Connection timed out.
Connecting to [www.google.com|74.125.19.147|:80](www.google.com|74.125.19.147|:80)... Closed fd 3
failed: Connection timed out.
Connecting to [www.google.com|74.125.19.99|:80](www.google.com|74.125.19.99|:80)... Closed fd 3
failed: Connection timed out.
Connecting to [www.google.com|74.125.19.103|:80](www.google.com|74.125.19.103|:80)...

I eventually stopped it by the end I didnt know how many timeouts it was going to deliver me.

Ping:
PING [www.google.com](www.google.com) (74.125.19.103) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (74.125.19.103): icmp_seq=1 ttl=246 time=186 ms
64 bytes from [www.google.com](www.google.com) (74.125.19.103): icmp_seq=2 ttl=246 time=186 ms
64 bytes from [www.google.com](www.google.com) (74.125.19.103): icmp_seq=3 ttl=246 time=186 ms

--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 186.356/186.521/186.722/0.383 ms

Mirror Ping:
PING archive.canonical.com (91.189.90.142) 56(84) bytes of data.
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=1 ttl=46 time=327 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=2 ttl=46 time=328 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=3 ttl=46 time=328 ms
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=4 ttl=46 time=328 ms

--- archive.canonical.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 327.119/327.969/328.360/0.760 ms

As you can see it all appears to be working normally. I'll find that 7.10 Server edition CD now. Thanks!

---

### Post by amo-ej1 on 2008-09-09
Nervermind the traceroute, could you now paste (or better attach it in a seperate file)  the output of 

```

strace wget www.google.com --tries=1

```

---

### Post by amo-ej1 on 2008-09-09
Or try something like this first: 
```

edb@lapedb:~$ telnet www.google.com 80
Trying 64.233.183.104...
Connected to www.l.google.com.
Escape character is '^]'.

```

Then type "GET index.html" then it should display the html code of the page (in normal circumstances)

Edit: btw you're 100% sure you're not firewalled or proxied ? Did you try other things like ssh, ftp, or  access e-mail  ?

---

### Post by Kingsley8891 on 2008-09-09
Thanks for the quick reply amo-ej1, I'm currently doing the strace, I'll output all of it in the next post (and the telnet), could you tell me how to use/connect to something using ssh or ftp? (I'd be able to normally but i haven't gotten much use out of connecting to stuff in Ubuntu Console Sorry!)

Edit: Yes, I'm 100% sure, I recently changed ISP's and my old one DID proxy me, which is why my Internet Explorer wouldn't work, I checked with my ISP and they use a direct connection to the internet, the only firewall settings i had on ubuntu in Webmin were just logging the packets sent and received.

---

### Post by amo-ej1 on 2008-09-09
Type

ftp ftp.debian.org

enter anonymous as username, enter as password, then after logging in terminate like this:

```

ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxrwsr-x    8 1176     1176         4096 Sep 08 21:12 debian
226 Directory send OK.
ftp> quit
221 Goodbye.

```

Have you tried to access the next hop in your network ? Being either the gui of your home router, or your isp's homepage ? 

To try pop. you could try telnet pop.gmail.com 110

```

edb@lapedb:~$ telnet pop.gmail.com 110
Trying 64.233.183.109...
Connected to gmail-pop.l.google.com.
Escape character is '^]'.

```

Or to try snmp you could try 

```

edb@lapedb:~$ telnet smtp.gmail.com 25
Trying 64.233.183.111...
Connected to gmail-smtp.l.google.com.
Escape character is '^]'.
220 *************************************
^]

```

Simply to figure out if it is an http only problem, because at ip level everything seems fine to me.

---

### Post by amo-ej1 on 2008-09-09
If you have iptables settings, start by flushing them, when you're troubleshooting issues, try to have an as clean as possible working situation and then move up by adding functionality to figure out what is going wrong at which point.

---

### Post by Kingsley8891 on 2008-09-09
Everything for telenet and the strace seems to be timing out, I'll post them soon, I'm just letting all the connections time out.
I'll try smtp and the others next. I don't have a browser installed on my server (seeing as I don't use it) But i'm able to access my servers port 80 and through SSH (which is what i'm issuing all these commands on) I'll try to telnet port 80 of my router, and see what happens!

---

### Post by amo-ej1 on 2008-09-09
At this point it smells like all outbound tcp connections are dropped somewhere.

---

### Post by Kingsley8891 on 2008-09-09
Haha! Something happened, FTP connected. Port 21 is forwarded to my Server in the router. I wonder if that has anything to do with it?
But then again Port 80 is forwarded too... There goes my idea. Lol.

kingsley@ubuntu:~$ telnet smtp.gmail.com 25
Trying 209.85.133.111...
Trying 209.85.133.109...
telnet: Unable to connect to remote host: No route to host

Connected to ftp.debian.org.
220 saens.debian.org FTP server (vsftpd)
Name (ftp.debian.org:kingsley): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxrwsr-x    8 1176     1176         4096 Sep 08 21:12 debian
226 Directory send OK.
ftp> quit
221 Goodbye.

Edit (again): I can connect to my router via port 80.

---

### Post by amo-ej1 on 2008-09-09
What has forwarding to do with that ? It only has to do with incoming traffic, not outgoing

---

### Post by Kingsley8891 on 2008-09-09
I know, just a mini-brainwave type thing, Everything else wasnt working then FTP decided to like me suddenly, can the repositories be in FTP other than http?

This is a bit of a pickle!

---

### Post by amo-ej1 on 2008-09-09
sure they can, simply edit your sources.list and let them point to ftp urls.

---

### Post by Kingsley8891 on 2008-09-09
Sounds like a plan, just a few files that aren't updating. 

I'll work it out, Thanks mate!

Edit:
kingsley@ubuntu:~$ sudo traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (74.125.19.147), 30 hops max, 40 byte packets
 1  iConnect625w (192.168.1.254)  2.907 ms  4.191 ms  4.476 ms
 2  loop0.lns10.mel4.internode.on.net (150.101.212.32)  104.047 ms  109.398 ms  114.423 ms
 3  150.101.212.6 (150.101.212.6)  119.435 ms  123.981 ms  128.853 ms
 4  pos2-1.bdr1.syd6.internode.on.net (150.101.120.122)  304.971 ms  309.946 ms  314.826 ms
 5  pos5-0.bdr1.syd7.internode.on.net (150.101.120.66)  320.572 ms  333.941 ms  335.190 ms
 6  pos5-0.bdr1.sjc2.internode.on.net (203.16.213.162)  335.824 ms  326.170 ms  330.995 ms
 7   (74.125.48.77)  362.307 ms  211.828 ms  213.649 ms
 8   (209.85.250.255)  193.729 ms  198.435 ms  203.577 ms
 9   (209.85.251.94)  209.788 ms  193.536 ms  193.847 ms
10  [www.google.com](www.google.com) (74.125.19.147)  223.033 ms  228.313 ms  232.951 ms

Just so you know :P

---

