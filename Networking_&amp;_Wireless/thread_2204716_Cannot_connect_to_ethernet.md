---
title: "Cannot connect to ethernet"
date: 2014-02-10
forum: Networking &amp; Wireless
---

### Post by kevinbrizz on 2014-02-10
I have scoured through the Ubuntu forum for the past 2 nights now, and I am completely stumped.

Here's me problem:

I have a laptop and an HTPC; both run ubuntu

I just moved apartments.
In my last apartment, my HTPC (Zotac Zbox) and laptop never had problems connecting to the internet.
I had my HTPC plugged in via ethernet cable, and used wifi for my laptop 

Now I moved into my new apartment, and for some reason the laptop runs fine, but the HTPC will not connect to the ethernet

Any help is greatly appreciated

here is what happens when I run a ifconfig command:
```

eth0      Link encap:Ethernet  HWaddr 00:01:2e:47:ee:16  
          inet6 addr: fe80::201:2eff:fe47:ee16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1584905 (1.5 MB)  TX bytes:203015 (203.0 KB)
          Interrupt:42 Base address:0xc000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21067 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1421028 (1.4 MB)  TX bytes:1421028 (1.4 MB)

```


I think my problem is that i do not have an "inet addr." under eth0

---

### Post by varunendra on 2014-02-10
Welcome to the forums Kevin!

Does this HTPC get its IP from a DHCP server? Does the Ethernet seem to be active in Ubuntu?

Please post back the outputs of the following commands from the HTPC -
```
sudo lshw -numeric -C network
nm-tool
cat /etc/NetwormManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/network/interfaces
```

---

### Post by kevinbrizz on 2014-02-10
Thanks for the help, I REALLY appreciate it

```
kevinbrizz@kevinbrizz-ZBOXSD-ID12-ID13:~$ sudo lshw -numeric -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller [10EC:8168]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 00:01:2e:47:ee:16
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:42 ioport:e800(size=256) memory:fdffb000-fdffbfff memory:fdffc000-fdffffff
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc. [168C:37]
       vendor: Atheros Communications Inc. [168C]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feb80000-febfffff memory:feb70000-feb7ffff



```



```
kevinbrizz@kevinbrizz-ZBOXSD-ID12-ID13:~$ nm-tool


NetworkManager Tool


State: connecting


- Device: eth0  [Normal] -------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        00:01:2E:47:EE:16


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on



```


```
kevinbrizz@kevinbrizz-ZBOXSD-ID12-ID13:~$ cat /etc/NetworkManager/NetworkManager.conf


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=00:01:2E:47:EE:16,


[ifupdown]
managed=true

```



```
kevinbrizz@kevinbrizz-ZBOXSD-ID12-ID13:~$ cat /var/lib/NetworkManager/NetworkManager.state


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```




```
kevinbrizz@kevinbrizz-ZBOXSD-ID12-ID13:~$ cat /etc/network/interfaces


auto lo
iface lo inet loopback

```

---

### Post by kevinbrizz on 2014-02-10
I really don't know what you are asking with your first two questions.  Imagine you're walking you're inept cousin through this

---

### Post by varunendra on 2014-02-10
> **kevinbrizz said:**
> I really don't know what you are asking with your first two questions.  Imagine you're walking you're inept cousin through this

No problem. :)

Does this HTPC and your laptop connect to the same router (or modem) which has both Ethernet and Wireless interfaces? If yes, please post the output of -
```
nm-tool
```
..from the laptop when it is connected to internet.

From the output of the same command in the HTPC, it is clear that your wired connection is set to get its IP address from DHCP.

Just so you know (not necessary right now for our troubleshooting) -

- DHCP is a software program (a "Network Settings server") that usually (but not necessarily) runs in the Modem or Router that you connect to for Internet access.

- If this feature is not enabled in the router, the devices (like your HTPC) would try but never get an IP address (or other related settings), thus not being able to connect to the network.

- Normal Solutions are : 1) Enable DHCP server with relevant settings in the router, Or, 2) Manually assign required settings in the devices instead of relying on DHCP

There can also be a (problematic) situation where DHCP is enabled, but the device can't get its settings from it. In that case, we have more than one possible fix, but for now, you are not interested in those. :)

**PS:**
Instead of using 'Quote' tags that you are currently using, please use 'Code' tags for posting command outputs. Please follow the "Using Code Tags" link in my signature below to see how, and edit your above post to change the 'Quote' tags into 'Code' tags.

---

### Post by kevinbrizz on 2014-02-10
```
kevinbrizz@ChrUbuntu:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        20:89:84:5E:24:14


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         67.186.99.90
    Prefix:          23 (255.255.254.0)
    Gateway:         67.186.98.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        F4:B7:E2:A8:44:A5


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 

```

---

### Post by varunendra on 2014-02-11
Is your network is a typical one, where the internet comes via a cable that is plugged into a router/modem, then the modem connects to the local devices via cable and wifi ?
Is this modem/router under YOUR control?

From your IP address and netmask, it seems that the access-point is being controlled directly by your ISP (Internet Service Provider)?

Making a few assumptions, whose validity rely on the answers to above questions, please try the following -

Open network configuration (Alt-F2 > nm-connection-editor) and,
go to "**Wired" tab > double-click your connection name > goto [s]"IPv6 Settings"[/s] "IPv4 Settings" tab > set "Method" to "Manual" > click "Add" button** > enter the following details in their respective fields (press 'Enter' after finishing each field, or it won't be accepted) -
```
Address : 67.186.99.190
Prefix : 23
Gateway : 67.186.98.1

DNS servers : 75.75.75.75, 75.75.76.76 *(note that there is only one comma followed by a space, rest are dots)*
```
Save and close the settings. Does it let you connect?

If not, can you provide a little more detail on how the Internet connection comes into your apartment and distributed to the devices there? The connection type, cable, devices involved?

---

### Post by kevinbrizz on 2014-02-11
My internet comes via a cable that is plugged into a modem, then the modem connects to the local drivers via ethernet chord. (at the moment, I do not have a router)

I don't know what you are asking when you asked if the modem is under my control

Also, I could not enter the IPv6 address you gave me. My network configuration window will not allow me to enter "." (periods) between the numbers.  The only punctuation it will allow me to use are ":" (colons)

---

### Post by varunendra on 2014-02-12
> **kevinbrizz said:**
> I don't know what you are asking when you asked if the modem is under my control
I meant - do you have access to its admin control webgui? So that we can change some of its settings like LAN side IP address, DHCP range etc - if required.

And for the kind of networking you mentioned, the modem (usually an ADSL one) also has inbuilt router function. But that is not necessary afaik.

> Also, I could not enter the IPv6 address you gave me. My network configuration window will not allow me to enter "." (periods) between the numbers.  The only punctuation it will allow me to use are ":" (colons)

Sorry, that was a terrible mistake (typo). What I suggested was an IPv4 address, not an IPv6 type. Accordingly, please try the same in IPv4 tab, and let us know if it worked.

---

### Post by kevinbrizz on 2014-02-12
My modem is not under my control


As for when entering the code in the IPv4 settings:
My HTPC is telling me that a connection is established, however, I am still unable to load any webpages, refresh my software updater, nor can I 'ping' out to a website

---

### Post by varunendra on 2014-02-12
If it is not under your control, then it must be under the control of your Internet Service Provider. Call them and simply tell them that your computer is not getting its IP address from the modem via cable. Post back what they have to say.

If this modem connects via cable, what does your laptop's WiFi connect to?
Is it a different device or the same modem (with both Ethernet and WiFi interfaces)?
Can you determine and post back its full model no.? So that I can look up the web to see actually what kind of device it is, maybe its user manual too..

---

### Post by kevinbrizz on 2014-02-12
Just got off the phone with Comcast (my ISP) and they do not think the problem is on their end.  Since I am able to connect to the internet using my laptop (and a friend's laptop, as well); they think the problem lies with my HTPC's network settings and/or driver.

Right now, I am not using wifi.  I'm just using an ethernet chord that's hooked up to the modem; only using one device at a time by switching out the ethernet chord.

The modem is a NETGEAR High Speed Cable Modem (docsis 3.0) 
model number:CMD31T

---

### Post by varunendra on 2014-02-12
I've no idea about such modems/services and have no idea how to proceed.

The driver you have is known to have a few problems sometimes, but I'm really not sure if it is worth fiddling with it without something concrete to work on.

If you wish to try a few shots in the dark, please try resetting the "IPv4 Settings" to "Automatic (DHCP)", and then in a terminal -
```
sudo mii-tool -F 100baseTx-FD eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient
```
The first command will change the connection speed to 100 Mb/s - Full Duplex, which is a lot slower than the current 1 Gb/s - Full Duplex, but sometimes it may help connecting smoothly. Also, the change will be lost at next boot, so if it helps the interface getting a valid network configuration from the modem, we may have to take additional steps to make it permanent.

I really wish and hope someone with more experience with such devices/services drops in and share their knowledge with us.

---

### Post by kevinbrizz on 2014-02-12
Lowering the connection speed didn't do the trick.

Thanks for helping though, Varun

---

### Post by Iowan on 2014-02-12
> **kevinbrizz said:**
> As for when entering the code in the IPv4 settings:
My HTPC is telling me that a connection is established, however, I am still unable to load any webpages, refresh my software updater, nor can I 'ping' out to a website

Pinging by name, or IP address?
Can you ping the gateway?

---

### Post by varunendra on 2014-02-12
Thanks for dropping in Iowan :)

I hope you have seen such devices/services before, or otherwise know more than I do - which is 'zero' :P

---

### Post by Iowan on 2014-02-12
You're much ahead of me... Once we get past basic networking - ESPECIALLY if/when we drift into drivers - I'm lost.
I'm curious if there is actually a connection established, and/or how far the connection goes.

---

### Post by kevinbrizz on 2014-02-12
I only know how to ping by name.  All I did was try to Ping google.com

---

### Post by Iowan on 2014-02-12
If you're still set up like post #7, try to ping the gateway(router?):
```
 ping -c3 67.186.98.1
```
Next, I'd try to ping a nameserver:
```
 ping -c3 75.75.75.75
```
Another nameserver (Google's) is 8.8.8.8.

---

### Post by kevinbrizz on 2014-02-13
After reconfiguring to post #7's settings, here is what my HTPC sent me when I entered the codes:

```
kevinbrizz@kevinbrizz-ZBOXSD-ID12-ID13:~$ ping -c3 67.186.98.1
PING 67.186.98.1 (67.186.98.1) 56(84) bytes of data.
From 67.186.99.190 icmp_seq=2 Destination Host Unreachable


--- 67.186.98.1 ping statistics ---
3 packets transmitted, 0 received, +1 errors, 100% packet loss, time 2007ms

```


```
kevinbrizz@kevinbrizz-ZBOXSD-ID12-ID13:~$ ping -c3 75.75.75.75
PING 75.75.75.75 (75.75.75.75) 56(84) bytes of data.


--- 75.75.75.75 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms

```

---

### Post by varunendra on 2014-02-13
Obviously you are not connected logically.

Do you have or can get a cross-cable? We can use it to connect the laptop and the HTPC directly to each other (via the cable) and ping each other (after a temporary manual IP assignment) to see if the Ethernet interface of the HTPC is functioning properly or not.

The Ethernet port of the laptop is already proven to be functional since it can connect to internet. So if the above mutual connection failed, we'd know for sure whether the problem is with the port/driver or with the network configuration.

So far we haven't been able to determine if the HTPC's ethernet port is working properly at all.

---

### Post by Iowan on 2014-02-13
Also, check **route -n** to verify the traffic is trying to use the proper interface. **ifconfig -a** should verify your IP settings.

---

### Post by kevinbrizz on 2014-02-13
Iowan:




```
kevinbrizz@kevinbrizz-ZBOXSD-ID12-ID13:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         67.186.98.1     0.0.0.0         UG    0      0        0 eth0
67.186.98.0     0.0.0.0         255.255.254.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

```





```
kevinbrizz@kevinbrizz-ZBOXSD-ID12-ID13:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:2e:47:ee:16  
          inet addr:67.186.99.190  Bcast:67.186.99.255  Mask:255.255.254.0
          inet6 addr: fe80::201:2eff:fe47:ee16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3277991 (3.2 MB)  TX bytes:608674 (608.6 KB)
          Interrupt:42 Base address:0xc000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10713631 (10.7 MB)  TX bytes:10713631 (10.7 MB)

```




Varun: I'll have to run to RadioShack and pick up a cross-cable after work

---

