---
title: "Home network for dummies"
date: 2015-09-06
forum: Networking &amp; Wireless
---

### Post by SebastianoS on 2015-09-06
Good afternoon folks, 

tomorrow I'll face a problem that quite confused me a long time ago, this time I'm asking your help first. I'll get my hands on a new PC that I want to use as a backup/media server and I plan to run Ubuntu 14 LTS. My question is: how do I setup the LAN and the sharing? Here are a few details that might be of some help:


[LIST]
[*]I don't have any other OS running than Ubuntu (or *buntu) in any of my machines
[*]I can't use a wired connection, everything must be wireless
[*]I'd like to have remote access to this server, with screen sharing and all
[/LIST]

So, what I would like to achieve is, for example, running a backup from my laptop and saving everything on the server, or playing a movie on my laptop from the server again: data must be stored and retrieved from this new PC. So, what's the plan? SSH? Samba? Folder sharing? I remember trying and ending up with a completely screwed LAN, save me this time :D

Cheers

---

### Post by The Cog on 2015-09-06
Do you have control of the router? 
In order to forward incoming connections to the server, port-forwarding configuration is needed in the router.
Your router probably allocates IP addresses when devices connect to the wireless network. You probably want a fixed address for the server, which would be done by configuring a reserved address in the router.

Can we see what IP address/network your laptop gets assigned? Show the output from the command "ifconfig".

---

### Post by Morbius1 on 2015-09-06
Is avahi functioning on this Ubuntu 14,04 machine? And are we talking about only lan access or do you intend to do something over the internet?

To find out ping yourself:
```
ping your-host-name.local -c4
```
To find out your host name run this command:
```
hostname
```

---

### Post by SebastianoS on 2015-09-06
I do have control, and my main laptop is now running on a fixed IP of my choice:

> eth0      Link encap:Ethernet  HWaddr ac:22:0b:1d:e4:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:63748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80280842 (80.2 MB)  TX bytes:80280842 (80.2 MB)


wlan0     Link encap:Ethernet  HWaddr 24:0a:64:4e:4b:f7  
          inet addr:192.168.1.149  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260a:64ff:fe4e:4bf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2039363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1456063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2275006818 (2.2 GB)  TX bytes:215717424 (215.7 MB)

---

### Post by SebastianoS on 2015-09-06
Honestly, I have no idea what you are talking about with AVAHI, but I'll google it ASAP. Here's the output, btw

> PING 192.168.1.149 (192.168.1.149) 56(84) bytes of data.
64 bytes from 192.168.1.149: icmp_seq=1 ttl=64 time=0.063 ms
64 bytes from 192.168.1.149: icmp_seq=2 ttl=64 time=0.054 ms
64 bytes from 192.168.1.149: icmp_seq=3 ttl=64 time=0.050 ms
64 bytes from 192.168.1.149: icmp_seq=4 ttl=64 time=0.053 ms


--- 192.168.1.149 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.050/0.055/0.063/0.004 ms




It would be handy to have access from outside, but it's not mandatory: I can easily work around it via cloud services so for the moment I would focus on local connection

Thanks!

Edit: sorry, I might have misunderstood: were you talking about the server or my laptop? I'll have the server by tomorrow afternoon, and I'll go for a vanilla installation of ubuntu: is it a default component?

> **Morbius1 said:**
> Is avahi functioning on this Ubuntu 14,04 machine? And are we talking about only lan access or do you intend to do something over the internet?

To find out ping yourself:
```
ping your-host-name.local -c4
```
To find out your host name run this command:
```
hostname
```

---

### Post by Morbius1 on 2015-09-06
>                      I do have control, and my main laptop is now running on a **[COLOR=#0000cd]fixed IP[/COLOR]** of my choice:
Then you don't need avahi unless you want the clients of this machine to "browse" to find this machine. So you can ignore my post.

And you didn't do what I asked you pinged the ip address not the hostname.local address. But it makes no never mind.

---

### Post by SebastianoS on 2015-09-06
I have to say that not all of my devices are running on a fixed ip, for example all my mobile devices running android rely on router DHCP: however yes, my main laptop, the one I want to backup on the server, has its own fixed IP at the end of the available range (so it should never overlap devices getting their address via DHCP)

---

### Post by The Cog on 2015-09-06
Looking good. How did you fix the address? Local configuration in the PC, or by tying the MAC address to that IP address in the router's DHCP configuration?
You ought to either use the DHCP settings in the router to allocate that address to your MAC address, or adjust the router so that it doesn't ens up handing that address to a different device on the network. Either way, doesn't really matter. You can allocate a different address to the server in the same way.

I don't do a lot of file sharing here, and just tend to use SSH/SFTP. I can put addresses into my file manager like this: **sftp://pi@192.168.0.103/**
rsync for backups uses ssh nicely too.

---

### Post by SebastianoS on 2015-09-06
It's a local configuration via network-manager, but now that you mention it I like the solution directly on the router. 

Would this SSH/SFTP solution work when it comes to backup? Is there a way to "mount" a partition from another PC - AKA have my laptop see the server HD as if it was its own?

---

### Post by The Cog on 2015-09-06
There is a way, I think, but ssh isn't really suitable for that I don't think, because I think SSH logs in as one user and doesn't do the permissions on the full way that (say) NFS would. So I would suggest using NFS for the remote file mounting.

A quick google turned up this link
[https://www.howtoforge.com/how-to-configure-a-nfs-server-and-mount-nfs-shares-on-ubuntu-14.04](https://www.howtoforge.com/how-to-configure-a-nfs-server-and-mount-nfs-shares-on-ubuntu-14.04)
which after a quick glance I think should provide the info you need.

P.S.
If the server is being opened up to the internet, read up on nfs security. I can't remember if it has any. You might be wise to use a firewall to only allow SSH fron the internet to your server. 
And make sure your SSH password is good (or use password-less key-based logins instead):
[http://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login](http://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login)

---

### Post by SebastianoS on 2015-09-07
Super cool, I'll give it a shot today! Thank you!

---

