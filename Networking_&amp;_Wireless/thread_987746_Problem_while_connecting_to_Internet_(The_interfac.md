---
title: "Problem while connecting to Internet (The interface does not exist, ERROR)"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by anshulbhatt28 on 2008-11-19
Hi,
I am new to linux i have installed Ubuntu8.04 to external maxtor hard drive, the other os's which i am using are win 2k and xp installed to internal hard drives, i am not able to configure internet settings in ubuntu 8.04, i am using broadband inet connection through ethernet cable which is directly connected to my computer which has inbuilt network interface card(Ethernet Controller Intel corp/PRO/100 VE Network Connection PCI bus4, device 8), i am able to see the connection connected in networks ubuntu shows it as windows network i configured it as wired connection and via using static ip, subnet mask, gateway and also provided DNS as provided to me by the ISP and also after looking at windows tcpip properties. and then i checked up in terminal by typing sudo gedit /etc/network/interfaces it is showing me the iface eth0 with all the settings i entered. when i type sudo ifdown eth0 it gives me error:SIOCADDRT: No such process failed to bring up eth0, when i open network tools and click on configure button after selecting eth0 it gives me error: THe interface does not exist, check that it is correctly typed in terminal when i type gksu network-admin the window opens up, but the unlock button remains greyed out, when i try to ping -c5 127.0.0.1 or the server or any other website it says connect:Network is unreachable.

PLease help me resolving this bcoz here no one knows how to resolve this all from my isp people to other technical people all are window OS fans, I am stuck for 4 days tried different solutions nothing works out :confused::confused:

---

### Post by n5kb on 2008-11-19
Hello,

Please tell me what you have tried so far.

Do you know what your ip is? If no: goto term and sudo ifconfig

Also try ifup and ifdown and put the eth nimber in the command.

Example: my ethernet card is eth0 so I would type "ifup eth0" or "ifdown eth0"

I hope this helps

---

### Post by divinequran on 2008-11-19
Check whether eth0 is up or fails when the system boots [eth0 FAILED]. if it fails then try to install the required modules.

---

### Post by anshulbhatt28 on 2008-11-19
[B]Hi,

the main issue is whenever i click on configure button in network tools after selecting eth0 it gives error as follows

The interface does not exist, Check that it is correctly typed

i am pasting the output of various comds i typed in terminal[/B]

ab@ab-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:d1:6f:93:5f  
          inet addr:xxx.xx.xxx.xxx  Bcast:xxx.xx.xxx.xxx  Mask:255.255.255.0 
          inet6 addr: fe80::219:d1ff:fe6f:935f/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:213 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:23017 (22.4 KB)  TX bytes:6935 (6.7 KB) 

ab@ab-desktop:~$ ifdown eth0 
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied 
ab@ab-desktop:~$ ifup eth0 
ifup: failed to open statefile /var/run/network/ifstate: Permission denied 
ab@ab-desktop:~$ sudo ifdown eth0 
[sudo] password for ab: 
ifdown: interface eth0 not configured 
ab@ab-desktop:~$ sudo network-admin 

(network-admin:6104): Gtk-WARNING **: Unknown property: GtkComboBox.items 


** (network-admin:6104): CRITICAL **: Unable to lookup session information for process '6104' 
ab@ab-desktop:~$ gksu network-admin 
ab@ab-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01) 
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01) 
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01) 
ab@ab-desktop:~$ 


Please help me :confused::confused::confused:

---

### Post by superprash2003 on 2008-11-20
are you able to ping your router?which ISP are you connected to?

---

### Post by anshulbhatt28 on 2008-11-20
i am not able ping the server or the router whenever i try to ping the server it says 
connect: Network is unreachable.

My ISP is 24online(elite technologies) its a direct connection via ethernet cable to my home pc

---

### Post by superprash2003 on 2008-11-21
does it require any ISP username and password to connect?

---

