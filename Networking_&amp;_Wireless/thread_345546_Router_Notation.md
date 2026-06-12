---
title: "Router Notation"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by Pobega on 2007-01-24
I'm trying to get my router to always recognize my laptop as one connection. What I mean is, when I connect I am always randomly assigned a name which is either new-host, new-host2 or new-host3. My desktop computer (Windows) always shows up as "Schmuck" (What I have it registered as) so everything always works right with it.

My laptop, however, changes it's name from time to time. Therefore I have to constantly go in and update my port forwarding software!

Is there any way I can set my laptop's name from within Ubuntu, or is there something I have to do in the router? (It always worked with Windows, so I've never done this myself before.)

---

### Post by koenn on 2007-01-24
add this line
```
send host-name "Schmuck" ; 
```
to /etc/dhcp3/dhclient.conf
There might already be an example ther that you can use or modify. Be sure to remove the # in front of it then.

Then, update by running
```
sudo dhclient
```

It will probably work.

---

### Post by Pobega on 2007-01-24
Worked perfectly, thanks!

---

