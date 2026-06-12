---
title: "connected to network but not internet"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by K.krstnsn on 2009-01-26
ok, so i have this INSANE issue with ubuntu. 

Lets say im connected to a wireless network, which is connected to the internet. Sometimes when i comeback to my computer while its been idle for a little bit. itll be connected to the network but not the internet. The only fix is to reboot the computer..... 


Things ive tried.

[LIST]
[*]Switch networks
[*]Turn on/off networkcard
[/LIST]

---

### Post by sarath_it on 2009-01-26
Well I cant answer your problem, given limited avenues, but I can guide u to somethings that might help.

is this your home wireless network? 
check routers's dchp clients table.. is your comp still connected?

try 
ifconfig wlan0 down
ifconfig wlan0 up

/etc/init.d/networking restart

check the syslog in
gnome-system-log

---

### Post by K.krstnsn on 2009-01-26
Well, i have a static ip set.

The thing i think is weird is.... if i reconnect to my network. itll reconnect to the network but theres still no internet. The same thing happens if i connect to another open network around me. It connects but there is no internet.

---

### Post by sarath_it on 2009-01-26
How about dns? is that working? 
check route info in gnome-nettool
 
next time, keep the syslog open, may be u will see something interesting :)

---

### Post by ussndmac on 2009-01-26
> **K.krstnsn said:**
> Well, i have a static ip set.

The thing i think is weird is.... if i reconnect to my network. itll reconnect to the network but theres still no internet. The same thing happens if i connect to another open network around me. It connects but there is no internet.


Hmm...this is similar to what happens to my machine with wifi.

- the pc says it sees the wap
- the wap log says the pc connected
- the pc can't ping the wap or anything on the net the wap is wired to

the entire network is static ip so dns should be out of the picture...

Mac

---

