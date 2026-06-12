---
title: "why doesn't firefox connect to internet???"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by chechojp on 2009-06-12
I am using hardy heron and my internet connection is working fine but somehow firefox wont connect, right now I am using epiphany but i need to use some firefox plugins....i tried to install firefox again but it doesnt work...help please

---

### Post by x33a on 2009-06-12
check if is set to offline mode.

file -> work offline.

if yes, then uncheck this.

---

### Post by chechojp on 2009-06-15
nope...that's not the problem.....the box is not checked....if someone needs more info to reply please tell me what to post i will do it as soon as i can

---

### Post by Sealbhach on 2009-06-15
Can you ping to websites? Try this in a terminal:

```
ping -c 5 bbc.co.uk
```

and paste the results here.

.

---

### Post by chechojp on 2009-06-15
```
sergio@sergio-laptop:~$ ping -c 5 bbc.co.uk
PING bbc.co.uk (212.58.254.252) 56(84) bytes of data.
64 bytes from virtual3.rbsov.bbc.co.uk (212.58.254.252): icmp_seq=1 ttl=243 time=236 ms
64 bytes from virtual3.rbsov.bbc.co.uk (212.58.254.252): icmp_seq=2 ttl=243 time=235 ms
64 bytes from virtual3.rbsov.bbc.co.uk (212.58.254.252): icmp_seq=3 ttl=243 time=238 ms
64 bytes from virtual3.rbsov.bbc.co.uk (212.58.254.252): icmp_seq=4 ttl=243 time=236 ms
64 bytes from virtual3.rbsov.bbc.co.uk (212.58.254.252): icmp_seq=5 ttl=243 time=235 ms

--- bbc.co.uk ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 235.656/236.586/238.838/1.218 ms
sergio@sergio-laptop:~$ 

```
My connection is working...right now I am using epiphany in my laptop so i thing the problem is only with firefox....

---

### Post by Sealbhach on 2009-06-15
Strange. It's not a DNS problem either.

Have a look in the network settings in Firefox - Edit/Preferences.


.

---

### Post by x33a on 2009-06-15
> **Sealbhach said:**
> Strange. It's not a DNS problem either.

Have a look in the network settings in Firefox - Edit/Preferences.


.

yes, maybe it's set to use a proxy.

---

### Post by PukingPenguin on 2009-06-15
Firefox has been picky in the past about the ipvb6 seetitngs. Open FF, and in the address bar type :
about:config

Type in the filter box:
ipv
and find the line that says 

```
network.dns.disableIPv6;false
```

right click to select "toggle value" to change it to:

```
network.dns.disableIPv6;true
```

Course, it could be something else, but this might do it, too. And if it borks something, just toggle the value back.

---

