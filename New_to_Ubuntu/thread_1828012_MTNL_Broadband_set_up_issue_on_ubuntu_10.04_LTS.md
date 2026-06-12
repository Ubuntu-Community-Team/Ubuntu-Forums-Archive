---
title: "MTNL Broadband set up issue on ubuntu 10.04 LTS"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by usarbjit on 2011-08-18
Hi,

I am new to Ubuntu. I am trying to access Internet on Ubuntu 10.04 LTS but no success. After reading few threads in this community. Have executed the following to detect the modem/internet settings.


```
XXXXXXX@ubuntu:~$ sudo dhclient eth0
[sudo] password for XXXXXXXXXXXX: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
XXXXXXXXXXX:~$ 
```


Please note that I am able to use MTNL broadband on Windows XP.

Regards,
usarbjit

---

### Post by im.saravanan on 2011-08-18
hi friend. Dont struggle with commands. Go to network manager and in wired connections tab . Add a new connection. And give the same setting as you gave in windows. If required restart uid machine. Thats all. Enjoy. Try ubuntu 11.04 its superb.

---

### Post by usarbjit on 2011-08-18
Hi Friend,

Thanks for your suggestion. But I don't use username and password to get connected on Internet. It is just plug and play in Windows XP.

I have tried to network settings. But I am not sure what should be filled in IP address, gateway,netmast etc fields in ubuntu.

so please advise

---

### Post by gandaran on 2011-08-19
> **usarbjit said:**
> Hi Friend,

Thanks for your suggestion. But I don't use username and password to get connected on Internet. It is just plug and play in Windows XP.

I have tried to network settings. But I am not sure what should be filled in IP address, gateway,netmast etc fields in ubuntu.

so please advise
does the computer connect to a router?
if this is one of those broadbands that don't use a router you can check the settings in the windows XP connection setup, it shouldn't be difficult to find them and just fill the same on ubuntu, you probably just need an IP or dchp IP, leave all other field settings blank.

---

### Post by usarbjit on 2011-08-19
Computer is connected to DSL Modem

Please guide me how to find the connections in windows xp. I didn't entered anywhere IP address and DHCP IP to get internet connection.

---

### Post by usarbjit on 2011-08-19
After reading more on this community, I have executed the below commands so that i will get quick help


```
XXXXXX@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24608 (24.6 KB)  TX bytes:24608 (24.6 KB)

XXXXX@ubuntu:~$ iwconfig
lo        no wireless extensions.

XXXXXdhuragawas@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use 

Iface
XXXXXX@ubuntu:~$ ping -c 208.67.219.101
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or 

address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
XXXXXX@ubuntu:~$ ping -c 3 208.67.219.101
connect: Network is unreachable
XXXXXX@ubuntu:~$ ping -c 3 www.opendns.com
ping: unknown host www.opendns.com
XXXXX@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller 

(rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset 

Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High 

Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 

1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 

2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI 

Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI 

Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI 

Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI 

Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI 

Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC 

Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE 

Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE 

Controller (rev 01)
01:00.0 Ethernet controller: Atheros Communications Device 1083 (rev 

c0)
XXXXXXX@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
XXXXXXX@ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=128)
XXXXXX@ubuntu:~$ 

```

---

### Post by im.saravanan on 2011-08-19
Hi

It seems 10.04 has no drivers for your network card.

In the terminal run the command

$ifconfig

If eth0 is not seen in the output- most probably your network  card driver is not loaded. 

one more method is. In the terminal run the command

$ nm-tool
 and see whether device eth0 is reported. if the network card is detected. then follow the next.Else try installing driver for your network card. OR download and install UBUNTU 11.04 it has drivers for all the latest devices. 


Do this step by step if network card is detected.

system>preference>network connections>Wired>Add>Give connection name as MTNL or anything  you like>check the box connect automatically>IPv4 Settings>Method->Automatic (DHCP). Save and exit.

Restart machine if required. 

or 


Check with MTNL and get dns server address. IP can be 192.168.1.2 subnet 255.255.255.0 and gateway is probably 192.168.1.1 the address of the router.

Try and report.

---

### Post by usarbjit on 2011-08-19
I have execute the below command

nw-tool

Its says network manager status: disconnected.

Are you sure that ubuntu 11.04 will work on Atheros AR8151 motherboard?

---

### Post by im.saravanan on 2011-08-19
i can only say my system has atheros network adapter . it works in 11.04.

remember if u run a command and report. Do not report what u understand. just copy and paste the output of the command . So that the forum members can help u in a better way.

---

### Post by usarbjit on 2011-08-20
Thanks. I am installed Ubuntu 11.04 but after installation, I see desktop with suspend and system settings options only. 

However, it is defecting motherboard Atheros now.

Is anything went wrong during installation? I have download Ubuntu ISO image using Ubuntu official site. Installed with help of Wubi.

Please help.

---

### Post by grahammechanical on 2011-08-20
Ha. Now you give us some information.

> Installed with help of Wubi.

Information like this is important. So, is knowing if you want to connect by ethernet (wired) or wireless. You do not specifically say what method you have.

I do not know much about Wubi but I suggest that you remember that it might seem that you are booting into Ubuntu as a separate operating system but it is in fact working through the Windows operating system. It is working as if it is a special Windows program/application. So, make sure that the Internet/networking connection is working in Windows. Do not switch off the connection in windows before you shut windows down and then boot into Ubuntu.

Is you machine a laptop?

Regards.

---

### Post by usarbjit on 2011-08-20
Thanks to you both Gramhammechanical and saravanan.

I had installed Ubuntu 10.04 LTS version using CD with help of Wubi on Windows XP but my network card ( Atheros AR8151 ) was not detected. So not able to connect to Internet using ADSL connection.

As suggested by Saravanan, I have uninstalled Ubuntu 10.04 LTS version and installed Ubuntu 11.04 version. At first, I was not letting Ubuntu installation complete as my understanding was it will be installed in maximum 20 minutes, so interrupted the installation process. Later on, I waited for 3 hours for Ubuntu 11.04 installation process complete ( with all language packages).

Gramhammechanical -  I am using PC with Ethernet connection.

---

