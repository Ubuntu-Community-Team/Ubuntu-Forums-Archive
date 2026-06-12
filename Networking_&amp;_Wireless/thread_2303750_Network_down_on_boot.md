---
title: "Network down on boot"
date: 2015-11-21
forum: Networking &amp; Wireless
---

### Post by Noelinho on 2015-11-21
I'm using Ubuntu Server 14.04.3 (32-bit) in Virtualbox on Windows 7 and using a bridged adaptor. My network is 192.168.1.1/24 and the server runs at 192.168.1.60, which is outside of the DHCP range of the router.

On boot, no errors show and there is no delay whilst waiting for the network. However, the server is not available on the network. Running ifconfig returns the following relevant information:

eth0
inet addr: 192.168.1.60
Bcast: 192.168.1.255
Mask: 255.255.255.0
HWaddr: 08:00:27:8a:e9:20 (this is the same as the MAC address defined in Virtualbox)

The contents of /etc/network/interfaces is:

auto eth0
iface eth0 inet static
address 192.168.1.60
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254
dns-nameservers 8.8.8.8

auto lo
iface lo inet loopback

To get network running after boot, I have to run **sudo ifdown eth0**, followed by **sudo ifup eth0**. Then, it works fine. Then, everything works fine.

I've also noticed if I make a change to the interfaces file above, networking loads properly on the first reboot, but on subsequent boots, I have to take the adaptor down and bring it back again before it works.

Am I doing something wrong, or do I need to set something up in addition to what I'm doing? The fact everything works on the first boot after a change makes me think I need to do something to make the change permanent, but I can't work out what that might be. Anyone able to point me in the right direction?

---

### Post by chili555 on 2015-11-21
That is one busy file! Also, typically, lo appears first. Please try:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.60
netmask 255.255.255.0
gateway 192.168.1.254
dns-nameservers 8.8.8.8
```Restart the interface:```
sudo ifdown eth0 && sudo ifup -v eth0
```Now does it survive a reboot?

---

### Post by Noelinho on 2015-11-21
Thanks for the response. The only reason the loopback was listed below was because I'd seen a suggestion elsewhere previously that it might solve the problem.

I've changed the file to what you suggested and it hasn't solved the issue unfortunately. The settings work sometimes - less than half the time, but it does sometimes come up.

Bringing down eth0 and back up again always works though, immediately.

---

### Post by chili555 on 2015-11-21
We could check the log:```
dmesg | grep eth
```Perhaps something is (probably) amiss during boot.

Please run this when you boot and the ethernet is _not_ up.

---

### Post by Noelinho on 2015-11-21
When the Ethernet isn't working on boot, I get the following information:

[4.728071] e1000 0000:00:03.0 eth0 (PCI:33Mhz:32-bit) 08:00:27:8a:e9:20
[4.731764] e1000 0000:00:03.0 eth0 Intel(R) PRO/1000 Network Connection
[15.707645] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX

I get exactly the same output whether the Ethernet is working or not.

If I take the adaptor down and bring it back up:

[272.453255] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[272.453874] IPv6: ADDRCONF(NETDEV_UP) eth0: link is not ready
[272.453940] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

Here, if the Ethernet is already up, the first and second lines are sometimes reversed.

Is that any help? I appreciate the help - I've been stumped by this for months!

---

### Post by chili555 on 2015-11-21
> Is that any help?Not really.

Is there any difference here whether the interface is up or down?```
sudo ethtool eth0
```The driver in question, e1000, has several available parameters that we might try to manipulate.

I hesitate to rely on brute force, also known as /etc/rc.local, but maybe.

---

### Post by Noelinho on 2015-11-21
There's no difference at all in running that between the network working or not.

I'm not sure what /etc/rc.local does - do you want me to run it?

---

### Post by chili555 on 2015-11-21
> **Noelinho said:**
> There's no difference at all in running that between the network working or not.

I'm not sure what /etc/rc.local does - do you want me to run it?/etc/rc.local is the last resort when everything looks perfect but it just doesn't work! It simply runs the commands behind the scenes automatically as you boot. Please open a terminal and do:```
sudo nano /etc/rc.local
```...or whichever text editor you've been using so far.

Add three lines above the last line, exit 0.```
ifdown eth0
sleep 1
ifup eth0
```Proofread carefully, save and close the text editor. Reboot.

---

### Post by Noelinho on 2015-11-21
Ah, ok. Yes, it may not be the perfect solution, but it's a lot better than having to manually run the commands every time I switch it on! Thanks for your help.

---

### Post by chili555 on 2015-11-21
> **Noelinho said:**
> Ah, ok. Yes, it may not be the perfect solution, but it's a lot better than having to manually run the commands every time I switch it on! Thanks for your help.So all fixed? Solved??

---

### Post by Noelinho on 2015-11-21
> **chili555 said:**
> So all fixed? Solved??

It seems to be - ping responds just before the login screen appears, and that's good enough for what I need it for.

---

