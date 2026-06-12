---
title: "xp not able to connect to the samba server"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by weiqiang on 2007-06-12
I have set up 1 ubuntu server, two xp michines running xp. They go up to internet through the linksys router, one of the xp's is able to connect the samba sever through wireless, while the other one is not able to. Every time I typed the ip address in the windows explorer address bar and press enter, it always warned me that "windows cannot find \\xxx.xxx.x.xxx\share....." it's weird coz the other xp machine is connecting very smoothly.
Here is output of ipconfig /all from xp
Windows IP Configuration

        Host Name . . . . . . . . . . . . : XXXXXX
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : vc.shawcable.net

Ethernet adapter Local Area Connection 7:

        Connection-specific DNS Suffix  . : vc.shawcable.net
        Description . . . . . . . . . . . : 3Com Gigabit LOM (3C940)
        Physical Address. . . . . . . . . : XX-XX-XX-XX-XX-XX
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.XXX
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 64.59.XXX.XX
                                            64.59.XXX.XX
        NetBIOS over Tcpip. . . . . . . . : Disabled
        Lease Obtained. . . . . . . . . . : 2007 6 11 12:03:56 PM
        Lease Expires . . . . . . . . . . : 2007 6 12  12:03:56 PM

Anybody has any idea why it's not working? 
it's more like a xp problem :)

---

### Post by Gausian on 2007-06-12
the way i got it to work was to have a static ip on the samba comp and set WINS to "Yes" in the config.

then add the WINS server in your XP tcp/ip settings.

---

### Post by weiqiang on 2007-06-12
Thanks
but why one of xp's is working, the other one is not?

---

