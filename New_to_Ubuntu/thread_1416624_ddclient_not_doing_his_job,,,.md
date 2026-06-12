---
title: "ddclient not doing his job,,,"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by mamut0o1 on 2010-02-26
Good morning all; I have setup ddclient a while back and from time to time I notice it does not do his Job. This morning my home server was down and I decided to do "sudo ddclient" to send an update to dyndns and nothing happens. I tried restarting the service and nada...has anyone come across a problem like this? Could it be that I have something not configured right?

Any help would be greatly appreciated.
Thanks!

Mamut

---

### Post by stoogiebuncho on 2010-02-26
Are there error messages in the output that you can post to help us out?

Run this in a terminal:
```
sudo ddclient -daemon=0 -debug -verbose -noquiet
```

If there are error messages or other things of interest, post them back here.  **Note that there will probably be some personal information in this output, including your username and password, so be sure to strip that stuff out before posting.**

---

### Post by mamut0o1 on 2010-02-26
> **stoogiebuncho said:**
> Are there error messages in the output that you can post to help us out?

Run this in a terminal:
```
sudo ddclient -daemon=0 -debug -verbose -noquiet
```

If there are error messages or other things of interest, post them back here.  **Note that there will probably be some personal information in this output, including your username and password, so be sure to strip that stuff out before posting.**

yes; it gave me a warning that "it skipped" updating my current IP from the "old one"

-So after you told me to issue that command I restarted the service again and this time I tried: sudo ddclient -force and I got this: SUCCESS:  updating ...   
So thanks it's working now. I would like to ask you where can I check or how often ddclient is suppose to send updates?

---

### Post by stoogiebuncho on 2010-02-26
> **mamut0o1 said:**
>  I would like to ask you where can I check or how often ddclient is suppose to send updates?

Glad it's working.  How often it runs really depends on how you set it up.  In the past, I have used the command 
```
sudo ln -s /usr/sbin/ddclient /etc/cron.hourly/opendns
```
to make it run hourly (as you can see, the command adds a link to ddclient in the /etc/cron.hourly/ folder, which should run every hour.

Do you remember how you set yours up originally?

---

### Post by mamut0o1 on 2010-02-26
> **stoogiebuncho said:**
> Glad it's working.  How often it runs really depends on how you set it up.  In the past, I have used the command 
```
sudo ln -s /usr/sbin/ddclient /etc/cron.hourly/opendns
```
to make it run hourly (as you can see, the command adds a link to ddclient in the /etc/cron.hourly/ folder, which should run every hour.

Do you remember how you set yours up originally?

No; to be honest I don't remember but I think I will use that soft link you sent; or is it better to use the -force statement?
If I do updates every hour; is that consider abusive?

thanks again!

---

### Post by sandyd on 2010-02-26
> **stoogiebuncho said:**
> Glad it's working. How often it runs really depends on how you set it up. In the past, I have used the command 
```
sudo ln -s /usr/sbin/ddclient /etc/cron.hourly/opendns
```
to make it run hourly (as you can see, the command adds a link to ddclient in the /etc/cron.hourly/ folder, which should run every hour.
 
Do you remember how you set yours up originally?
 the conf for ddclient is /etc/ddclient.conf

---

