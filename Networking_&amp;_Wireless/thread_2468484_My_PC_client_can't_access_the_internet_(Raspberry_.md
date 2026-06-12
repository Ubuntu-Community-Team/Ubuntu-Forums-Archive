---
title: "My PC client can't access the internet (Raspberry Pi Tor Transparent Proxy)"
date: 2021-10-31
forum: Networking &amp; Wireless
---

### Post by zevraamb on 2021-10-31
Hello everyone,
 
I want to use my Raspberry PI 4 8GB as a transparent TOR proxy between my PC and the Internet.
I based myself on this tutorial that I found: [https://blog.itpro.tv/building-a-transparent-tor-proxy-with-a-raspberry-pi/](https://blog.itpro.tv/building-a-transparent-tor-proxy-with-a-raspberry-pi/)
There is also a corresponding webinar that explains the configuration here: [https://www.youtube.com/watch?v=HEmYm3SlZn0](https://www.youtube.com/watch?v=HEmYm3SlZn0)

I have followed all the steps mentioned in the tutorial but when connecting a client (my PC) to the Raspberry PI, it seems that my PC manages to get an IP from the DHCP server configured on the Raspberry PI but my issue is that my PC still can't access the Internet, and I can't figure why.

If you can help me with that, I would be forever grateful :)

Below I will explain briefly what I did :
 

[LIST=1]
[*]Following the tutorial, I flashed the latest version of Ubuntu (in my case the desktop version 21.10) on a MicroSD Card and put it in my Raspi memory slot
[*]After the fist configuration of Ubuntu, I went in /boot/firmware/config.txt and edited dtoverlay=vc4-fkms-v3d in order to avoid HDMI output freezes on my Raspi (it appears that it is a recent and known issue that will be corrected soon)
[*]I did step 4 and 5 of the mentioned above tutorial without changing anything (except putting my name for my Raspi as the hostname in step 5)
[*]For step 6, as it appears that "cloud-init" is not installed by default on the latest versions of Ubuntu desktop, I had to manually change my USB NIC name interface into “eth1”. To do that, I put some additional content into the /etc/netplan/10-network.yaml configuration file as follows: 
```
network:  
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: false
      addresses: [192.168.0.1/24]
    <random interface name of my USB NIC based on its macaddress>:
      match:
        macaddress: “<the MAC address of my USB NIC>”
      set-name: eth1
      dhcp4: true
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
```
[*]Then I did step 7 to 11 of the mentioned above tutorial without changing anything. There was no error on my side. After step 11, I could ping4 google.fr from my Rasperry PI, tor was up and running without errors, the same with my ufw and my dhcp server configured for my eth0 interface. Still, when connecting a PC to the ethernet port of my Rasperry PI, the PC couldn’t access the Internet. The connected client is a Windows PC, and when connecting the ethernet cable between eth0 and my PC, the network settings on my PC read “Network X, no Internet”
[/LIST]

After doing all that, I wondered if the problem was that my ISP box router at home also uses the 192.168.0.0/24 IP range to assign IP addresses to devices in my house.
I thought that using the same range of private IPs before and after my Raspberry PI proxy might be a problem (I'm not an expert at networking). So I started the tutorial again and made the following changes to the various files, in order to use the 172.16.0.1/12 private IP range before my Raspi proxy (eth0):

/etc/netplan/10-network.yaml : I put "addresses: [172.16.0.1/12]" for eth0

```
network:version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: false
      addresses: [172.16.0.1/12]
    <random interface name of my USB NIC based on its macaddress>:
      match:
        macaddress: “<the MAC address of my USB NIC>”
      set-name: eth1
      dhcp4: true
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]


``` 
/etc/dhcp/dhcpd.conf :

```
subnet 172.16.0.0 netmask 255.240.0.0 {
range 172.16.0.2 172.16.0.254;
option routers 172.16.0.1;
option domain-name-servers 172.16.0.1;
}
```

/etc/tor/torrc :

```
VirtualAddrNetwork 10.192.0.0/10
AutomapHostsSuffixes .onion,.exit
AutomapHostsOnResolve 1
TransPort 172.16.0.1:9040
DNSPort 172.16.0.1:5353
```

/etc/ufw/before.rules : I just changed the first PREROUTING rule

```
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A PREROUTING -i eth0 -p tcp -m tcp -d 172.16.0.1 --dport 22 -j ACCEPT
-A PREROUTING -i eth0 -p udp -m udp --dport 53 -j REDIRECT --to-ports 5353
-A PREROUTING -i eth0 -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j REDIRECT --to-ports 9040
COMMIT
```
 
But again, after doing all that, my PC can’t access the Internet when it is connected on my Raspi eth0 interface (however on my Raspberry PI, I can still ping4 google.fr so it seems that there is no issue on my USB NIC eth1 interface). According to the tutorial, and when watching the webinar, it seems that if I had the correct config, I would just have to plug my PC into my Raspi and it must be able to get an IP from the DHCP server and be able to access the Internet... I can't figure why my PC can't.

Could you help me to resolve my issue please ?

Thanks a lot by advance !

---

