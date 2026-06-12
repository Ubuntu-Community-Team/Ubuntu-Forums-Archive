---
title: "How to create two loopback interfaces."
date: 2014-07-28
forum: Networking &amp; Wireless
---

### Post by ricardo20 on 2014-07-28
Hello everybody,

I’d like to ask you how to create two loopback interfaces (like the 127.0.0.0) for local communications between applications. It would be important if they don´t disappear when the pc is rebooted.

Many thanks for your help

All the best 

Ricardo Sousa

---

### Post by bab1 on 2014-07-28
> **ricardo20 said:**
> Hello everybody,

I&#8217;d like to ask you how to create two loopback interfaces (like the 127.0.0.0) for local communications between applications. It would be important if they don´t disappear when the pc is rebooted.

Many thanks for your help

All the best 

Ricardo Sousa

You only need one loopback interface defined.  See /etc/network/interfaces.  It should look like this (using the cat command) CODE]
$ cat /etc/network/interfaces
```

auto lo
iface lo inet loopback


```
You can define multiple host names for the entire 127 subnet using the /etc/hosts file.  Using the cat command again you should see something like this
```

cat /etc/hosts
# Loopback Interface
127.0.0.1	localhost
127.0.1.1 ubuntu

```
You can use any name alias any 127 network address from 127.0.0.1 to 127.255.255.254.  Most folks have only the 2 as shown above.  The 127..0.1.1 usually is mapped to the host name of the system.

---

### Post by ian-weisser on 2014-07-28
There are already lots of safe, secure, and persistent ways for processes and services to communicate, and even to trigger each other. Pipes, names pipes, sockets, unix sockets, dbus signals, tcp/udp ports, and more.

Asking for multiple loopbacks implies that one of these other methods may work better.

Personally, I find dbus or upstart-socket-bridge to be quite handy for launching short-lived helper applications and temporary server instances. It keeps the number of daemons small.

If you want to be _certain_ that both processes are on the same machine, you can use dbus or unix sockets instead of the loopback interface (which is just another way to connect to tcp/udp ports)

---

