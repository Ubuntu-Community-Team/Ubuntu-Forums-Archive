---
title: "Networking has stopped working"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by princeofgonville on 2008-01-14
Hello,

I have had Gutsy installed for several months and it worked fine. But over the last week it's suddenly been unable to connect to the network. I have tried DHCP and static addresses and neither work. We have a small office network with macs, Windows machines and this Linux box plugged into an 8-port switch, which is then connected to the Broadband Router. The router does the DHCP and DNS stuff. All the other machines can network properly (which is how I can talk to you). So it' all Cat5 wired (not Wifi).

On the Linux Box, Firefox can't access google.com or our internal server (by name or by IPaddress). At the terminal, it can't ping the router (192.168.1.254) or anything else local or remote. (Host unreachable)

If I run dhclient eth0, it tells me (sorry about typos):
  There is already a pid file   (etc)
  killed old client proces (etc)
  (...)
  Listening on LPF/eth0/00:01:02:15:b2:e9
  Sending on LPF/eth0/00:01:02:15:b2:e9
  Sending on socket / fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
  (intervals 7, 14,12,10,15 )
  no DHCPOFFERS received
  no working leases in persistent databaser - sleeping

The router seems to have seen something. If I try to use DHCP, it sees
    Unknown-00-01-02-15-b2-e9 (inactive) 169.254.x.y

If I use Static IP addresses it sees:
    Unknown-00-01-02-15-b2-e9 (inactive) 192.168.1.75
    (which is the correct IP address; subnet is 255.255.255.0, gateway is 192.168.1.254 as on all the other machines ).

So the Router obviously knows it's there, but it can't establish communications.

OK, so what's changed? I installed SMBclient and we plugged a printer into the network that connects using Windows-to-windows sharing. I tried disconnecting the printer to see if that helps - sadly not. And I can't imagine that SMB client would cause the network to fail at that level. Does anyone have any ideas? Cos I'm stumped! Please help.

---

### Post by MariusSilverwolf on 2008-01-14
Let's look at this logically for a second . . . . 

Before installing SMB Client, the system in question could connect.
After installing SMB Client, the system in question could not connect.

Ergo, something in the SMB Client configuration is preventing communication, OR the installation of SMB Client changed your network configuration.

Or, the cable connecting to that system has been sheared or shorted somewhere along the path and it can't establish communications.

What happens if you replace the cable?  Or uninstall SMB Client?  I didn't have to install any additional software to allow my Gutsy machine to find the printer attached to my Windows machine across the network; the SMB protocol was already in place.

---

### Post by princeofgonville on 2008-01-14
OK, logically:

1) network cable - swapping to a different network cable (that is known to work) doesn't help. Trying this cable in another machine shows that the cable in the Linux box is OK.

2) uninstalling SMB doesn't help

If it helps, the router is a SpeedTouch ADSL router.  If anyone has any ideas please let me know.
Thanks

---

### Post by Mark F on 2008-01-14
I'm having a similar problem. Fresh Xubuntu install on laptop where network was previously working. Other computers working OK. What gives?

---

