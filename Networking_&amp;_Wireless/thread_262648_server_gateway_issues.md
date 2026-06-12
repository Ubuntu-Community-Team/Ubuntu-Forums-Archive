---
title: "server gateway issues"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by sim-x on 2006-09-22
Hello everyone, 

this is the setup i have at our house. The internet comes in the house and is switched to 8 rooms. In my room, i switch the line again to my windows box and my ubuntu-server box.  All the machines in the house are windows boxes and are set to dhcp. My ubuntu box has a static ip (192.168.1.114). The house gateway is 192.168.1.1

Recently, me and other people in the house were not able to connect to the internet. The reason ended up being that their windows machines, including mine, were using the ubuntu box's IP as their gateway address. To fix their connections, I had to switch my server off :(

Any idea of why this happened? What must I do to keep my ubuntu box running and have their machines connect to the correct gateway? I want to keep their machines on dhcp so as to not annoy everyone (that and the house router/gateway is not in my room). Thanks for your help!

sim-x, seattle.

---

### Post by spd106 on 2006-09-22
This is odd, do you have a dhcp-server running on your box?

---

### Post by sim-x on 2006-09-22
Most probably.. How do I check and how do I turn it off?

Thanks!

---

### Post by spd106 on 2006-09-23
You could check whether the dhcpd process is running in System Monitor or **ps | grep dhcp** at the terminal and look for dhcp3-server, ignore the dhclient process. The most likely package to have is dhcp3, but you may have another such as dhcpd or udhcpd.

Unless you need it, I would strongly suggest that you uninstall it eg through Synaptic or **sudo aptitude remove dhcp3-server**.

Alternatively you could move the dhcp3-server init script from /etc/init.d/. This will stop the server daemon starting on boot.

---

### Post by sim-x on 2006-09-23
Thanks, I tried **ps | grep dhcp** but there was nothing.. i checked /etc/init.d and there is no dhcp package. This is the content of my init.d:

acpid              dnsmasq                          makedev            pcmciautils  skeleton
alsa-utils         evms                             mdadm              ppp          squid
apache2            exim4                            mdadm-raid         pppd-dns     ssh
atd                glibc.sh                         module-init-tools  procps.sh    stop-bootlogd
bootclean.sh       halt                             mountall.sh        rc           sysklogd
bootlogd           hdparm                           mountdevsubfs      rc.local     udev
bootmisc.sh        hostname.sh                      mountvirtfs        rcS          umountfs
checkfs.sh         hwclock.sh                       mtab               README       umountnfs.sh
checkroot.sh       keymap.sh                        mysql              reboot       umountroot
clamav-freshclam   klogd                            mysql-ndb          rmnologin    urandom
console-screen.sh  linux-restricted-modules-common  mysql-ndb-mgm      rsync        waitnfs.sh
cron               loopback                         networking         sendsigs
dns-clean          lvm                              nvidia-kernel      single

---

### Post by sim-x on 2006-09-23
errata: the system has **dhcp3-client** and **dhcp3-common**

---

### Post by spd106 on 2006-09-24
I notice that you have squid installed. Is this setup as the LAN proxy server? If so then that's typically why you would have all the other hosts pointed to it. As far as I know Squid isn't setup to force other hosts to use it, you would have to do this manually. I have very little experience with Squid though, so I could be mistaken.

---

