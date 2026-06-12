---
title: "network manager"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by gdn1947 on 2009-03-31
Ubuntu 8.10. Network Manager shows the two computers so that part of the connection chain appears to be OK but I cannot connect to websites which are available through my desktop and router. Any solutions please. Thanks

---

### Post by hyper_ch on 2009-03-31
can you ping your router? can you poing google.com?

---

### Post by gdn1947 on 2009-03-31
Hi, Pinging [www.google.com](www.google.com) produces "The address 'www.google.com cannot be found'

For info I noticed that the Network device on the devices tab of Network Tools says Loopback Interface. I have changed that to Auto eth0 but that has no effect and it just changes back to Loopback Interface.

---

### Post by hyper_ch on 2009-03-31
what's the output of

```

cat /etc/resolv.conf

```

can you ping the router?

---

### Post by gdn1947 on 2009-03-31
Result is nameserver 10.0.0.2.

If it is simply a case of entering 10.0.0.2 in the Network Address and hitting Ping then the answer is that all the statistics are 0

---

### Post by netwarriorwy on 2009-03-31
Run these commands on a terminal.

> ifconfig

If you see something like eth0 is because the problem is not in your computer. But if you only see lo (loopback), it means the ethernet interface is down. So you have to run this:

> sudo ifconfig eth0 up

The left click on the Network Manager and choose "Edit Connections..." go to the "Wired" tab and check if you've already configured a connection. If not press "Add" and configure one. Choose a name and put it on the "Connection Name" field. If you've never modified your home router, you're connection should be DHCP, so just press "OK" and thats it.

Run > ifconfig again and see if you get eth0.

Try pinging your router 

> ping 192.168.1.1 

or

> ping 192.168.0.1

Let us know what happens!:rolleyes:

---

### Post by hyper_ch on 2009-03-31
do you have a nameserver running at 10.0.0.2 or is this a gateway to a router that has nameserver resolution?

---

### Post by gdn1947 on 2009-03-31
Just found that you have to put [http://10.0.0.2](http://10.0.0.2) but the result is that the address cant be found.

---

### Post by gdn1947 on 2009-03-31
> **hyper_ch said:**
> do you have a nameserver running at 10.0.0.2 or is this a gateway to a router that has nameserver resolution?

Im sorry but the questions are too difficult!! The situation here is that three desktops and my Ubuntu laptop are connected to a 4 port wired router. Im afraid my expertise ends about there!!

---

### Post by netwarriorwy on 2009-03-31
> **gdn1947 said:**
> Result is nameserver 10.0.0.2.

If it is simply a case of entering 10.0.0.2 in the Network Address and hitting Ping then the answer is that all the statistics are 0

That because that is your DNS address. It means you can't go outside, so your problem must be in your computers LAN network configuration. Try what I suggested b4.

---

### Post by gdn1947 on 2009-03-31
Results from your requested actions

ifconfig...OK   eth0 and lo

sudo ifconfig eth0 up....OK

Network Manager action...eth0

ifconfig...OK   eth0 and lo

ping.... address cannot be found

---

### Post by hyper_ch on 2009-03-31
paste the output of:

```

cat /etc/network/interfaces

```

```

ifconfig

```

```

iwconfig

```

---

### Post by stig on 2009-03-31
Could this be related to the problem that I have in a current thread here:

[http://ubuntuforums.org/showthread.php?p=6987800](http://ubuntuforums.org/showthread.php?p=6987800)

I'm failing to get a connection on startup with one of my two networked PCs, but if I give the command sudo /etc/init.d/networking restart in the terminal I can then get a connection to the Net (but still no network).

---

### Post by gdn1947 on 2009-03-31
paste the output of:


cat /etc/network/interfaces

auto lo
iface lo inet loopback


ifconfig


eth0 with related text
lo with related text


iwconfig


lo   no wireless extensions

eth0   no wireless extensions

pan0 no wireless extensions

---

### Post by hyper_ch on 2009-03-31
(1) when being asked to post output of a command or file enclose it in [noparse]```

```[/noparse] tags - for each one individually - makes it simpler to read

(2) do you use network manager?

(3) post the output of
```

lspci

```

---

### Post by gdn1947 on 2009-03-31
My resident Windows expert (son) who is rapidly expanding his knowledge of Ubuntu has resolved the issue. 

Solution: gksudo gedit /etc/network/interfaces and change the text to 'auto eth0' and 'iface eth0 inet dhcp'. 

Question is, Why does this have to set up manually from a fresh install?

Thank you for taking the time to try and resolve this issue

---

