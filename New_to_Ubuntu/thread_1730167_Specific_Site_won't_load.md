---
title: "Specific Site won't load"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by KDoc on 2011-04-15
Hi Folks, 

Not an absolute beginner to Linux, but fairly ignorant with respect to Ubuntu. 

I've set my parents up with an Ubuntu box which I am attempting to  adminster over vnc and their connection's a bit slow (approx. 4Mb). Generally most  things work, just not a specific site they want. Namely, [www.tropicalglen.com]("http://www.tropicalglen.com"). 

I found this thread; [http://ubuntuforums.org/showthread.php?t=868048](http://ubuntuforums.org/showthread.php?t=868048) which talks about the Restricted Extra package, which I have since ensured is installed and re-booted. And have tried with both flashplayer plugin versions in the package. 

But tropicalglen.com simply does not want to load, letalone play anything. I just can't get the page up. XP from the same ADSL connection can load the site. Telnet from ubuntu to 80 shows it's there. 

What else can I try please?

Probably should add: Ubuntu v 10.10

---

### Post by b0b138 on 2011-04-15
Works fine here. Make sure you dont have multiple flashplugin installed or gnash.  Theres a script here on the forum called flashaid, which will remove duplicate/conflicting plugins

---

### Post by spikoley on 2011-04-15
Maybe it is a DNS issue.  Try switching to [OpenDNS]("https://store.opendns.com/setup/device/ubuntu/") or [Google's DNS]("http://code.google.com/speed/public-dns/docs/using.html").  

On a side note, this feels like a spam post trying to pump a lame Adsense site.  I feel this because you only have one post and who would want to go to that lame site.  It looks like a time warp back to '98.  Hopefully I am wrong and this is not an attempt to get hits.

---

### Post by KDoc on 2011-04-15
Thanks Bob, 

Flashaid installed and run. Definitely no gnash. Still no joy. 

The site just appears to be plain html, on the homepage at least. I can't see a reason why it shouldn't load.

---

### Post by KDoc on 2011-04-15
> **spikoley said:**
> Maybe it is a DNS issue.  Try switching to [OpenDNS]("https://store.opendns.com/setup/device/ubuntu/") or [Google's DNS]("http://code.google.com/speed/public-dns/docs/using.html").  

On a side note, this feels like a spam post trying to pump a lame Adsense site.  I feel this because you only have one post and who would want to go to that lame site.  It looks like a time warp back to '98.  Hopefully I am wrong and this is not an attempt to get hits.

Spikoley,

definitley not a spam post, just never had cause to register with forum before. 

Obviously not a dns issue as both XP and ubuntu telnet connect to site from same ADSL connection.

As for the snide comment about who would ever want to go to a site that's a timewarp back to the 80's. I think you might find, if you ask your own parents, whether they might like (what appears to be a treasure trove. Don't know and can't be assed to trawl the site) a site full of the music they listened to when they were younger, their response might be similar.

---

### Post by bashologist on 2011-04-15
So is this a connectivity issue flash issue or both? I was thinking dns too but do you have the site available to other clients on your network?

---

### Post by KDoc on 2011-04-15
Short Answer: I don't know. 

Personally I doubt it's a flash issue as the site simply doesn't even load the home page. I tried what Bob suggested anyway, because as I originally said, I don't know the quirks of Ubuntu.

It has to be a connectivity issue, of some sort, but the site DOES load from XP at the same address. And as said, a telnet to 80 _from_the_Ubuntu_box in question does connect. But Firefox simply times out. and doesn't give me any other error to work on. 

It's a fresh 10.10 install with no messing about other than basic simple set up.

---

### Post by KDoc on 2011-04-15
A quick dig from the Ubuntu box:

```
dig [www.tropicalglen.com]("http://www.tropicalglen.com")

; <<>> DiG 9.7.1-P2 <<>> [www.tropicalglen.com]("http://www.tropicalglen.com")
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55094
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.tropicalglen.com]("http://www.tropicalglen.com").        IN    A

;; ANSWER SECTION:
[www.tropicalglen.com]("http://www.tropicalglen.com").    14400    IN    CNAME    tropicalglen.com.
tropicalglen.com.    14400    IN    A    216.139.210.13

;; AUTHORITY SECTION:
tropicalglen.com.    14400    IN    NS    adns.aus.siteprotect.com.
tropicalglen.com.    14400    IN    NS    bdns.aus.siteprotect.com.

;; Query time: 534 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Apr 16 11:32:14 2011
;; MSG SIZE  rcvd: 122

```

---

### Post by wgn on 2011-04-15
Possibly a silly question.  Have you tried another browser?  If it's possibly a Firefox issue, try Epiphany.

---

### Post by KDoc on 2011-04-15
> **wgn said:**
> Possibly a silly question.  Have you tried another browser?  If it's possibly a Firefox issue, try Epiphany.

No questions are silly when you're asking for help. 

Epiphany installed and connection attempted. Still no joy. So, it's not Firefox. 

It's not firewall, because every other website (so far tried) does connect, no problem. Where to look next? Can't be the ISP blocking it, XP and telnet connect. 

DNS not an issue as shown above with dig. traceroute completes in 17 steps/300ms. 

What are my options here? Install Wireshark and try to sniff what's happening?

---

### Post by KDoc on 2011-04-24
Turned out to be an MTU issue.

---

### Post by wgn on 2011-04-24
Glad you were able to fix it.  Sorry we couldn't be more help.
You should mark the thread as [SOLVED].

---

