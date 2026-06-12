---
title: "Atheros QCA9565 / AR9565 , Dell Inspiron 3521"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by bte_rajan on 2013-11-18
I have dell Inspiron 3521 laptop, which comes with preinstalled Ubuntu 12.04. But wireless does not detect networks

 please help

here is some command which i have tried to know about my system

lshw -C network  *-network    
           
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 74:86:7a:23:72:8a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=10.154.4.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network UNCLAIMED
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0500000-c057ffff memory:afb00000-afb0ffff

---

### Post by chili555 on 2013-11-18
> product: QCA9565 / AR9565 Wireless Network Adapter
Please see here: [http://askubuntu.com/questions/355742/no-wireless-in-dell-inspiron-1521-with-12-04/355816#355816](http://askubuntu.com/questions/355742/no-wireless-in-dell-inspiron-1521-with-12-04/355816#355816)> Your wireless device is covered in the driver ath9k but only in kernels 3.8 and later. Please see here: [http://askubuntu.com/questions/215498/upcoming-support-for-qualcomm-atheros-ar9565-wireless](http://askubuntu.com/questions/215498/upcoming-support-for-qualcomm-atheros-ar9565-wireless)

You could update your 12.04 to 12.04.3 LTS which uses the 3.8.0-xx kernel or reinstall Ubuntu 13.04. You could certainly also compile the compat-wireless linked here. Cool! A link within a link!

Post back if you get stuck.

---

### Post by bte_rajan on 2013-11-18
Thanks for the reply, 
I check version of  ubuntu in my system. here is the terminal output                                                         
cat /etc/lsb-release DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"

                                                             uname -r
3.2.0-56-generic

 please help (I am beginner ) what should i do next     &#8211;

---

### Post by chili555 on 2013-11-18
Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install linux-backports-modules-cw-3.8-precise-generic
```Reboot and let us hear your report.

---

### Post by bte_rajan on 2013-11-18
Thanks a lot. its working.............. I spent almost a month searching for the solution from DELL support centre and various other sources :P.  Thank you very much again !!!

---

### Post by chili555 on 2013-11-18
A month? Dr. Chili is glad you came to the right place! Glad it's working. Please mark the thread Solved so that the searchers will find it: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by bte_rajan on 2013-11-19
Thanks again, I now have another issue, wireless detects networks and I am able to connect to one of the network. but still I am unable to browse internet.
do I need to configure any thing in my mozila firefox explore before starting ??

---

### Post by chili555 on 2013-11-19
> **bte_rajan said:**
> Thanks again, I now have another issue, wireless detects networks and I am able to connect to one of the network. but still I am unable to browse internet.
do I need to configure any thing in my mozila firefox explore before starting ??Possibly. In Firefox, select Edit > Preferences > Advanced > Network > Connection > Settings . In most cases, 'no proxy' is the preferred setting. We would love to see the results of:```
nm-tool
ping -c3 8.8.8.8
```

---

### Post by bte_rajan on 2013-11-19
here is the terminal output

  nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [DU-Wireless] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        BC:85:56:5F:36:C5

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    MKu:             Infra, 90:84:0D:DF:52:C1, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    *default:        Infra, 00:18:E7:0E:DA:4D, Freq 2437 MHz, Rate 54 Mb/s, Strength 40

  IPv4 Settings:
    Address:         192.168.1.137
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             10.103.1.11


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        74:86:7A:23:72:8A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

---

### Post by chili555 on 2013-11-19
> IPv4 Settings:
Address: 192.168.1.137
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1

[COLOR="#FF0000"]DNS: 10.103.1.11[/COLOR]
Where did that DNS nameserver come from? Did you set up a static IP address? Please don't tell me it was provided by the router by DHCP!?! How does it compare to other devices on the same router and network?

---

### Post by sioxs on 2013-11-19
> Please don't tell me it was provided by the router by dhcp!?!
LOL!!!
Stranger things have happened! Mine goes to 10.64.64.64 when no access to the modum is present from the router

---

### Post by bte_rajan on 2013-11-20
I have now setup IPv4 setting in
Edit Connections--- Wireless---default---edit---IPv4 Settings---manual     and then saved it

I am using wired connection in my laptop that has different IPv4 setting and it works fine. but some time I need wifi connection. so I am trying this

but still unable to browse internet when wired connection is disabled, and wireless is connected.

---

### Post by chili555 on 2013-11-20
I suspect there is something wrong in your static settings. If you'd care to share them, we'll take a look and see if we can fine-tune them. In most cases, however, setting the IPv4 settings as 'Automatic (DHCP)' works perfectly well. Is there some reason you are using manual methods which, obviously, won't work?

---

### Post by bte_rajan on 2013-11-20
previously I was using IPv4 settings as 'Automatic (DHCP)' but it doesn&#8217;t work so I tried setting up connection as manual. but as you suspected that also doesn't work. regarding your query about "static settings" . please tell what should i do (what command I use) to provide you all the necessary information that you need about my system

---

### Post by chili555 on 2013-11-20
With only the ethernet attached, get a good connection and run:```
nm-tool
```Copy and paste the result for IPv4 settings and DNS. Do the same for wireless. Post them both here. Obviously, the DNS is incorrect for wireless as I implied above, and we need to see what the ethernet gets and correct it.

Generally, if you can't connect with wireless, it isn't a DHCP vs. static IP address problem. It is a problem elsewhere. By the time Doc Chili is called in to consult, we have to back all this out.

---

### Post by bte_rajan on 2013-11-20
here is the terminal output

nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        BC:85:56:5F:36:C5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [DU] -----------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        74:86:7A:23:72:8A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.154.4.5
    Prefix:          16 (255.255.0.0)
    Gateway:         10.154.1.1

    DNS:             8.8.8.8


nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [DU-Wireless] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        BC:85:56:5F:36:C5

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    MKu:             Infra, 90:84:0D:DF:52:C1, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    skk:             Infra, 00:23:69:2C:43:28, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    *default:        Infra, 00:18:E7:0E:DA:4D, Freq 2437 MHz, Rate 54 Mb/s, Strength 39

  IPv4 Settings:
    Address:         192.168.1.137
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             10.103.1.11


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        74:86:7A:23:72:8A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

---

### Post by chili555 on 2013-11-20
Your wireless settings:> IPv4 Settings:
Address: 192.168.1.137
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1

DNS: 10.103.1.11
Do you have two routers? Isn't your wired and wireless router one and the same? Shouldn't your wireless be trying to connect here?> IPv4 Settings:
Address: 10.154.4.5
Prefix: 16 (255.255.0.0)
Gateway: 10.154.1.1

DNS: 8.8.8.8Is 10.154.1.1 a large corporate setup? In a home network, it's pretty unusual to have a Class B network.

And who on earth is 10.103.1.11??

---

### Post by bte_rajan on 2013-11-21
I am using My University Network for both wired and wireless connection, nothing is personal or home based. all this IPv4 setting are provided by my university.

---

### Post by bte_rajan on 2013-11-21
After consulting my university's network operator I changed my DNS server

here is the terminal output

nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [default] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        BC:85:56:5F:36:C5

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    DGB6NVQ1-43440:  Infra, AC:72:89:57:D4:F2, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    MKu:             Infra, 90:84:0D:DF:52:C1, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    skk:             Infra, 00:23:69:2C:43:28, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    *default:        Infra, 00:18:E7:0E:DA:4D, Freq 2437 MHz, Rate 54 Mb/s, Strength 41

  IPv4 Settings:
    Address:         192.168.1.137
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             10.103.1.11


- Device: eth0  [DU] -----------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        74:86:7A:23:72:8A

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.154.4.5
    Prefix:          16 (255.255.0.0)
    Gateway:         10.154.1.1

    DNS:             10.103.1.11

but still I am unable to use Internet when I unplug wired connection.

---

### Post by chili555 on 2013-11-21
Please change your IPv4 settings to Automatic(DHCP), reboot and try to connect. What are your symptoms? Does it try? Are you challenged for the encryption key? What do the logs say?> cat /var/log/syslog | grep -e etwork -e ath | tail -n25Then try:```
sudo -i
echo "options ath9k nohwcrypt=1" >> /etc/modprobe.d/ath9k.conf
modprobe -r ath9k
modprobe ath9k
exit
```Any improvement?

---

### Post by bte_rajan on 2013-11-22
I have now changed IPv4 settings to Automatic(DHCP) (for wireless connection only).

Still I am unable to browse internet through Mozilla Firefox but able to connect to default wireless network.(When only wireless connection is Connected and wired connection is unpluged)

 When I switch on firefox it says "Server not found"

here is the terminal output of your suggested commnads

grep -e etwork -e ath | tail -n25 
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info>   address 192.168.1.137
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info>   prefix 24 (255.255.255.0)
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info>   gateway 192.168.1.1
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info>   hostname 'rajan-Inspiron-3521'
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info>   nameserver '10.103.1.11'
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 22 12:49:30 rajan-Inspiron-3521 NetworkManager[932]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 22 12:49:31 rajan-Inspiron-3521 NetworkManager[932]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 22 12:49:31 rajan-Inspiron-3521 NetworkManager[932]: <info> Policy set 'DU' (eth0) as default for IPv4 routing and DNS.
Nov 22 12:49:31 rajan-Inspiron-3521 NetworkManager[932]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 22 12:49:31 rajan-Inspiron-3521 NetworkManager[932]: <info> Activation (wlan0) successful, device activated.
Nov 22 12:49:31 rajan-Inspiron-3521 NetworkManager[932]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 22 12:49:36 rajan-Inspiron-3521 NetworkManager[932]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Nov 22 12:49:41 rajan-Inspiron-3521 NetworkManager[932]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Nov 22 12:49:41 rajan-Inspiron-3521 NetworkManager[932]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Nov 22 12:49:41 rajan-Inspiron-3521 NetworkManager[932]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Nov 22 12:49:41 rajan-Inspiron-3521 NetworkManager[932]: <info> Policy set 'default' (wlan0) as default for IPv4 routing and DNS.
Nov 22 12:49:41 rajan-Inspiron-3521 NetworkManager[932]: <info> Policy set 'default' (wlan0) as default for IPv4 routing and DNS.
Nov 22 12:49:50 rajan-Inspiron-3521 NetworkManager[932]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 22 12:49:50 rajan-Inspiron-3521 NetworkManager[932]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 22 12:49:50 rajan-Inspiron-3521 NetworkManager[932]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 22 12:49:50 rajan-Inspiron-3521 NetworkManager[932]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
rajan@rajan-Inspiron-3521:~$ sudo -i
[sudo] password for rajan: 
root@rajan-Inspiron-3521:~# echo "options ath9k nohwcrypt=1" >> /etc/modprobe.d/ath9k.conf
root@rajan-Inspiron-3521:~# modprobe -r ath9k
root@rajan-Inspiron-3521:~# modprobe ath9k

---

### Post by chili555 on 2013-11-22
With the wireless only connected, please show us:```
ping -c3 192.168.1.1
ping -c3 10.103.1.11
ping -c3 www.google.com
iwconfig
```Your syslog looks pretty solid, actually.

---

### Post by bte_rajan on 2013-11-23
ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=3 ttl=255 time=4.58 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 1 received, 66% packet loss, time 2006ms
rtt min/avg/max/mdev = 4.582/4.582/4.582/0.000 ms

ping -c3 10.103.1.11
PING 10.103.1.11 (10.103.1.11) 56(84) bytes of data.

--- 10.103.1.11 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms


ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:E7:0E:DA:4D   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:550  Invalid misc:106   Missed beacon:0

eth0      no wireless extensions.

---

### Post by chili555 on 2013-11-23
> ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=3 ttl=255 time=4.58 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 1 received, 66% packet loss, time 2006ms
rtt min/avg/max/mdev = 4.582/4.582/4.582/0.000 msYou can ping the gateway, so we know you *are* connected to the wireless access point.> ping -c3 10.103.1.11
PING 10.103.1.11 (10.103.1.11) 56(84) bytes of data.

--- 10.103.1.11 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms
But you cannot ping the DNS nameserver. If you can't get to it, it can't do the work of reolving names like [www.google.com](www.google.com) into numbers like 74.125.131.104. Therefor, you are connected to the wireless access point but you can't reach the internet.

I suggest the you return to whoever or wherever you were given the DNS nameserver 10.103.1.11 and tell them it is invalid. When you are given a valid DNS nameserver, make the change in your system and you should be all set.

---

### Post by bte_rajan on 2013-11-24
okay thanksss, I will try that and let you know the results

---

### Post by nitzien123 on 2014-02-14
> **chili555 said:**
> Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install linux-backports-modules-cw-3.8-precise-generic
```Reboot and let us hear your report.

I didnt even have to reboot. Thanks a zillion!

---

