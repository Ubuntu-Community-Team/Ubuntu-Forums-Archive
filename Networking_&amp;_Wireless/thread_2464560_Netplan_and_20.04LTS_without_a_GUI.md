---
title: "Netplan and 20.04LTS without a GUI"
date: 2021-07-05
forum: Networking &amp; Wireless
---

### Post by 0rcward on 2021-07-05
hi There,

I have a few questions around the latest release of 20.04 and the server builds without a GUI interface. I have like all my other Servers attempted to build a 20.04 Server without a GUI as I prefer to work with the CLI rather than the GUI however this is proving to be very difficult to manage both the Network Connections as well as the VPN tunnels should we need to or want to manage them. Currently I have a virtual Server with 4 Virtual NICs and a VPN connection to manage a L2tp Tunnel however I have had it (in my horror) had to build the GUI interface and connect via RDP to manage, start, stop and create Tunnels. 

Before going into more detail I need to make it clear that I am using the Network and VPN Solutions that are provided by Ubuntu rather than building OpenVPN or similar. 

Almost All the resources I have found on the net refer to using the GUI to accomplish this however I would prefer to build, maintain and manage my network connections and VPN tunnels via the CLI but cannot find an documentation or examples to show how this should be done with the new Ubuntu release (Specifically around Netplan). My Question is how do I create a persistent VPN tunnel and bring up 4 NICs with Statically assigned Addresses without relying on the GUI to get this done. In the event that I have used the GUI , where do I find the config files that are setting the NIC's and VPN Setting and how do I (using the CLI) make the necessary static IP Changes and convert the VPN connection to Persistent. Given it's a server I would prefer to allocate my resources to the roles allocated and not the GUI I would prefer to be able manage these connections via the CLI. Any Advice, examples or Documentation on this would be greatly appreciated.

Kind Regards,
Lloyd

---

### Post by TheFu on 2021-07-05
You don't need a GUI.   Please realize that 99% of what makes an Ubuntu Server is not created nor written by Canonical, so avoiding openvpn or wireguard VPNs is just penalizing yourself, not being "pure".

/etc/netplan/ is where netplan config files are located.  There are manpages about them and a website, netplan.io, with lots of other documentation and examples.

As for automatically bringing up a VPN, that would happen using a systemd "unit" file that you create with a dependency on the network being active.  On my servers, I just use a script, to bring up the VPN as desired, since I don't want it running all the time.  I have another script to bring it down.

$ more ~/bin/vpn-stop
```
echo "Turning off link tun0"
/usr/bin/sudo /sbin/ip link set tun0 down
echo "Killall openvpn"
/usr/bin/sudo /usr/bin/killall openvpn
```
My vpn-start script is more complex because it allows picking an exit node location The last line is:
```
/usr/bin/sudo /usr/sbin/openvpn "$OVPN_DIR/$SEARCH" &
```

There are lots and lots of example "unit" files on your system already and the systemd guys do create a bunch of documentation to wade through.  Unfortunately, I find their docs non-pithy because they provide many options, some are subtle.  Look in /etc/systemd/system/ for local examples.

I would strongly encourage looking at wireguard as the VPN if setting one up today.

There's lots of documentation on help.ubuntu.com too. Just stay in the "Server" documentation for your release.  20.04 Server docs are here: [https://ubuntu.com/server/docs](https://ubuntu.com/server/docs)

---

### Post by chili555 on 2021-07-05
You may get some additional guidance here:```
 /usr/share/doc/netplan/examples

```

---

