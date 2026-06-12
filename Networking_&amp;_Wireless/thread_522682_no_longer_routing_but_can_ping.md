---
title: "no longer routing but can ping"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by sanchoquixote on 2007-08-10
Hi,
  Could you please tell me what's up? When I type a domain into browser it doesn't resolve

when im logged in under maintenance i can route no problem

checked resolve.conf and it points to router

tried wget to [www.gnome.org](www.gnome.org) works to resolve ip but doesn't get index.html

any ideas?

---

### Post by sanchoquixote on 2007-08-11
strangely, as far as far as i can tell the problem appears to exist within X, as ive said in maintenance/recovery mode everything is hunky dory but when i log in from regular startx that's when problems happen, where does routing occur in X?

---

### Post by sanchoquixote on 2007-08-11
nope wrong, even before X starts there's a problem, does anyone know how profiles are loaded? what daemons etc?

---

### Post by DeHorde on 2007-08-11
Not sure, but it sounds like it might be a networkmanager problem (due to the fact it is not a problem in repairmode). Could it be a wrong route/ using a wrong interface? (netstat -nr) Can you stil ping you router/gateway? 

Or maybe its a DNS problem:
Can you do ping 66.249.66.162 (google)? 

I think I remember having changed my /etc/nsswitch.conf because of weird errors:
```

#hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files dns

```

These are the first things I can think of...

---

