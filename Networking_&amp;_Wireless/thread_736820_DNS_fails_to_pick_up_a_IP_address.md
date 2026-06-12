---
title: "DNS fails to pick up a IP address"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by Living2007 on 2008-03-27
whenever I connect to the Internet, my DNS is supposed to pick up a IP address so I can browse the internet, but the DNS failsto pick up under a dial-up connection with my ISP at DCSI.

Why is this failing? :confused:

---

### Post by Eiríkr on 2008-03-27
I'm afraid your post is quite confusing.  Do you mean that, after dialling in to your ISP, you cannot browse the internet?  Or, do you mean that you cannot remotely access your own machine over the internet?  Or, are you running your own DNS server and your server fails to properly cache name resolution requests?  Some more detail would be helpful.

Cheers,

Eiríkr

---

### Post by jakev383 on 2008-03-27
I think you used DNS instead of DHCP.
When you connect, what does ```
ifconfig
``` show?
How do you know dhcp is failing?

---

### Post by Living2007 on 2008-03-27
It's definatly DNS. Mr. Gardner, our schools Linux Maniac, idenified to me that the DSN as failed. You need an IP to explorer the internet, and everytime you connect onto the internet through Dial-Up, it goes to the DNS server, takes an IP Address nujmber and uses it. My Windows Workes fine but Ubuntu fails.

---

### Post by Eiríkr on 2008-03-27
Please open a terminal, type in each of the following, and paste the results into a post here in this thread.

```
ifconfig
cat /etc/resolv.conf
cat /etc/dhcp3/dhclient.conf
```

Thank you,

Eiríkr

---

### Post by Living2007 on 2008-03-30
Here is the result. Remember, I'm trying to get my dial-up working

```
living2007@LivingLinux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:F6:2C:7E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20512 (20.0 KB)  TX bytes:20512 (20.0 KB)

living2007@LivingLinux:~$ ifconfig cat /etc/resolv.conf
Usage:
  ifconfig [-a] [-v] [-s] <interface> [[<AF>] <address>]
  [add <address>[/<prefixlen>]]
  [del <address>[/<prefixlen>]]
  [[-]broadcast [<address>]]  [[-]pointopoint [<address>]]
  [netmask <address>]  [dstaddr <address>]  [tunnel <address>]
  [outfill <NN>] [keepalive <NN>]
  [hw <HW> <address>]  [metric <NN>]  [mtu <NN>]
  [[-]trailers]  [[-]arp]  [[-]allmulti]
  [multicast]  [[-]promisc]
  [mem_start <NN>]  [io_addr <NN>]  [irq <NN>]  [media <type>]
  [txqueuelen <NN>]
  [[-]dynamic]
  [up|down] ...

  <HW>=Hardware Type.
  List of possible hardware types:
    loop (Local Loopback) slip (Serial Line IP) cslip (VJ Serial Line IP) 
    slip6 (6-bit Serial Line IP) cslip6 (VJ 6-bit Serial Line IP) adaptive (Adaptive Serial Line IP) 
    strip (Metricom Starmode IP) ash (Ash) ether (Ethernet) 
    tr (16/4 Mbps Token Ring) tr (16/4 Mbps Token Ring (New)) ax25 (AMPR AX.25) 
    netrom (AMPR NET/ROM) rose (AMPR ROSE) tunnel (IPIP Tunnel) 
    ppp (Point-to-Point Protocol) hdlc ((Cisco)-HDLC) lapb (LAPB) 
    arcnet (ARCnet) dlci (Frame Relay DLCI) frad (Frame Relay Access Device) 
    sit (IPv6-in-IPv4) fddi (Fiber Distributed Data Interface) hippi (HIPPI) 
    irda (IrLAP) ec (Econet) x25 (generic X.25) 
    eui64 (Generic EUI-64) 
  <AF>=Address family. Default: inet
  List of possible address families:
    unix (UNIX Domain) inet (DARPA Internet) inet6 (IPv6) 
    ax25 (AMPR AX.25) netrom (AMPR NET/ROM) rose (AMPR ROSE) 
    ipx (Novell IPX) ddp (Appletalk DDP) ec (Econet) 
    ash (Ash) x25 (CCITT X.25) 

living2007@LivingLinux:~$ ifconfig cat /etc/dhcp3/dhclient.conf
Usage:
  ifconfig [-a] [-v] [-s] <interface> [[<AF>] <address>]
  [add <address>[/<prefixlen>]]
  [del <address>[/<prefixlen>]]
  [[-]broadcast [<address>]]  [[-]pointopoint [<address>]]
  [netmask <address>]  [dstaddr <address>]  [tunnel <address>]
  [outfill <NN>] [keepalive <NN>]
  [hw <HW> <address>]  [metric <NN>]  [mtu <NN>]
  [[-]trailers]  [[-]arp]  [[-]allmulti]
  [multicast]  [[-]promisc]
  [mem_start <NN>]  [io_addr <NN>]  [irq <NN>]  [media <type>]
  [txqueuelen <NN>]
  [[-]dynamic]
  [up|down] ...

  <HW>=Hardware Type.
  List of possible hardware types:
    loop (Local Loopback) slip (Serial Line IP) cslip (VJ Serial Line IP) 
    slip6 (6-bit Serial Line IP) cslip6 (VJ 6-bit Serial Line IP) adaptive (Adaptive Serial Line IP) 
    strip (Metricom Starmode IP) ash (Ash) ether (Ethernet) 
    tr (16/4 Mbps Token Ring) tr (16/4 Mbps Token Ring (New)) ax25 (AMPR AX.25) 
    netrom (AMPR NET/ROM) rose (AMPR ROSE) tunnel (IPIP Tunnel) 
    ppp (Point-to-Point Protocol) hdlc ((Cisco)-HDLC) lapb (LAPB) 
    arcnet (ARCnet) dlci (Frame Relay DLCI) frad (Frame Relay Access Device) 
    sit (IPv6-in-IPv4) fddi (Fiber Distributed Data Interface) hippi (HIPPI) 
    irda (IrLAP) ec (Econet) x25 (generic X.25) 
    eui64 (Generic EUI-64) 
  <AF>=Address family. Default: inet
  List of possible address families:
    unix (UNIX Domain) inet (DARPA Internet) inet6 (IPv6) 
    ax25 (AMPR AX.25) netrom (AMPR NET/ROM) rose (AMPR ROSE) 
    ipx (Novell IPX) ddp (Appletalk DDP) ec (Econet) 
    ash (Ash) x25 (CCITT X.25) 
```

---

### Post by koenn on 2008-03-30
you have several problems
1- your ipconfig shows you have no IP address for your eth0 (that's a NIC), so no matter what Mr Gardner says, you're going to need to get an IP address, presumably from DHCP - not DNS. 

2- your ifconfig only shows an eth0 device. With dial-up, you'd expect a ppp device. Are you sure your dial-ip is set up properly ? It looks as if it's not set up (or running) at all

3- you did not execute 'cat /etc/resolv.conf', you executed "ifconfig cat /etc/resolv.conf', which is a nonsens statement, so you did not get any useful output there. 
Same for 'cat /etc/dhcp3/dhclient.conf"

---

### Post by Living2007 on 2008-03-30
What Is DCHP? Also, does ubuntu install dial-up moden drivers during the setup or do I have to download the driver myself.

It is a NetComm 56K (I'll find the Poduct Code Number Later today)

PS: Where was no result for "cat /etc/resolv.conf" & "cat /etc/dhcp3/dhclient.conf"

---

### Post by koenn on 2008-03-30
1/
Dynamic Host Configuration Protocol (DHCP) is a network protocol that enables a DHCP server to automatically assign an IP address to an individual computer
[http://kb.iu.edu/data/adov.html](http://kb.iu.edu/data/adov.html)
This means : your ISP can use dhcp to make sure your computer has a valid IP address.

2/
real modems don't need drivers. You just connect them to a serial port (external modem), or they create their own serial port (internal modems); linux talks directly to the serial port, and all you have to do is configure your connection according to your ISP's parameters (eg username, password, ... )
You can use wvdial
[http://ubuntuforums.org/showthread.php?t=35284](http://ubuntuforums.org/showthread.php?t=35284)
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)


however, there are also so-called winmodems, which are not real modems because they rely on the computer's processor and some help from the operating system to act as a modem. They are designed to be used with WIndows, so in this case you'll have to do some work to get them to work with Linux. They might also not work at all. 
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent) => setting up a winmodem with Lucent chipset (I found at least 1 model of Netcomm 56k int. modem retail (lucent) (IN5920_1 V9.2 PCI Modem) (IN5920_1 V9.2 PCI Modem), but *you* check)


3/
> there was no result for "cat /etc/resolv.conf" & "cat /etc/dhcp3/dhclient.conf"
Are you sure you're using Linux ?

---

### Post by Living2007 on 2008-04-02
Where is the Ubuntu driver for a NetComm 56K V.92 Internal Modem (IN5920_1) under [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

---

### Post by mozetti on 2008-04-02
> **Living2007 said:**
> PS: Where was no result for "cat /etc/resolv.conf" & "cat /etc/dhcp3/dhclient.conf"

Because you didn't type the command correctly. This is what you typed:```
ifconfig cat /etc/resolv.conf
``` and ```
ifconfig cat /etc/dhcp3/dhclient.conf
```

You should have typed this:```
cat /etc/resolv.conf
``` and ```
cat /etc/dhcp3/dhclient.conf
```

---

### Post by Living2007 on 2008-04-03
Does anyone know where to find the driver for a NetComm IN5920_1 V9.2 PCI Modem for Ubuntu 7.10

---

### Post by koenn on 2008-04-03
read this sticky : [http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098)
and use scanmodem to find what driver you need

---

### Post by Living2007 on 2008-04-09
What pages have the Winmoden driver for Ubuntu 7.10 for the following modem:

NetComm 56K V.92 Internal Modem (IN5920_1)

---

