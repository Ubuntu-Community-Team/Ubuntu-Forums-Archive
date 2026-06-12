---
title: "Basic DDNS setup updating IP but cant connect/ping"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by md-mrcl on 2014-10-20
Hi everyone!

[COLOR=#000000][FONT=Arial]I've been attempting to put the ddns working in my test server, which is a ubuntu server vm using NAT. After a while I've ended with the following config.
[/FONT][/COLOR]```

[COLOR=#000000][FONT=Consolas]# /etc/ddclient.conf[/FONT][/COLOR]
protocol=namecheap
use=if, if=eth0
server=dynamicdns.park-your-domain.com
login=mloureiro.com
password='ad02******************************' 
[COLOR=#000000][FONT=Consolas]@
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]And when I run ddclient, it actually did update the ip on namecheap webpage.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
```

# ddclient -daemon=0 -noquiet -debug -verbose
=== opt ====
opt{cache}                           : <undefined>
opt{cmd}                             : <undefined>
opt{cmd-skip}                        : <undefined>
opt{daemon}                          : 0
opt{debug}                           : 1
opt{exec}                            : <undefined>
opt{facility}                        : <undefined>
opt{file}                            : <undefined>
opt{force}                           : <undefined>
opt{foreground}                      : <undefined>
opt{fw}                              : <undefined>
opt{fw-login}                        : <undefined>
opt{fw-password}                     : <undefined>
opt{fw-skip}                         : <undefined>
opt{geturl}                          : <undefined>
opt{help}                            : <undefined>
opt{host}                            : <undefined>
opt{if}                              : <undefined>
opt{if-skip}                         : <undefined>
opt{ip}                              : <undefined>
opt{login}                           : <undefined>
opt{mail}                            : <undefined>
opt{mail-failure}                    : <undefined>
opt{max-interval}                    : 2592000
opt{min-error-interval}              : 300
opt{min-interval}                    : 30
opt{options}                         : <undefined>
opt{password}                        : <undefined>
opt{pid}                             : <undefined>
opt{postscript}                      : <undefined>
opt{priority}                        : <undefined>
opt{protocol}                        : <undefined>
opt{proxy}                           : <undefined>
opt{query}                           : <undefined>
opt{quiet}                           : 0
opt{retry}                           : <undefined>
opt{server}                          : <undefined>
opt{ssl}                             : <undefined>
opt{syslog}                          : <undefined>
opt{test}                            : <undefined>
opt{timeout}                         : <undefined>
opt{use}                             : <undefined>
opt{verbose}                         : 1
opt{web}                             : <undefined>
opt{web-skip}                        : <undefined>
=== globals ====
globals{daemon}                      : 60
globals{debug}                       : 1
globals{if}                          : eth0
globals{login}                       : mloureiro.com
globals{password}                    : ad02******************************
globals{protocol}                    : namecheap
globals{quiet}                       : 0
globals{server}                      : dynamicdns.park-your-domain.com
globals{use}                         : if
globals{verbose}                     : 1
=== config ====
config{@}{atime}                     : 0
config{@}{cacheable}                 : ARRAY(0x166c0d0)
config{@}{cmd}                       : <undefined>
config{@}{cmd-skip}                  :
config{@}{fw}                        :
config{@}{fw-login}                  : <undefined>
config{@}{fw-password}               :
config{@}{fw-skip}                   :
config{@}{host}                      : @
config{@}{if}                        : eth0
config{@}{if-skip}                   :
config{@}{ip}                        : <undefined>
config{@}{login}                     : mloureiro.com
config{@}{max-interval}              : 2592000
config{@}{min-error-interval}        : 300
config{@}{min-interval}              : 300
config{@}{mtime}                     : 0
config{@}{password}                  : ad02******************************
config{@}{protocol}                  : namecheap
config{@}{server}                    : dynamicdns.park-your-domain.com
config{@}{status}                    :
config{@}{use}                       : if
config{@}{warned-min-error-interval} : 0
config{@}{warned-min-interval}       : 0
config{@}{web}                       : dyndns
config{@}{web-skip}                  :
config{@}{wtime}                     : 30
=== cache ====
cache{@}{atime}                      : 1413759468
cache{@}{host}                       : @
cache{@}{mtime}                      : 0
cache{@}{status}                     : failed
cache{@}{warned-min-error-interval}  : 0
cache{@}{warned-min-interval}        : 0
cache{@}{wtime}                      : 30
cache{http://mloureiro.com}{atime}   : 0
cache{http://mloureiro.com}{backupmx} : 0
cache{http://mloureiro.com}{custom}  : 0
cache{http://mloureiro.com}{host}    : http://mloureiro.com
cache{http://mloureiro.com}{mtime}   : 0
cache{http://mloureiro.com}{mx}      :
cache{http://mloureiro.com}{script}  : /nic/update
cache{http://mloureiro.com}{static}  : 0
cache{http://mloureiro.com}{status}  : notfqdn
cache{http://mloureiro.com}{warned-min-error-interval} : 1413758503
cache{http://mloureiro.com}{warned-min-interval} : 0
cache{http://mloureiro.com}{wildcard} : 0
cache{http://mloureiro.com}{wtime}   : 30
cache{ubsrv}{atime}                  : 0
cache{ubsrv}{host}                   : ubsrv
cache{ubsrv}{ip}                     : 10.0.2.15
cache{ubsrv}{mtime}                  : 1413759524
cache{ubsrv}{status}                 : good
cache{ubsrv}{warned-min-error-interval} : 0
cache{ubsrv}{warned-min-interval}    : 0
cache{ubsrv}{wtime}                  : 30
DEBUG:    get_ip: using if, eth0 reports 10.0.2.15
DEBUG:
DEBUG:     nic_namecheap1_update -------------------
INFO:     setting IP address to 10.0.2.15 for @
UPDATE:   updating @
DEBUG:    proxy  =
DEBUG:    url    = http://dynamicdns.park-your-domain.com/update?host=@&domain=mloureiro.com&password=ad02******************************&ip=10.0.2.15
DEBUG:    server = dynamicdns.park-your-domain.com
CONNECT:  dynamicdns.park-your-domain.com
CONNECTED:  using HTTP
SENDING:  GET /update?host=@&domain=mloureiro.com&password=ad02******************************&ip=10.0.2.15 HTTP/1.0
SENDING:   Host: dynamicdns.park-your-domain.com
SENDING:   User-Agent: ddclient/3.8.1
SENDING:   Connection: close
SENDING:
RECEIVE:  HTTP/1.1 200 OK
RECEIVE:  Cache-Control: private
RECEIVE:  Content-Length: 231
RECEIVE:  Content-Type: text/html
RECEIVE:  Server: Microsoft-IIS/7.5
RECEIVE:  Set-Cookie: ASPSESSIONIDQQABQAQR=IDIKGAACKADNMOACKDGKMJDC; path=/
RECEIVE:  X-Frame-Options: SAMEORIGIN
RECEIVE:  X-Powered-By: ASP.NET
RECEIVE:  Date: Sun, 19 Oct 2014 23:07:44 GMT
RECEIVE:  Connection: close
RECEIVE:
RECEIVE:  <?xml version="1.0"?><interface-response><Command>SETDNSHOST</Command><Language>eng</Language><IP>10.0.2.15</IP><ErrCount>0</ErrCount><ResponseCount>0</ResponseCount><Done>true</Done><debug><![CDATA[]]></debug></interface-response>
SUCCESS:  updating @: good: IP address set to 10.0.2.15

```

(as can be seen on the log, it updated to 10.0.2.15 which is the default IP for NAT)

[COLOR=#000000][FONT=Arial]However when I try to connect/ping (*mloureiro.com*) it simply fails.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I've thought it could be because of the router, so I have shutdown the firewal, but still not working.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Any idea how can I fix, or at least debug this problem?[/FONT][/COLOR]

---

### Post by Doug S on 2014-10-20
Hi and welcome to Ubuntu forums.

I get:```
doug@doug-64:~$ nslookup mloureiro.com
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
Name:   mloureiro.com
Address: 10.0.2.15
```Note that 10.0.2.15 is not a public IP address, but rather reserved for local use. Therefore it is not possible to route on the Wide Area Network (WAN).

---

### Post by oldos2er on 2014-10-21
Moved to Networking & Wireless.

---

### Post by md-mrcl on 2014-10-22
> **Doug S said:**
> Hi and welcome to Ubuntu forums.

I get:```
doug@doug-64:~$ nslookup mloureiro.com
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
Name:   mloureiro.com
Address: 10.0.2.15
```Note that 10.0.2.15 is not a public IP address, but rather reserved for local use. Therefore it is not possible to route on the Wide Area Network (WAN).


Thanks for the fast reply

I've changed the:
```
use=if, if=eth0
```
to:
```
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
```

So nslookup returns:
```

root@ubsrv:~# nslookup mloureiro.com
Server:        192.168.1.1
Address:    192.168.1.1#53


Non-authoritative answer:
Name:    mloureiro.com
Address: 85.139.9.41

```

But from ping.eu site:
```

[COLOR=#A5A5A6][FONT=Verdana]Server:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**127.0.0.1**[/FONT][/COLOR]

[COLOR=#A5A5A6][FONT=Verdana]Address:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**127.0.0.1**[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]#53[/FONT][/COLOR]

[COLOR=#A5A5A6][FONT=Verdana]Non-authoritative answer:[/FONT][/COLOR]
[COLOR=#A5A5A6][FONT=Verdana]Name:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**mloureiro.com**[/FONT][/COLOR]

[COLOR=#A5A5A6][FONT=Verdana]Address:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**85.139.9.41**[/FONT][/COLOR]
```

I'm confused, my address changed form localhost to 192.168.1.1 (my router IP), should the address be the 85.139.9.41 (it's my pub address checked on checkip.dyndns.com)?



(thanks @oldos2er for moving it to the right place)

---

### Post by Doug S on 2014-10-22
> **md-mrcl said:**
> should the address be the 85.139.9.41 (it's my pub address checked on checkip.dyndns.com)?Well, unless I misunderstand what you want, yes. it has to be a public IP address for the rest of the world to be able to reach your site. However, I don't get any response for ping, nor does any web server respond (which you never said there was a web server, I just tried it is all.)

---

### Post by md-mrcl on 2014-10-28
Just to mark this as solved

> 
[COLOR=#000000]So nslookup returns:[/COLOR]
[COLOR=#000000]Code:
root@ubsrv:~# nslookup mloureiro.com
Server:        192.168.1.1
Address:    192.168.1.1#53


Non-authoritative answer:
Name:    mloureiro.com [/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]Address: 85.139.9.41
[/FONT][/COLOR]

This actually worked, not sure how, been testing several stuff on the router, and probably changed some setting that allowing the requests to pass.

THanks a lot @Doug

---

