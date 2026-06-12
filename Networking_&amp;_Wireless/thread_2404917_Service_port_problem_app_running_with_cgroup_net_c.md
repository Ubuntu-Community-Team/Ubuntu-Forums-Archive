---
title: "Service port problem app running with cgroup net_cls as system service"
date: 2018-10-30
forum: Networking &amp; Wireless
---

### Post by remco-remco on 2018-10-30
Hi everyone,
I'm stuck.. Hope anyone can give me a clue.

I'm running an app as system service via systemd.
The app is running as a different user (non root) with a net_cls cgroup to mark network packets.
The app does connect to the outside world using the correct routing table, the ip rule, iptables forward etc seems to work fine.

Now the problem is that the app opens a tcp port 6060 for incoming connections, verified with netstat -l
But it's not working. 
With tcpdump i see incoming packages but the app never reply to it.

Running the app without cgroup net_cls works fine, it does reply to the incoming tcp packages (but then of course the app is not using the correct routing table, outgoing interface etc).
How can i make sure that inbound initiated tcp connections will also work? running the app as non root user and with cgroup net_cls to have outbound initiated traffic using the correct routing table (different wan interface).

Hope someone can help me.
Thanks in advance.
Remco

---

### Post by remco-remco on 2018-10-31
Perhaps somehow i need to associate the incoming connection to the cgroup net_cls id? or place some kind of input iptable rule to direct the incomming packet to the cgroup???

---

### Post by remco-remco on 2019-02-20
Ok, i figured out that when a process that runs under cgexec (to follow a different net_cls cgroup to use a different routing table) starts a listening port for incoming connections it's not using this cgroup anymore.
Seems that (child process?) listening port does not follow the same net_cls cgroup to reply as being used for outbound initiated connections... 

Basically running a program with cgexec (cgroup) is only usable for outgoing initiated connections...
When there is a inbound initiated connection the reply package just follows the main routing table...

---

