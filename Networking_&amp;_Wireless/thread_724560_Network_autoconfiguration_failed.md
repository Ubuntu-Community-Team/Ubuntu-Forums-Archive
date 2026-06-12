---
title: "Network autoconfiguration failed"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by §cinc§ on 2008-03-14
I've had an issue while installing ubuntu 7.10 on my pc.
While configuring the network with DHCP an error stopped the install with a "Network autoconfiguration failed"  and asked me to press enter to continue...
Network Configuration Method:
              
              Retry network autoconfiguration    --->   Same Error again
              Retry network autoconfiguration with a DHCP hostname  ---> none, tried one and didn't work
              Configure network manually --->  IP: 192.168.0.1 net Mask: 255.255.255.0 gateway: 192.168.0.1 Name server addresses: no local domain name in the router/left empty Hostname: ubuntu
              Do not configure network settings at this time


Well as you can tell I probably failed at manually configuring my network but the install went on anyways. Under system>administration>Network Tools under the tab 'Devices'>Network device: Ethernet interface (eth0) The option 'configure' is grayed out also under Interface Information all the information listed says "not available" 

I assume this is a problem with the networking card not being detected by OS system and I have no idea how to fix this. Please help. 
Thanks for your time, this is probably my last attempt at using linux before I go out and buy windows. I'm banging my head on the wall here.:mad:

---

### Post by §cinc§ on 2008-03-14
Ive been reading for days with no good post to be found.
Ive tried to list the hardware with  ```
lshw -C network
```

[IMG]http://i76.photobucket.com/albums/j11/scamm3r/screenshot.jpg[/IMG]

Doesn't look good :confused:

---

### Post by §cinc§ on 2008-03-15
> ifconfig


[http://i76.photobucket.com/albums/j11/scamm3r/ifconfig.jpg[/IMG]"][IMG]http://i76.photobucket.com/albums/j11/scamm3r/ifconfig.jpg[/IMG]]("[IMG)

---

### Post by Iowan on 2008-03-15
A couple more things to check - post results of **lspci**.  If you know the chipset for your NIC, that would be helpful, too.

---

### Post by §cinc§ on 2008-03-15
> lspci

[IMG]http://i76.photobucket.com/albums/j11/scamm3r/screenshot3.jpg[/IMG]

Does this help at all?

---

### Post by Iowan on 2008-03-15
I found [this]("http://ubuntuforums.org/showthread.php?t=598346&highlight=nforce2+ethernet") post of a similar problem - but no solution (yet).  Unfortunately, I can't help with a driver problem.

---

### Post by §cinc§ on 2008-03-15
November 5th, 2007 with all the posters not seen since.
I dont think ill hold my breath.
Is there a link were I can get some info on manually installing drivers?
Im pretty good at doing anything I want if I have a manual to read and A few Q&A along the way.

---

### Post by Iowan on 2008-03-15
[Another]("http://ubuntuforums.org/showthread.php?t=270862") post - at least your controller shows up in **lspci**
[Bug report]("https://lists.ubuntu.com/archives/ubuntu-bugs/2004-October/012476.html")

---

### Post by §cinc§ on 2008-03-15
Theres light at the end of the tunnel ;-)

[detailed bug report](https://bugs.launchpad.net/ubuntu/+bug/8967)

thanks for the help I think the bug report might work, ill get working on duplicating this on my own. Might take a bit though i don't even know were to start they kinda jumped to the middle of the problem were he had issues.

---

### Post by §cinc§ on 2008-03-28
Gave up, Going to XP to today.:frown:

---

