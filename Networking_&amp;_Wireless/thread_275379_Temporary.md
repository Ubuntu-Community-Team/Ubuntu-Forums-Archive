---
title: "Temporary"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by jcounsel on 2006-10-11
Hi:

I have a server set up with Breezy, and it has been working wonderfully as a file server for 2 weeks.  This morning it is not reachable, and I notice I can not start my cli web browser. 

I reboot, and, when it tries to reach ntp.ubuntulinux.org to sync  the clock, I get this error:

Error:  Temporary failure in name resolution

No other computer on the network can see the server, and the server can't see anyone else either.  I ping cnet using their IP address: 216.239.122.220 (which works from my 'client' computer) and get Destination Host Unreachable.

During boot, the computer states networking setup is 'OK.'  

Here are the contents of my resolv.conf file:

namerserver 192.168.1.1
namesrever xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

The xxx.xxx.xxx.xxx are actual nameservers that work on other 'client' machines.

Why does the TCP/IP not appear to be setup correctly when no changes were made?

Any suggestions on how to fix this problem?

Thanks,

Counsel

---

### Post by wieman01 on 2006-10-11
Your computer has been disconnected, that's for sure. Usually the computer won't complain about the network being down if it is (physically) disconnected. You are sure the cables are alright?

Are you using DHCP or Static IP? Please post the commands of:
> ifconfig
> route
> sudo gedit /etc/network/interfaces
Have you configure IP Tables recently or installed a firewall configuration tool such as Firestarter? Can you ping other computers in the network?

---

### Post by jcounsel on 2006-10-11
Sigh...

The server is set up on its own firewalled router/switch.  Seems a joke was pulled...Nice secretary 'owed me one' and unplugged the cable on the router/switch...

Now....

It is getting cold, and revenge is best served in that manner... :D

Sorry to trouble everyone :)

Counsel

---

### Post by wieman01 on 2006-10-11
> **jcounsel said:**
> Sigh...

The server is set up on its own firewalled router/switch.  Seems a joke was pulled...Nice secretary 'owed me one' and unplugged the cable on the router/switch...

Now....

It is getting cold, and revenge is best served in that manner... :D

Sorry to trouble everyone :)

Counsel
Don't worry, that's what this forum is for. Nice secretary you've got there. ;-)

---

