---
title: "/etc/network/interfaces:4: option with empty value"
date: 2018-08-06
forum: Networking &amp; Wireless
---

### Post by arigatomanga on 2018-08-06
Hi all,

I am trying to install [OpenIMSCore]("https://www.openimscore.com/installation-guide") and following the steps from [this link]("http://cryingengineers.blogspot.com/2011/09/how-to-install-open-ims-core-in-ubuntu.html") and I am getting the below error when trying to restart the network,

[INDENT]*root@ubuntu16:~/.test/OpenIMSCore# /etc/init.d/networking restart*[/INDENT]
[INDENT]*[....] Restarting networking (via systemctl): networking.serviceJob for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.*[/INDENT]
[INDENT][I] failed!
[/I][/INDENT]
[INDENT]*root@ubuntu16:~/.test/OpenIMSCore# systemctl status networking.service*[/INDENT]
[INDENT]*&#9679; networking.service - Raise network interfaces*[/INDENT]
[INDENT]*   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)*[/INDENT]
[INDENT]*  Drop-In: /run/systemd/generator/networking.service.d*[/INDENT]
[INDENT]*           &#9492;&#9472;50-insserv.conf-$network.conf*[/INDENT]
[INDENT]*   Active: failed (Result: exit-code) since Sat 2018-08-04 01:17:51 IST; 19s ago*[/INDENT]
[INDENT]*     Docs: man:interfaces(5)*[/INDENT]
[INDENT]*  Process: 27064 ExecStop=/sbin/ifdown -a --read-environment --exclude=lo (code=exited, status=1/FAILURE)*[/INDENT]
[INDENT]*  Process: 27167 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)*[/INDENT]
[INDENT]*  Process: 27164 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm settle (code=ex*[/INDENT]
[INDENT]* Main PID: 27167 (code=exited, status=1/FAILURE)*[/INDENT]
[INDENT][/INDENT]
[INDENT]*Aug 04 01:17:51 ubuntu16 systemd[1]: Starting Raise network interfaces...*[/INDENT]
[INDENT]*Aug 04 01:17:51 ubuntu16 sh[27164]: /etc/network/interfaces:4: option with empty value*[/INDENT]
[INDENT]*Aug 04 01:17:51 ubuntu16 sh[27164]: ifquery: couldn't read interfaces file "/etc/network/interfaces"*[/INDENT]
[INDENT]*Aug 04 01:17:51 ubuntu16 ifup[27167]: /etc/network/interfaces:4: option with empty value*[/INDENT]
[INDENT]*Aug 04 01:17:51 ubuntu16 ifup[27167]: /sbin/ifup: couldn't read interfaces file "/etc/network/interfaces"*[/INDENT]
[INDENT]*Aug 04 01:17:51 ubuntu16 systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE*[/INDENT]
[INDENT]*Aug 04 01:17:51 ubuntu16 systemd[1]: Failed to start Raise network interfaces.*[/INDENT]
[INDENT]*Aug 04 01:17:51 ubuntu16 systemd[1]: networking.service: Unit entered failed state.*[/INDENT]
[INDENT]*Aug 04 01:17:51 ubuntu16 systemd[1]: networking.service: Failed with result 'exit-code'.*[/INDENT]



After debugging I found that the issue was with the /etc/network/interfaces file, when added the below params (from DEVICE, HWADDR to PEERDNS) and start the network I am getting the above error.

[http://3.bp.blogspot.com/-_r4woSSZ3Vs/TndVMcsKeDI/AAAAAAAAAAQ/av-r0J6a_Qs/s640/Screenshot.png](http://3.bp.blogspot.com/-_r4woSSZ3Vs/TndVMcsKeDI/AAAAAAAAAAQ/av-r0J6a_Qs/s640/Screenshot.png)


Did anyone face the same issues while modifying the interfaces file (my /etc/hosts file & /etc/resolv.conf file are similar to the once provided in the above link).


Any reference on this would also be of great help !

Thanks in advance.

---

### Post by wildmanne39 on 2018-08-06
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by steeldriver on 2018-08-06
Notice the comment above the HWADDR line?

> 
#Give ur Hardware address the one that will be shown in ifconfig eth0


You need to do that (except that your interface name may no longer be eth0 as a result of persistent net naming rules)

---

### Post by arigatomanga on 2018-08-06
@steeldriver

I have checked my HWaddress in ifconfig and updated the same in the interface file..

---

### Post by chili555 on 2018-08-06
The trouble with following an seven year old guide from a non-Ubuntu source is that they are often, as in this case, wrong. I'm not sure what version of Ubuntu this might have worked in; perhaps the Fedora version, or maybe Gentoo.

As steeldriver points out, your relevent interface is likely no longer eth0. Find out:```
ifconfig
```Or else:```
ip addr show
```Then change your interfaces file to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.0.0
gateway 192.168.1.100
dns-nameserver 192.168.1.100
```Of course, substitute your details here, including the ethernet interface name.

I am skeptical that the address, gateway and dns-nameserver are all the same, but, then, I know nothing about Open IMS Core.

---

