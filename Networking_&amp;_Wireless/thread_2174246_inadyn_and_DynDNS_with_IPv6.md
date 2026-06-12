---
title: "inadyn and DynDNS with IPv6"
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by geohei on 2013-09-13
Hi.

Did anybody successfully manage to configure inadyn in order to transmit an IPv6 address to DnDNS (dyndns.org).
If yes, many I have the details (= insdyn.conf).
If not, is there any other DDNS cient (e.g. ddclient, ...?) which is able to do this?

Thanks,

---

### Post by sanderj on 2013-09-14
Hi,

In the past, I've used inadyn-mt to do AAAA dyndns.


From my archive:

```

inadyn-mt \
--dyndns_system [email]default@freedns.afraid.org[/email] \
--alias blabla.mooo.com,U3hWYTdVblablalbalMTM0 ip6 \
--ip_server_name ipv6.whatismyv6.com /

```


I don't know if things still work; the dyndns landscape has changed.

---

### Post by geohei on 2013-09-14
Thanks a lot, but this doesn't work either.
It really seems that a lot changed regarding DDNS.
However I'm surprised that routers like FRITZ!Box manage to handle DDNS (in my case DynDNS) for IPv4 and IPv6 without any problem.

BTW ... DynDNS support said yesterday that they will issue a client "soon", whatever this means ...

---

### Post by sanderj on 2013-09-14
I checked, and it all works for me:

sudo apt-get install libao-dev
Get inadyn-mt (note the mt) from [http://sourceforge.net/projects/inadyn-mt/](http://sourceforge.net/projects/inadyn-mt/) , unpack, configure, make, make install

Go to [http://freedns.afraid.org/](http://freedns.afraid.org/) and register an account and a subdomain. Manually create an AAAA for it (as a test).
Then go to [http://freedns.afraid.org/dynamic/](http://freedns.afraid.org/dynamic/) and find the long secret code for your subdomain (tip: bottom of page, in the 'wget' 'curl' or 'crontab' command)
With that code, run inadyn-mt like below

That works for me. Hopefully this info helps you?


```
$ inadyn-mt --dyndns_system default@freedns.afraid.org --alias somethingblabla.mooo.com,somesecretpdjBOb1VDOjEwMTMzMzAy ip6 --ip_server_name dhis.org /
Sat Sep 14 07:42:09 2013: S:INADYN: Started 'inadyn-mt version 02.24.38_audible' - dynamic DNS updater.
Sat Sep 14 07:42:11 2013: N:DYNDNS: My IP address: 2001:470:aaaa:bbbb:4eb:4097:9a7a:cf70
Sat Sep 14 07:42:11 2013: W:INADYN: IP address for alias 'somethingblabla.mooo.com:ip6' needs update to '2001:470:aaaa:bbbb:4eb:4097:9a7a:cf70'...
Sat Sep 14 07:42:13 2013: W:INADYN: Alias 'somethingblabla.mooo.com' to IP '2001:470:aaaa:bbbb:4eb:4097:9a7a:cf70' updated successfully.
Sat Sep 14 07:42:13 2013: W:INADYN: DYNDNS Server response:
HTTP/1.1 200 OK
Server: nginx
Date: Sat, 14 Sep 2013 05:42:13 GMT
Content-Type: text/plain
Content-Length: 93
Connection: close
Vary: Accept-Encoding
Cache-Control: no-store, no-cache, must-revalidate
Cache-Control: post-check=0, pre-check=0
Pragma: no-cache
Expires: Mon, 26 Jul 1997 05:00:00 GMT
X-Cache: MISS

Updated 1 host(s) somethingblabla.mooo.com to 2001:470:aaaa:bbbb:4eb:4097:9a7a:cf70 in 0.104 seconds
```

---

### Post by geohei on 2013-09-14
That looks very good. Many thanks for the testing!
I'll give it a try this afternoon.

Meanwhile some more ?s.
1. Is this secret code (hash) for you "U3hWYTdVblablalbalMTM0" (posting above)?
2. Do you know if hash is also required for dyndns.org (Provider: DynDNS)?
3. Is afraid.org totally free and has no expiry (like free DynDNS after 1 month)?

... later ...

I did some testing.

a. I managed to find my hash!
b. I only have inadyn as opposed to inadyn-mt. Do I need inadyn-mt or is inadyn sufficient?
c. inadyn works for ipv4 on afraid.org, but the "ip6" tag after "--alias" is not accepted!

... later ...

Stuck!
./configure works without errors.
make fails ...

```
root@mede-u1204:/home/geohei/inadyn-mt.v.02.24.38# make
Making all in src
make[1]: Entering directory `/home/geohei/inadyn-mt.v.02.24.38/src'
make  all-am
make[2]: Entering directory `/home/geohei/inadyn-mt.v.02.24.38/src'
gcc -DHAVE_CONFIG_H -I.    -I /usr/local/include -I /usr/local/include -g -O2  -g -O2 -MT inadyn_mt-base64utils.o -MD -MP -MF .deps/inadyn_mt-base64utils.Tpo -c -o inadyn_mt-base64utils.o `test -f 'base64utils.c' || echo './'`base64utils.c
mv -f .deps/inadyn_mt-base64utils.Tpo .deps/inadyn_mt-base64utils.Po
gcc -DHAVE_CONFIG_H -I.    -I /usr/local/include -I /usr/local/include -g -O2  -g -O2 -MT inadyn_mt-dyndns.o -MD -MP -MF .deps/inadyn_mt-dyndns.Tpo -c -o inadyn_mt-dyndns.o `test -f 'dyndns.c' || echo './'`dyndns.c
In file included from dyndns.h:39:0,
                 from dyndns.c:107:
wave_util.h:35:19: fatal error: ao/ao.h: No such file or directory
compilation terminated.
make[2]: *** [inadyn_mt-dyndns.o] Error 1
make[2]: Leaving directory `/home/geohei/inadyn-mt.v.02.24.38/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/geohei/inadyn-mt.v.02.24.38/src'
make: *** [all-recursive] Error 1
root@mede-u1204:/home/geohei/inadyn-mt.v.02.24.38#
```

Thanks,

---

### Post by geohei on 2013-09-14
Hi.

Sorry ... newbie question:

Compile error:
```
...
ao/ao.h: No such file or directory
...
```

[http://ubuntuforums.org/showthread.php?t=2174246&p=12788363#post12788363]("http://ubuntuforums.org/showthread.php?t=2174246&p=12788363#post12788363")

Can someone help?

Thanks,

---

### Post by steeldriver on 2013-09-14
Did you remember to do this?
vvvvvvvvvvvvvvvvvvvvvvvvv

> **sanderj said:**
> 
sudo apt-get install libao-dev


---

### Post by bapoumba on 2013-09-14
Threads merged.

---

### Post by geohei on 2013-09-14
> **sanderj said:**
> ...
sudo apt-get install libao-dev
...
That's what I missed! Thanks steeldriver !!!
> **bapoumba said:**
> Threads merged.
Thanks for the merge!

All works fine. Also for DynDNS.
```
root@radome:/home/geohei/inadyn-mt.v.02.24.38# inadyn-mt
Sat Sep 14 20:28:17 2013: S:INADYN: Started 'inadyn-mt version 02.24.38_audible' - dynamic DNS updater.
Sat Sep 14 20:28:19 2013: N:DYNDNS: My IP address: 2001:1610:xxxx:xxxx:ba27:yyyy:fe62:yyyy
Sat Sep 14 20:28:19 2013: W:INADYN: IP address for alias 'zzzz.dyndns.org:ip6' needs update to '2001:1610:xxxx:xxxx:ba27:yyyy:fe62:yyyy'...
Sat Sep 14 20:28:20 2013: W:INADYN: Alias 'zzzz.dyndns.org' to IP '2001:1610:xxxx:xxxx:ba27:yyyy:fe62:yyyy' updated successfully.
Sat Sep 14 20:28:20 2013: W:INADYN: DYNDNS Server response:
HTTP/1.1 200 OK
Date: Sat, 14 Sep 2013 20:28:20 GMT
Server: Apache
X-User-Status: vip
Content-Type: text/plain
Accept-Ranges: none
Connection: close

good aaa.93.ccc.ddd
```
DynDNS config looks like this:

/etc/inadyn-mt.conf
```

root@radome:/home/geohei/inadyn-mt.v.02.24.38# cat /etc/inadyn-mt.conf
# /etc/inadyn-mt.conf
username <username>
password <password>
alias zzzz.dyndns.org ip6
dyndns_system dyndns@dyndns.org
update_period_sec 600
ip_server_name dhis.org \
```
MANY THANKS FOR THE HELP !!!

---

### Post by geohei on 2013-09-18
After some days now, I noticed that, if the IPv4 or IPv6 is changed using DynDNS web site, inadyn-mt doesn't detect this. It seems that inadyn-mt doesn't check the hostame zzzz.dyndns.org and only uses /tmp/inadyn_ip.cache to check. If I delete this file, the update works again.

Is there any option which tells inadyn-mt to actually check zzzz.dyndns.org instead of using /tmp/inadyn_ip.cache and just assuming that the addresses didn't change?

---

