---
title: "ports don't listen, supposedly open"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by fayuca on 2008-07-21
hello, i am new to linux, and to this forum, after some years of fiddling with the idea i finally installed hardy, so i still don't know much about the workarounds, although i'm always ready to learn...

i'm having a problem right now, i'm trying to set up port forwarding... i am behind a router with an static IP, and my admin already opened the ports over there, forwarding all connections to my computer... over here i've tried enabling and disabling 'ufw', setting rules for the ports to allow connections, but when i try this test [http://www.canyouseeme.org/]("http://www.canyouseeme.org/") i get a timeout for all of the ports i'm trying to open, sometimes i even get 'connection refused'... even the test inside the 'transmission' preferences panel says that the port is closed... i've looked around and i found some information about allowing ports with iptables, but i don't really understand what that is about...

i get this from netstat, while transmission is running, but then again i don't really know what i'm doing

```
~$ netstat -an | grep "LISTEN "
tcp        0      0 0.0.0.0:51413           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     
tcp6       0      0 :::631                  :::*                    LISTEN
```


does anyone know what could be going on? is there something else in ubuntu that could be blocking the connection?

---

### Post by SpaceTeddy on 2008-07-21
first things first - 

have you tried connecting to these ports from within the same subnet - i.e. without the firewall in between ? That would tell you if the error is with the machine itself, or if it is with the network.

secondly, could you use tcpdump and see if anything from the outside world even reaches you ? tcpdump will grab the packets before they are delivered to the appropriate services. To install it, type
```
sudo apt-get install tcpdump
```
and then to run it 
```
sudo tcpdump -n
```

if you have multiple network adapters, you might also need to specify the -i flag to tell it the network card to listen on. 

So, if you can locally connect and KNOW that the packets reach you (from internally as well as externally) there is either the routing or the firewall left to blame. But i will get to that once you can be sure that this is really a network and not a host problem.

Hope we can figure this out.

---

### Post by fayuca on 2008-07-21
SpaceTeddy - thanks for such a fast reply, it is working now

we removed the firewall and filters at the router just for my computer, and now the ports do listen, that is, while there is an open program listening to them, otherwise they refuse the connection, but i guess that's good, right? :)

i even enabled ufw again and everything keeps going OK

once again, thanks a lot!

---

