---
title: "Ifconfig drops eth0 after manual IP configuration"
date: 2017-06-24
forum: Networking &amp; Wireless
---

### Post by vbowers on 2017-06-24
I am new to Linux, but not new to IT or networking. I am trying to set up an Ubuntu 16.04 LTS server as a DNS/DC server. One of my first steps is to set a static IP address.

Networking works fine under DHCP. When I went into NetworkManager, the initial screen showed the correct DHCP network info. When I clicked on the Options button with Wired hightlighted, NetworkManager did not offer any options for eth0 as it should have, instead it asked me to create a new connection. Interestingly, if I choose that option, it starts at eth1, apparently aware that eth0 is in use.

I confirmed that eth0 exists by running ifconfig, which reported lo and eth0 as up, with valid information. I then ran nano and edited /etc/network/interfaces to set the eth0 interface to static, as shown at [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic) .  After doing this, I rebooted the system to have it take effect. After the reboot, the virtual machine (running a vm under Windows10 Hyper-V using a static MAC address on the VM, which is not standard, though I tried this both ways) was unable to communicate with local or Internet hosts. Running ifconfig showed that the VM now only recognized lo as an interface, eth0 had disappeared. 

I have worked on this for several days and have not made any progress. Any assistance would be greatly appreciated, as this makes no sense to me. I feel like this *should* be straightforward, especially given the excellent examples provided online, but this has really kicked my ass. Hopefully once I get this worked out I will be able to get my new DNS/DC server up and running.

Thanks!

---

### Post by papibe on 2017-06-24
Hi vbowers.

I believe you are trying to set this up on a Ubuntu Desktop edition.

Server and Desktop editions require different network set ups. On a desktop the network is managed by NetworkManager, so any direct modification of files, like /etc/network/interfaces does not work unless you start by either disabling or uninstalling NM.

The simplest way to set up a static IP is to edit the interface setting instead of creating a new one. Edit your current working DHCP eth0 connection and then go to 'IPv4 Settings'. There you can change DHCP to manual (static), and set up IP, mask, gateway and DNS.

I'm not familiar with Hyper-V but I think access to the rest of the world needs a proper configuration of both the virtual switch, and the selection of a proper IP settings within the network segment you are working with.

Hope it helps. Let us know how it goes.
Regards.

PS.: It is more common to set up services on a server than a desktop, so if you are doing this exercise as preamble for future work, I'd recommend trying it out this goals on a server edition. Just a thought

---

### Post by vbowers on 2017-06-27
Thanks for your reply. I am using the server version of Ubuntu 16.04. After 6 attempts at setting a working static IP address via command line, I loaded the gui and tried using NetworkManager, just to see if that would do the trick. It did not, as described above. Also, I was trying to edit eth0, not create a new interface. I mentioned eth1 only because after clicking Options in NetworkManager, it seemed important to note that a) Options didn't give me eth0 to modify to a static IP and b) that it wanted to create a new interface starting at eth1, which seems to show that it was aware there existed an eth0, but was not allowing me to modify it.

I was editing /etc/network/interfaces using nano when at the command line. I am happy to share copies of that file and anything else that might be of assistance in fixing this issue.  For instance, here is my edit for that file:

iface eth0 inet static
   address 192.168.1.100
   netmask 255.255.255.0
   gateway 192.168.1.1
   network 192.168.1.0
   broadcast 192.168.1.255
   dns-nameservers 192.168.1.1 208.67.222.222 208.67.220.220
   dns-domain BowersHome.net
   dns-search BowersHome.net

---

### Post by chili555 on 2017-06-27
You omitted the 'auto' declaration. That implies exactly the behavior you experienced; eth0 is not started on boot.

Please try:```
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 208.67.222.222 208.67.220.220
dns-domain BowersHome.net
dns-search BowersHome.net
```Reboot.

---

### Post by vbowers on 2017-06-27
You had me so excited! I definitely overlooked that. Edited interfaces file to add the command and rebooted. After reboot, ran ifconfig and it still only reports lo. I ran "ifconfig eth0" and it reports on the interface (MAC address, etc) but without any IPv4 or IPv6 information. So it considers that the interface is there, but not "live".

???   I *really* appreciate your follow up, this is my fourth post in various forums and you are the first to make a follow up post. Thank you, thank you!

---

### Post by chili555 on 2017-06-27
Let's see:```
 lspci -nnk | grep 0200 -A3
```When you find the driver in use, check the log for messages about it:```
dmesg | grep <driver_you_found>
```

---

### Post by vbowers on 2017-06-27
Looking around and found system.d error "Failed to start Raise Network Interface". Unfortunately, it doesn't say much more than that. Not a very informative error message.

After typing in the first line you asked for, I got no response at the command line.

---

### Post by chili555 on 2017-06-27
How about:```
sudo lshw -C network
```

---

### Post by vbowers on 2017-06-27
```
networking.service - Raise network interfaces
Loaded: loaded (/lib/systemd/system/network.service; enabled; vendor preset:
Drop-In: /run/systemd/generator/netowrking.service.d
      50-insserv.conf-$network.conf
Active: failed (Result: exit-code) since Tue 2017-06027 20:46:42 EDT; 23s ago
Docs: man:interfaces(5)
Process: 2147 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/F
```

Here's the lshw result:

```
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: eth0
serial: 00:15:5d:01:66:09
size: 100Mbit/s
capabilities: ethernet physical
configuration: autonegotiation=off broadcat=yes driver=hv_netvsc firmware=N/A link=no multicast
st=yes speed=100Mbit/s
```

---

### Post by chili555 on 2017-06-27
> After the reboot, the virtual machine (running a vm under Windows10 Hyper-V> driver=hv_netvsc> $ modinfo hv_netvsc
filename:       /lib/modules/4.10.0-24-generic/kernel/drivers/net/hyperv/hv_netvsc.ko
description:    Microsoft Hyper-V network driver
I regret that we have exceeded my limited knowledge.

Perhaps this helps: [https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/connect-to-network](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/connect-to-network)

I wish I could be of more help.

---

### Post by vbowers on 2017-06-27
Ran sudo ifup eth0, here's the result:

```
/etc/network/interfaces:2: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

Think I've located the issue, just not sure what is meant or how to fix

Yeah, got my virtual switch going. Think if that (virtual switch) were the issue, DHCP would not have worked. Think this misplaced option message may be the key. Any ideas on that?

---

### Post by papibe on 2017-06-28
Could you get back to DHCP (files not NM), reboot and post the results of these commands?
```
ip addr

ip route 

cat /etc/resolv.conf

```
Regards.

---

### Post by chili555 on 2017-06-28
> Think this misplaced option message may be the key. Any ideas on that?I think it is. That suggests an error on line 2 of the file. Please proofread and correct it. Post it here for our inspection if you are unsure. Be certain that you haven't removed or disturbed the loopback stanzas.

---

### Post by vbowers on 2017-06-29
Sorry for the delay, a household with a 2 week old is not conducive to regular time availability to work on issues.  :)

Once I do the manual edit, I can't get DHCP to work again. Commenting out the static addy lines and reentering the dhcp info does not resurrect the interface. I can go back to a checkpoint I have saved before doing the static setup, if that won't mess up the troubleshooting.

As for chili555's request for the interfaces file, here is the exact content for it:

# This file describes the network interfaces available on your system
and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
dns-nameservers 192.168.1.1 208.67.222.222 208.67.220,220
dns-domain BowersHome.net
dns-search BowersHome.net

#The is an autoconfigured IPv6 interface
iface eth0 inet6 auto

---

### Post by chili555 on 2017-06-29
```
# This file describes the network interfaces available on your system
and how to activate them. For more information, see interfaces(5). [COLOR="#FF0000"]<--May I assume that this is part of one long line and not a new line? It should be commented out, if a new line.
[/COLOR]
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255  [COLOR="#FF0000"]<--Not needed, please remove.[/COLOR]
dns-nameservers 192.168.1.1 208.67.222.222 208.67.220,220
dns-domain BowersHome.net
dns-search BowersHome.net

#The is an autoconfigured IPv6 interface
iface eth0 inet6 auto
```After correcting the file, restart the interface:```
sudo ifdown eth0 && sudo ifup -v eth0
```We'd love to see the exact results. We are confident that there will be a couple of hiccups, but we'd like to see them.

---

### Post by vbowers on 2017-06-29
Chili555: Dude, you are awesome! Do you live on here?  ;)

As a test, I simply commented out (#) that second line, saved and ran the restart command. That did it! Very odd, as I never (knowingly) touched that line. But when you pointed it out, it did seem odd. Based on that error message about line 2, it did seem to be a potential issue, so tested it separately. And BINGO, it came up and is pinging sites successfully. ifconfig reports all is well, so I think that's it.

In retrospect, simple. But because I never knowingly edited that area, just didn't suspect it. It was "standard" code. Well, huh. Test, don't assume!

Thanks again for your help, I can now move on to the "tough" stuff of getting Samba to emulate a DC. 

Thanks also for papibe for chiming in. The more eyes the better!  Linux community comes through!

---

### Post by chili555 on 2017-06-29
> In retrospect, simple. But because I never knowingly edited that area, just didn't suspect it.Stuff happens! I've had more than a few 'what the heck just happened' moments myself.

I'm glad it's working as expected. Please use thread tools to mark Solved. The searchers will appreciate it.

---

