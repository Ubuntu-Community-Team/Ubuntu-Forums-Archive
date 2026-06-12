---
title: "How to Drop by UserAgent IpTables?"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by bennychidge on 2009-05-22
I am setting up a whitelist and blacklist and wish to have googlebot in my whitelist::

```
"66.249.71.225 - - [19/May/2009:17:48:43 +0000] "GET /sitemap.xml HTTP/1.1" 304 - "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
```

I also wish to place this useragent in my blacklist

```
"[error] [client 77.68.45.175] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)"
```

I cant for the life of me find how to do the drop command in iptables and I cant seem to find this anywhere on Google.

I can for an ip add 

```
-A blacklist -s 77.68.45.175 -j DROP
```

to my blacklist chain but how do I do this with a useragent? whats the syntax? Any examples? Any links?


Thanks in advance

---

### Post by alphacrucis2 on 2009-05-22
> **bennychidge said:**
> I am setting up a whitelist and blacklist and wish to have googlebot in my whitelist::

```
"66.249.71.225 - - [19/May/2009:17:48:43 +0000] "GET /sitemap.xml HTTP/1.1" 304 - "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
```

I also wish to place this useragent in my blacklist

```
"[error] [client 77.68.45.175] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)"
```

I cant for the life of me find how to do the drop command in iptables and I cant seem to find this anywhere on Google.

I can for an ip add 

```
-A blacklist -s 77.68.45.175 -j DROP
```

to my blacklist chain but how do I do this with a useragent? whats the syntax? Any examples? Any links?


Thanks in advance

You want it to match text in the packets? When I used netfilter/iptables it didn't have that capability, you could only match against stuff in the protocol headers but having a quick look it seems you can match text patterns in the more recent version using the string module. The man page for iptables says this:

> string

This modules matches a given string by using some pattern matching strategy. It requires a linux kernel >= 2.6.14.
--algo bm|kmp
    Select the pattern matching strategy. (bm = Boyer-Moore, kmp = Knuth-Pratt-Morris) 
--from offset
    Set the offset from which it starts looking for any matching. If not passed, default is 0. 
--to offset
    Set the offset from which it starts looking for any matching. If not passed, default is the packet size. 
--string pattern
    Matches the given pattern. --hex-string pattern Matches the given pattern in hex notation. 

I would guess you would have to be careful with this as it could suck up a bit of cpu overhead. I would suggest doing a search on iptables string match or something like that for examples.

---

### Post by alphacrucis2 on 2009-05-22
Curious about this myself I went to the source so to speak. The netfilter.org site. Have a look at the Netfilter extensions howto. In particular section 3.18.

[http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-3.html]("http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-3.html")

---

### Post by bennychidge on 2009-05-23
this is quite interesting

[http://spamcleaner.org/en/misc/w00tw00t.html](http://spamcleaner.org/en/misc/w00tw00t.html)

---

### Post by garycahill on 2011-05-24
This might help you out:

[http://www.servercircle.com/Server-Firewalls/IPtables-match-on-string-of-characters_415](http://www.servercircle.com/Server-Firewalls/IPtables-match-on-string-of-characters_415)

It's about strings and how to use them.

---

