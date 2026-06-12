---
title: "Wireless is recognized as ethernet?"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by dermanus on 2007-04-18
I was having various problems with my wireless, mainly that I had to use the terminal to connect to anything, and I have to do it every time I booted up. Nothing major, but it is kinda annoying. I also cannot view any available wireless networks without using the terminal. I read a little more about Ubuntu, and realized that part of the problem might be that my wireless card is eth1, not wlan0 which it maybe should be.

My question is three-fold: Can I change it? Will it fix the problems? And is it worth the hassle?

---

### Post by dbott67 on 2007-04-18
The logical name for each adapter is bound to the MAC address in this file:
```
dbott@edgy:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:c5:0c:ad:05 arp 1
[COLOR=Red]**wlan0**[/COLOR] mac 00:16:ce:31:88:6f arp 1

```

Your file may contain eth0 and eth1, instead of eth0 and wlan0.  Just change the logical name accordingly:
```
sudo gedit /etc/iftab
```

-Dave

---

### Post by dermanus on 2007-04-18
It sorta worked. It definitely saw the new wlan0, but I couldn't get it to see the card, despite it knowing the MAC address for the device.

Assuming I do get it to see the card that way, would the constant terminal based connections go away?

---

### Post by marvlowe on 2007-04-19
I have the same problem, my wireless connection is identified as eth1, not wlan0.  I'm guessing that this is why there is no way to hookup to any wireless network besides the one it was originally set up for.  If I do the edit suggested does this allow for detection of any available wireless networks the way Windows XP does?

Marv Lowe

---

### Post by dbott67 on 2007-04-19
@marvlowe: There is a package in the repos called "[NetworkManager]("http://www.gnome.org/projects/NetworkManager/")"
```
sudo apt-get install network-manager-gnome
```
That can be used to detect & connect to wrieless networks (WEP, WPA, etc.)

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

-Dave

---

### Post by marvlowe on 2007-05-09
I checked the iftab file listed as follows:

eth0 mac 00:03:25:0c:22:d1 arp 1
wlan0 mac 00:0c:41:bd:2a:1e arp 1ul

Yet my only successful wireless connection is eth1 not wlan0. I also installed the Network manager. I assumed it would start up automatically after I rebooted. It didn't and I can find the program in the Applications,  so I'm still unable to connect wireless except for the first wireless system I got up and running on.  How do I start the network manager? Any ideas why the first wireless setup was listed as eth1 instead of wlan0?

Marv

---

### Post by dbott67 on 2007-05-10
Hi Marv,

Can you post the output of the following commands:
```
scpl@dns2:~$ [COLOR=Blue]**cat /etc/network/interfaces**[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

``````
scpl@dns2:~$[COLOR=Blue]** ifconfig -a**[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:E0:29:7C:65:3F
          inet addr:192.168.128.59  Bcast:192.168.128.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe7c:653f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:732483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:352562729 (336.2 MiB)  TX bytes:6776681 (6.4 MiB)
          Interrupt:9 Base address:0x4c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1740 (1.6 KiB)  TX bytes:1740 (1.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

``````
scpl@dns2:~$ [COLOR=Blue]**iwlist scanning**[/COLOR]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

``````
scpl@dns2:~$ [COLOR=Blue]**sudo lshw -C network**[/COLOR]
  *-network
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:e0:29:7c:65:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.128.59 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:feafbc00-feafbcff irq:9

``````
scpl@dns2:~$ [COLOR=Blue]**cat /etc/iftab**[/COLOR]
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:e0:29:7c:65:3f arp 1

```*Note: if you can't get online with your system & you have a USB thumb drive (or floppy or some other removable media you can write to) you can use the 'redirect' function to write the output of the commands to a file and then copy them to the USB. Start in your home directory (**cd ~**):*

```
cat /etc/network/interfaces > interfaces.txt
``````
ifconfig -a > ifconfig.txt
``````
iwlist scanning > iwlist.txt
``````
sudo lshw -C network > lshw.txt
``````
cat /etc/iftab > iftab.txt
```Copy all 5 files to floppy/USB, bring them over to Windows and then post them here. All five files should be in your home directory.

-Dave

---

### Post by marvlowe on 2007-05-10
I tried the first command. Didn't get very far, here was the output:

marv@marv-laptop:~$ scpl@dns2:~$ cat/etc/network/interfaces
bash: scpl@dns2:~$: command not found

---

### Post by DarkN00b on 2007-05-10
Thank you! I have been trying to fix this since I got my Broadcom4318 based card working. wlan has always showed up as eth. I editted /etc/iftab to reflect the above. I also had to change /etc/network/interfaces from this:

```
iface eth0 inet dhcp
wireless-essid ******

auto eth0
```

so that it now reads ```
iface wlan0 inet dhcp
wireless-essid ******

auto wlan0
```

I don't use network-manager, I use the Network monitor panel 
applet along with manual configuration. Everything works perfectly now! [img]http://e.deviantart.com/emoticons/h/headbang.gif[/img]

---

### Post by dbott67 on 2007-05-10
@Marv:

The command is just:
```
cat /etc/network/interfaces
```[I][COLOR=Blue](without the **scpl@dns2:~$** --- that's my username@hostname).[/COLOR]

[/I]I've edited the above post to highlight the commands.  Sorry for the confusion.

-Dave

---

### Post by marvlowe on 2007-05-10
That was stupid of me. Here goes again.

marv@marv-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid wiflyer
wireless-ap 00:13:06:02:12:FE

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Wiflyer
wireless-key s:

marv@marv-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:25:0C:22:D1  
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe0c:22d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6539456 (6.2 MiB)  TX bytes:1056753 (1.0 MiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:09:5B:0E:E6:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

marv@marv-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

marv@marv-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Card
       product: ISL37300P
       vendor: NETGEAR MA401RA Wireless PC
       physical id: 0
       version: Eval-RevA
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@00:0e.0
       logical name: eth0
       version: 01
       serial: 00:03:25:0c:22:d1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.1.147 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d0004000-d0005fff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:09:5b:0e:e6:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.3.6 link=no multicast=yes wireless=IEEE 802.11b

marv@marv-laptop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:03:25:0c:22:d1 arp 1
wlan0 mac 00:0c:41:bd:2a:1e arp 1

Thanks for the help.
Marv

---

### Post by dbott67 on 2007-05-10
> **marvlowe said:**
> That was stupid of me. Here goes again.
No worries! 

I'm just going to wrap your output in 'code' tags to make it easier to read and then highlight some stuff:

```
marv@marv-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto [COLOR=Blue]eth1[/COLOR] [COLOR=Red]*<--- just change [COLOR=Blue]eth1[/COLOR] to [COLOR=Blue]wlan0[/COLOR]*[/COLOR]
iface[COLOR=Blue] eth1[/COLOR] inet dhcp[COLOR=Red]* <--- just change [COLOR=Blue]eth1[/COLOR] to [COLOR=Blue]wlan0[/COLOR]*[/COLOR]
wireless-essid wiflyer
wireless-ap 00:13:06:02:12:FE
*[COLOR=DarkSlateBlue]wireless-key s:your-ascii-wep-key-goes-here  [COLOR=Red]<--- you may need to add this line[/COLOR][/COLOR]*

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

[COLOR=Blue]*# Just comment out this entire section (add a '#' in front of each line)*[/COLOR]
[I][COLOR=SlateGray][COLOR=Blue]# [/COLOR]auto wlan0
[COLOR=Blue] #[/COLOR] iface wlan0 inet dhcp
[COLOR=Blue] #[/COLOR] wireless-essid Wiflyer
[COLOR=Blue] #[/COLOR] wireless-key s:[/COLOR][/I]

``````

marv@marv-laptop:~$ ifconfig -a
[COLOR=Green] eth0[/COLOR]      Link encap:Ethernet  HWaddr [COLOR=Green]00:03:25:0C:22:D1  [/COLOR][COLOR=Green]*<--- wired ethernet MAC address* [/COLOR] 
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe0c:22d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6539456 (6.2 MiB)  TX bytes:1056753 (1.0 MiB)
          Interrupt:11 

[COLOR=Blue] eth1[/COLOR]      Link encap:Ethernet  HWaddr [COLOR=Blue]00:09:5B:0E:E6:35[/COLOR]  [COLOR=Red]*<-- this is the MAC address of your wireless NIC*[/COLOR]
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
``````

marv@marv-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

``````

marv@marv-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Card *[COLOR=Red]<--- I have no idea what this is, but it's probably related to the other MAC address in the iftab file.[/COLOR]*
       product: ISL37300P
       vendor: NETGEAR MA401RA Wireless PC
       physical id: 0
       version: Eval-RevA
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@00:0e.0
       [COLOR=Blue]logical name: [COLOR=Red]eth0[/COLOR][/COLOR]
       version: 01
       serial: [COLOR=Green]00:03:25:0c:22:d1 *<--- wired ethernet MAC address*[/COLOR]
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.1.147 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d0004000-d0005fff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       [COLOR=Blue]logical name:[COLOR=Red] eth1[/COLOR][/COLOR]
       serial: [COLOR=Blue]00:09:5b:0e:e6:35[/COLOR] [COLOR=Red]*<-- wireless NIC MAC address again*[/COLOR]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.3.6 link=no multicast=yes wireless=IEEE 802.11b
``````

marv@marv-laptop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac [COLOR=Green]00:03:25:0c:22:d1[/COLOR] arp 1 [COLOR=Green]*<--- wired ethernet MAC address*[/COLOR]
wlan0 mac[COLOR=Blue] 00:0c:41:bd:2a:1e[/COLOR] arp 1 [COLOR=Red]*<-- Not your wireless NIC MAC address*[/COLOR]

```It should read:
```
eth0 mac [COLOR=Green]00:03:25:0c:22:d1[/COLOR] arp 1 [COLOR=Green]*<--- wired ethernet MAC address*[/COLOR]
wlan0 mac[COLOR=Blue] 00:09:5b:0e:e6:35[/COLOR] arp 1 [COLOR=Red]*<-- I've changed this to be your wireless NIC MAC address*[/COLOR]

```So, just edit your **iftab** and **interfaces** files to read like above & you should be okay. 

After that, you'll need to reboot.  Try running the commands form the previous post again & see if eth1 has been changed to wlan0 & if wlan0 reports any output when you type **iwlist scanning**.

-Dave

---

### Post by dbott67 on 2007-05-10
I edited the above post a few times, so take the time to re-read it carefully.

-Dave

---

### Post by marvlowe on 2007-05-10
I've made the changes to the 2 files. Here's what they look like now.

The interfaces file

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid wiflyer
wireless-ap 00:13:06:02:12:FE


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcpb

# auto wlan0
# iface wlan0 inet dhcp
# wireless-essid Wiflyer
# wireless-key s:

The Iftab file:

marv@marv-laptop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:03:25:0c:22:d1 arp 1
wlan0 mac 00:09:5b:0e:e6:35 a mrp 1

I didn't add the wireless-key S: line since I didn't know what my ascii wep key was. At any rate after re-booting I'm still not any wireless network indication. How do I start the network manager so it will search for the available wireless networks?

Marv

---

### Post by dbott67 on 2007-05-10
NetworkManager should start automatically.  If you don't see an icon with 'escalating bars' like the one below, we can always install/re-install NM.

[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]
Try installing network-manager-gnome:
```
sudo apt-get install network-manager-gnome
```

After installation, restart you computer. A "Network Manager" icon should appear along the top that you can click on to configure & select networks, etc.

Before that, though, we should see if your wireless card detects any wireless networks.  What's the output of:
```
dbott@dapper:~$ [COLOR=Red]iwlist scanning[/COLOR]

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              [COLOR=Red]Encryption key:on[/COLOR]
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              [COLOR=Red]Encryption key:on[/COLOR]
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

You'll notice that my laptop detects 2 networks using wlan0, and both APs use encryption.  You'll need to know the type of encryption (WEP64/128, WPA1/2, etc.) and the key in order to connect.

-Dave

---

### Post by marvlowe on 2007-05-10
I tried the scan and the output said Failed to read scan data : No data available.

I should point out that my wireless card Link light is blinking, not steady on as it should be and is when running in Windows.  It also stayed on when I got wireless working on my other wireless network some 900 miles from where I am now.  I have a wireless Linksys router here and I'm only a few feet away from it so I know there is a very strong signal.  When I go to Networking it shows my wireless connection enabled with the with the Network name Wiflyer, the name of my wireless network it does work on. 

Also I tried installing network manager a second time and the system said it was already installed.

Marv

---

### Post by dbott67 on 2007-05-10
Before we move onto the next step, is the device now recognized as wlan0?

---

### Post by marvlowe on 2007-05-10
I believe the answer is yes. I wento to Networking and click on the properties for the wireless connection. The heading stated "Settings for interface Wlan0". It went through a configuration step and I thought maybe after that it would work but when I rebooted, no luck.  I get two connection icons in the upper right hand corner. One simply says no connection the other says connected eth0. When I click on it the only other option that comes up is lo, no Wlan0.  

Note also even though Network manager is installed I don't get that icon on the task bar.

Marv

---

### Post by dbott67 on 2007-05-10
> **marvlowe said:**
> Note also even though Network manager is installed I don't get that icon on the task bar.

Marv

I think the icon is missing if there's no wireless interface enabled.

There are a few things to keep in mind:

1. Under normal circumstances, only 1 interface should be active at one time.  This means that your wireless probably won't work while the network cable is plugged in (which is possibly why the icon is not showing).

Try unplugging the LAN cable and then enter the following commands:
```
sudo ifdown eth0
``````
sudo ifup wlan0
``````
sudo dhclient wlan0
```Then finally, try scanning for wireless again:
```
iwlist scanning
```2. Wireless encryption can be a bit of a problem while troubleshooting.  **I recommend disabling WEP or WPA on the router while you're trying to get connected.**  Once you get a connection, re-enable WEP and then try to connect again.

-Dave

---

### Post by marvlowe on 2007-05-11
Looks like I'm going backwards here. I was able to shut off eth0 but not able to turn on wlan0. Here's the text.

marv@marv-laptop:~$ sudo ifdown eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 4618
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:03:25:0c:22:d1
Sending on  LPF/eth0/00:03:25:0c:22:d1
Sending on  Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_pactet: please consult README file regarding broadcast address.
marv@marv-laptop:~$ ifup wlan0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied

The ethernet cable was not connected when I issued the ifdown command. I reconnected the cable and tried re enabling the eth0 connect and got the same response (failed to ope statefile/var/run/network/ifstate: Permission denied). So now I can't connect using  Ubuntu at all.

Marv

---

### Post by dbott67 on 2007-05-11
To get the wired working again, you need to prefix each command with 'sudo' (that's why you're getting 'permission denied').

**To bring an interface up:**
```
sudo ifup [COLOR=Blue]*<interface_name>*[/COLOR]
```Replace [COLOR=Blue]*<interface_name>*[/COLOR] with eth0, eth1, wlan0, etc.

For example:
```
sudo ifup eth0
```**To bring an interface down:**
```
sudo ifdown [COLOR=Blue]*<interface_name>*[/COLOR]
```**To obtain an IP from a DHCP server:**
```
sudo dhclient [COLOR=Blue]*<interface_name>*[/COLOR]
```-Dave

---

### Post by NilsE on 2007-05-11
Semi off topic and I don't want to confuse the issue so I won't.  

One side note however, is if the nm-applet icon does not show up on panel you can right click on the panel and "add to panel" the "notification area" which is in the utilities near the bottom.

---

### Post by marvlowe on 2007-05-11
Thanks. Here's the output. How do I 'wake it up?'

Marv

marv@marv-laptop:~$ sudo ifup wlan0
Password:
ifup: interface wlan0 already configured
marv@marv-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:09:5b:0e:e6:35
Sending on   LPF/wlan0/00:09:5b:0e:e6:35
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
marv@marv-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

sit0      Interface doesn't support scanning.

---

### Post by Praill on 2007-05-11
When I got this working this is what I did:

```

sudo apt-get install wpa-supplicant network-manager-gnome

```

then:
```

gksudo gedit /etc/network/interfaces

```

**Comment out everything but the "lo" (loopback) entry.**
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1 
#iface eth1 inet dhcp 
#wireless-essid wiflyer
#wireless-ap 00:13:06:02:12:FE
#wireless-key s:your-ascii-wep-key-goes-here  <--- you may need to add this line

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

# Just comment out this entire section (add a '#' in front of each line)
# auto wlan0
 # iface wlan0 inet dhcp
 # wireless-essid Wiflyer
 # wireless-key s:

```

Im assuming the reason for this that by default the system is using network-manager for all the devices. When you comment out this config it allows network-manager-gnome to control these devices.

You must be using edgy? This step was not required for me in Feisty.

---

### Post by marvlowe on 2007-05-11
I was not able to install. This is message:

marv@marv-laptop:~$ sudo apt-get install wpa-supplicant network-manager-gnome
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wpa-supplicant

---

### Post by marvlowe on 2007-05-11
Since the system said I already had Network manager gnome installed, I just went ahead and commented everything out of of the interfaces file except the lo as indicated. Lo and behold my wireless card link is on solid, and when I scanned I got the following:

marv@marv-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:2B:78:E4
                    ESSID:"Belkin_Pre-N_460744"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Signal level:16/153  Noise level:15/153
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 02 - Address: 00:06:25:88:9E:05
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:50/153  Noise level:15/153
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

sit0      Interface doesn't support scanning.

It looks like I'm just about ready to go but I still can't find the network manager icon. I tried the add but couldn't find it in the list of programs that could be added. Anything else I should do?

Marv

---

### Post by dbott67 on 2007-05-11
> **Praill said:**
> When I got this working this is what I did...

[COLOR=Red]**Comment out everything but the "lo" (loopback) entry.**[/COLOR]
...  You must be using edgy? This step was not required for me in Feisty.

This is interesting.  I recall reading posts about people having to comment out the entries in /etc/network/interfaces.  Strangely enough, I did not have to do it on my laptop which is running Edgy & NetworkManager.

@Marv: which version of Ubuntu are you running (Dapper, Edgy, Feisty)?

As for the icon, is there an network icon on the toolbar that you can click on?  Single-click it (left button) and a menu should drop down.

When I get home I'll check to see the actual applet name, but I think it's just called **nm-applet**.  Try opening a terminal and type in:
```
nm-applet
```

-Dave

---

### Post by NilsE on 2007-05-11
If the nm-applet does not run after every boot then you may need to add it to the: 

System/Preferences/Sessions  Startup Programs section.  

Just select new and name it whatever you want.  Mine is "NetworkManager Applet" and the command is nm-applet

---

### Post by marvlowe on 2007-05-11
I down loaded this version of Ubuntu from their web site in January when I go to the about Ubuntu information it says:
Thank you for your interest in Ubuntu 6.10
                - the Edgy Eft - released in October 2006. ar

So I guess I'm running Edgy. What are all the code names, different release levels?  I see the latest appears to by 7.04.

Marv

PS I'm running wireless just fine now.

---

### Post by dbott67 on 2007-05-12
> **marvlowe said:**
> What are all the code names, different release levels?  I see the latest appears to by 7.04.

Marv

PS I'm running wireless just fine now.

Glad to hear it's working.

Ubuntu's mandate is to release a new version every 6 months (timed along-side the latest Gnome release).  The version numbers are based on the year/month, so Edgy 6.10 was released in October 2006.  Feisty Fawn 7.04 was released in April 2007.

4.10 - Warty Warthog
5.04 - Hoary Hedgehog
5.10 - Breezy Badger
6.06 - Dapper Drake (release date pushed back 2 months; also is known as LTS - Long term support for 3 yrs.)
6.10 - Edgy Eft
7.04 - Feisty Fawn
7.10 - Gutsy Gibbon

-Dave

---

### Post by Praill on 2007-05-16
glad to hear its working.. the reason you received that error is because i had a minor typo. Its wpasupplicant not wpa-supplicant.

PS. I wouldnt recommend feisty yet.. its still in beta

PSS. on the subject of versions and codenames.. what exactly is the methodology behind the seemingly aribitrary version numbers? why is dapper 6.06 and feisty 7.04?

---

### Post by Praill on 2007-05-16
nm.. i think i just got it... the first number is an incremental year since development started and the second number is the month it was released in

---

### Post by DarkN00b on 2007-05-17
Its year (200**7**), followed by month (**04**).

---

