---
title: "Firefox forwards to lame-delegation-domain.com"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by neocon2005 on 2007-03-26
I have noticed a strange problem lately. Some websites that I want to visit on firefox (or opera) gets redirected to lame-delegation-domain.com (ip [http://8.4.112.108/)](http://8.4.112.108/))! This doesn't happen to all sites but just some (such as ubuntuforums.org!). Can somebody please help me troubleshoot this issue (such as checking /etc/hosts file etc). No problems when accessing the web from my WinXP laptop. Thanks in advance.

---

### Post by koenn on 2007-03-26
sounds like a browser hijack or a dns problem. 
what do you get when you run
```
dig ubuntuforums.org
```. 

Should be something like this : 
```
n@nix:~$ dig ubuntuforums.org

; <<>> DiG 9.3.2 <<>> ubuntuforums.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43321
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 5

;; QUESTION SECTION:
;ubuntuforums.org.              IN      A

;; ANSWER SECTION:
ubuntuforums.org.       1021    IN      A      ** 82.211.81.186**

;; AUTHORITY SECTION:
ubuntuforums.org.       77380   IN      **NS      ns1.xlogicdns.com.**
ubuntuforums.org.       77380   IN      **NS      ns2.xlogicdns.com.**

```

---

### Post by chili555 on 2007-03-26
Since you can readily log into your XP laptop, I would do so and open the terminal and do ipconfig /all. I believe it will show the DNS configuration. Write down the two or three DNS server IP addresses.

Go back to Ubuntu and sudo gedit /etc/resolv.conf to amend the file to remove the nameservers you have, unless they are the same, and replace them with the ones XP is using. The file should look something like this, substituting the IP addresses you found:```
nameserver 205.152.37.23
nameserver 205.152.132.23
```It would be interesting to know how the hijacker got on board, but I imagine you just want it to work.

---

### Post by neocon2005 on 2007-03-26
Thank you very much. Attached is the output from the dig command. It looks normal to me; maybe I am missing something.
I don't have access to my laptop at this moment; I will check it out as soon as I get home (about 6-8 hours later).

```
; <<>> DiG 9.3.2 <<>> ubuntuforums.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 246
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 5

;; QUESTION SECTION:
;ubuntuforums.org.		IN	A

;; ANSWER SECTION:
ubuntuforums.org.	1103	IN	A	82.211.81.186

;; AUTHORITY SECTION:
ubuntuforums.org.	62920	IN	NS	ns5.xlogicdns.com.
ubuntuforums.org.	62920	IN	NS	ns1.xlogicdns.com.
ubuntuforums.org.	62920	IN	NS	ns2.xlogicdns.com.
ubuntuforums.org.	62920	IN	NS	ns3.xlogicdns.com.
ubuntuforums.org.	62920	IN	NS	ns4.xlogicdns.com.

;; ADDITIONAL SECTION:
ns1.xlogicdns.com.	149320	IN	A	63.219.151.3
ns2.xlogicdns.com.	149320	IN	A	205.234.154.1
ns3.xlogicdns.com.	149320	IN	A	66.117.40.198
ns4.xlogicdns.com.	149320	IN	A	216.129.109.1
ns5.xlogicdns.com.	149320	IN	A	205.177.124.51

;; Query time: 12 msec
;; SERVER: 68.94.156.1#53(68.94.156.1)
;; WHEN: Mon Mar 26 12:41:28 2007
;; MSG SIZE  rcvd: 233

```

Yes it would be interesting how the hijacker got onboard (after resolving the problem :) so as to close the hole!

---

### Post by koenn on 2007-03-26
The DNS lookup for ubuntuforums looks OK. It's most likely a hijack. [http://82.211.81.186](http://82.211.81.186) in Firefox address bar should get you to ubuntuforums.org. 
Does it do that or does it get redirected ? 
can you post your hosts file (just in case it's a simple hosts hack) - that's the output of
```
cat /etc/hosts
```

---

### Post by chili555 on 2007-03-26
This is rather fascinating! I was not aware that these kind of hacks had made their way to linux. Have you seen this in linux before, koenn? I'd be very interested to know how this happened and how to prevent it in the future. 

I wonder if it's possible that one of his DNS servers is actually who is hacked?

---

### Post by neocon2005 on 2007-03-26
Hi Folks
Thanks a lot for all the feedback. The problem seems to have fixed itself, for now atleast. What I tried to do was as follows:
Googled for SBCYahoo (my ISP) DNS servers. I commented out all the entries in my /etc/resolv.conf and entered the DNS servers I got through Google. Didn't seem to work. So I rebooted the machine and looks like the resolv.conf file got overwritten because it is back to the original now! Anyways, everything seems fine now. I will keep an eye open though and report back if the problem crops up again. Thanks a bunch for your suggestions though. I have enclosed my /etc/hosts and /etc/resolv.conf below but both look innocuous though.
/etc/hosts:
```
127.0.0.1 localhost
#127.0.1.1      sekkar-desktop
192.168.1.106 UbuntuDesktop
192.168.1.101 WinLaptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
/etc/resolv.conf
```
nameserver 68.94.156.1
nameserver 68.94.157.1

```
I had typed 206.13.31.13 ,206.13.28.60 ,206.13.31.5 for DNS which got lost on reboot.

---

### Post by koenn on 2007-03-27
I asked to look at your hosts file to see if there were any weird entries (like ubuntuforums' IP address matched to lame-delegation-domain.com or something) but as there are only local addresses it looks OK to me too. 

68.94.156.1 apparently belongs to 
SBC Internet Services, Inc.
   1701 Alma dr
   Plano, TX 75075
   US
so if they own / run SBCYahoo, your resolv.conf is legit as well.

IP > I was not aware that these kind of hacks had made their way to linux. Have you seen this in linux before, koenn?
Never seen on Linux. I don't know how they work either. I can imagine one could abuse DNS, either through /etc/hosts, by running a rogue DNS server or taking control of an existing DNS server,  by poluting the dns cache, by manipulating the chaching/forwarding dns server that runs on broadband routers, and so on. The idea is always the same : substitute one address for another. How to go about it, beats me. 

Then, I suppose a rogue or compromised proxy server could have this effect as well, or one could mess with the browser cache or with the javascript scripts that make up lots of firefox's functionality (eg browser.js in /usr/share/firefox/chrome/browser.jar, or just prefs.js )  . And then I probably don't even know half of it. Here, the trick would be to subsitue one URL for another (rather than addresses), or swap chached files or so.

And again, how to go about it, i have no idea. I would assume this sort of manipulations require root access (or maybe just running firefox as root ? ).

---

