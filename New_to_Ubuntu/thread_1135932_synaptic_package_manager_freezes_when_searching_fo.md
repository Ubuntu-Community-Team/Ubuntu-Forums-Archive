---
title: "synaptic package manager freezes when searching for best server."
date: 2009-04-24
forum: New to Ubuntu
---

### Post by thebestofall007 on 2009-04-24
hi, i just upgraded my intrepid ibex to jaunty and i am having a problem with synaptic package manager locking up (graying out) when i go to settings>repositories>download from other server. when i click "select best server" option the problem shows and i have to force the app to quit. 

does anyone else have this bug?

if i open it with the terminal, i get this output:

lou@lou-laptop:~$ sudo synaptic
synaptic: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
lou@lou-laptop:~$ 

the fatal IO error happens after i forced the app to quit.

---

### Post by spiderbatdad on 2009-04-24
Please check to see if you have a file called /etc/apt/apt.conf
and post any contents back here.

---

### Post by thebestofall007 on 2009-04-25
> **spiderbatdad said:**
> Please check to see if you have a file called /etc/apt/apt.conf
and post any contents back here.

that file does not exist on my system.

---

### Post by spiderbatdad on 2009-04-25
You are probably experiencing a temporary problem related to the timing of your action. The servers are all under extreme load for several days after a new release.

---

### Post by thebestofall007 on 2009-04-25
> **spiderbatdad said:**
> You are probably experiencing a temporary problem related to the timing of your action. The servers are all under extreme load for several days after a new release.

i'll post back if the problem still persists.

---

### Post by thebestofall007 on 2009-04-25
i have a feeling this is a bug because i can manually ping addresses shown below the meter using the ping command in the terminal and address(es) return a reply.

for example if i ping the address ftp.riken.jp i get:

lou@lou-laptop:~$ ping ftp.riken.jp
PING riksun.riken.go.jp (134.160.38.1) 56(84) bytes of data.
64 bytes from riksun.riken.go.jp (134.160.38.1): icmp_seq=1 ttl=44 time=263 ms
64 bytes from riksun.riken.go.jp (134.160.38.1): icmp_seq=2 ttl=44 time=272 ms
64 bytes from riksun.riken.go.jp (134.160.38.1): icmp_seq=3 ttl=44 time=266 ms
64 bytes from riksun.riken.go.jp (134.160.38.1): icmp_seq=4 ttl=44 time=262 ms
64 bytes from riksun.riken.go.jp (134.160.38.1): icmp_seq=5 ttl=44 time=265 ms
64 bytes from riksun.riken.go.jp (134.160.38.1): icmp_seq=6 ttl=44 time=269 ms
64 bytes from riksun.riken.go.jp (134.160.38.1): icmp_seq=7 ttl=44 time=274 ms
^C
--- riksun.riken.go.jp ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6001ms
rtt min/avg/max/mdev = 262.431/267.718/274.675/4.397 ms
lou@lou-laptop:~$

if i wait for the app to "fix itself" (like one would do if a program is simply unresponsive) it stays locked up.

---

### Post by lxme on 2009-04-27
Up;

Same problem here.
no /etc/apt/apt.conf 

I don't believe it will fix itself either.

---

### Post by thebestofall007 on 2009-05-02
well, crap. i was installing windows xp as a dual boot (NOT because i wanted to but because i had to) in order to run a firmware update tool for an rca pearl mp3 player that only runs on windows and windows hammered my bootloader (dammit windows, i hate you and you are now banned from my hard drive). i couldnt repair grub so i had to reinstall jaunty and for some reason, THE SERVER SEARCH TOOL WORKS NOW on my system! i am still curious, however, if anyone else has had this problem with the server tool.

---

