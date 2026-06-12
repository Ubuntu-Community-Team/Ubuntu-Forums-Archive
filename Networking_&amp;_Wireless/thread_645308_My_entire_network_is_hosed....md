---
title: "My entire network is hosed..."
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by arkat on 2007-12-19
First I'm FREEAKING out... at my wits end and will do ANYTHING to get this fixed. 

I installed Feisty on VMWare 2 days ago... 

Now all my network connections on all the pc's running Windows XP in the house can't connect to the internet. Everything was working fine prior to this and have tried everything to fix this but I AM STUCK!

- on XP network connections showing a DHCP address that is NOT from my router (showing DHCP 192.168.1.100)
- show that i am connected - yet I cannot connect to the internet 
- ran ip config to see what's what and i'm showing Tunnel Adapter Teredo and and IP address that's shows...

IP 192.168.1.109
Subnet 255.255.255.0
IP: fe80::240:2bff:fe61:5744e%4
Default Gateway 192.168.1.12

I've uninstalled the VMWare crap, deleted the nic cards and reinstalled, rebooted the network routers, etc etc etc...

HELP HELP HELP... i'm freaking. I will pay royally to have someone walk me through this nightmare.

arkat

---

### Post by scxtt on 2007-12-19
can't you set static IPs based off the IP of your router?  almost reads like VMware created a virtual network, then set those devices to be default ... i've used VMware server in Linux and Windows and never had an issue like that ...

---

### Post by arkat on 2007-12-19
> **scxtt said:**
> can't you set static IPs based off the IP of your router?  almost reads like VMware created a virtual network, then set those devices to be default ... i've used VMware server in Linux and Windows and never had an issue like that ...
If I understood you correctly, setting a static Ip on the network connection gives me nothing on this computer... let alone fixing the remainder of the network connections.  I need a wholistic solution that will cure / fix this mess across the entire network... I'm in tears. (really.. I am)

---

### Post by Skidpad on 2007-12-19
What's your physical situation?  Is this an all-wired network?  You said you re-booted your router, but have you *reset* it and returned it to its factory default settings?

If you are wireless, can you connect a computer via ethernet cable directly to your router and see if you can connect?

---

### Post by scxtt on 2007-12-19
if setting static IPs based off your router doesn't get your network connection working on any PC you config, then you've got a larger problem outside of Ubuntu / VMware ...

do you know the IP/netmask of your router (what make,model?) and how to set static IPs in Windows?

---

### Post by vek on 2007-12-21
I'm pretty sure the December 18 update knocked Vmwares networking stuff out completely.  Theres been various fixes floating around.

Currently, I'm also running it in vmware and the only way I can get it to work is to each time I boot up, manually bring up the interface:
sudo ifconfig eth0 up
sudo dhclient &

Hope this helps.  There are TAR files floating around which patch vmware, but I'm holding out for an official fix.

---

### Post by scxtt on 2007-12-21
arkat and i went over this for a few hours in IM - turned out to be a combo of the router and a (currently diskless) NAS device that was messing things up ...

---

