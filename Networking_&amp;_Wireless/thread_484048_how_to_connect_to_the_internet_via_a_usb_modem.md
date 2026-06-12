---
title: "how to connect to the internet via a usb modem"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by shlumpi on 2007-06-25
i have adsl and i want to connect to netvision (an israely ISP)
they use PPTP/L2TP
i have a Dynamode HomeAccess M-ADSL-USB-C50
i installed debian before and it recognized my modem
i need a dialer to connect to the ISP
anyone knows one?
please don't tell me to switch to a network modem (i don't know the name exactly but i think it's called ethernet {10/100) modem)
i don't have enough money and i had alot of problems with the modems they sell in israel
they're not that good
the debian i installed (and later uninstalled to install ubuntu) is 40r0
it's for a pentium 4 computer
the ubuntu i installed is the latest stable i386 one
thanks

---

### Post by kevdog on 2007-06-25
Did you consult this page first and use the scanModem tool?

[https://help.ubuntu.com/community/DialupModemHowto?highlight=%28modem%29](https://help.ubuntu.com/community/DialupModemHowto?highlight=%28modem%29)

---

### Post by shlumpi on 2007-06-28
yes
i also tryed usbadslmodemmanager ([http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/))
[http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page](http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page)
anyway
now the situation is a little different
i'm now trying to connect to the internet using a script that the ISP made for linux users (that is the biggest support they'll give linux users and it's useless to call support)

[http://cables2.netvision.net.il/linux/l2tp-dialer.tar.gz](http://cables2.netvision.net.il/linux/l2tp-dialer.tar.gz)
i checked to make sure that ubuntu recognizes my modem so i wrote in the terminal
lsusb
and it came up with
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0572:cb00 Conexant Systems (Rockwell), Inc. E-Tech ADSL Modem v2
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

i installed the script with success
they say to write ./start <interface>
 so i in the terminal CDd to the folder with that file
did ./start 0572:cb00
it first denied permission so i sudo'd it and it wrote
l2tpd: no process killed
You have problems with the connection. Try stopping and starting 0572:cb00 interface.

the "You have problems with the connection. Try stopping and starting 0572:cb00 interface." part is just some useless "it doesn't work message since where it says 0572:cb00 if i wrote ./start meow the error message would write meow so it doesn't tell me anything

as you can see the script uses l2tpd ([http://sourceforge.net/projects/l2tpd](http://sourceforge.net/projects/l2tpd)) - the latest version
[http://sourceforge.net/projects/l2tpd](http://sourceforge.net/projects/l2tpd)

when i did
sudo ./stop 0572:cb00
it wrote
l2tpd: no process killed
grep: /var/lib/dhcp/dhclient-0572:cb00.leases: No such file or directory
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported
	   
i saw it's looking in the dhcp folder but when i ran sudo dhclient it only looked for ethernet devices:
Listening on LPF/eth0/00:0c:f1:c8:48:4c
Sending on   LPF/eth0/00:0c:f1:c8:48:4c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Is there any way to make it search in the usb?
thanks

---

