---
title: "Ubuntu18.04 as router."
date: 2020-02-13
forum: Networking &amp; Wireless
---

### Post by r00tr4t on 2020-02-13
Hello.

I'm trying to setup a ubuntu 18.04 as a router but it do not work.
This is what i did.

Add /sys/class/net to outputlog.text
[http://ix.io/2bCb](http://ix.io/2bCb)
Assign wlx7c8bca059cf7 as the WAN side going  to the Internet (BAD).
Assign enp2s0 as the LAN side (SAFE).
Created the 50-cloud-init.yaml

Installed ```
$apt install isc-decp-server 
```
Edited the dhcpd.conf ass follow.
[http://ix.io/2bCK ]("http://ix.io/2bCK")

Restarted the service with
```
$sudo service isc-dhcp-server restart
```

Edited the $/etc/sysctl.conf souch it became


Rebooted the machine.
```
 $ sysctl net.ipv4.ip_forward 
net.ipv4.ip_forward = 1

```

I first tested creating the ip-tables ass follow.
```
 $ sudo iptables -t nat -A POSTROUTING -o enp2s0 -j MASQUERADE 
```
I do not for now care about the security so it should be fine for now
Then installed ```
 $ sudo apt install iptables-persistent 
```
Such that the iptables stays when i reboot.
After that I tested the ```
 $ sudo dpkg-reconfigure iptables-persistent 
```
Now after I rebooted the computer the it remembered my tables but the network did not work on the (safe) side.

Then the I added an extra row to the iptables  ```

$ iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

```

No that did not work ether.
in the /etc/dhcp/dhcpd.conf it could be observed that the following lines was in it.
```

alias {interface "enp2s0";
fixed-addres 192.168.2.1;
option subnet-mask 255.255.255.0;
}

```
That came from some forum on the net to fix that the interfaces going to DOWN state all the time. But id did not work ether.

Now my Iptables look like this: [URL="http://<br /> http://ix.io/2bCJ"]
http://ix.io/2bCJ[/URL]
Or perhaps the standard iptable output is proffered then that result can be found [http://ix.io/2bCB ]("http://ix.io/2bCB")

So do any one have any suggestion's on how to fix that?

---

