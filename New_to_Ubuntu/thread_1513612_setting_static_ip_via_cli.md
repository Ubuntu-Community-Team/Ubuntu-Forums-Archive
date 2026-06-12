---
title: "setting static ip via cli"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Bob Bertrands on 2010-06-19
Hey all

In order to make my computer have a static ip adress I did some research and found out I had to change /etc/network/interfaces and /etc/resolv.conf.
My router has ipadress 10.0.0.138.

Here's how these files now look:

```
# Edited by Bob Bertrands 19/06/2010
nameserver 195.238.2.22
nameserver 195.238.2.21
nameserver 10.0.0.138

``````

# edited by Bob Bertrands 19/06/2010
mapping hotplug
    script grep
    map eth0

auto eth0
iface eth0 inet static
    address 10.0.0.80
    netmask 255.255.255.0
    gateway 10.0.0.138
    broadcast 10.0.0.255

```With these settings I do seem to have a static ip and I can access my pc, using this ip, from a different pc, which has an ipadress via auto DHCP, in the same network.
I cannot access the internet from this pc & dns doesn't work, except for my internal adresses. 

I don't see what I'm doing wrong, please help

B

---

### Post by cariboo on 2010-06-19
If you are using a desktop version newer than 9.04 you have to set a static ip address using Network-Manager. Right-click the network-manager icon in the top panel and select edit, next highlight your device in the window that opens, then click edit. Once the editing window opens, click the IPv4 Settings tab. Once in the settings window, select manual in the method drop down, then click the Add button. Enter your ip address and press enter, then enter your netmask address and press enter and finally enter your gateway ip address and press enter. Enter your dns address provided by your isp in the DNS Server text box, then click apply. Enter your password, to apply the changes. To make the changes take affect, either restart networking, or reboot.

---

### Post by Bob Bertrands on 2010-06-20
Thanks for the quick replay. 
I have a few remarks, listed below:

1 So you're saying it's imposible to set a static ip via cli.
2 I need to use the cli cause I'm running ubuntu without the gui.
3 I'm using 9.04 but it's possible to install a newer version.

B

---

### Post by The Cog on 2010-06-20
Of course it's possible to set up a static IP using CLI. 

I've been doing that on my desktop for more years than I would like to admit to. It's currently running 10.04, but I've done the same for every version since Hoary Hedgehog.

My etc/networks/interfaces looks like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.8.101
netmask 255.255.255.0
gateway 192.168.8.1

```I notice that there's nothing in there about hotplug, so I wonder if that is interfering with normal workings.

My current /etc/resolv.conf looks like this:
```
nameserver 192.168.8.1
```which you will notice is using my router as its name server. But I didn't always do it like that. My previous router (before it died) didn't have an inbuilt nameserver, so I used to point to a pair of ISP supplied nameservers just as you do.

One file that I found out about recently is /etc/nsswitch.conf. This affects name resolution - the order in which different methods are tried. I think the "hosts" entry is the important one for name resolution. My /etc/nsswitch.conf looks like this:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

There are a number of things that could be the problem. 

Firstly, make absolutely sure that the IP address you are allocating is not also being allocated to another PC by DHCP. The easiest way to check this is to try to ping your static address while your static PC is disconnected or powered off. 

Secondly, see if you can talk to the external nameservers. Try the command ```
dig +short @195.238.2.22 www.ubuntuforums.com
``` and see if you can get a response. I can't get a response from that address from where I am, so maybe it's not a public nameserver. I can get a response from ```
dig +short @8.8.8.8 www.ubuntuforums.com
``` which is a public nameserver (google's I think), so maybe you could try that one.

One problem I can think of is that I think (not certain) that the nameservers are tried in order - if the first one times out then the second is tried etc., but the answer from the first nameserver to trespond is used. If the first nameserver to respond says "no such name" then that is the answer, other nameservers in the list are not tried. I think this fact supports the theory that you cannot contact the nameservers you have listed first. if you could, then I would not expect you to be able to resolve internal hosts by name because the external nameservers would be saying "no such name". 

If you can get a DNS response from 8.8.8.8 then your basic internet connectivity and routing are working fine.

---

### Post by Bob Bertrands on 2010-06-20
Hello Cog

My DHCP adress pool is 10.0.0.39-10.0.0.42 so no computer is allready using 10.0.0.80. If I ping 10.0.0.80 from another pc , the ubuntu 9.04 pc responds as supposed.

When I excecute
```
dig +short @195.238.2.22 www.ubuntuforums.com
dig +short @8.8.8.8 www.ubuntuforums.com

```

I get the correct IP's returned from any computer with an automatic DHCP IP, but the computer with the static IP. The staticippc returns connection timed out to both commands.

If I ping directly to the ip's of sites, I don't get responses either.

So it seems the problem is located somewhere else. I was thinking maybe my router doesnt support more than 4 ip's or something. (router = thomson speedtouch 510, an ancient router due to be replaced)

---

### Post by The Cog on 2010-06-20
I can only think of two possibilities at this stage.

Firstly, your router is doing a kind of firewall thing, and only passing packets from PCs which have DHCP leases. If that's the case, I don't know what to do.

Second possibility, you have the wrong gateway address. You could check your default route on the working PCs - the command is **route print** for windows, or **route -n** for linux.

Does your router let you allocate fixed addresses to chosen MAC addresses in its DHCP setup? That might be an solution.

---

### Post by Bob Bertrands on 2010-06-20
My router can't do the mac adress thing.

The output of route -n is:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth1

```

Seems like 10.0.0.138 is my gateway.

I will checkout the dhcp-firewall possibility

---

### Post by The Cog on 2010-06-20
So it looks like your routing is right. I figured it probably was, but it was worth checking. I can't think of anything else other than that your router is being picky about what addresses it is prepared to handle.

Just one last thing to check though - can you somehow double-check the subnet mask. Looking at ifconfig on a DHCP configured PC will confirm whether it's 255.255.255.0.

---

### Post by Bob Bertrands on 2010-06-22
Checked, the subnetmask on both pc's are the same.

---

