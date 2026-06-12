---
title: "Acessing Windows share through VPN"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by ghstzr0 on 2007-01-11
Hi,

I am trying to access a windows share on a windows network (for work).  I personally use Ubuntu (Edgy) and want to connect to a folder that is share on the LAN on my personal Windows box at the office.  My company uses a VPN that is started by going to a website and logging in...  the VPN connection is then initiated via a firefox plugin.  I CAN remote connect to my windows box via rdesktop (RDPv5) and all works well.  Enter the problem:  samba cannot seem to see the VPN'd domain, or connect to my box.  If I open firefox and type smb://myworkdomain/myworkcomputername I get nothing...  if I type smb:/// I get a list of other windows workgroups that are on my local network at home, but the domain for my work is not on the list.  How can I get SAMBA to see my connection through the VPN???

---

### Post by FLPCGuy on 2007-01-11
> **ghstzr0 said:**
> Hi,

I am trying to access a windows share on a windows network (for work).  I personally use Ubuntu (Edgy) and want to connect to a folder that is share on the LAN on my personal Windows box at the office.  My company uses a VPN that is started by going to a website and logging in...  the VPN connection is then initiated via a firefox plugin.  I CAN remote connect to my windows box via rdesktop (RDPv5) and all works well.  Enter the problem:  samba cannot seem to see the VPN'd domain, or connect to my box.  If I open firefox and type smb://myworkdomain/myworkcomputername I get nothing...  if I type smb:/// I get a list of other windows workgroups that are on my local network at home, but the domain for my work is not on the list.  How can I get SAMBA to see my connection through the VPN???

It is tough enough connecting the same OS through a VPN connection but mixing protocols and clients can make troubleshooting extremely difficult.  There are also Windows issues aside from the possibility that you aren't running the same protocols.  To quote Microsoft:
 "VPN 		  clients can gain access to NetBIOS resources across a Point-to-Point Tunneling 		  Protocol (PPTP) VPN tunnel or a Layer 2 Tunneling Protocol (L2TP) VPN 		  tunnel" [PPTP is the Windows default not L2TP].    

There may also be packet substitution issues with a VPN.  
"When a Windows-based VPN server has only one network 		  adapter, VPN clients may not be able to access resources on the VPN server in 		  certain situations. Typically, VPN clients may experience this issue if the VPN 		  connection is made to the actual IP address of the VPN server. ...when the VPN client tries to access resources on the internal network that is 		  behind the firewall, the VPN client will try to access the private IP address 		  of the VPN server instead of the IP address that the VPN client used to make 		  the VPN connection."

I suspect one of these two common issues may be your problem, but that's just a guess. You would have to inspect the packets at various stages to see where the mismatch is occurring.

---

