---
title: "How to assign an additional IP/hostname to a chrooted environment ?"
date: 2021-10-27
forum: Networking &amp; Wireless
---

### Post by marietto2008 on 2021-10-27
Hello.

I've got a crazy idea that I want to share with you. Premising that I'm running FreeBSD 13R,I've created a Linux/Ubuntu chroot environment on FreeBSD. It works well for a lot of (graphical) applications. Recently I've installed the original VNC server on another instance of Ubuntu that I've emulated with bhyve. As u probably knows,it accepts the connections only if you use the original VNC-viewer client. So,I've thought : what about to install it inside the chroot environment of the Linux Ubuntu os that I have configurated in FreeBSD ? So,I did it and it worked. At least,the graphical interface runs correctly as u can see below. Unfortunately it does not work because it detects that the chroot environment doesn't have a real network stack and a real IP and it won't connect to any VNC server. So,is there an hacky method to assign a network stack and a real IP address to the chroot ? I tried to work on this crazy idea following the tutorials below but in front of the first problems I stopped...

[https://ibb.co/f1sXNvx](https://ibb.co/f1sXNvx)

[https://unix.stackexchange.com/questions/98808/how-to-assign-an-additional-ip-hostname-to-a-chrooted-environment](https://unix.stackexchange.com/questions/98808/how-to-assign-an-additional-ip-hostname-to-a-chrooted-environment)
[https://blog.scottlowe.org/2013/09/04/introducing-linux-network-namespaces/](https://blog.scottlowe.org/2013/09/04/introducing-linux-network-namespaces/)


```
root@marietto:/usr/home/marietto # /usr/sbin/chroot /compat/ubuntu /bin/bash


root@marietto:/# uname

Linux


root@marietto:/# ip

Cannot open netlink socket: Address family not supported by protocol


root@marietto:/# ip netns

Cannot open netlink socket: Address family not supported by protocol


root@marietto:/# ifconfig

bridge: error fetching interface information: Invalid argument


root@marietto:/# sudo ip

sudo: unable to resolve host marietto: Temporary failure in name resolution

Cannot open netlink socket: Address family not supported by protocol


root@marietto:/# sudo ip netns add mario

sudo: unable to resolve host marietto: Temporary failure in name resolution

Cannot open netlink socket: Address family not supported by protocol
```

---

### Post by TheFu on 2021-10-28
chroot don't have their own hostnames or ip stacks.
Use a VM or Linux Container if you need more separation than a chroot provides.  The Ubuntu LXD container system can do most things that a full VM does - it isn't like Docker. However, it has protections where security impacts would break the container. For those, we have to specifically allow root - the real root from the base OS - to do things, since having root passthru to a Linux Container breaks the most important security aspects.  I've setup an NFS server under LXD. It was a terrible idea.  NFS is one of those kernel things that needs direct root passthru.  I've also setup netfilter in an lxd container.  Again - bad idea.  To add "more security", I had to break the primary security that lxd provided. Not a good idea.

Adding userland Linux doesn't magically make the BSD kernel do what is desired.

Only my router runs BSD.  I haven't touched real BSD since the mid-1990s. Sorry. 

Sometimes we need to ask whether doing something is a good idea or not. That isn't always clear and it is highly dependent on the purpose and environment.

---

