---
title: "Ubuntu 12.04 intermittent DNS issue"
date: 2014-03-04
forum: Networking &amp; Wireless
---

### Post by s-sven on 2014-03-04
Suddenly I have DNS issues on my Ubuntu 12.04 desktop system. I use it as a host for 4-5 virtual machines using Vbox. Some ubuntu servers, centos servers and windows vms. All my vms, experience no network DNS issues at all. It is only on the host system that this is happening.

I have trawled the forums and found one thread with a similar problem, # out dns-masq in the network manager for example. 

I am stomped as to why this behaviour is occuring. The only thing that has changed was an update through the "Update Manager" a few days ago. I have attached a file with latest updates.
[IMG]http://gclean.se/LatestPackagesinstalled.jpg[/IMG]

I have one Dlink DGE-528T network card and the onboard Realtek RTL8111 network card, both tested and same behaviour is observed. I can think of no more way of digging to narrow down where this is going wrong.


When running dig the reponses are always timely, like 20-30ms, but when the issue appear the process hangs for seconds or a minute before displaying the results.
:~$ dig [www.google.com]("http://www.google.com")

; <<>> DiG 9.8.1-P1 <<>> [www.google.com]("http://www.google.com")
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4084
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.google.com]("http://www.google.com").                            IN         A

;; ANSWER SECTION:
[www.google.com]("http://www.google.com").                  275        IN         A          173.194.32.49
[www.google.com]("http://www.google.com").                  275        IN         A          173.194.32.48
[www.google.com]("http://www.google.com").                  275        IN         A          173.194.32.52
[www.google.com]("http://www.google.com").                  275        IN         A          173.194.32.51
[www.google.com]("http://www.google.com").                  275        IN         A          173.194.32.50

;; Query time: 30 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Tue Mar  4 08:31:28 2014
;; MSG SIZE  rcvd: 112

When I use curl, the time lapse is visible when the issue is happening.
:~$ curl -w "@curl-timing.cfg" -o /dev/null -s [http://www.google.com](http://www.google.com)
      DNS lookup                          :  5.058  #Sometimes this value is 5,10,15 even 20.x
      Connect to server (TCP)             :  5.074
      Connect to server (HTTP/S)          :  0.000
      Time from start until transfer began:  5.074
      Time for redirection (if any)       :  0.000
      Total time before transfer started  :  5.094

             Total time                   :  5.094
             Size of download (bytes)     :  258
             Average d/l speed (bytes/s)  :  50.000

When I ping, it is also visible that the DNS service somehow stops working intermittenly.
:~$ ping google.com
PING google.com (173.194.32.36) 56(84) bytes of data.
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=1 ttl=55 time=15.8 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=2 ttl=55 time=16.4 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=3 ttl=55 time=16.3 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=4 ttl=55 time=15.8 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=5 ttl=55 time=16.3 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=6 ttl=55 time=16.7 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=7 ttl=55 time=16.4 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=8 ttl=55 time=16.5 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=9 ttl=55 time=16.7 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=10 ttl=55 time=16.1 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=11 ttl=55 time=16.8 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=12 ttl=55 time=15.6 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=13 ttl=55 time=15.8 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=14 ttl=55 time=15.8 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=15 ttl=55 time=21.9 ms
64 bytes from 173.194.32.36: icmp_req=16 ttl=55 time=16.2 ms                                      #What happened here!
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=17 ttl=55 time=15.5 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=18 ttl=55 time=15.8 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=19 ttl=55 time=16.8 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=20 ttl=55 time=16.5 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=21 ttl=55 time=16.4 ms
64 bytes from arn06s02-in-f4.1e100.net (173.194.32.36): icmp_req=22 ttl=55 time=16.6 ms


I have tried using my own ISPs DNS servers, also tried with Googles open dns, I also entered the google searchdomain but it made no difference.

Does anyone have any suggestions what might go wrong here?

---

### Post by s-sven on 2014-03-05
Maybe this sheds light on the situation for someone, I tested commenting out #dns-masq again to see what happened and i get the following response when pinging google.com.

ping [www.google.com](www.google.com)
PING [www.google.com.gclean.se](www.google.com.gclean.se) (212.97.134.28) 56(84) bytes of data.
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=1 ttl=51 time=26.0 ms
64 bytes from 212.97.134.28: icmp_req=2 ttl=51 time=26.5 ms
64 bytes from 212.97.134.28: icmp_req=3 ttl=51 time=26.3 ms
64 bytes from 212.97.134.28: icmp_req=4 ttl=51 time=26.3 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=5 ttl=51 time=26.9 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=6 ttl=51 time=26.7 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=7 ttl=51 time=26.4 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=8 ttl=51 time=26.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=9 ttl=51 time=25.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=10 ttl=51 time=27.5 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=11 ttl=51 time=25.5 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=12 ttl=51 time=26.2 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=13 ttl=51 time=25.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=14 ttl=51 time=25.8 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=15 ttl=51 time=25.9 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=16 ttl=51 time=26.7 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=17 ttl=51 time=26.4 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=18 ttl=51 time=26.9 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=19 ttl=51 time=26.4 ms
64 bytes from 212.97.134.28: icmp_req=20 ttl=51 time=26.3 ms
64 bytes from 212.97.134.28: icmp_req=21 ttl=51 time=26.4 ms
64 bytes from 212.97.134.28: icmp_req=22 ttl=51 time=25.9 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=23 ttl=51 time=26.0 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=24 ttl=51 time=25.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=25 ttl=51 time=26.9 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=26 ttl=51 time=26.4 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=27 ttl=51 time=26.9 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=28 ttl=51 time=26.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=29 ttl=51 time=25.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=30 ttl=51 time=27.1 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=31 ttl=51 time=25.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=32 ttl=51 time=26.4 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=33 ttl=51 time=25.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=34 ttl=51 time=26.5 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=35 ttl=51 time=25.8 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=36 ttl=51 time=25.9 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=37 ttl=51 time=25.6 ms
64 bytes from 212.97.134.28: icmp_req=38 ttl=51 time=25.5 ms
64 bytes from 212.97.134.28: icmp_req=39 ttl=51 time=26.3 ms
64 bytes from 212.97.134.28: icmp_req=40 ttl=51 time=26.1 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=41 ttl=51 time=26.0 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=42 ttl=51 time=26.0 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=43 ttl=51 time=26.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=44 ttl=51 time=26.9 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=45 ttl=51 time=26.6 ms
64 bytes from wsb28.surf-town.net (212.97.134.28): icmp_req=46 ttl=51 time=25.8 ms



Needless to say that is not google! It looks like I have messed up the DNS settings somehow, but where? I

---

### Post by papibe on 2014-03-05
Hi s-sven.

Who is doing the DNS service in your LAN? Is it your router or a dedicated server?

Could you post the result of this command?
```
nm-tool
```
Regards.

---

### Post by s-sven on 2014-03-05
Interesting:


NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        FC:75:16:6D:F8:97

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth2  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        74:D0:2B:9C:B6:08

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.10.108
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4



It is the router who takes care of the DNS service, ubuntu is set to Automatic(DHCP) and the routers DNS servers are 195.67.199.12 and 195.67.199.13.

Looked in /etc/resolv.conf and found some lefter over config from my troubleshooting, removed all entries and restarted network manager. Now back to square one, while pinging [www.google.com](www.google.com) the following happens.

 ping [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (173.194.32.50) 56(84) bytes of data.
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=1 ttl=55 time=17.2 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=2 ttl=55 time=19.3 ms
64 bytes from 173.194.32.50: icmp_req=3 ttl=55 time=17.7 ms
64 bytes from 173.194.32.50: icmp_req=4 ttl=55 time=16.7 ms
64 bytes from 173.194.32.50: icmp_req=5 ttl=55 time=17.0 ms
64 bytes from 173.194.32.50: icmp_req=6 ttl=55 time=17.6 ms
64 bytes from 173.194.32.50: icmp_req=7 ttl=55 time=17.4 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=8 ttl=55 time=17.3 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=9 ttl=55 time=16.5 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=10 ttl=55 time=17.5 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=11 ttl=55 time=16.4 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=12 ttl=55 time=17.1 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=13 ttl=55 time=17.4 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=14 ttl=55 time=17.4 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=15 ttl=55 time=16.9 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=16 ttl=55 time=17.4 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=17 ttl=55 time=19.1 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=18 ttl=55 time=16.8 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=19 ttl=55 time=17.6 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=20 ttl=55 time=16.8 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=21 ttl=55 time=17.4 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=22 ttl=55 time=17.4 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=23 ttl=55 time=16.3 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=24 ttl=55 time=16.1 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=25 ttl=55 time=16.6 ms
64 bytes from 173.194.32.50: icmp_req=26 ttl=55 time=17.1 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=27 ttl=55 time=16.6 ms
64 bytes from 173.194.32.50: icmp_req=28 ttl=55 time=17.2 ms
64 bytes from 173.194.32.50: icmp_req=29 ttl=55 time=16.5 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=30 ttl=55 time=17.0 ms
64 bytes from arn06s02-in-f18.1e100.net (173.194.32.50): icmp_req=31 ttl=55 time=16.6 ms

---

### Post by s-sven on 2014-03-05
I discovered that the DHCP settings on the Router had the 8.8.8.8 and search domain manually set. So removed those and it now works fine!

---

### Post by papibe on 2014-03-05
I see that your machine is directly connecting to goole's DNS, so your router is not slowing down your DNS request.

Let's see if the problem lays in a network problem (from your ISP to google).

Could you post the result of this command?
```
mtr -nrc 2 8.8.8.8
```
Optionally, you could watch for a few seconds the output of this:
```
mtr -n 8.8.8.8
```
and check if there's a point where you have a significant 'Loss' of packages. You can press q to end the trace.

Let us know how it goes.
Regards.

---

### Post by s-sven on 2014-03-05
Thanks for the tip on my traceroute, that will come in handy next time troubleshooting network issues!

---

