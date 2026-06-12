---
title: "Network Traffic / Bandwidth monitoring"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by lundrog on 2008-02-04
I am looking for way to monitor the traffic of each device on our network, ( mostly windows XP devices, ) we have over 100 client devices, and over 10 servers. I want to know if some are taking more bandwidth than others, and it would be nice to be able to have a map of traffic and what they are connecting to.

Additionally, is it possible to get something to auto find / search for devices which would allow for a over all topology of the network for this monitoring?

I have looked at zenoss, Zabbix, Hyperic HQ, and so many of them you either have to manually add each device on the network, and or install agent software.

I would prefer something that I do not have to install software onto for this to work.

Thanks

---

### Post by lundrog on 2008-02-06
Anyone?

---

### Post by ComputerHermit on 2008-02-06
```

sudo apt-get install etherape

```

---

### Post by jhenager on 2008-02-08
> **ComputerHermit said:**
> ```

sudo apt-get install etherape

```

That, and ethereal. Etherape is a nice real time, graphical representation of what is going on, but it doesn't allow you to capture and save history.
If you understand protocols, ethereal is the tool to use.

---

### Post by whowd on 2008-02-18
ntop is what you want. You'll have to span your outbound internet port to the box running ntop, or use netflow or sflow, but it works very well.

w

---

### Post by Rogers on 2008-02-18
> **whowd said:**
> ntop is what you want. You'll have to span your outbound internet port to the box running ntop, or use netflow or sflow, but it works very well.

w

To elaborate a little more.... and I believe it runs on port 3000 not port 80 so make sure you line your browser up.  NTOP rocks.

What is ntop?

ntop is a network traffic probe that shows the network usage, similar to what the popular top Unix command does. ntop is based on libpcap and it has been written in a portable way in order to virtually run on every Unix platform and on Win32 as well.

ntop users can use a a web browser (e.g. netscape) to navigate through ntop (that acts as a web server) traffic information and get a dump of the network status. In the latter case, ntop can be seen as a simple RMON-like agent with an embedded web interface. The use of:

    * a web interface
    * limited configuration and administration via the web interface
    * reduced CPU and memory usage (they vary according to network size and traffic) 


**apt-get install ntop**

---

### Post by lundrog on 2008-02-20
Thanks, anything I need to do on the port I am connect to via the switch on the network? or anything to enable on the other switches?

Thanks

---

