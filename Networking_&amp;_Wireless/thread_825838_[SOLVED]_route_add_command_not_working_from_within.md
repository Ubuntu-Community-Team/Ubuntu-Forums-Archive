---
title: "[SOLVED] route add command not working from within script"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by JohnsonCT on 2008-06-11
I have a script that adds a couple of routes that I want to execute after initiating a PPPoE connection. A sample from the script is as follows:

```
#!/bin/sh
route add -net 41.160.0.0 netmask 255.240.0.0 ppp0
route add -net 196.208.0.0 netmask 255.248.0.0 ppp0
route add -net 41.144.0.0 netmask 255.248.0.0 ppp0
route add -net 41.240.0.0 netmask 255.248.0.0 ppp0
route add -net 164.148.0.0 netmask 255.252.0.0 ppp0
route add -net 196.208.0.0 netmask 255.252.0.0 ppp0
```

If I execute the script so: :$ sudo ./AddRoutes.sh

I get a **SIOCADDRT: No such device** error. This error is repeated for every time route is called.

The strange thing is, if I simply type any one of the 'route add ...' commands in at the command line, it works as expected.

Why does this not work from within a script, yet works fine at the command line?

Any help will be appreciated.

---

### Post by nixscripter on 2008-06-11
Try putting this in your script before the commands, just as a check. See if it fails:

```

if ifconfig -a | grep ppp0 >/dev/null
then 
     echo "Setting up ppp0..."
else 
     echo "Interface ppp0 not found" &1>2
     exit 1
fi

```

---

### Post by JohnsonCT on 2008-06-11
> **nixscripter said:**
> Try putting this in your script before the commands, just as a check. See if it fails:

```

if ifconfig -a | grep ppp0 >/dev/null
then 
     echo "Setting up ppp0..."
else 
     echo "Interface ppp0 not found" &1>2
     exit 1
fi

```

The script returns "Setting up ppp0..." so the interface is definitely there.

What else could be causing this?

---

### Post by JohnsonCT on 2008-06-13
I'm still struggling with this. The ppp0 interface is definitely there. It also shows up in ifconfig, yet I'm still getting the SIOCADDRT: No such device error.

What could cause this error if the device does exist?

---

### Post by nixscripter on 2008-06-13
Other people have had the same problem, without an answer. I also mixed up the SIOCADDRT and SIOCSIFADDR errors, I think.

The former (your case), ironically, usually happens when there is no route to the network. Since you didn't specify a gateway for those entries, it has to go look for one, and if the network is not known (i.e. there is no device configured with that address), it will complain.

What is your routing table before you attempt to execute the script, and after you succeed by hand? I'm also assuming you're root for all this.

One other thing just occurred to me:

```

route add -net 41.160.0.0 netmask 255.240.0.0 ppp0
[color=red]route add -net 196.208.0.0 netmask 255.248.0.0 ppp0[/color]
route add -net 41.144.0.0 netmask 255.248.0.0 ppp0
route add -net 41.240.0.0 netmask 255.248.0.0 ppp0
route add -net 164.148.0.0 netmask 255.252.0.0 ppp0
[color=red]route add -net 196.208.0.0 netmask 255.252.0.0 ppp0[/color]

```

Why one network with two masks?

---

### Post by nixscripter on 2008-06-13
EDIT: whoops, this was a double post. How do I delete it?

---

### Post by JohnsonCT on 2008-06-13
> **nixscripter said:**
> What is your routing table before you attempt to execute the script, and after you succeed by hand? I'm also assuming you're root for all this.


The script itself is run using sudo. The routing table before running a manual route add is:
```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
196.209.21.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0

```

and after:
```

$ sudo route add -net 17.255.248.0 netmask 255.255.254.0 ppp0
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
196.209.21.1    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
17.255.248.0    0.0.0.0         255.255.254.0   U     0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0

```

If one must specify a gateway for this to work, what would one put for the gateway for a PPP connection?

> **nixscripter said:**
> 
One other thing just occurred to me:

```

route add -net 41.160.0.0 netmask 255.240.0.0 ppp0
[color=red]route add -net 196.208.0.0 netmask 255.248.0.0 ppp0[/color]
route add -net 41.144.0.0 netmask 255.248.0.0 ppp0
route add -net 41.240.0.0 netmask 255.248.0.0 ppp0
route add -net 164.148.0.0 netmask 255.252.0.0 ppp0
[color=red]route add -net 196.208.0.0 netmask 255.252.0.0 ppp0[/color]

```

Why one network with two masks?

I didn't notice that. I got this routing information from my ISP. Strange that their router would have redundant entries like that. I'm sure it wouldn't break the routing, if I could get it to work automatically!

---

### Post by nixscripter on 2008-06-14
You seem to have one destination set up in the beginning: 196.209.21.1.

At the risk of ticking off your ISP, what happens if you first:

```
sudo route add default gw 196.209.21.1
``` in the script?

---

### Post by JohnsonCT on 2008-06-17
I've solved the problem. I was generating the script from Windows and there was a carriage return and newline character at the end of each line. As a result, the interface was ppp0^M, which doesn't exist. Strange that bash wouldn't pick this up as a windows newline. By chance, I opened the file up in an editor that showed the newline characters, which was when the penny dropped.

So the route command was working perfectly after all. It was just the pesky carriage returns that were messing things up.

Thanks for your help.

---

### Post by nixscripter on 2008-06-19
No problem. You might want to mark this thread as solved.

---

