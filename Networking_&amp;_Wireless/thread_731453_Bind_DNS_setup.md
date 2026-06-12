---
title: "Bind DNS setup"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by colsinc on 2008-03-21
Hi.  I have been following the how to 
[http://ubuntuforums.org/showthread.php?t=236093]("http://ubuntuforums.org/showthread.php?t=236093")
but have not been able to get dns working.  My named.conf.local file contains:
[HTML]]zone "butlerbob.com" {
        type master;
        file "/etc/bind/zones/butlerbob.com.db";
        };[/HTML]

and the ./zones/butlerbob.com.db

[HTML]
butlerbob.com.          IN      SOA     ubuntu-mmx.butlerbob.com. (
                        2006081401      ;serial number, based on date
                        21600           ;refresh after 6 hours
                        3600            ;Retry after 1 hour
                        604800          ;Expire after 7 days
                        3600            ;Minimum TTL of 1 hour
)
ubuntu-mmx              IN      A       192.168.0.100
butlerbob.com.          IN      NS      ubuntu-mmx
//
ubuntu                  IN      A       192.168.0.2
www                     IN      CNAME   ubuntu[/HTML]

What am I doing wrong?

As you may have guessed, the DNS server is 192.168.0.100, and the web server is 192.168.0.2
The webserver is working and accessible at [http://localhost/](http://localhost/) locally and by 192.168.0.2 from another computer on the LAN.
I'm not forgetting to change my computers DNS to 192.168.0.100

Also if someone could tell me how to work out what the webservers address will be as I have just been using every combination I could think of for testing it - [www.ubuntu.butlerbob.com](www.ubuntu.butlerbob.com), [http://ubuntu.butlerbob.com](http://ubuntu.butlerbob.com), [www.butlerbob.com??](www.butlerbob.com??)

I'm running Xubuntu 7.10 on both these machines

Also I noticed that [www.you.com](www.you.com) seems to work the same as [http://localhost/](http://localhost/) even though there is no entry in the hosts list.  what's with this?

---

### Post by Eiríkr on 2008-03-22
A couple things --

The initial square bracket "]" in your named.conf.local file is just a typo here on the boards, right?  If that's in the actual file, it needs removing.   

Are there any errors noted in /var/log/syslog?
```
cat /var/log/syslog | grep named
```

Your zones file doesn't look quite right.  A sample based on mine:
```
;
; Zone file for home network homelan.org
;
$ttl 38400
@       IN      SOA     ubuntu.homelan.org. admin.homelan.org. (
                        1203324117      ; serial #
                        10800           ; refresh in seconds
                        3600            ; retry in seconds
                        604800          ; expire in seconds
                        38400 )         ; min in seconds
;
                NS      ubuntu        ; name server
                ; MX    10 mail.homelan.org ; Mail server, as yet unimplemented (2008-02-18)
;

localhost       A       127.0.0.1

ubuntu          A       192.168.10.10
                TXT     "Better a long wind... than a broken one."
;www            CNAME   ubuntu

modem           A       192.168.0.1
                TXT     "The DSL modem."

router          A       192.168.10.1
                TXT     "The router."

ibook           A       192.168.10.11
                TXT     "The old Mac."

ws              A       192.168.10.12
                TXT     "The main workstation."
```

The "@" at the beginning refers to the domain (zone) name, in this case [font=courier]homelan.org[/font].  Were this spelled out in the DNS conf file, it would be followed by a single period, telling the named daemon *not* to add the domain name after it.  

Conversely, any item without the period on the end will have the domain name added on.  So "ubuntu" as a fully-qualified domain name (FQDN) would become "ubuntu.homelan.org", or in your case, "ubuntu.butlerbob.com".  

One very useful tool for checking your DNS config is the [font=courier]dig[/font] command.  Have a look at [this other DNS HOWTO over on TLDP.org](http://tldp.org/HOWTO/DNS-HOWTO-5.html) for further details and some good examples of how this command can be used.  

HTH,

Eiríkr

---

