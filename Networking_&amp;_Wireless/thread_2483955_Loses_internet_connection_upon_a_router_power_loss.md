---
title: "Loses internet connection upon a router power loss or network connection interruption"
date: 2023-02-13
forum: Networking &amp; Wireless
---

### Post by rhinofiresecurity-glynn on 2023-02-13
Hi. I use Ubuntu for our business CCTV recorders and find that upon a power loss or network reboot/interruption at the router or a network switch, the Ubuntu unit does not re-access the internet. If I reboot the CCTV recorder, it regains internet connection. I have tried both DHCP and static addresses on the recorder- does not resolve.
By using a static, I maintain connection to the cameras and internal network, but no internet connection. 
This has occurred on many versions of Ubuntu since I started using Linux instead of Windows for my CCTV recorders OS. 
My current install is using Focal Fossa 20.04.5 LTS.
This occurs on the different hardware units I use: Intel NUC's (Celeron to i5'), Full Intel i3 machines, Intel Celeron CCTV custom units (these have two NIC's with 16 PoE ports- can be set up as three different networks or bridged as one). My best results are with my custom units, as to maintain recording of cameras, I bridge all the nics a to make it essentially an inbuilt 18 port switch- cameras maintain connection and recording even if internet connection is no longer.
Issue will occur if I simply remove the patch lead from the unit to the network, leave off for say 5 mins or so and then repatch. Internet is lost and does not reconnect. Reboot the unit and it resolves.
I use 8.8.8.8 as the DNS.

I have 'ok' knowledge' around Ubuntu, specially really only to my industry- CCTV
What am I missing or doing wrong please?

---

### Post by TheFu on 2023-02-14
Of course when the router or network switch fails, then the internet goes down.  That's obvious.  If it doesn't automatically reconnect, then something about your network architecture is wrong.  I don't see that.

For example, I monitor our WAN connectivity every few minutes and can see when and how long the internet is down for about the last 6 months. 
```
# ./internet-up-summary.sh 
  Using /var/log/internet-up.log ... 
 Period 20230212-062611  - 20230214-163211
  Total Time: 3480 (min) 58.00 (hrs)
  Percent Up Time: 99.37 % 
  Percent Down Time: 0.63 % 
  Total Down Time: 22 min or 0.37 hrs
 Currently: UP
```

and back in January:
```
# ./internet-up-summary.sh /var/log/internet-up.log.6.gz 
  Using /var/log/internet-up.log.6.gz ... 
  Using /tmp/internet-up.log.6
 ... 
 Period 20230101-062611  - 20230108-062411
  Total Time: 10078 (min) 167.97 (hrs)
  Percent Up Time: 98.71 % 
  Percent Down Time: 1.29 % 
  Total Down Time: 130 min or 2.17 hrs
 Currently: UP
```
For each of those failures, I didn't have to take any action for connectivity to come back.  In January, I pulled the WAN router and did a full OS upgrade, so it was down for a bit. Everything on the LAN reconnected when I was done and reloaded the network settings back into the freshly installed router OS.

My network architecture and infrastructure services are probably setup very different from most non-enterprise (i.e. small bus/home) networks.
a) All devices that don't move are configured with static IPs in each OS configuration.  I'm using netplan for this, never network-manager.
b) All devices point to a LAN DNS server and that DNS is NOT the router. I use an lxc container for this purpose.
c) Any DHCP reservations point to a DHCP server that is NOT the router.  I use an lxc container for this purpose.  I place reserved IPs outside the dynamic DHCP range - this is very important. The dynamic DHCP range allows 3 devices - just enough that when a new device gets added, I can get it a reserved IP within a week.
d) Any guest devices are placed onto a different subnet with a different DHCP server just for "unknown" devices. There's a router with active firewall blocking guest devices from the important parts of the network. Guest devices get internet, nothing else.
e) My systems generally use Intel NICs, which I've found to be better supported and don't have issues the cheaper, more common NICs seem to have.  I've been fortunate, only a few Marvell and Realtek NICs are left now, though both have failed in the past.
f) When I create a bridge, it is for VMs only and not with any bonding.  This has more to due with my ignorance. I always manually create the bridges I want for virtual machines. I don't use any automatically created NAT or bridges.  This is more about habit, since 10+ yrs ago, automatically created bridges had terrible performance.
g) My DNS servers are 1.1.1.1 and 1.0.0.1, which is from a more privacy considerate CDN than google. I doubt this matters, but having at least 2 DNS IPs is important.

If you are bridging so many devices, ensure you have STP enabled.  Also, if power outages are causing the router and switch issues, it is time to include a small UPS in your solutions.  I support the PoE requirements could require a larger UPS than the computers would need alone.

I don't think the issue is with Ubuntu.  I think it is in the network architecture.

BTW, you shouldn't need to reboot anything just to bring networking backup.
```
sudo systemctl restart networking.service
sudo systemctl restart network-online.target
```
Only 1 of those should be needed, even in the worst situation, assuming the hardware isn't failed.

---

