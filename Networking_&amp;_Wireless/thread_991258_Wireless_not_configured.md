---
title: "Wireless not configured??"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by sauce345 on 2008-11-23
Hello i am trying to run the command:

sudo ifdown wlan0

and it returns:

ifdown: interface wlan0 not configured

What does this mean?  I can connect to wireless networks just fine with it.  Help would be appreciated, thanks!!:)

---

### Post by bmw4l1f3 on 2008-11-24
jon, I did some searching and this is what I found

ifdown is a much higher level command than ifconfig <interface> down. The difference between the two commands is that with ifup/ifdown the process calls ifconfig, and parses the commands in the /etc/network/interfaces file, I believe passing the parameters to iwconfig, and then sets the route.

I suspect that there are no commands within the /etc/network/interfaces file. If ifup/ifdown are not working then try using the ifconfig statement instead. You are not really telling us what you want to do, so that is about as much advice as I can offer right now.


-Mac

---

### Post by melojo on 2008-11-24
post the output of 

```
lspci
```

and

```
lshw -C network
```

also you might check if there are restricted drivers that need loading.

#

Press System &#8594; Administration &#8594; Hardware drivers
let us know if their are any.
#

and enable 

This will give us some information.

---

