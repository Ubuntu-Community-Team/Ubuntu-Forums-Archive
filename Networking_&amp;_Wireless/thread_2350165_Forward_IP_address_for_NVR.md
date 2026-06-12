---
title: "Forward IP address for NVR"
date: 2017-01-21
forum: Networking &amp; Wireless
---

### Post by serverman2020 on 2017-01-21
Hi Guys,

Linux semi-newbie here. I currently have two home linux systems running at the moment - one ubuntu server and one NVR.

At the moment, my home network is running on the IP address of 192.168.0.XXX with the IP of the NVR being 192.168.0.195

The NVR has a seperate network for the IP cameras of 10.1.1.XXX

My goal is to try to access the 10.1.1.XXX cameras from the main network. After doing some homework, it seems I need to forward the ports of these IP cams. Unfortunately, the NVR doesnt allow this through the User Interface. The NVR has a linux busybox system running on it - luckily I managed to connect to the Busybox system via telnet CLI. 

SOO I think I'm halfway there... somehow I need to edit some files in the telnet connection to foward say cam one 10.1.1.1 to 192.168.0.195:1

Eventually my plan is to have the NVR and the ubuntu server both recording (ubuntu sever via zoneminder etc). I don't have a POE switch, so thats why I'd like to keep my cameras connected to the NVR. 

Does anyone know how I can acheive this? Am I on the right path??

---

### Post by geeksmith on 2017-01-22
Does the NVR have to NAT the 10.1.1.0 network? If not, then you can add a route to that network via the NVR and access that subnet without port forwarding.

If that's not enough detail, please reply and I'll give a more verbose response.

---

### Post by serverman2020 on 2017-01-22
Hi Guys,

Linux semi-newbie here. I currently have two home linux systems running at the moment - one ubuntu server and one NVR.

At the moment, my home network is running on the IP address of 192.168.0.XXX with the IP of the NVR being 192.168.0.195

The NVR has a seperate subnet for the IP cameras of 10.1.1.XXX

There are two ethernet devices on the NVR eth0 (where is connects to the main 192.168.0.XXX network) and eth1 (where it connects to the cameras)

My goal is to try to access the 10.1.1.XXX cameras from the main  network. After doing some homework, it seems I need to forward the ports  of these IP cams. Unfortunately, the NVR doesnt allow this through the  User Interface. The NVR has a linux busybox system running on it -  luckily I managed to connect to the Busybox system via telnet CLI. 

SOOOO I think I'm halfway there... somehow I need to edit some files in  the telnet connection to foward say cam one 10.1.1.1 to 192.168.0.195:1

Eventually my plan is to have the NVR and the ubuntu server both  recording (ubuntu sever via zoneminder etc). I don't have a POE switch,  so thats why I'd like to keep my cameras connected to the NVR. 

Does anyone know how I can acheive this? Am I on the right path??

---

### Post by cariboo on 2017-01-22
Merged to similar threads.

---

### Post by serverman2020 on 2017-01-23
Hi Geeksmith,

I tried changing the internal IP of the NVR to  192.168.0.XXX for the internal cameras. It says its not permitted to be  the same as the main network.

Is this what you mean?

---

### Post by geeksmith on 2017-01-23
Not quite. Right now the NVR is translating the 10.1.1.0 network addresses into its own 192.168.0.195, making everything on the 10.1.1.0 network unreachable without some work to forward ports through to hosts on the 10.1.1.0 network. That approach, as you mentioned, is very limiting. This type of setup is called network address translation (NAT), or more accurately source NAT (SNAT). Linux firewalls also call this NAT mode masquerade, since all the 10.1.1.0 network is masquerading behind the 192.168.0.195 address.

What I'm asking is whether NAT can be disabled on the NVR. By so doing, you could route directly to the 10.1.1.0 network via 192.168.0.195, which would act as an IP gateway to the 10.1.1.0 network. This would allow you to access each camera by its 10.1.1.xxx IP address without the need for port forwarding or other nonsense.

If you can disable NAT on the NVR and have it still act as an IP gateway, then your systems on the 192.168.0.0 network can add a route to the 10.1.1.0 network using the NVR 192.168.0.195 as the gateway to reach that network. In Linux, you run a simple command like this:

```
sudo ip route add 10.1.1.0/24 via 192.168.0.195
```

You can also add routes like this through the network manager GUI by editing the Ethernet interface IPv4 settings and adding a static route. The same is possible in Windows and MacOS.

If the NVR doesn't allow you to disable NAT, then there's another option. You could add a 2nd NIC to any system on your 192.168.0.0 network and assign an IP address on the 2nd NIC in the 10.1.1.0 network. That system could access all the cameras directly. It could also act as the IP gateway to the cameras for the other 192.168.0.0 hosts if you enabled IP routing on that system.

---

### Post by serverman2020 on 2017-01-24
Hi Geeksmith,

Thanks for your detailed response. I've had a look at the UI of the NVR, and there isnt any option for disabling NAT. Could this be achieved with the BusyBox telnet login?

If not, then luckily the Ubuntu server i'm running has x2 NICs. At the moment, only one is utilised for the 192.168.0.0 network. I have it set up with virtual machines, and each virtual machine has a bridged virtual NIC and an unique IP address.

My goal is to set up a VM for the CCTV. Am i right in saying, that I should connect the 2nd NIC of the server directly in to one of the POE ports? Once I've done this, how exactly should I edit the /etc/network/interfaces file for this required set up? Will the VM still be able to be accessed from the 192.168.0.0 network?

---

### Post by geeksmith on 2017-01-24
I'm not sure about changing NAT settings on the NVR via busybox shell. It's probably possible, but if they don't offer an option to do so in the GUI, then I'm not sure how making the change manually will affect warranty/support status.

If you want to go the other route, then you can plug your 2nd NIC into one of the ports on the NVR or into an external switch connected to the NVR. Here are the additions you'd make to the interfaces file:
```
auto eth1
iface eth1 inet static
    address 10.1.1.5
    netmask 255.255.255.0

```

This obviously assumes that eth1 is the name of the interface and that 10.1.1.5 is not already in use. I suggest making these changes before plugging in the NIC.

---

### Post by serverman2020 on 2017-01-25
Geeksmith - thanks for staying with this thread. Ok I think we're nearly there!

enp4s0 - The NIC currently in use on my Host and Virtual Machines (bridged)

enp5s0 - The currently free NIC

The /etc/network/interfaces file on my host set up:

```

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.0.69
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1
        bridge_ports enp4s0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
iface enp4s0 inet manual
```

The /etc/network/interfaces on a VM:

```
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ens3
iface ens3 inet static
        address 192.168.0.86
        broadcast 192.168.0.255
        netmask 255.255.255.0
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1


```

So am I correct in saying that the new Survelliance VM be accessible via 192.168.0.0 network and through that we can gain access to the 10.1.1.0 network also? How would we change these files to acheive this?

---

### Post by geeksmith on 2017-01-25
If I understand your desired network layout, the Host machine will be the gateway between the networks and the VM will simply use the Host to obtain a route to the NVR. If that's incorrect, let me know.

On the Host machine, do the following:

**Host IP address setup**
Add the following stanza to /etc/network/interfaces:
```

auto enp5s0
iface enp5s0 inet static
    address 10.1.1.5
    netmask 255.255.255.0

```

**Physical connection**
Plug the cable into the NVR network and the Host NIC

**Bring the interface up**
```
sudo ifup enp5s0
```

**Verify connectivity**
Ping some addresses in the 10.1.1.0 network to verify that you have a connection.

**Enable routing**
Run this command to enable IPv4 routing on the Host:
```
sudo sysctl net/ipv4/ip_forward=1
```

This will only be in effect until you reboot. To make it permanent, edit /etc/sysctl.conf and uncomment the line below.
```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```

**The rest of the network**
**Routes**
At this point your Host machine is acting as a gateway to access the NVR network. However, the rest of the hosts on the network do not know this! The only routes they know are:
[LIST]
[*]The loopback network (127.0.0.0/8)
[*]Their local LAN (192.168.0.0/24)
[*]Everything else goes through the default gateway (192.168.0.1)
[/LIST]

There are two ways to inform the rest of the hosts on the network that your Host machine is the gateway to the NVR network.
[LIST=1]
[*]Configure the gateway (192.168.0.1) with a route to the NVR network through your Host.
[*]Configure every host on the network with a route to the NVR network through your Host.
[/LIST]

**Easy way -- the LAN router**
Obviously the first option is easier to do. If your router (192.168.0.1) allows you to configure a static route to 10.1.1.0/24 through 192.168.0.69 then you're set. Take a look at the configuration interface for the router -- it may be buried in the advanced settings somewhere. Add the route and try pinging the NVR hosts from any host n the regular LAN and it should work.

**Less easy way -- touch every host**
If that doesn't work, or if you just want to try this on one host, you can add the route to one system on the network and try it out. Maybe the VM is a good candidate for this. Add the route to the system with this command:
```
sudo ip route add 10.1.1.0/24 via 192.168.0.69
```

Then try pinging some of the NVR network hosts. Perhaps start with 10.1.1.5, then try the cameras.

Like the route setting on the Host, the route you added will not persist across a reboot. If you want to make it persist, edit /etc/network/interfaces on the VM and make the primary network interface stanza look like this (you can leave the rest of the file alone):
```

# The primary network interface
auto ens3
iface ens3 inet static
        address 192.168.0.86
        broadcast 192.168.0.255
        netmask 255.255.255.0
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1
        post-up ip route add 10.1.1.0/24 via 192.168.0.69
        pre-down ip route del 10.1.1.0/24 via 192.168.0.69

```

Again, you only need to mess with the VM directly if you're unable to add the route to your router (192.168.0.1). A similar configuration will need to be done on every host on the LAN that you'd like to access the NVR network.

That's it! This may look like a lot of work, but it's not so bad once you start. If you run into any problems let us know.

---

### Post by geeksmith on 2017-01-25
By the way, if you only want the surveillance VM to access the NVR network, then this can be simplified. It still requires the physical connections and some setup on the VM, but not much else. If the rest of the hosts need to access the NVR network directly, then go with the approach I described above.

---

### Post by serverman2020 on 2017-01-25
Geeksmith,

Excellent response! The thing I want to do here is have only the VM access the NVR 10.1.1.0 network. I still want the VM to have a 192.168.0.XX IP address from enp4s0 bridged NIC, but also have the VM access to the enp5s0 NIC and thus the NVR. I would have thought all I would need to do is configure the VM to use the enp5s0 NIC?

Is this correct?

(BTW I'm using KVM QEMU for my virtual machines)

---

### Post by geeksmith on 2017-01-25
Yes, that's correct -- from your first post I thought you needed to access the NVR network from the LAN, not just from one host. All you need to do is configure and connect the 2nd physical NIC, then attach it to the VM, which it sounds like you're able to do (since you did it for the 1st NIC). Probably a similar bridge setup, except that the Host machine won't require an IP address on that 2nd NIC. It can simply bridge the VM traffic into the network.

---

### Post by serverman2020 on 2017-01-26
Hi Geeksmith,

To be honest, I'm a bit unsure how to do this. I followed some guides online, and managed to "hack" my way in to creating the virtual machine bridge.

How would I go about giving my VM a 192.168.0.XX IP address, and at the same time, give the VM access to the second NIC?

Thanks!
T

---

### Post by geeksmith on 2017-01-26
I haven't done this with qemu/KVM, but I'm very familiar with the underlying systems that they use. A good walk-through of adding a bridge can be found here:
[https://wiki.ubuntu.com/KvmWithBridge](https://wiki.ubuntu.com/KvmWithBridge)

Based on that article, you'd need to add br1 to the system just like you did br0, but using enp5s0 in the bridge_ports section. Your resulting interfaces file on the Host would like like this:
```

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
        address 192.168.0.69
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1
        bridge_ports enp4s0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
iface enp4s0 inet manual


auto br1
iface br1 inet static
        bridge_ports enp5s0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
iface enp5s0 inet manual

```

Note the lack of an IP address in br1 -- you don't need one, since you're just bridging VM traffic. You can add one if you want, but it's not necessary. Run:
```
sudo ifup br1
```
...to bring up the interface.

You'll then need to edit the VM's XML config file in /etc/libvirt/qemu and add another section for a network interface using br1. You should already have an entry for an interface using br0.
```

    <interface type='bridge'>
      <mac address='00:01:01:01:01:ff'/>
      <source bridge='br1'/>
    </interface>

```

At this point you make this configuration active by shutting down all VMs and running:
```
sudo /etc/init.d/libvirtd restart
```

Finally,  fire up the VM and edit its network config. The VM's interfaces file should look something like this:
```

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ens3
iface ens3 inet static
        address 192.168.0.86
        broadcast 192.168.0.255
        netmask 255.255.255.0
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1

# The NVR network interface
auto ens4
iface ens4 inet static
        address 10.1.1.5
        netmask 255.255.255.0

```

I'm guessing the name is ens4, but you may have to tweak that. To bring up the NVR network interface in the VM:
```
sudo ifup ens4
```

Now ping some hosts in the NVR network from the VM to see if it's all working. Done!

---

### Post by serverman2020 on 2017-01-26
Mate! This is fantastic. Thank you so much.

I've managed to ping my cameras and its all go!

Thanks again! Now to set up Zoneminder..............

---

### Post by geeksmith on 2017-01-26
Great! Best of luck to you!

---

