---
title: "Unable to mount network drive when mtu set to 8192"
date: 2016-10-11
forum: Networking &amp; Wireless
---

### Post by doctorbrown on 2016-10-11
I am trying to configure my eth0 network to use jumbo frames with mtu of 8192. I have read many posts and much info about this. The reason I am doing this is because I can improve the network transfer rate to my NAS by almost double.

The issue I am having is that when I set the mtu to anything more than 1500, I am unable to mount the file systems on the NAS.

To be more specific, here's my scenerio:
Running Ubuntu 14.04. The NAS is NetGear RN10200. I know that my network is able to handle the jumbo frames because I have it configured and working from my Windows 7 system to the NAS. 

With the default network configuration, I measured the transfer rate at 35 MegBytes/Sec to the NAS and 47 MegBytes/Sec from the NAS.

Then I ran the commands
```
sudo ifconfig eth0 mtu 8192
```
This will to enable the jumbo frames because I see an immediate increase in the transfer rate to 76 MBytes/sec. But this setting is lost when I reboot the system.

My research indicates it might be due to setting coming from the DHCP server, which is my Netgear WNDR3700. I should mention that all three devices in the equation, Win7 system, NAS and Ubuntu system are connected to a GByte switch so the data is not travelling through the router.

So I changed the /etc/dhcp/dhclient.conf file as follows:
Add the lines:
```
default interface-mtu 4096;
supercede interface-mtu 4096;
```
and removed the option interface-mtu,
 from the request line.

When I rebooted the system, ifconfig showed the correct mtu of 8192, but now the two cifs file systems will not mount. If I execute the command 
```
sudo ifconfig eth0 mtu 1500
``` The file system will now mount but the ifconfig command still shows the mtu is 8192 and the transfer rate is still at the high rate.

Is there something else I'm missing? How can I get the file systems to mount when the system boots and with those settings of the dhcp config?

Thanks for any pointers and help you can provide.

---

### Post by doctorbrown on 2016-10-18
After much research and experimentation, I think Network-Manager is playing a key role in this issue. But I don't know why. 

The result of my testing shows that if I use NM to bring up the network, then I can't mount remote filesystems if the network is configured for jumbo frames. If I disable NM and use ifup and config figure the network, then I can mount the filesystems with jumbo frames enabled.

I disabled NM by adding the word 'manual' to the file /etc/init/network-manager.override
Here are my config files that work:
/etc/network/interfaces file:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo eth0
iface lo inet loopback
iface eth0 inet dhcp
```
Relevent info in /etc/dhcp/dhclient.conf:
```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
send host-name = gethostname();
default interface-mtu 8192;
supercede interface-mtu 8192;

request subnet-mask, broadcast-address, time-offset, routers,
 domain-name, domain-name-servers, domain-search, host-name,
 dhcp6.name-servers, dhcp6.domain-search,
 netbios-name-servers, netbios-scope,
 rfc3442-classless-static-routes, ntp-servers,
 dhcp6.fqdn, dhcp6.sntp-servers;
```Is there anyway to configure Network Manager to work, or is it better just to abandon it?

---

