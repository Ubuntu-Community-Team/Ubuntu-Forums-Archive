---
title: "How can I see exactly what is downloading?"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-02-25
I'm running 10.10 and my conky shows that I'm constantly downloading.  Sometimes it is 4 or 5 Kib other times more.  I think part of this is a script I have that checks my Gmail, but how can I see exactly what is connecting to where and what is being downloaded?

---

### Post by runeh76 on 2011-02-25
Im not sure what u exactly mean, but u can check ur open connections with
```
netstat -t
```

---

### Post by seawolf167 on 2011-02-25
pktstat will show everything that is being transferred over a specific interface

```
sudo apt-get install pktstat
```

then figure out which interface you are using

```
ifconfig
```

and pass it to pktstat (it'll probably be eth0)

```
sudo pktstat -i eth0
```

---

### Post by uRock on 2011-02-25
EtherApe will show who you are connecting to and can be used to deduct what is connecting to the web.

---

### Post by GrouchyGaijin on 2011-02-25
> **runeh76 said:**
> Im not sure what u exactly mean, but u can check ur open connections with
```
netstat -t
```
Thanks 
When I tun netstat -t I get this:

```

Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 john-laptop:59637       ber01s02-in-f147.:https ESTABLISHED
tcp        1      0 john-laptop:41949       a93-158-110-171.dep:www CLOSE_WAIT 
tcp        0      0 john-laptop:34859       ber01s02-in-f147.1e:www ESTABLISHED
tcp        0      0 john-laptop:46341       ber01s02-in-f83.1:https ESTABLISHED
tcp        0      0 john-laptop:46342       ber01s02-in-f83.1:https ESTABLISHED
tcp        0      0 john-laptop:37335       ber01s02-in-f83.1:https ESTABLISHED
tcp        0      0 localhost.localdo:46198 localhost.localdo:56871 ESTABLISHED
tcp        0      0 john-laptop:41347       ec2-174-129-193-1:https ESTABLISHED
tcp        0      0 john-laptop:38270       ber01s02-in-f189.:https ESTABLISHED
tcp        0      0 john-laptop:50736       95.100.5.115:www        ESTABLISHED
tcp        0      0 john-laptop:57008       ber01s02-in-f18.1:https TIME_WAIT  
tcp        0      0 john-laptop:34739       ber01s02-in-f165.:https ESTABLISHED
tcp        1      0 john-laptop:44808       geotrust-crl-ilg.ve:www CLOSE_WAIT 
tcp        1      0 john-laptop:41948       a93-158-110-171.dep:www CLOSE_WAIT 
tcp        1      0 john-laptop:41950       a93-158-110-171.dep:www CLOSE_WAIT 
tcp        0      0 john-laptop:37323       ber01s02-in-f83.1:https ESTABLISHED
tcp        1      0 john-laptop:41947       a93-158-110-171.dep:www CLOSE_WAIT 
tcp        0      0 localhost.localdo:56871 localhost.localdo:46198 ESTABLISHED
tcp        0      0 localhost.localdo:56871 localhost.localdo:46198 ESTABLISHED

```
How can I expand the fields so I can read the urls?

---

### Post by GrouchyGaijin on 2011-02-25
> **seawolf167 said:**
> pktstat will show everything that is being transferred over a specific interface

```
sudo apt-get install pktstat
```

then figure out which interface you are using

```
ifconfig
```

and pass it to pktstat (it'll probably be eth0)

```
sudo pktstat -i eth0
```

Thank you

It is eth0.  When I run it I get this:
```


 bps    % desc                                                                                 
 21.4k  37% arp
            icmp echo ALL-SYSTEMS <-> dyn-ks-net85-cust147
  21.3   0% icmp6 :: <-> ff02::1:ff65:f99a
  70.5   0% icmp6 fe80::14d8:320a:8586:eeed <-> ff02::1:ffee:d13d
 141.0   0% icmp6 fe80::1851:ec43:4f90:243f <-> ff02::1:ffee:d13d
            icmp6 fe80::18a6:3316:95ee:625e <-> ff02::1:ff1d:13cd
            icmp6 fe80::18a6:3316:95ee:625e <-> ff02::1:ff4a:304f
            icmp6 fe80::18a6:3316:95ee:625e <-> ff02::1:ff7d:202e
            icmp6 fe80::18a6:3316:95ee:625e <-> ff02::1:ff97:32d5
            icmp6 fe80::18a6:3316:95ee:625e <-> ff02::1:ffa1:b76f
  23.5   0% icmp6 fe80::18a6:3316:95ee:625e <-> ff02::1:ffaa:f95a
            icmp6 fe80::1d66:a90b:5c97:32d5 <-> ff02::1:ff16:ee7b
            icmp6 fe80::1d66:a90b:5c97:32d5 <-> ff02::1:ff46:73b8
            icmp6 fe80::1d66:a90b:5c97:32d5 <-> ff02::1:ff54:8930
            icmp6 fe80::1d66:a90b:5c97:32d5 <-> ff02::1:ff57:6756
            icmp6 fe80::1d66:a90b:5c97:32d5 <-> ff02::1:ff5f:20c8
            icmp6 fe80::1d66:a90b:5c97:32d5 <-> ff02::1:ffa1:1049
resolving 85.89.91.192

```
I have no idea what this means.  Is there a way to interpret this?

---

### Post by runeh76 on 2011-02-25
> **GrouchyGaijin said:**
> Thanks 
When I tun netstat -t I get this:

```

Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 john-laptop:59637       ber01s02-in-f147.:https ESTABLISHED
tcp        1      0 john-laptop:41949       a93-158-110-171.dep:www CLOSE_WAIT 
tcp        0      0 john-laptop:34859       ber01s02-in-f147.1e:www ESTABLISHED
tcp        0      0 john-laptop:46341       ber01s02-in-f83.1:https ESTABLISHED
tcp        0      0 john-laptop:46342       ber01s02-in-f83.1:https ESTABLISHED
tcp        0      0 john-laptop:37335       ber01s02-in-f83.1:https ESTABLISHED
tcp        0      0 localhost.localdo:46198 localhost.localdo:56871 ESTABLISHED
tcp        0      0 john-laptop:41347       ec2-174-129-193-1:https ESTABLISHED
tcp        0      0 john-laptop:38270       ber01s02-in-f189.:https ESTABLISHED
tcp        0      0 john-laptop:50736       95.100.5.115:www        ESTABLISHED
tcp        0      0 john-laptop:57008       ber01s02-in-f18.1:https TIME_WAIT  
tcp        0      0 john-laptop:34739       ber01s02-in-f165.:https ESTABLISHED
tcp        1      0 john-laptop:44808       geotrust-crl-ilg.ve:www CLOSE_WAIT 
tcp        1      0 john-laptop:41948       a93-158-110-171.dep:www CLOSE_WAIT 
tcp        1      0 john-laptop:41950       a93-158-110-171.dep:www CLOSE_WAIT 
tcp        0      0 john-laptop:37323       ber01s02-in-f83.1:https ESTABLISHED
tcp        1      0 john-laptop:41947       a93-158-110-171.dep:www CLOSE_WAIT 
tcp        0      0 localhost.localdo:56871 localhost.localdo:46198 ESTABLISHED
tcp        0      0 localhost.localdo:56871 localhost.localdo:46198 ESTABLISHED

```
How can I expand the fields so I can read the urls?

Thats a real good question  :lolflag:  i wanna know too!!?
I think u could use what urock posted, but i try to check if u can use netstat like that.

---

### Post by runeh76 on 2011-02-25
Here u go

```
netstat -t -n
```
:popcorn:



edit: didnt remember say this...u can check with ```
netstat --help
``` different variants.

---

### Post by GrouchyGaijin on 2011-02-25
> **uRock said:**
> EtherApe will show who you are connecting to and can be used to deduct what is connecting to the web.

With etherape I get an error that no suitable device is found.

---

### Post by uRock on 2011-02-25
> **GrouchyGaijin said:**
> With etherape I get an error that no suitable device is found.
You have to run it as root, which should be offered in your Applications> Internet menu. If not, then run **sudo etherape** in a terminal.

---

### Post by GrouchyGaijin on 2011-02-25
sudo etherape worked - thank you!

---

