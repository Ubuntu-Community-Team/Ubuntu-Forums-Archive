---
title: "nmap"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Malice007 on 2009-08-13
I want to find every local ip on my whole network. When I type:

sudo nmap -O 192.168.2.0/24 

I get only the wireless router and my laptop. What I want is everything not just wireless. Example my popcorn hour media box IP and info..the wired computers ips that are connected to the hub/switch. 

Is there a way to do this?

---

### Post by credobyte on 2009-08-13
If it would be possible, you could *map* the whole city :)

---

### Post by rbc on 2009-08-13
Try this:
sudo nmap -PR -sP 192.168.1.0/24j

---

### Post by Malice007 on 2009-08-13
sudo nmap -PR -sP 192.168.1.0/24j

is not giving my the os and what the device is.. I have over 24 computers wired in....I want to get the os and the ip of everything with the laptop.....

---

### Post by Malice007 on 2009-08-13
What I want and it does not have to be nmap is. I want to turn on my laptop type a command or open a program and have it list all the ip's wired/wireless and the os's. I have many computers on batery backup and they keep the same ip but some items like the one media box changes ips when shut off or power loss..

---

### Post by rbc on 2009-08-13
[http://nmap.org/zenmap/](http://nmap.org/zenmap/)
zenmap is a GUI frontend for nmap. I am not sure if it lists the types of operating systems.
There is also AngryIP Scanner. There is a Debian/Ubuntu version, but it does not list the OS type.

---

### Post by hovzio on 2009-08-13
try this, this should give you just about everything:
```

sudo nmap -T Aggressive -O -v 192.168.1.*
```


this will give some info to the os if available, it picks up a bunch of stuff, the  "*" glob at the end will try anything available  whithin 192.168.2.1-255; i think its 255 :)  For the os detection you have to run nmap with root privs... like mentioned above zennmap may be easier to use. Otherwise nmap has a long but nice man page. From what you described, nmap is exactly what you are looking for, you can even set up little script run from cron to check every so often, this could be put in a log file, this in turn could also be turned over to a series of tests(some regex per chance?)... happy computing

---

