---
title: "ufw an samba"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by shanep-server on 2009-09-13
Ok i used a tutorial to open up the ufw ports for samba however i'm retarded an I put in some wrong entries. Now I need to remove a few entries

when I type in 

sudo ufw status I recieve this

137/udp ALLOW 192.168.0.0/24
138/udp ALLOW 192.168.0.0/24
139/tcp ALLOW 192.168.0.0/24
137/UDP ALLOW 192.168.1.0/24
138/UDP ALLOW 192.168.1.0/24
139/TCP ALLOW 192.168.1.0/24
445/TCP ALLOW 192.168.1.0/24
5353/UDP ALLOW 192.168.0.0/16

My shares are working i don't think i need all these entries an would like to know how to remove the uneccessary ones. The tutorial I followed had 1 guys saying 192.168.1.0/24 an another guy saying 192.168.0.0/16 so i don't know what all that means or what model I should follow I just want it correct without unneeded entries.

---

### Post by swerdna on 2009-09-14
If you run the GUFW GUI, you will (probably) be able to highlight and delete the extraneous ones

---

### Post by shanep-server on 2009-09-14
thank you that is a very useful app!

If anyone knows which model I should be using to allow Samba threw ufw that would help too.

192.168.1.0/24 or 192.168.0.0/24 also with port 5353 should I use /24 or /16?

What is this IP/16 IP/24 really doing? Why do U need to type out

sudo ufw allow proto to port 137 from 192.168.0.0/24 or 192.168.1.0/24

instead of the normal opening port

sudo ufw allow 137

Any info would help me out a lot.

---

### Post by izziere on 2009-09-14
It depends on what your network address is.  Some use 192.168.1.0, others 192.168.0.0.  Check your ifconfig.

The /nn is about how many addresses are permitted for samba.  The 192.168.0.0/24 means you are allowing anything in range of 192.168.0.1 to 192.168.0.255 access.  192.168.0.0/16 means you are allowing 192.168.0.0 - 192.168.255.255 access the share.

---

### Post by shanep-server on 2009-09-14
ok so my router being 192.168.0.1 when i use 192.168.0.0/24 i'm basically saying anything computer on my network of 192.168.0.1-255 can enter threw said port? Is that correct.

---

### Post by swerdna on 2009-09-14
> **shanep-server said:**
> ok so my router being 192.168.0.1 when i use 192.168.0.0/24 i'm basically saying anything computer on my network of 192.168.0.1-255 can enter threw said port? Is that correct.

Yes

PS what's port 5353 for

---

### Post by swerdna on 2009-09-14
I get an error message from this:```
sudo ufw allow proto to port 137 from 192.168.0.0/24
```but this works```
sudo ufw allow proto udp to port 137 from 192.168.0.0/24
```

BTW what do you mean by "instead of the normal opening port"?

---

### Post by shanep-server on 2009-09-15
yes u are correct i just typed that wrong u have to specify either tcp or udp in that line or it won't work. I just got excited when I was typing it out.

---

### Post by shanep-server on 2009-09-15
also the 5353 was in the tutorial I was following I'm not sure exactly what that one is for. I didn't ask questions lol i just wanted my shares to work properly with ufw working.

---

### Post by swerdna on 2009-09-15
> **shanep-server said:**
> also the 5353 was in the tutorial I was following I'm not sure exactly what that one is for. I didn't ask questions lol i just wanted my shares to work properly with ufw working.

You don't need 5353 -- it's for multicast DNS, you need these four:
```
sudo ufw allow proto udp to any port 137 from 192.168.29.0/24
sudo ufw allow proto udp to any port 138 from 192.168.29.0/24
sudo ufw allow proto tcp to any port 139 from 192.168.29.0/24
sudo ufw allow proto tcp to any port 445 from 192.168.29.0/24
```

Plus you need to enable connection tracking nf_conntrack_netbios_ns in the text file "ufw" located at /etc/default/ufw

For full info see the segment titled "Opening the UFW Firewall for Samba" in this tutorial:
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by shanep-server on 2009-09-15
what is multicast DNS? I understand DNS but not multicast or why it would be located on the tutorial for samba ufw configuration. I edited the /etc/default/ufw file already I thought I was supposed to open up port 135 as well? That is un necessary as well?

---

### Post by swerdna on 2009-09-15
> **shanep-server said:**
> what is multicast DNS? I understand DNS but not multicast or why it would be located on the tutorial for samba ufw configuration. I edited the /etc/default/ufw file already I thought I was supposed to open up port 135 as well? That is un necessary as well?

Q1: I don't know what MCDNS is. Try Google.
Q2: Not for a small office / home office workgroup. (different if using like windows server 2003 etc).

---

