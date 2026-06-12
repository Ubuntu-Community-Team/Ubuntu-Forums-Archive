---
title: "[SOLVED] DSL Network Dropping"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by browndruid on 2008-01-07
I've recently successfully installed Gutsy Gibbon, and it's working great, with just one issue.

The network periodically reconfigures itself. In order to configure my DSL, I have to enter in specific DNS servers. No problem here, since I just save it as location "DSL" and I just have to click on that whenever the reset happens. When that does happen, the DNS server changes to 172.16.0.254, which is the IP of my DSL modem.

My only thoughts (thoughts of a rather unexperienced Ubuntu user) are that I would be able to make some sorts of changes to a file that would hold the DNS servers.

If it helps, the only other computer on the network is running OS X, and it automatically configures the DSL through use of DHCP.

Any ideas? Thanks!

---

### Post by browndruid on 2008-01-08
Also, I'm using Earthlink, if there are any reported problems with that ISP.

Thanks!

---

### Post by browndruid on 2008-01-08
Update:

Whenever I come back from standby, I have to select the proper DNS settings not once, but twice.

Ideas?

---

### Post by browndruid on 2008-01-08
Success!

I was finally able to find the file that I needed to edit while looking through the OpenDNS website. I changed to the OpenDNS servers while I was at it, using this code:
```

$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit

```
I then checked to make sure it worked by going into suspend mode (what I meant when I said standby in last post), and the connection worked right away!

If I experience future problems, I'll post them here.

---

