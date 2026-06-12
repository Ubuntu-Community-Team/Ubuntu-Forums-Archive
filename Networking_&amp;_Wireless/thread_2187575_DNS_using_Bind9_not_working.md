---
title: "DNS using Bind9 not working"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by yoyorhino on 2013-11-12
I am setting up a new system on 12.04.  I am working on DNS, but after I restart bind9 I check the log file and I keep getting this error "Nov 12 15:48:59 duncan named[29757]: dns_rdata_fromtext: /etc/bind/zones/tvbdomain.db:17: near eol: unexpected end of input"

The top 22 lines of my tvbdomain.db file are:
```

; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for home.lan
; Note: The extra ... at the end of the domain names are important.

; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be iterated upward to prevent
; undesirable consequences. A good format to use is YYYYMMDDII where
; the II index is in case you make more that one change in the same day.

$ORIGIN duncan
$TTL 1500
duncan.tvbdomain. IN SOA w3.mybusiness.com  (
    2013110817 ; serial
    360 ; refresh
    720 ; retry
    28800 ; expire
    38400) ; minimum


;NS indicates that ubuntu is the name server on home.lan
;MX indicates that ubuntu is (also) the mail server on home.lan
           IN NS duncan 
```

I keep searching and can't find what is wrong with line 17, but I am WAY new to this.  Any help you can give me would be great! 

Thanks!

---

### Post by Doug S on 2013-11-12
> **yoyorhino said:**
> ; Note: The extra ... at the end of the domain names are important.That comment line is important. You are missing some. While the error is listed as of line 17, that often doesn't mean the error actually occurs on that line, but rather just where named figured out for sure there was an error. Suggest that you use the [Ubuntu serverguide]("https://help.ubuntu.com/13.10/serverguide/dns.html") as a reference for this stuff. I would be tempted to try this (You replace the IP addresses with whatever you are really using):```
; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for home.lan
; Note: The extra ... at the end of the domain names are important.

; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be iterated upward to prevent
; undesirable consequences. A good format to use is YYYYMMDDII where
; the II index is in case you make more that one change in the same day.

$TTL 1500
@ IN SOA duncan.tvbdomain. w3.mybusiness.com. (
        2013110817 ; serial
        360 ; refresh
        720 ; retry
        28800 ; expire
        38400) ; minimum
        IN      A       192.168.1.1
;NS indicates that ubuntu is the name server on home.lan
;MX indicates that ubuntu is (also) the mail server on home.lan
@       IN      NS      duncan.tvbdomain.
duncan  IN      A       192.168.1.1
www     IN      A       192.168.1.2
```

---

### Post by yoyorhino on 2013-11-13
Thank you for your suggestions.  I am looking at the configuration page and trying to learn where it isn't working.  I made your suggestions but I still get the same error.  

```

; Use semicolons to add comments.
; Host-to-IP Address DNS Pointers for home.lan
; Note: The extra ... at the end of the domain names are important.


; The following parameters set when DNS records will expire, etc.
; Importantly, the serial number must always be iterated upward to prevent
; undesirable consequences. A good format to use is YYYYMMDDII where
; the II index is in case you make more that one change in the same day.


$ORIGIN duncan
$TTL 1500
@ IN SOA duncan.tvbdomain. (
    2013110818 ; serial
    360 ; refresh
    720 ; retry
    28800 ; expire
    38400) ; minimum
    IN A 10.18.253.34
;NS indicates that ubuntu is the name server on home.lan
;MX indicates that ubuntu is (also) the mail server on home.lan
@          IN NS duncan.tvbdomain.
duncan     IN A 10.18.253.34

```

---

### Post by yoyorhino on 2013-11-13
I think I have solved it.  I went through and deleted everything that was a copy from the previous server that I had commented out so it shouldn't have pulled any info anyways and it started giving me a "soa record not at top of zone" error.  I went back through what Doug S gave me and saw I didn't take out the $ORIGIN duncan line.  Once I did that it works great.  Hopefully the rest of the config will go smoothly.  

Thanks for the help!!

---

