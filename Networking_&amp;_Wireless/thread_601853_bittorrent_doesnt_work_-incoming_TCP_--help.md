---
title: "bittorrent doesnt work -incoming TCP --help"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by nalleballe on 2007-11-03
nat@DL:~$ netstat -tnl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:2401            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:111              0.0.0.0:*               LISTEN
tcp6       0      0 :::53716                      :::*                    LISTEN

Hi! Im having trouble setting up my Bittorrent cause it having trouble with incoming TCP. This is new stuff to me and i have NO idea to get hang of this. Please help me open this up. Im using DSL modem and a router. (double OS) All ports ive tried is closed. Whats wrong?

---

### Post by 444 on 2007-11-03
netstat -pntl
To show the process name. And which torrent client are you using?

---

### Post by nalleballe on 2007-11-03
nat@DL:~$ netstat -pntl
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:6880          0.0.0.0:*               LISTEN     10406/java
tcp        0      0 0.0.0.0:2401            0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:4711            0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:4712            0.0.0.0:*               LISTEN     -
tcp        0      0 127.0.0.1:45100         0.0.0.0:*               LISTEN     10406/java
tcp        0      0 0.0.0.0:5999            0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     -

and azureus. THANX

---

### Post by 444 on 2007-11-03
You need to forward the port on your dsl modem, and possibly on your router as well.

---

### Post by nalleballe on 2007-11-04
and how is this done? please help. networking isnt my cup of java at all....

---

### Post by nalleballe on 2007-11-04
PS/ got DSL modem via vired router.

---

### Post by 444 on 2007-11-04
You go to the address of the modem in your browser. Some of them support simply typing "dslrouter" in the address bar instead of the actual ip address. Then there would be a forwarding menu somewhere, and you would tell it to forward the bittorrent port to the ip address of the router. There should also be a menu that lists the ip addresses of all the connected devices, that's how you'd find the ip of your router.

---

