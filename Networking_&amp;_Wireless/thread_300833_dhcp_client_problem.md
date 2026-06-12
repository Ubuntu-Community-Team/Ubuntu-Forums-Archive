---
title: "dhcp client problem"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by bijesz on 2006-11-16
Hi,

I'm using  ubuntu 6.10 server. It'll be a production server.
For some reason I installed several times the os.

My problem is that the dhcp client is not working, when I start dhclient the dhcp discover fails and the "no dhcpoffers received"
message  appear.

At the installation I've selected fixed IP because it will be on a lan.

But later i decided to change the ip to dynamic because I need to install some packege from the internet, and it's faster to connect it to a dsl line (dsl is behind a router which act as dhcp server).

To do this I've changed my /etc/network/interfaces file:
iface eth0 inet dhcp

after:
ifdown eth0
ifup eth0

After ifup the dhcp discover failed.

Earlier I installed the server with same configuration except that I selected dynamic ip configuration at setup. 
With this configuration after the install the dhcp request succeeded each time.

In my opinion the installer configured something somewhere
when i chose dhcp config, and it didn't did this when i selected the fix ip in the installer.

So the question is what else should change?
The DHCP servers are OK.

I appreciate any help thanks.

---

### Post by darrenm on 2006-11-16
Only thing I can think is to purge the dhcp3 config and reinstall

```
sudo apt-get --purge remove dhcp3-client dhcp3-common
sudo apt-get install dhcp3-client dhcp3-common
```

---

### Post by bijesz on 2006-11-16
> **darrenm said:**
> Only thing I can think is to purge the dhcp3 config and reinstall

```
sudo apt-get --purge remove dhcp3-client dhcp3-common
sudo apt-get install dhcp3-client dhcp3-common
```

Hi,

Thanks for the reply. 
Unfortunately this didn't help.

The problem is maybe in the dhclient.conf file.
Any idea?

---

### Post by bijesz on 2006-11-16
Some update:

I analyzed the ethernet traffic on the lan, and it seems that the server is not sending out any dhcp request, although dhclient writes out that dhcpdiscover is in progress.

I think the problem must be in dhclient, particularly in dhclient.conf

---

### Post by bmillsap on 2006-11-16
Have you rebooted the computer or restarted networking, or just done ifdown/ifup?  I noted in response to another question on DHCP that I had issues with my machine reinstating a lease with my ISP if I just took an interface down and up after I made configuration changes.  It seemed to work if I restarted networking.

---

### Post by bijesz on 2006-11-16
Some update

I made restart and network service restart it didn't help.

It seems that the problem is not with the dhcp configuration.

When the server is configured to static ip address the networking is not working.

I can ping the server's ip address and the loopback ip address as well.
But if I try to ping an external ip address there is no response.
Pinging the server's ip address from another pc resulted also negative result.

So it seems the problem with networking subsystem ](*,) 
I start too feel hate when i think about linux.

---

### Post by dataw0lf on 2006-11-16
Can I get an iptables -L?

could be that your OUTPUT chain is being dropped.

Course, you wouldn't be replying with an ICMP packet if so...

hmmm, what's the dhcp server look like? You sure it's advertising?

---

### Post by bijesz on 2006-11-17
Hi folks,

Thanks for replies, the problem has been solved.
The problem was with the utp cable.

The shame is on me :)

Old school teaching: start your debug process at the lowest level possible.

Have a nice day.

---

