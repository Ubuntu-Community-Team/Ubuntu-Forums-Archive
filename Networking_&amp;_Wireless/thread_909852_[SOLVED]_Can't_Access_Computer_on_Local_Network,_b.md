---
title: "[SOLVED] Can't Access Computer on Local Network, but no Problem from Outside"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by dcajacob on 2008-09-03
Hi All,

I have a home network with several computers, one is a laptop and another a desktop, both have Ubuntu Hardy on them.  I had finally figured out SSH and was able to access my dekstop via SSH and VNC within the network, locally (wireless network).  I could even access the desktop while at work, by tunnelling through my router.  

But today, for whatever reason, I seem to have lost the ability to access the dekstop locally.  Mind you, it still works great from outside the router.  So, for example, from the laptop, within my home network,

```
ssh $USER@$ROUTER_IP
```

works great and I slide right in, but

```
ssh $USER@$COMPUTER_NAME
```

just hangs and finally times out.  I also can't ping the other computer locally, nor can I ping the laptop from the desktop.  Both ways seem to ignore each other.  But, I can ping the router's internal IP from both computers and I get internet access on both computers.

Does anyone have any suggestions?  I had finally thought I was getting the hang of things and now I am completely stumped!  Thanks in advance!

---

### Post by pi_31415926535898 on 2008-09-04
I'm new to Ubuntu (Linux in general), but I'd say this sounds like a networking problem more than an OS-specific problem.

If you can access your system(s) via IP but not via $COMPUTER_NAME, then editing your Hosts file may help:

```
sudo gedit /etc/hosts
```

and add the following:

```
<IP address> <computer name>
```

for example:

```
192.168.0.2 remotepc
```

If that's off the mark, then I may misunderstand the question, or my expertise may lie elsewhere.

What happens when you try this:

```
ping <computer name>
```

--
Stan

---

### Post by dcajacob on 2008-09-04
I fixed my own problem.  I had played with QoS in my router and somehow that killed me somewhere.  Revoking the changes fixed the problem.  Thanks!

---

