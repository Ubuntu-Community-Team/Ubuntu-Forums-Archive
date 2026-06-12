---
title: "FTP Server Setup proftpd"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by mwacky on 2007-09-04
I'm trying to setup an ftp server on a wireless connection, which I'm unsuccessful getting a static ip to stick, I'm receiving errors trying to install proftpd, gproftpd.  The error mentions the local machine's name is not associated with an ip address:

```
mwacker@Smithers:/etc/proftpd$ sudo apt-get install proftpd gproftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
proftpd is already the newest version.
gproftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up proftpd (1.3.0-21ubuntu1) ...
 * Starting ftp server proftpd                                                   - IPv4 getaddrinfo 'Smithers' error: No address associated with hostname
 - warning: unable to determine IP address of 'Smithers'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gproftpd:
 gproftpd depends on proftpd (>= 1.2.10); however:
  Package proftpd is not configured yet.
dpkg: error processing gproftpd (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 proftpd
 gproftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Suggestions?

---

### Post by styler13189 on 2007-09-05
I am having the same problem!

---

### Post by mwacky on 2007-09-05
I found the solution, can't post it until later, stay tuned.  Basically I had to modify the hosts and interfaces files to set my hostname and specify dhcp.  Then everything installed great and I'm up and running.  I will provide details later.

---

### Post by mwacky on 2007-09-05
Setup: Ubuntu 7.04, wireless connection through standard Belkin Wireless Router.  Dynamic DNS registered.

Changed network settings, Remember to back these up first:

1. add hostnames here:
/etc/hosts

Here's Mine:
```
127.0.0.1 localhost
127.0.1.1 Smithers.wacker.homeftp.net localhost.domain localhost Smithers 


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```



2. add hostname here, for dhcp:
/etc/network/interfaces

Here's Mine:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
  Smithers smithers.wacker.homeftp.net

auto wlan0
iface wlan0 inet dhcp

```

[This]("http://www.cpqlinux.com/hostname.html") article was very useful in helping.

3. sudo apt-get install proftpd gproftpd
      This installs proftpd with the gui.

4. sudo gproftpd
	Add users, directories, etc.

5. Of course, set your Virtual Server mappings in the Firewall for your host, likely will jump on ip change if you can't keep it static, the Belkin Wireless Router is really easy to setup these mapping and dyndns.

---

