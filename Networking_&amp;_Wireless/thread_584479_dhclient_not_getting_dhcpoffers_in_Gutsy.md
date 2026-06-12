---
title: "dhclient not getting dhcpoffers in Gutsy"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by galmeida2007 on 2007-10-21
I have an Intel PRO/Wireless 3945ABG Network Connection card.
In Feisty and now in Gutsy I cannot get an IP address using dhcp. I have 128 bit WEP encryption.
Using an static IP address works fine, but If I configure it to get by dhcp its network configuration it fails.

After messing around a while I managed to get it working. I had to do the following:

Uninstall dhcdbd, network-manager and network-manager-gnome (I'm using gnome)
Set a 60 seconds timeout in /etc/dhcp3/dhclient.conf (default timeout is 30 seconds)

Now it works when system starts. But if run dhclient to ask for network configuration again I get the following output:

root@galmeidalap:/etc/dhcp3# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:77:62:a2:c7
Sending on   LPF/eth1/00:1b:77:62:a2:c7
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
Trying recorded lease 192.168.0.2
PING 192.168.0.254 (192.168.0.254) 56(84) bytes of data.

--- 192.168.0.254 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 8.332/8.332/8.332/0.000 ms
bound: renewal in 7004 seconds.
root@galmeidalap:/etc/dhcp3# 

Running wireshark to check network traffic in another computer connected to my home network I can see that my router is sending the dhcpoffers requested by my laptop (the problem machine).

Sometimes I get a dhcpoffer between the dhcpdiscover messages and dhclient reports no dhcp offers received and takes the recorded lease as before. See the following output:

root@galmeidalap:/etc/dhcp3# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:77:62:a2:c7
Sending on   LPF/eth1/00:1b:77:62:a2:c7
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:77:62:a2:c7
Sending on   LPF/eth1/00:1b:77:62:a2:c7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.0.254
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
root@galmeidalap:/etc/dhcp3# dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:77:62:a2:c7
Sending on   LPF/eth1/00:1b:77:62:a2:c7
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
Trying recorded lease 192.168.0.2
PING 192.168.0.254 (192.168.0.254) 56(84) bytes of data.

--- 192.168.0.254 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 9.686/9.686/9.686/0.000 ms
bound: renewal in 6141 seconds.
root@galmeidalap:/etc/dhcp3# 

In some very rare cases I get a dhcpack after one or two dhcprequests, as it should be.
It seems that the wireless card misses most of the dpcpoffers or the dhcp client (dhclient) receives them after timing out

My other computer, with a wired network card (Intel 82562EZ 10/100 Ethernet Controller) works flawlessly under Gutsy either in roaming mode (using network-manager) as in manual mode (using gnome network-admin and the settings in /etc/network/interfaces). This computer and my problematic laptop (Dell Latitude D520) are in the same home network using the same router, which is also conected to an access point to allow wireless access to my laptop.

Needless to say, this same laptop connects using dhcp flawlessly under Windows XP Professional in this same network.

Looks like that Feisty is clearly in beta state, and Gutsy in near alpha state, at least regarding wireless networking and graphics cards (see my related post regarding Google Earth crashing along with the gnome session in this same laptop. Under Feisty Google Earth used to run OK if not using compiz or beryl. Under compiz or beryl it had a choppy display, but it didn't crash!. This post is in the Desktop Environments forum ("Google Earth crashes and restarts X session").

---

### Post by mateuszbaranski on 2008-01-06
I had the same problems with wirless network in gutsy - I do not have any networks when clicking right button on knetworkmanager.

I tried to reinstall knetworkmanager, network-manager, wpasupplicant - the same story:
```

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
It is strange that in wifi-radar I can see my wireless network from router.

Any help would be appreciated

Edited: I finally menaged to run my card after several reinstalling mentioned packages.

---

### Post by kenklay on 2008-01-16
Similar problem here with a Toshiba Tetra laptop.  Checked drivers because I have dual boot and windows says my wireless is Intel Pro/wireless 2100A and Ubuntu reports it as Intel PRO/wireless 2200BG.  The iwp2100 driver does not seem to work at all so at least with the ipw2200 driver the router signal is recognized.  Wireless works when booting on Windows XP.

I tried uninstalling the 3 programs listed  in the first post but that did not do me no good.  I did get a permission error when tring to write to the license file if I try to manually enter the router connection.

---

### Post by kenklay on 2008-01-16
I found my problem.  This is a bit embrassing but I was entering the key in wrong.

---

### Post by arnomuhren on 2008-02-13
I'm experiencing the same problems, with the same network card as galmeida2007:
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Listening on LPF/eth1/00:1c:bf:2e:de:83
Sending on   LPF/eth1/00:1c:bf:2e:de:83
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
etc...

I've set a static IP for now, but that ofcourse doesn't solve the DCHP-problem...any news on this issue yet?

---

### Post by aacooper on 2008-02-13
I'm having an identical problem, running madwifi.  My dhcp requests for the ethernet card don't work, either.

I was running Feisty and everything worked, and I upgraded to Gutsy today.  The first boot into Gutsy worked just fine, but when I rebooted again (about the time arnomuhren posted), I apparently can't get any dhcp offer at all.

(My touchscreen drivers were also working on the first boot into Gutsy, and have also failed to work on the second and any subsequent boots.)

---

### Post by arnomuhren on 2008-02-14
I must note that using a static IP doesn't work either, it loses connectivity after a while.
@aacooper: Are you using the same card, having the same problems as well?

---

