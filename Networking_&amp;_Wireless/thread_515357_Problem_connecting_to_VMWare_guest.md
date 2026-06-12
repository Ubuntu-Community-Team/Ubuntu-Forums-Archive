---
title: "Problem connecting to VMWare guest"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by dcroxton on 2007-08-01
I have installed trixbox (a pre-configured Linux distribution for VoIP) as a guest os on my Ubuntu Feisty computer.  The guest os has its own ip address, and I can communicate to and from it fine from other computers in my home network.  However, the Feisty host has problems communicating with it.

I can ping it, and I can telnet into open ports (80, 22), but I can't actually *use* those ports.  When I try to open a web page on the guest, it just sits there with "Waiting for host...," and ssh just sits there as well.  No error, but no response.  Also, I don't see any indication in the guest os log information that a connection attempt was made.

I have very little idea how to go about debugging this problem.  I'm hoping it's some common problem with vmware virtual machines that I'm overlooking.  Any help would be appreciated.

(I wasn't sure where this question should go, since it's networking, but also vmware.  If I put it in the wrong forum, please excuse it and tell me where it would go better.)

Sincerely,
Derek

---

### Post by dcroxton on 2007-08-02
Help!

---

### Post by Stoned on 2007-09-04
Same problem....:(
I can connect on the virtual machine from all pc of my lan...only the pc that host the virtual machine can't connect....
I use vm-ware server from repository with ubuntu 7.04

---

### Post by James Little on 2007-09-04
What kind of networking connection have you configured for VMWare...bridged or NAT?

---

### Post by Stoned on 2007-09-04
Bridged....
Also on vmware forum there is a post about this problem...
[http://www.vmware.com/community/thread.jspa?threadID=100327](http://www.vmware.com/community/thread.jspa?threadID=100327)

---

### Post by James Little on 2007-09-04
what kernel are you running? I'm on 2.6.20-16-generic and bridged networking works fine BUT, I installed from the tarball on the vmware site, not the ubuntu package. 

I take it you've gone through the steps outlined in that vmware thread; checking iptables etc?

---

### Post by Krijk on 2007-09-04
If its a new NIC or GB NIC try:

```
ethtool -K eth0 tx off
ethtool -K eth0 sg off
ethtool -K eth0 tso off
```


[http://ubuntuforums.org/showthread.php?t=542958](http://ubuntuforums.org/showthread.php?t=542958)

---

### Post by Stoned on 2007-09-04
> **Krijk said:**
> If its a new NIC or GB NIC try:

```
ethtool -K eth0 tx off
ethtool -K eth0 sg off
ethtool -K eth0 tso off
```


[http://ubuntuforums.org/showthread.php?t=542958](http://ubuntuforums.org/showthread.php?t=542958)

Working fine =D>
For me is necessary only the first command...
Thanks

---

