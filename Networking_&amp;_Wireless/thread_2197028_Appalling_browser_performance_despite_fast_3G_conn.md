---
title: "Appalling browser performance despite fast 3G connection"
date: 2014-01-01
forum: Networking &amp; Wireless
---

### Post by felgro on 2014-01-01
This is a recent problem that is making me punch holes through walls. Two points up front -


    1. My connection speed is fine. Using the various speedtest tools out there, it is consistently over 1mbps, 6mbps+ on a good day.
    2. My download speeds and file transfers (P2P, torrents, ftp etc.) are similarly fine. 



My browser performance (whether FF, Chrome or Opera) however is decidedly NOT fine. Over the last few weeks it has been in the toilet. HTTP is bad and HTTPS is worse.

I used curl as described at -

How to debug slow browsing speed?

to try and see what the problems may be. These are the outputs -

```


bob@beelzebubba:~/curl$ curl -w "@curl-timing.cfg" -o /dev/null -s http://www.google.com/

  DNS lookup                          :  0.162
  Connect to server (TCP)             :  0.442
  Connect to server (HTTP/S)          :  0.000
  Time from start until transfer began:  0.442
  Time for redirection (if any)       :  0.000
  Total time before transfer started  :  0.752

         Total time                   :  0.752
         Size of download (bytes)     :  260
         Average d/l speed (bytes/s)  :  345.000

bob@beelzebubba:~/curl$ curl -w "@curl-timing.cfg" -o /dev/null -s https://www.facebook.com/

  DNS lookup                          :  0.230
  Connect to server (TCP)             :  0.729
  Connect to server (HTTP/S)          :  1.620
  Time from start until transfer began:  1.620
  Time for redirection (if any)       :  0.000
  Total time before transfer started  :  2.079

         Total time                   :  2.080
         Size of download (bytes)     :  0
         Average d/l speed (bytes/s)  :  0.000

bob@beelzebubba:~/curl$ curl -w "@curl-timing.cfg" -o /dev/null -s https://www.google.com/

  DNS lookup                          :  0.118
  Connect to server (TCP)             :  0.435
  Connect to server (HTTP/S)          :  1.375
  Time from start until transfer began:  1.375
  Time for redirection (if any)       :  0.000
  Total time before transfer started  :  1.825

         Total time                   :  1.825
         Size of download (bytes)     :  263
         Average d/l speed (bytes/s)  :  144.000

```

Generally terrible. My questions are -


    What could cause this out of the blue?
    How can I fix it? There is very little of help googling. 



Yes I've cleared caches, nuked cookies, started browsers in safe mode etc.

---

### Post by felgro on 2014-01-02
Same old story. Spent days spitting blood over an annoying problem, finally resort to posting help request - then almost immediately find a fix. Only found by accident via a link from a virtual machine tech forum -

[URL="http://askubuntu.com/questions/272358/extrememly-slow-dns-lookup/272574#272574"]http://askubuntu.com/questions/272358/extrememly-slow-dns-lookup/272574#272574

[/URL]```

127.0.1.1 is the loopback IP address on which the  NetworkManager-controlled instance of dnsmasq listens. 
Dnsmasq runs  locally and accepts DNS queries at 127.0.1.1 and forwards these queries  to an external 
nameserver whose address is furnished by NetworkManager.  This scheme does not always work well and 
if you have any problem with  it (as you do) then it is advisable to disable NetworkManager-controlled  dnsmasq. 

To disable it, edit /etc/NetworkManager/NetworkManager.conf

  sudo gedit /etc/NetworkManager/NetworkManager.conf
  
and comment out the line
  dns=dnsmasq
 
so that it looks like the following.
  #dns=dnsmasq
  
Then restart network-manager.
```

Seems to have don the trick.

[URL="http://askubuntu.com/questions/272358/extrememly-slow-dns-lookup/272574#272574"]
[/URL]

---

