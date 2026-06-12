---
title: "[SOLVED] Sharing a wireless connection (single connecton)"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by borobudur on 2006-10-30
An [Access Point]("http://en.wikipedia.org/wiki/Access_Point") without a rooter.
```
~~~ Internet ~~~  <--->  --- eth0 ---
                                          --- ra0 ---   <--->   laptop
```
**Server**
[LIST]
[*]Installed [hostap]("http://hostap.epitest.fi/"). This is a software which makes it possible to use a regular wireless card as an access point.
[*]Installed a [dhcp-server]("http://en.wikipedia.org/wiki/Dhcp#Der_DHCP-Server"). Followed this [HowTo]("http://ubuntuguide.org/wiki/Ubuntu_dapper#DHCP_Server").
[*]Configuration of the */etc/default/dhcp3-server* file
[INDENT]The network interfaces which the DHCP server should listen to:[/INDENT] 
```
INTERFACES="ra0"
```
[*]Configuration of the */etc/dhcp3/dhcpd.conf* file
```
 # A slightly different configuration for an internal subnet.
 subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
  option domain-name-servers 62.2.17.60, 62.2.24.162, 62.2.17.61, 62.2.24.158;
  option domain-name "mydomain";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
 }

```
[*](1)Set the network interface *ra0* to static 192.168.0.1 (subnet mask 255.255.255.0)
[*](2)Then configure the NAT
[INDENT]Type all the following commands in a root terminal, DO NOT use sudo.[/INDENT]
```
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```
where *eth1* is the network card that the Internet is coming from
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
[*]Install dnsmasq and ipmasq using apt-get:
```
apt-get install dnsmasq ipmasq
```
[*]Restart dnsmasq:
```
/etc/init.d/dnsmasq restart
```
[*]Reconfigure ipmasq to start after networking has been started:
```
dpkg-reconfigure ipmasq
```
[*]Repeat steps 1 and 2.
[*]Add the line *net/ipv4/ip_forward = 1* to */etc/sysctl.conf*
[*]Reboot. (Optional)
[*]Add following lines to */etc/network/interfaces* ([HowTo]("http://www.freewrt.org/trac/wiki/Documentation/Howto/Network"))
```
wireless-essid connectionpoint
wireless-mode Ad-Hoc
```
[INDENT]if you want to do MAC filtering, add the following:[/INDENT]
```
wireless-macmode 2
wireless-mac 00:01:02:03:04:05 06:07:08:09:0a:0b

```
[INDENT]better then using the *iwconfig* command to setup the interface[/INDENT]
```
sudo iwconfig ra0 essid connectionpoint
sudo iwconfig ra0 mode ad-hoc

```[/LIST]

**Client**
Notebook with a wireless card.
[LIST]
[*]Set the network interface to dynamic (dhcp-client)
[*]Used the *iwconfig* command to setup the interface
```
sudo iwconfig ra0 essid connectionpoint
sudo iwconfig ra0 mode ad-hoc

```[/LIST]

Have fun!
borobudur

---

### Post by borobudur on 2006-10-31
Found it!

Followed this [ HowTo]("http://ubuntuforums.org/showthread.php?t=91370"), perfect!

Thanks [ anaoum]("http://ubuntuforums.org/member.php?u=24878")

---

