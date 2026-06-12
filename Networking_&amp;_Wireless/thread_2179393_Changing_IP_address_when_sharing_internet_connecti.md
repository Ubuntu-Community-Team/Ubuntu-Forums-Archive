---
title: "Changing IP address when sharing internet connection"
date: 2013-10-08
forum: Networking &amp; Wireless
---

### Post by chris1379 on 2013-10-08
I have a computer set up in Windows XP that uses wifi for the internet connection and shares it to the other computers. The sharing is through a wireless router with DHCP disabled. Windows XP uses 192.168.0.1 but Ububtu 12.04 uses 10.42.0.1. I would like to dual-boot without changing ip addresses. I need to change the IP address in Ubuntu because one of the PCs has a static IP in the 192.168.0.x range. I read an older post the suggests I need to edit and compile Network Manager to fix it. I'm hoping there is an easier way.

---

### Post by apmcd47 on 2013-10-08
I would have thought Network Manager is already running on your system. You will need the following IP addresses:
[LIST]
[*]Unique address for your Ubuntu system
[*]Address for router (gateway address)
[*]Address for your DNS server
[*]
[/LIST]
I imagine the DNS server will be your router, or maybe you can get it to use the one provided by your broadband provider (you could try the one used by your PC if it has one set up)

I'm using KDE but I imagine this will work for all flavours of Ubuntu:
[LIST=1]
[*]There should be a network item in your system tray (bottom or top right corner of your screen, depending on your desktop). Right-click this and select the "network mangaement settings"
[*]Make sure you are looking at the "Network Connections" panel and select the "Wired" tab
[*]Double click the "Wired Connection 1" entry (it should be the only one in the list)
[*]You sould have an "Edit Network Connection" dialog open. Open the "IPv4 Address" tab
[*]There should be a "Method" field with "Automatic (DHCP)" selected. Change this to "Manual"
[*]The other fields should become editable. Use the above addresses. Don't worry about the subnet mask; it will choose the correct one for you.
[/LIST]
The network manager dialogs may use different wording from desktop to desktop so you may have to look around if you cannot find exactly what I describe.

Good luck

Andrew

---

### Post by chris1379 on 2013-10-09
I'm thinking this will only work with the one PC that has a manually set  IP address. The laptop and smart phones need DHCP from the Ubuntu PC.  The wireless router only acts as a switch or hub. Setting the wired NIC  to "shared to other computers" works except the IP range is wrong for  the static IP PC. It needs to be static to work with the android phone  that controls several functions on it. In Windows that IP address is  192.168.0.XXX. Ubuntu wants to use 10.42.0.X.

---

### Post by chris1379 on 2013-10-12
I was able to get it working using the instructions [HERE]("https://help.ubuntu.com/community/Internet/ConnectionSharing") . I used iptables and advanced router configuration. Here it is for anyone else facing this situation.

Internet <<==>> wlan0 <> Ubuntu gateway <> eth1 <<==>> Wireless Router
DHCP is turned off on the router as required by Windows ICS 

wlan0 = the network adapter with internet (internal wireless card).
eth1 = the network adapter to which a second computer is attached (internal or LAN).
192.168.0.x = IP subnet for eth1

Configure internal network card

Configure your internal network card (eth1) for static IP like so:

sudo ip addr add 192.168.0.1/24 dev eth1

The external and internal network cards cannot be on the same subnet.

Configure NAT

Configure iptables for NAT translation so that packets can be correctly routed through the Ubuntu gateway.

sudo iptables -A FORWARD -o wlan0 -i eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -F POSTROUTING
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

The first rule allows forwarded packets (initial ones). The second rule allows forwarding of established connection packets (and those related to ones that started). The third rule does the NAT.

IPtables settings need to be set-up at each boot (they are not saved automatically), with the following commands:

    Save the iptables: 

sudo iptables-save | sudo tee /etc/iptables.sav

    Edit /etc/rc.local and add the following lines before the "exit 0" line: 

iptables-restore < /etc/iptables.sav

Enable routing

    Configure the gateway for routing between two interfaces by enabling IP forwarding: 

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

Edit /etc/sysctl.conf and uncomment: 

#net.ipv4.ip_forward=1

... so that it reads:

net.ipv4.ip_forward=1

Advanced Gateway Configuration

DHCP/DNS server

This is deceptively easy, and will be acceptable for most situations. However, it will not allow the ICS client to see computers on different subnets.

    Install software. 

sudo aptitude install dnsmasq

    Stop the server. After dnsmasq has been installed, it is automatically started, so it will need to be stopped before changes can be made. 

sudo /etc/init.d/dnsmasq stop

    Make a backup of the well-commented configuration file (we won't use any of this, but it's handy to have a copy of for reference later). 

sudo cp /etc/dnsmasq.conf /etc/dnsmasq.conf-backup

    Edit /etc/dnsmasq.conf with your favorite text editor, and add the following two lines: 

interface=eth1
dhcp-range=192.168.0.2,192.168.0.200,72h

(My router and static ip computer are higher than 192.168.0.200)

Note: The "interface" should match the interface that your clients are connected to, and the "dhcp-range" should be within the gateway's private IP subnet that you configured according with the "Gateway set up" directions above.

    Start the DHCP/DNS server. 

sudo /etc/init.d/dnsmasq start

Now, your clients should be able to pull an automatic ip address and resolve host names.

This is mostly copied/pasted from the above listed document and adapted to my setup. I hope this helps someone else.

Chris

---

### Post by chris1379 on 2013-11-25
I changed motherboards and had to reinstall Mint 13. This isn't working now because Network Manager starts dnsmasq which keeps it from running for the DHCP/DNS server. Can someone help me figure out what I did wrong.

---

### Post by chris1379 on 2013-11-28
I got it to work.

edit /etc/NetworkManager/NetworkManager.conf and comment out the &#8220;dns=dnsmasq&#8221; line in the "[main]" section.

Use following command and answer YES to enable dynamic updates:
  sudo dpkg-reconfigure resolvconf

If I missed anything, please post it here to help others.

---

### Post by chris1379 on 2014-08-05
I have Mint 17 installed as an alternate OS and this topic has come up again. Does anyone know if there is an easier way to do this now?

---

