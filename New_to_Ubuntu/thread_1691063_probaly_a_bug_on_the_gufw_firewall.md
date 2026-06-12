---
title: "probaly a bug on the gufw firewall"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by werty2010 on 2011-02-19
when i set the gufw to incoming/outgoing to deny while im listening to radio on rhythmbox ,the connection/streaming stays open until im forced to close it by hand.
maybe its a bug. if not why is this happening?

---

### Post by JKyleOKC on 2011-02-19
The firewall only blocks NEW connections, and by default allows you to create new outgoing connections (if it didn't, you couldn't use the network at all). Once a connection has been established, it's allowed to continue even if you've blocked new outgoing packets.

It's no bug; if it didn't work this way, you would not be able to use the networks at all because once a connection gets established, there are literally hundreds of transactions every minute in both directions over it. 

If you want to disconnect from the network, the quickest method is to literally pull the plug (if wired) or turn off the wireless (most laptops have a button or switch to do this). Network Manager can disconnect, also.

---

### Post by werty2010 on 2011-02-19
thanks
i have one more question:
when i set incoming/outcoming connections to deny and then i set some exceptions to outgoing to allow ,nothing still is allowed to "move". the only setting that seems to work is set incoming to deny and outgoing to allow
since im moving a lot and connecting to a lot of pubic hotspots, could you tell me how to configure it ?

---

### Post by JKyleOKC on 2011-02-19
I believe that the sequence of the rules is important, so you might try setting the "allow" exceptions ahead of the "deny all" rule. However other posters have shown their configurations in the same sequence you are using so ufw may sort this out on its own...

---

### Post by ajgreeny on 2011-02-19
I suspect you are suffering from the paranoia that is a symptom of ex Windows users, who all feel that a firewall application is needed when using ubuntu, in the same way that, for example, Zone-alarm is often used in windows.

The firewall in ubuntu is iptables, not gufw which is simply a way of configuring iptables.  If you are using a standard desktop machine, with no mail or file server which interfaces with the internet, you probably do not need to make any changes to the default settings that you get when ubuntu is installed

---

