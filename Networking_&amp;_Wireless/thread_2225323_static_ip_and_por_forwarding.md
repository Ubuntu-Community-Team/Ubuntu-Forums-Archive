---
title: "static ip and por forwarding"
date: 2014-05-20
forum: Networking &amp; Wireless
---

### Post by satimis on 2014-05-20
Hi all,

Host	Ubuntu 12.04 desktop 64bit
Guest	Ubuntu 12.04 LAMP/desktop 64bit
VirtualBox
2 NICs
Optic Fibre Broadband connection - interface
(connected to onboard NIC)
Static IP
Router not available

Host:-
$ cat /etc/network/interfaces```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address xx.xx.xxx.xx (static IP)
     dns-nameservers xxx.xxx.xxx.xxx  xxx.xxx.xxx.xxx
     netmask 255.255.255.252
     broadcast xx.xx.xxx.xx
     gateway xx.xx.xxx.xx

```

Guest:-
$ cat /etc/network/interfaces```

auto lo
iface lo inet loopback

```

$ sudo ifconfig
[sudo] password for satimis: ```

eth5      Link encap:Ethernet  HWaddr 08:00:27:d3:83:91  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fed3:8391/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32891 (32.8 KB)  TX bytes:16748 (16.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3724 (3.7 KB)  TX bytes:3724 (3.7 KB)

```


Network -> Adpater 1
Enable Network Adapter
Attached to: NAT


Please advise how to setup port-forwarding assigning a static IP to Guest so that the webserver can be connected/browsed on Internet.  I have been searching a while and couldn't find a guide to follow.  Pointers would be appreciatd.

Thanks

Rgds
satimis

---

### Post by TheFu on 2014-05-21
Don't have time to lookup the solutoin - ip-forwarding is set in /etc/sysctl.conf There is an example line that is commented out.

If deploying a new server today, I'd use 14.04 to a supported server until 2019.  Why start with an older release?  There are good reasons to use 12.04 still, so don't worry if you need it. It is smart to deploy LTS releases, as you already know.

---

### Post by satimis on 2014-05-21
> **TheFu said:**
> Don't have time to lookup the solutoin - ip-forwarding is set in /etc/sysctl.conf There is an example line that is commented out.

If deploying a new server today, I'd use 14.04 to a supported server until 2019.  Why start with an older release?  There are good reasons to use 12.04 still, so don't worry if you need it. It is smart to deploy LTS releases, as you already know.

Thanks for your advice.

Whether following article is related:
UBUNTU SERVER: “HOW TO ENABLE IP FORWARDING IN UBUNTU 12.04LTS SERVER EDITION
[http://ideasnet.wordpress.com/2013/05/29/ubuntu-server-how-to-enable-ip-forwarding-in-ubuntu-12-04lts-server-edition/](http://ideasnet.wordpress.com/2013/05/29/ubuntu-server-how-to-enable-ip-forwarding-in-ubuntu-12-04lts-server-edition/)

I have no problem installing new Ubunutu 14.04 VMs.  But I hesitate to install a clean copy of Ubuntu 14.04 on Host.  It would take me several days of work because I have >30 VMs running on this box.  

I must perform:-
-export all VMs
-store them on another HD (which is available)
-wide out the whole HD
-install a new copy of Ubuntu 14.04 as Host
-install other packages for running Oracle VirtualBox
-import all VMs
etc.

I just tested upgrading a VM of Ubuntu 12.04 to Ubuntu 14.04.  However after reboot I got problem on login```

Failed to load session "ubuntu"
		Log Out

```

Therefore I wouldn't consider upgrade.

If it is too difficult setting up port forwarding, I prefer purchasing a router instead.

Rgds
satimis

---

### Post by quigi on 2014-05-21
If I misunderstood your question, please elaborate on what you're trying to achieve.
Basics: to enable IP forwarding, [that article]("http://ideasnet.wordpress.com/2013/05/29/ubuntu-server-how-to-enable-ip-forwarding-in-ubuntu-12-04lts-server-edition/") suggests
```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```
That fails, because "echo" gets executed as root, but your shell does the output redirection, and doesn't have permission to write to the destination.  Instead, you can do this:****
```
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
```
After that, if your machine gets a packet destined for some other host, it will try and forward it in the right direction, according to its routing table.

If you need something fancier, e.g., NAT, let us know.  You may want to look at iptables.

---

### Post by satimis on 2014-05-21
> **quigi said:**
> If I misunderstood your question, please elaborate on what you're trying to achieve.
- snip -
Hi,

Thanks for your advice.

What I'm trying to achieve is:

Behind a router I can assign static IP to all VMs which are running webserver/website for testing.  If I need VM1, for example, to be browsed on Internet I just on router forward all ports to the static IP of VM1.

If without a router and VM1 running on NAT what can I do?  How can I made VM1 to be browsed on Internet?

TIA

Rgds
satimis

---

### Post by TheFu on 2014-05-25
Virtualbox is NOT production ready, IMHO.  It should be used only for desktop-on-desktop VMs, 1 or 2 at a time.

KVM is production-ready and has been since 10.04.  The KVM support is much better with 14.04 support being the best, by far, for server deployments.

It should be easy to backup and restore a hostOS. If it is that important, having a recoverable backup is absolutely critical. There really isn't much to backup besides /var and /etc in most situations on the hostOS anyway.

Enabling IP forwarding is trival, but forwarding 1 port is different and usually handled by iptables rules.  Get a router if that is what you need - plus it is better than directly connecting any Linux VM or host to the internet. Having a device that fails-closed is better than having a device that fails-open.

If you want to make a specific port from a specific VM available from the internet (assuming a single IP), ... well, the easiest way is to use different ports for each server
or
use a reverse proxy that handles name-based subdomains
or 
use a reverse proxy that handles directory-redirection
or
setup a tunnel
or
..... there must be 50 other ways, but these will depend on your specific setup - physical, logical, and network skillz.

---

### Post by satimis on 2014-05-25
> **TheFu said:**
> Virtualbox is NOT production ready, IMHO.  It should be used only for desktop-on-desktop VMs, 1 or 2 at a time.

KVM is production-ready and has been since 10.04.  The KVM support is much better with 14.04 support being the best, by far, for server deployments.

Hi,

Thanks for your advice.

I ran KVM before, later switching to VirtualBox because the later is easy to set up, in my opinion.

If I can't find a "not-too-complicate" solution forwaring ports to NAT IP, I'll buy a router instead.  

I tried running pfSense on VM before.  It worked as router assigning IP to other VMs.  But it failed to make the HOST connecting Internet.  After spending serveral days unable to find a solution, finally I gave up.  I'm reluctant installing pfSense on Host.  I expect keeping the Host clean only for running VirtualBox.

> 
If you want to make a specific port from a specific VM available from the internet (assuming a single IP), ... well, the easiest way is to use different ports for each server
or
use a reverse proxy that handles name-based subdomains
or 
use a reverse proxy that handles directory-redirection
or
setup a tunnel
or
..... there must be 50 other ways, but these will depend on your specific setup - physical, logical, and network skillz.
I'm very interested to find the latest solution.  I did it several years before with Perdition and MySQL on a VM for routing.  It worked for me, of course on Static IP, one Static IP for serveral websites running on VMs.  They can be browsed on Internet.  Now I need to do it again.  Could you please send me some pointers, or the key words for searching on Google.

Thanks

Rgds
satimis

---

