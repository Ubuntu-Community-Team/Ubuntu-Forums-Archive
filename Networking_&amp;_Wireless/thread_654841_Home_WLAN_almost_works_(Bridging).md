---
title: "Home WLAN almost works (Bridging?)"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by finneces on 2007-12-31
Iv been trying to set up my Ubuntu desktop as a wireless router.  I bought a Fritz USB WLAN, installed the windows driver wrapper ndiswrapper and was able to get my laptop to talk to the desktop (on the windows machine I clicked the connect to button and it connected).   Following the excellently detailed tutorial here:
[http://ubuntuforums.org/showthread.php?t=376283]("http://ubuntuforums.org/showthread.php?t=376283")

I modified my /etc/network/interfaces to look like this:
```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.conf

auto wlan0
iface wlan0 inet dhcp
wireless-mode master
wireless-essid "FliegendesSpaghettimonster"

#Bridge interface
auto br0
iface br0 inet static
    address 10.1.1.1
    network 10.1.1.0
    netmask 255.255.255.0
    broadcast 10.1.1.255
    bridge-ports eth0 wlan0
```

If I include this so called "bridging" stuff then I loose my connection to both the laptop and the world through my eth0.  So I commented out the bridging stuff and the did
/etc/init.d/networking stop   and then start
and then I have internet access on my desktop again, but cant network to my laptop.  Bummer.

If anyone has an idea how to rectify this, I would be most grateful.  

Oh, and at some point I would like to be able to make it a secure access (encripted) and with a password, caus right now its not.  If anyone knows how to this I would also be most greatful. 

P.S. when I run the networking start prorgram I see:
```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Waiting for br0 to get ready (MAXWAIT is 32 seconds).

```

and then it says ok.  Dont know if that helps...

---

### Post by Predator[23rd] on 2007-12-31
Hi!

I am also a bit new to this stuff but maybe I can be of a little assistance... and learn something too. So take my words not for granted, just as input to think about the problem and work your way up to your perfect router. :)

First let me recap your network setup:

You have a desktop machine which is connected to the internet via DSL or something else. You also have installed a wireless card to give your other wireless devices (PDA/MDA, notebook, microwave, etc.) internet access.

If that is the case all you need - AS FAR AS I KNOW - is to setup your Ubuntu machine to serve as DHCP Server (very easy, check the Ubuntu Server Documentation for a one page walk through) and enable NAT (also in the Ubuntu Server Documentation). 

When you setup NAT there is one thing to consider: IPV4_FORWARD! By the "echo 1 > /etc/proc/...." command you are setting up a temporary ip forwarding (which is key to NAT). As soon as you reboot it will be gone and set back to 0 (disabled). For a more permanent solution you need to edit /etc/sysctl.conf. But it is not enough to uncomment the "ipv4_forwarding" line, you have to delete the ".default." part in the line - as pedalwrench pointed out in his post you have already linked.

I hope this helps a bit. Please correct me if I am wrong. Thanks!

Predator out!
Resistance is futile.

---

### Post by finneces on 2007-12-31
Thanks for a quick response even on a holliday!

> **'Predator[23rd] said:**
> 
You have a desktop machine which is connected to the internet via DSL or something else. You also have installed a wireless card to give your other wireless devices (PDS, notebook, microwave, etc.) internet access.

Yes!  Exactly!  The microwave!  Now you see my predicament!  

> **'Predator[23rd] said:**
> 
If that is the case all you need - AS FAR AS I KNOW - is to setup your Ubuntu machine to serve as DHCP Server (very easy, check the Ubuntu Server Documentation for a one page walk through) and enable NAT (also in the Ubuntu Server Documentation). 

Following the instructions on the link I posted, and some other random google links, I installed dhcp-server, though I dont think I see it running, only client stuff:
```
ps aux | grep dhcp
dhcp      7221  0.0  0.2  14096  1068 ?        Ss   20:53   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
dhcp      7293  0.0  0.2  14088   988 ?        Ss   20:54   0:00 dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
```
Also, I did setup NAT (masqurading):
```
sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o ppp0 -j MASQUERADE

```
And I saved all the iptable stuff.
But that shouldnt be important for my current problem, which is that I loose outbound internet connection from my linux desktop/should be server when I include this bridging stuff.  I believe this bridging is vital for the desktop to act as a router, but if I loose all internet connection, then it sort of defeats the purpose.

Im not sure if my bridging thing is set up correctly, caus I really dont understand it, and not sure if there is something else Im forgetting.  It took me a long time to get this far and Im not about to give up yet, so I appreciate any help!

---

### Post by Predator[23rd] on 2007-12-31
Bridging is not vital for your machine to work as router. Correct iptables entries with ip forwarding is the important thing here.

Installing the dhcp-server package is not enough. You have to edit two entries: /etc/dhcp/dhcpd.conf to setup dhcp server details and /etc/default/dhcp3-server to tell the dhcp server which NIC "points towards your internal network".

/etc/dhcp/dhcpd.conf could be something like this:

[I]subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.110;
  option domain-name "hier_wohnt_das_spaghetti_monster"; 
  option domain-name-servers 195.58.160.194;
  default-lease-time 600;
  max-lease-time 7200;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}

subnet 192.168.10.0 netmask 255.255.255.0 {
  #dummy entry for the second NIC
}[/I]

/etc/default/dhcp3-server could be something like this:
[I]
INTERFACES = "wlan0"[/I]

After this you have to add three entries to iptables (if you need to empty all iptable routes you can type "iptables --flush" or just "iptables -F" to start from scratch). The commands are something like this:

[I]sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/16 -o wlan0 -j MASQUERADE
sudo iptables -A FORWARD -s 192.168.1.0/16 -o wlan0 -j ACCEPT
sudo iptables -A FORWARD -d 192.168.1.0/16 -m state --state ESTABLISHED,RELATED -i wlan0 -j ACCEPT
[/I]

Last step will be enabling ip forwarding to make NAT work:
open /etc/sysctl.conf and uncomment the line with "net.ipv4.conf.default.forwarding=1". dont forget to delete the ".default." part. Now restart your dhcp server and network. That SHOULD be it - as far as I know it. But as I said, I am also a bit new to this stuff and can be horribly wrong.

p.

---

