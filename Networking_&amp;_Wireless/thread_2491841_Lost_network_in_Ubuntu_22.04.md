---
title: "Lost network in Ubuntu 22.04"
date: 2023-10-22
forum: Networking &amp; Wireless
---

### Post by weirdygeekpsych on 2023-10-22
Hi guys,

The below issue is happening in VMware and when I load ubuntu recently it is showing SMBus host controller not enabled.

My internet in ubuntu was working fine until I installed docker.

I also made a suspended the ubuntu and it got failed.

I am not sure what caused the issue, now I cant connect to the internet.

here are the things I have tried:

1) updated name server in /etc/resolv.conf - failed 
Status: ping doesnt work

2)network-manager service start - failed
Status: no service found 

3) Added BIP rule in daemon/docker.json file to except my ethernet IP and closed and restarted docker service.
Status: still , no internet

4) systemd-resolve kill
Status: command success, still no internet

even after many times rebooting, I cant access the internet.

What I thought was docker replaced internet and tried to add bip rule in docker.json file.

still even after stopping docker service, it behaves same.

Help would be appreciated

Thanks,

---

### Post by TheFu on 2023-10-25
resolvconf is deprecated.  systemd-resolved is the replacement for years now. Disabled systemd-resolved, that will prevent DNS from working.

I don't see what docker has to do with anything.
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) is a little old, using old commands, but just replace ifconfig with **ip a**, route -n with **ip route** and dmesg with **journalctl** to get the same information.

Start with **ping**. Go in order.  It is likely you broke the DNS, but not the actually connectivity.

---

### Post by weirdygeekpsych on 2023-10-30
@TheFu

Thanks for the reply.

I wasnt aware of the resolv.conf is deprecated.

I got my internet icon back with *nmcli network on* and I changed my network setting to NAT with a restart. 

then I enabled systemctl systemd-resolved.

everything working fine now.

---

