---
title: "How can I connect to the Internet with a router and 3 pcs on a broadband connection?"
date: 2005-07-28
forum: Networking &amp; Wireless
---

### Post by philotech on 2005-07-28
[FONT=Courier New]Problem:  Win machines connect to internet fine on router, but my Ubuntu (first linux pc) cannot seem to connect.  It works if I disconnect the router and directly connect to the modem, however.  I figure it is the router and something with dhcp.

ifconfig eth0 shows that the router has assigned an ip address to the ubuntu box.  The subnet mask is correct.  Scope: Link UP BROADCAST RUNNING MULTICAST
No packets lost.  I can ping the router and all the other pc's on the lan.

netstat -r shows only two entries on kernel routing table, but according to the help texts I've read the Gateway is correct, However the destination IP ends with .0?  Genmask matches helpfiles examples too.  

I have also tried sudo /etc/init.d/networking restart and restarting the modem, then router and then rebooting my machine to no avail.  

Any helpful suggestions would be great.  
Thanks.[/FONT]

---

### Post by strikeforce on 2005-07-28
Does your router pass on dns settings or do you have to put your own dns servers in there.

e.g. try and ping [www.westnet.com.au](www.westnet.com.au)
or ping 203.10.1.9

Second one is a dns server first one is a website see what results come out.  It is definately a router issue I'm just trying to figure what specifically is the issue.

---

### Post by philotech on 2005-07-28
In terminal:
ping -c 3 [www.westnet.com.au](www.westnet.com.au)
ping: unknown host [www.westnet.com.au](www.westnet.com.au)

In Network tools:  No Such host.(for westnet.com.au)

203.10.1.9:  successful ping.

---

### Post by strikeforce on 2005-07-29
Your issue is dns settings.

The simple fix is to add to your /etc/resolv.conf file the following line.
```

nameserver 203.10.1.9

```

If you know of any other dns servers at them in the same method.

---

### Post by philotech on 2005-07-29
Hrm, I thought my router was supposed to do that for me.  Or is that only dhcp?
Thanks for the info.

---

### Post by Julius on 2005-07-30
If you don't use DHCP in your router then you have to manually specify DNS in your computer, I guess.
:S

---

### Post by spd106 on 2005-07-30
You should find out if your isp automatically assigns you the dns server or whether they give you the addresses and you have to tell the router where to find them. There should be a setting in the router configuration interface where you can specify where  it gets it's dns info from.

Then you can put the routers address in the resolv.conf. If it's not there already.

You can have more than one nameserver, just add it to the end of the line. Then if the first one fails you have a backup.

---

