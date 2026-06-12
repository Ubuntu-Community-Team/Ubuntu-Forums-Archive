---
title: "Firefox slow"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by squidmaster on 2007-09-23
Found a few things about FF 1.5 and such, but I am in 2.0.0.6 and I still have hold ups between pages.
I have a 3.4mb/s connection and my download rates are fine (usually around 350mB/s)

Anyway it takes about 15 seconds to even start loading a page, but once it's past that everything is really fast.

Any ideas?

---

### Post by JinxAu on 2007-09-23
Gday Squidmaster,

Just to make sure it's the browser and not related to other networking issues... have you checked how quickly your computer does a DNS lookup and the ping rates to the addresses you are visiting?

Check DNS with the following command:
```
dig www.google.com 
```

^ Replace [www.google.com](www.google.com) with the addresses you're trying to navigate to.

Check ping response with:
```
ping -c 10 www.google.com
```

If they are both responding without dramas, it sounds like it would be a problem relating to Firefox.

Cya round
Jinx

---

### Post by squidmaster on 2007-09-23
Sorry about that, I should have posted this info up first.

Anyway I know it's the browser or it's Ubuntu (which doesn't make any sense).
I have this dual boot in XP and Feisty Fawn.

Also the pages load fine in Symphony, DVN, and FBSD and PHLAK....

> squid@squid-mobile:~$ dig [www.google.com](www.google.com)

; <<>> DiG 9.3.4 <<>> [www.google.com](www.google.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44027
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.google.com](www.google.com).                        IN      A

;; ANSWER SECTION:
[www.google.com](www.google.com).         182238  IN      CNAME   [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com).       99      IN      A       209.85.165.147
[www.l.google.com](www.l.google.com).       99      IN      A       209.85.165.99
[www.l.google.com](www.l.google.com).       99      IN      A       209.85.165.103
[www.l.google.com](www.l.google.com).       99      IN      A       209.85.165.104

;; Query time: 760 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Sun Sep 23 22:33:41 2007
;; MSG SIZE  rcvd: 116



> squid@squid-mobile:~$ ping -c 10 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (209.85.165.147) 56(84) bytes of data.
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=1 ttl=239 time=69.6 ms
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=2 ttl=239 time=68.7 ms
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=3 ttl=239 time=70.4 ms
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=4 ttl=239 time=68.7 ms
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=5 ttl=239 time=71.0 ms
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=6 ttl=239 time=72.9 ms
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=7 ttl=239 time=73.9 ms
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=8 ttl=239 time=70.1 ms
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=9 ttl=239 time=72.7 ms
64 bytes from eo-in-f147.google.com (209.85.165.147): icmp_seq=10 ttl=239 time=73.3 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 45716ms
rtt min/avg/max/mdev = 68.717/71.177/73.987/1.869 ms


---

### Post by JinxAu on 2007-09-23
Can't say I have seen this issue before, but just going off previous posts, it seems disabling ipv6 support has helped others...

Apparently, this can be done by typing, "about:config" in the address bar. Then, setting disable.ipv6 to true.

More information:
[http://ubuntuforums.org/archive/index.php/t-438111.html](http://ubuntuforums.org/archive/index.php/t-438111.html)

Cya round
Jinx

---

### Post by JinxAu on 2007-09-23
I couldn't find disable.ipv6, but found network.dns.disableIPv6, so might be worth trying to set that to true, then restarting Firefox to see if it makes any difference.

Cya round
Jinx

---

### Post by squidmaster on 2007-09-23
Nope still the same problem...

---

### Post by JinxAu on 2007-09-23
Have you tried creating another user and testing it under that user?

Create a test user through:
System -> Administration -> Users and Groups.

Login as this user and see if Firefox responds any differently...

This should tell us if it is an issue specifically with Firefox or is related to the settings in your ~/.mozilla folder.

Cya round
Jinx

---

### Post by squidmaster on 2007-09-23
I just got rid of the 64-bit install because it was driving me crazy and it had the same problems so this is FRESH install of 7.04.... I am thinking about moving  back to V6.......

---

### Post by JinxAu on 2007-09-23
Have you tried using a different web browser?

Install using command line:
```
sudo apt-get install epiphany-browser
```

Is available via Applications -> Internet -> Epiphany

See if Epiphany does the same thing as Firefox...

Cya round
Jinx

---

### Post by squidmaster on 2007-09-24
I just like firefox so much I didn't want to change it :[

but I have....
well kinda
I used SongBird which runs from the mozilla engine.

---

### Post by squidmaster on 2007-09-24
OK so after some testing
Epiphany does it also.... I'm stumped. I spend all day fixing computer problems and working on them and then this comes along.
Haha man...

---

### Post by JinxAu on 2007-09-25
Yeah, bit of a weird one... I am out of ideas. :\

Maybe modifying the network settings (from dynamic to static or visa versa) might help.

There anyone else that has any ideas on how to fix this one?

/me appeals to the greater ubuntuforums.org community.

Cya round
Jinx

---

### Post by Warren Watts on 2007-09-25
Sometimes slow browser response is due to slow DNS lookups.
I wrote a handy Perl script that will scan the DNS servers listed in resolv.conf and determine which one is fastest.  You can then edit your resolv.conf file and put the fastest one at the top of the list.

Here's my post with the Perl script attached:

[Handy Perl script]("http://ubuntuforums.org/showpost.php?p=3397192&postcount=16")

---

