---
title: "DNS resolution failed to connect Starbuck Wifi's captive page"
date: 2018-04-28
forum: Networking &amp; Wireless
---

### Post by vimsical on 2018-04-28
I am running 17.10.  It recently started to fail to connect to Starbuck's Google Wifi captive page.  It will simply state that `aruba.odyssys.net` cannot be found.  The actual URL is likely geographic dependent.

So I opened a terminal and sure enough, it is not working:
```
&#955; dig aruba.odyssys.net

; <<>> DiG 9.10.3-P4-Ubuntu <<>> aruba.odyssys.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 12298
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;aruba.odyssys.net.        IN    A

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Sat Apr 28 13:45:53 PDT 2018
;; MSG SIZE  rcvd: 46
```

But my phone was able to connect.  I checked the network setting on my phone and found that is is 8.8.8.8 (and 8.8.4.4) for name resolution.  So I used the "gear" icon on my "Google Starbuck" and set the DNS to be manual with those two IPs.  Still, the captive page does not work.

Then I decided to check if it would have worked with those IP. Yes, it would:
```
&#955; dig @8.8.8.8 aruba.odyssys.net

; <<>> DiG 9.10.3-P4-Ubuntu <<>> @8.8.8.8 aruba.odyssys.net
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 39943
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;aruba.odyssys.net.        IN    A

;; AUTHORITY SECTION:
odyssys.net.        810    IN    SOA    ns-543.awsdns-03.net. awsdns-hostmaster.amazon.com. 1 7200 900 1209600 86400

;; Query time: 180 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sat Apr 28 13:45:59 PDT 2018
;; MSG SIZE  rcvd: 127
```

So finally, I just manually edited `/etc/resolv.conf` by commenting out the the nameserver 127.0.0.53 and adding `nameserver 8.8.8.8`.  Reload the captive page.  That worked perfectly.

I do not have a good understanding of what `systemd-resolve`is doing.  I thought it was acting as a local DNS cache and it would just use the DNS server obtained from DHCP (or manual setting by NetworkManager?).  But obviously it is not forwarding name look up properly.  Manually editing `/etc/resolv.conf` would work every time I need to use the Starbucks hotspot.  But what is the more proper way to deal with this so that `systemd-resolve` knows the proper DNS server to use?

Thanks!

---

