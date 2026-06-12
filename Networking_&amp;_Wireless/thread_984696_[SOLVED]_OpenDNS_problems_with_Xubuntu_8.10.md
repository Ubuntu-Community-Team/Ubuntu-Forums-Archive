---
title: "[SOLVED] OpenDNS problems with Xubuntu 8.10"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Lysander10 on 2008-11-16
I'm trying to use Xubuntu 8.10 amd64 and OpenDNS with a dynamic IP address. I got it setup without trouble, however, after several minutes, the DNS reverts to my ISP's default servers. The OpenDNS site has instructions on how to fix this issue, but they don't seem to work with Xubuntu 8.10(because of the new network manager possibly?). Can someone please give me a translation of these instructions for Xubuntu 8.10?

---

### Post by ciscosurfer on 2008-11-16
Can you provide a link to the exact insructions you are talking about?

EDIT: You can force your DNS to resolve to the OpenDNS servers by placing the entries in your router.

---

### Post by dmizer on 2008-11-16
The setting should work regardless of using NetworkManager or not.

Can you post the output of:
```
cat /etc/dhcp3/dhclient.conf
```

---

### Post by Lysander10 on 2008-11-17
#ciscosurfer: Here's a link to the instructions: [https://www.opendns.com/smb/start/device/ubuntu](https://www.opendns.com/smb/start/device/ubuntu)

Thanks for the tip about the router, but I'm a college student living in the dorms. I'm afraid changing router settings is a little out of the question.


#dmizer: The instructions I was referring to on the OpenDNS site instruct you to gksudo network-admin, and gnome-network-admin isn't installed in Intrepid, because it uses the new network manager.

The output of cat /etc/dhcp3/dhclient.conf is:

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}


I appreciate the help.

---

### Post by ciscosurfer on 2008-11-17
Open a Terminal and run the following commands```
sudo cp /etc/resolv.conf /etc/resolv.conf.auto
```Open the dhclient config file```
gksudo gedit /etc/dhcp3/dhclient.conf
```After the line```
#prepend domain-name-servers 127.0.0.1;
```add this line```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```So now you have something that looks like this```
#prepend domain-name-servers 127.0.0.1;
[COLOR=Red]prepend domain-name-servers 208.67.222.222,208.67.220.220;[/COLOR]
```Save and exit the file.

Take your interface down, then bring it back up (replacing eth0 if necessary with the interface you are currently using)```
sudo ifdown eth0 && sudo ifup eth0
```You can verify these stick by running```
cat /etc/resolv.conf
```The output should have lines that look like this```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

---

### Post by dmizer on 2008-11-17
> **Lysander10 said:**
> #dmizer: The instructions I was referring to on the OpenDNS site instruct you to gksudo network-admin, and gnome-network-admin isn't installed in Intrepid, because it uses the new network manager.

gksudo network-admin is essentially the same as (and about as permanent as) setting DNS servers in the NetworkManager applet.

The instructions you needed to follow are located under "To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:"

ciscosurfer has outlined this above.

---

### Post by Lysander10 on 2008-11-17
This worked perfectly. Thank you for the help!

---

