---
title: "pidgin dns error"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by hittingpilot on 2008-07-30
```
(23:29:16) dns: Got response for 'www.facebook.com'
(23:29:16) dnsquery: Error resolving www.facebook.com:
Name or service not known
(23:29:16) facebook: host lookup error: Error resolving www.facebook.com:
Name or service not known
Segmentation fault
<usr info>:~$ dns[8629] Error: getaddrinfo returned -2
dns[8630] Error: getaddrinfo returned -2
dns[8630]: Oops, father has gone, wait for me, wait...!
dns[8629]: Oops, father has gone, wait for me, wait...!
dns[8588]: Oops, father has gone, wait for me, wait...!

```

whenever I try to run facebook or MSN, I get these DNS errors, even though I'm circumventing a proxy in favor of a direct connection. Is this a serious problem? I've reinstalled pidgin a couple times to no avail...

---

### Post by knightcoder on 2008-07-30
> ```
(23:29:16) facebook: host lookup error: Error resolving www.facebook.com:
Name or service not known
Segmentation fault
```

It crashed here, man. Wow, one dns request not available and it crashed ??

I would check network connection on pigdin port.

---

### Post by radiobuzzer on 2009-06-28
I have the same problem, for one of my MSN accounts, which holds a really lot of contacts. Maybe more than 200 contacts.

That's on the latest pidgin. Pidgin 2.5.7 (libpurple 2.5.7) and in both 8.10 and 9.04 Ubuntus. 

I am trying to find whether there is already a bug reported in launchpad.net or we should open one.

---

### Post by MikeSD on 2009-06-28
Maybe trying some free DNS servers like ones from OpenDNS.com could help?
I use them all the time, they are Better than those my ISP sets via dhcp.

---

### Post by mdaud on 2009-08-19
I had same problem . when checked logs it said no more space left on drive.
my partition was full
little cleanup solved

---

### Post by kevdog on 2009-08-19
Did this happen in 2.5.6 version?

---

### Post by Milossh on 2009-10-22
> **kevdog said:**
> Did this happen in 2.5.6 version?

Yes. My pidgin just updated and it still FAILS with Segmenation fault error :/

I have tried everything: mv purple dir, free some space, play with permissions, turned of proxy, freeing ports, and it always fails when I send a message to someone.

```
(08:33:17) jabber: Unable to find caps: buddy might be offline
(08:33:17) jabber: Sending (ssl): <message type='chat' id='purpleed3b459c' to='xxxxxx@gmail.com'><active xmlns='http://jabber.org/protocol/chatstates'/><body>test</body></message>
dns[5121]: Oops, father has gone, wait for me, wait...!
Segmentation fault
abnormal@Eniac:~$ 
```

and dns[#] is always different.

---

### Post by Milossh on 2009-10-29
Any solution?

---

