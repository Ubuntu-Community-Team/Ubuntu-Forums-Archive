---
title: "Netplan syntax problems"
date: 2019-02-05
forum: Networking &amp; Wireless
---

### Post by steve234 on 2019-02-05
Hi all,

I've read the netplan examples here ([https://netplan.io/examples](https://netplan.io/examples)) but an still scratching my head with a syntax error.

I am trying to set up my DNS servers to avoid an issue I am having with DNS at a work site which uses a home wifi setup with a notoriously flakey DNS server - I have described the issue here:
[https://ubuntuforums.org/showthread.php?t=2411835](https://ubuntuforums.org/showthread.php?t=2411835)

I am following this tutorial for 18.04 ([https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/](https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/)) which tells me how to setup the DNS servers. 

Unfortunately when I 

```
$ sudo netplan --debug apply
```

I get an error about syntax - it does not seem to like the "nameservers" bit

```
/etc/netplan/01-network-manager-all.yaml line 1 column 0: unknown key nameservers
```

My /etc/netplan/01-network-manager-all.yaml line file looks like this:

```
# Let NetworkManager manage all devices on this systemnetwork:
  version: 2
  renderer: NetworkManager
nameservers:
addresses: [8.8.4.4, 8.8.8.8, 1.1.0.0, 1.1.1.1]

```

Any ideas what I am doing wrong?

---

### Post by Irihapeti on 2019-02-05
Netplan, or rather yaml, is very fussy about indentation. The "nameservers" line needs to have the same (or possibly more) indentation as the "renderer" line, and the "addresses" line needs to be further indented than the "nameservers" line.

So, to tweak the example you've given, it should look like this:
```

# Let NetworkManager manage all devices on this systemnetwork:
  version: 2
  renderer: NetworkManager
  nameservers:
    addresses: [8.8.4.4, 8.8.8.8, 1.1.0.0, 1.1.1.1]

```

I don't use NetworkManager, so I can't be sure that you won't need to make other changes, but try updating the formatting first and see if that does the job.

---

### Post by slickymaster on 2019-02-05
Also, be sure to use spaces in groups of four for indentation as Netplan does not appreciate tabs in its yaml files.

---

### Post by steve234 on 2019-02-05
Thanks, I now get two new errors:

If I use four spaces as indentation - e.g:

```
# Let NetworkManager manage all devices on this systemnetwork:
  version: 2
  renderer: NetworkManager
    nameservers:
    addresses: [8.8.4.4, 8.8.8.8, 1.1.0.0, 1.1.1.1] 
```


I get:

```

Invalid YAML at /etc/netplan/01-network-manager-all.yaml line 4 column 15: mapping values are not allowed in this context

```


If I use two spaces (to bring nameservers in line under renderer) or cut/paste irihapeti's example (and correct the "network" being on the wrong line) - like this:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  nameservers:
    addresses: [8.8.4.4, 8.8.8.8, 1.1.0.0, 1.1.1.1] 

```

I get:

```
Error in network definition /etc/netplan/01-network-manager-all.yaml line 2 column 2: unknown key nameservers 
```

---

### Post by slickymaster on 2019-02-05
You indentation doesn't seem to be correct. Here's an example from a production server I run:```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: no
      dhcp6: no
      addresses: [xxx.xxx.xxx.xxx/xx]
      gateway4: xxx.xxx.xxx.xxx
      nameservers: 
        addresses: [xxx.xxx.xxx.xxx,xxx.xxx.xxx.xxx]
```

---

### Post by chili555 on 2019-02-05
> Any ideas what I am doing wrong?Yes.

This yaml:```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```...means what it says. It says and means, let NM do all the work; so long, I'm outa here, buh bye.

I suggest that you revert the faulty changes and simply make the changes in Network Manager:

[IMG]https://i.postimg.cc/pTVwFwg5/Screenshot-from-2019-02-05-10-07-39.png[/IMG]

---

### Post by steve234 on 2019-02-06
> **chili555 said:**
> Yes.

This yaml:```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```...means what it says. It says and means, let NM do all the work; so long, I'm outa here, buh bye.

I suggest that you revert the faulty changes and simply make the changes in Network Manager:



Thanks chilli555 - that's bang-on. Made the changes in Network Manager and all is good - this has also (hopefully - I will test today) solved my other thread too.

---

