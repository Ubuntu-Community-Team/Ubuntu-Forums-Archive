---
title: "[SOLVED] Wired Internet Connection Issues....."
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by bcerge on 2008-11-28
Hey guys, 

After being perfectly contempt with Ubuntu 7.04 for the last 7 or 8 months, I finally installed 8.10.  I really dreaded doing it because I remember that it took me about 3 weeks to tweak everything to my liking (2.99 weeks for my wireless card).  

Here is my problem:
In order to get my most beloved BCM4318 AirForce One 54G card to work , I was going to use a wired connection to do all of the updates....I plug ethernet cable in and I can not connect to the internet. from my lswh -C network output, it appears that my eth0 port is enabled, and in my network manager the auto eth0 is greyed out so I can not select it.  When I plug ethernet cable in, the green lights start to circle, but then it gives me a "disconnected" message.  eth0 is my ethernet port.  Anyway, I could really use some help here. I might add too that the cable is coming strait from my modem to my computer, does not enter through a router. Thanks in advance.


       -bc


Dell Inspiron 1300 Notebook  (I know its old :P  )
-------------------------------------------
lshw -C network 

 *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:90:24:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:e8:b1:02
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 32:e5:2e:fc:68:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



-------------------------------------------------

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:14:22:90:24:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)


----------------------------------------------------------------

lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)







###################### Solved! #################################################


I have this down at my last post, but wanted to put it up here, these are the steps that I took to get my wired connection to work, and my wireless connection to work coming from a fresh install of Ubuntu 8.10

First, I learned from all this that when trying to get your wired connection to work, it DOES matter weather you are coming strait out of the modem OR if you are coming from your modem into router into your computer. Best way to get this to work is if you have another computer with Windows installed on it that has a wired connection. I used the connection coming out of the router to my computer.

1. Run the command prompt from Windows Machine and type ipconfig /all

2. Jot down the IP Address, Default Gateway, Subnet Mask, and DNS Servers.

3. Un-plug Ethernet from computer and into the machine where Ubuntu is installed.

4. Go to the network manager, go to the Wired Tab, select Auto eth0, and edit. Make sure that the Automatically Connect box is checked, and click the the IPv4 tab, on the drop down box where it says Method: Choose Manual.

5. Enter in the IP Address, Default Gateway, Subnet Mask, and the DNS servers that you jotted down. Select OK

6. I was able to connect to the Internet at this Point. I ran the update manager and installed all of the updates and Rebooted.

7. I went to System > Administration > Hardware Devices and now my BCM43XX hardware was present from the updates. I enabled it and rebooted.

8. I am now able to connect wireless to the Internet now at this point, but for some reason now my sound is pure static....lol ( I was so close to having this thing up and running!)

---

### Post by superprash2003 on 2008-11-29
have you tried system->admin->hardware drivers

---

### Post by bcerge on 2008-11-29
> **superprash2003 said:**
> have you tried system->admin->hardware drivers

Thank you for the reply.  Yes I have checked this, naturally there is nothing there and is as expected.  From what I understand though, you are supposed to be able to wire up to the net out of the box?

---

### Post by zika on 2008-11-29
> **bcerge said:**
> Thank you for the reply.  Yes I have checked this, naturally there is nothing there and is as expected.  From what I understand though, you are supposed to be able to wire up to the net out of the box?

No, that was the case with 8.04. 8.10 is a bit like Windows in that department. Open VPN connections after clicking on Network in Your panel. Click on eth0 and edit its settings. Enter Your IP address, netmask, gateway and DNS and choose Manul for DNS. It might not work from the first time but be patient. Once Your numebrs are remebered (netmask migt go to 24 instead of 255.255.255.0 but that is OK) You are on the rignt way. Be sure to check System settings and Connect automagically. If You do not get connected right away, restart machine, hopefully, You will be OK.

I tried to be as consise as possible...

---

### Post by bcerge on 2008-11-29
> **zika said:**
> No, that was the case with 8.04. 8.10 is a bit like Windows in that department. Open VPN connections after clicking on Network in Your panel. Click on eth0 and edit its settings. Enter Your IP address, netmask, gateway and DNS and choose Manul for DNS. It might not work from the first time but be patient. Once Your numebrs are remebered (netmask migt go to 24 instead of 255.255.255.0 but that is OK) You are on the rignt way. Be sure to check System settings and Connect automagically. If You do not get connected right away, restart machine, hopefully, You will be OK.

I tried to be as consise as possible...

Thanks man, I'll give this a shot when I get home from work, I believe I have made an attempt to do this, but i'll try it again and try to be a bit more patient.

---

### Post by zika on 2008-11-29
> **bcerge said:**
> Thanks man, I'll give this a shot when I get home from work, I believe I have made an attempt to do this, but i'll try it again and try to be a bit more patient.

kewords are 'patient' and 'restart'... :)

I've done it several times on different machines and every time, eventhough I thought I knew what I am doing, it took the same amount of time and the same number of trials and errors ... not (only) mine but Ibex's.

The thing about restart I found accidentally once I thought that I'm stupid enough and will never get that machine connected ... :)

Is there anybody that have Automatic DNS working ... ? That is the thing that I miss the most about Hardy. Networking worked really 'out of the box' ...

---

### Post by superprash2003 on 2008-12-01
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) .. 
@zika
Automatic DNS?? you mean DNS server ips given by router?

---

### Post by zika on 2008-12-02
> **superprash2003 said:**
> try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) .. 
@zika
Automatic DNS?? you mean DNS server ips given by router?

Sorry, I meant DHCP ...

---

### Post by superprash2003 on 2008-12-03
try this , manually edit the /etc/network/interfaces file and insert dhcp instead of static.. then restart networking and then try..

---

### Post by zika on 2008-12-03
> **superprash2003 said:**
> try this , manually edit the /etc/network/interfaces file and insert dhcp instead of static.. then restart networking and then try..

my /etc/network/interfaces:
> auto lo
iface lo inet loopbackwhen I click on Network Manager Applet and choose "VPN Connections" under ipv.4 I choose Manual between: 

1. Automatic (DHCP)
2. Automatic (DHCP) addresses only
3. Manual
4. Link-local only
5. Shared to other computers

and enter all the relevant IP's (IP address of my comp., subnet mask, gateway, DNS server) and after several re-enter-s and reboot everything works.

In Hardy it worked automagically ...

Which of those 5 (instead of Manual) do You suggest me to try (eventhough it's working now on all computers in my home so ...)?

---

### Post by zika on 2008-12-04
with this /etc/network/interfaces all the troubles with Network Manager are gone because he is gone out of the equation volontarily (not removed but insulted)  ...

> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
Doing it the way Linux meant to. Enjoy.

---

### Post by superprash2003 on 2008-12-04
well there was a bug initially with the network manager, im not sure if its fixed yet.. it could be the same issue.. so the solution is doing it manually in the interfaces file

---

### Post by bcerge on 2008-12-08
> **zika said:**
> No, that was the case with 8.04. 8.10 is a bit like Windows in that department. Open VPN connections after clicking on Network in Your panel. Click on eth0 and edit its settings. Enter Your IP address, netmask, gateway and DNS and choose Manul for DNS. It might not work from the first time but be patient. Once Your numebrs are remebered (netmask migt go to 24 instead of 255.255.255.0 but that is OK) You are on the rignt way. Be sure to check System settings and Connect automagically. If You do not get connected right away, restart machine, hopefully, You will be OK.

I tried to be as consise as possible...


Hey Guys, I never reported back, but I just wanted to say that the above information ended up working for me, and as a result I got my wireless card to work as well, so I am very grateful.  These are the steps that I took:

First, I learned from all this that when trying to get your wired connection to work, it DOES matter weather you are coming strait out of the modem OR if you are coming from your modem into router into your computer.  Best way to get this to work is if you have another computer with Windows installed on it that has a wired connection.  I used the connection coming out of the router to my computer.

1.  Run the command prompt from Windows Machine and type ipconfig /all

2.  Jot down the IP Address, Default Gateway, Subnet Mask, and DNS Servers.

3.  Un-plug Ethernet from computer and into the machine where Ubuntu is installed.

4.  Go to the network manager, go to the Wired Tab, select Auto eth0, and edit.  Make sure that the Automatically Connect box is checked, and click the the IPv4 tab, on the drop down box where it says Method: Choose Manual.

5.  Enter in the IP Address, Default Gateway, Subnet Mask, and the DNS servers that you jotted down.  Select OK

6.  I was able to connect to the Internet at this Point.  I ran the update manager and installed all of the updates and Rebooted.

7.  I went to System > Administration > Hardware Devices and now my BCM43XX hardware was present from the updates.  I enabled it and rebooted.

8.  I am now able to connect wireless to the Internet now at this point, but for some reason now my sound is pure static....lol ( I was so close to having this thing up and running!)


I know this probably isnt the right place to ask for it, but has anyone run into the problem where your sound just sounds like scratchy static??  I am going to copy these steps up at the first post and marked thread as solved.  Thanks guys!

---

