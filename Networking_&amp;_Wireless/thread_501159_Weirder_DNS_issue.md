---
title: "Weirder DNS issue"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by Buggin on 2007-07-14
I've got a primary and secondary DNS server to setup. Forward lookups are all functional on both servers. The secondary server can do reverse lookups as well (dig -x xxx.xxx.xxx.xxx). I actually copied the .rev file from secondary DNS to primary DNS. I still can not do reverse lookups. I get a no PTR error.

How can that be possible?? The same file on two Ubuntu servers running the same updated versions of everything and the secondary can do reverse lookups while the primary can't. And they are both using the same configuration file.

I updated all the serials when I last edited and reloaded bind. When I do a dig @localhost -x xxx.xxx.xxx.34 it prints out an invalid serial number that is not in any of my zone files. I'm also getting a NXDOMAIN error at this point.

Any help is greatly appreciated because I have to switch to a NEW classless subnet tomorrow so I'd like to get all the bugs worked out now. Oh, btw, it is a /26. Only I get stuck setting up a classless DNS the first time I ever attempt it.

HELP!!

---

### Post by Mr. C. on 2007-07-15
Its simply too difficult to diagnose problems based upon hearsay.  Clearly the servers are not both using the same configurations, or you'd get the same responses.

Show how you are obtaining results on both servers.  Show your SOA records for both servers.

Update both servers serial numbers, and restart bind on both servers.

How about some debug output ?  Have you enabled debug output from named to see what is going on?

You do realize that setting up classless reverse records is not straightforward, right ?

MrC

---

### Post by Buggin on 2007-07-15
i got the results by doing a dig@localhost -x ip.add.re.ss on each server
one would respond and the other wouldn't.. and the reverse zone file was an exact copy

i fixed it by starting all over on the master server and copying the zone files back over from the secondary

do a dns test on tiametcomm.com if you want to check behidn me and make suggestions but i think i got it straightened out

---

### Post by Mr. C. on 2007-07-15
That will be a challenge, since you have no A record:

```
$dig tiametcomm.com 

; <<>> DiG 9.4.1 <<>> tiametcomm.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44695
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;tiametcomm.com.                        IN      A

;; AUTHORITY SECTION:
tiametcomm.com.         255     IN      SOA     ns.tiametcomm.com. dave.tiametcomm.com. 2007071543 300 900 3600 300

;; Query time: 2 msec
;; SERVER: 192.168.3.200#53(192.168.3.200)
;; WHEN: Sun Jul 15 10:33:50 2007
;; MSG SIZE  rcvd: 76

$ dig a @ns2.tiametcomm.com. tiametcomm.com    

; <<>> DiG 9.4.1 <<>> a @ns2.tiametcomm.com. tiametcomm.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3245
;; flags: qr aa rd; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;tiametcomm.com.                        IN      A

;; AUTHORITY SECTION:
tiametcomm.com.         300     IN      SOA     ns.tiametcomm.com. dave.tiametcomm.com. 2007071543 300 900 3600 300

;; Query time: 112 msec
;; SERVER: 12.168.112.35#53(12.168.112.35)
;; WHEN: Sun Jul 15 10:34:41 2007
;; MSG SIZE  rcvd: 76

```

---

### Post by Buggin on 2007-07-15
oops... commented that out during debugging and forgot to uncomment it... my bad

---

### Post by Mr. C. on 2007-07-15
Better, but the reverse records have trouble:

$ dig tiametcomm.com                      
tiametcomm.com.         143     IN      A       12.168.112.35

$ dig -x 12.168.112.35
35.112.168.12.in-addr.arpa. 10648 IN    CNAME   35.32/27.112.168.12.in-addr.arpa.
35.32/27.112.168.12.in-addr.arpa. 148 IN PTR    ns2.tiametcomm.com.

$ dig 35.32/27.112.168.12.in-addr.arpa.
$ dig @ns.tiametcomm.com. 35.32/27.112.168.12.in-addr.arpa.

No answer from the last queries.

MrC

---

### Post by Buggin on 2007-07-15
well at this point there wouldn't be

we moved to the new classless ip range and the classless DNS hasn't been set up on the provider side yet

but then again it looks like you ran that before hand so i suppose there is an issue somewhere (it's all bad right now so I can't test anything related to reverse in anyway)

I do appreciate your help so far. What would help me most of all is if you (or anyone) could try tomorrow to do a dig @ns.tiametcomm.com -x 24.75.87.130 and if that works (IOW the provider has done their part for DNS... they said my part looked fine) then test this again and see what I might need to fix. 

Like I said this is my first attempt ever at DNS from scratch and I get stuck with a classless subnet on top of it. Only me.

BTW I'll be glad to post any config files or results from any command. I just don't know where to start... I've fixed everything I know to check. At this point I'm in need of guidance.

I will say though, that the ubuntu community has done it again, I posted this and the same thing at dnsstuff.com and I have gotten 0 replies there and plenty of viewings. [www.iloveubuntu.com](www.iloveubuntu.com)

---

### Post by Mr. C. on 2007-07-15
No results as of 7:30 PST.  I'll check again tomorrow.

MrC

---

### Post by Buggin on 2007-07-15
I'm actually waiting on updates from 2 different ISPs. The authoritative needs to point them to our provider (the entire class C) and our provider needs to point our subnet to us (which has been done as far as I can tell). I imagine it will get fixed in the AM tomorrow. If you can help me fix any config errors after that I'd really appreciate it.

---

### Post by Mr. C. on 2007-07-16
Yeah, that's typical.   I'll check again tomorrow.

MrC

---

### Post by Mr. C. on 2007-07-16
5:48pm PDT: no response to:

```
$ dig -x 24.75.87.131
```

MrC

---

### Post by Buggin on 2007-07-16
yeah.. according to dnsstuff.com reverse lookups they have duplicate zone entries for that class C... maybe they made the new one without getting rid of the old (broken) one

---

