---
title: "Tunneling all internet traffic from Windows through Ubuntu box?"
date: 2007-09-27
forum: Networking &amp; Wireless
---

### Post by Jabran Asghar on 2007-09-27
Hi,

Just looking for a possibility to route all network traffic from a Windows XP Machine through SSH tunnel (OpenSSH, Feisty).

I know basics of SSH tunneling and OpenSSH setup, and have been using it for sometime. Following describes more about why and what I want to do.

**For the enthusiast only:**
I use Mobile broadband card (HSDPA 3.6Mbps) very frequently for internet access. But I have found that sometimes my SIP based VOIP (eyeBeam, [www.counterpath.com](www.counterpath.com)) software does not works very well on the Mobile connection despite 3.6 Mbps speed. While, when using the same VOIP software through ADSL (through my fixed line) it always works. I figured out that When using Mobile connection, the ping to my VOIP provider's server (which is not local) takes much longer (350ms to 400ms) than when doing the same from fixed-line ADSL (~150ms). While pinging my Ubuntu box from the mobile connections is always very fast. I have my Ubuntu Box always online, so I thought of the following Idea:
	
**What I want to do:**
- Connect to Internet using Mobile broadband on my laptop -> Already working
- Establish a tunnel to my home Ubuntu Box, such that all the SIP traffic should go through my ADSL line. This way,  the network delay caused by the Mobile connection will be eliminated as my Ubuntu box at home will act as proxy. -> **(How?)**

**What I need to know:**
- I understand that I can specify local/remote port ranges through ssh to be redirected to/from the ssh server. But how to make the ssh server to act as proxy? For example, In my VOIP software, I am providing domain/IP and port for my VOIP service provider server. If I redirect ports through ssh tunnel, then to use the ssh tunneling I shall have to use the local IP (in VOIP software configuration) instead of the domain of SIP server. The question How to forward the SIP connection request from the SSH server to the original server? or if I rephrase, How I can use SSH server + tunnleing as a Proxy (if I am understanding it correctly)?
	
Thanks for any hints. :-)
	
Jabran

---

### Post by mips on 2007-09-27
Any specific reason for using SSH ?

Either way you will have do let your ubuntu box act as a router.

---

### Post by Jabran Asghar on 2007-09-28
> **mips said:**
> Any specific reason for using SSH ?
So that only I can use my box for, not anyone else. SSH authentication will ensure that.

> **mips said:**
> Either way you will have do let your ubuntu box act as a router.
Any quick hints how to do this?

Thanks.

---

### Post by mips on 2007-09-28
I will search for a few links and get back to you later.

---

