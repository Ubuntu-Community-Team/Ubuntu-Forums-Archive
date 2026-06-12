---
title: "if config wlan0: error fetching interface information: Device not found"
date: 2018-07-29
forum: Networking &amp; Wireless
---

### Post by 83chivo on 2018-07-29
I have these errors while trying to work with multiple programs from terminal:  (I've an Nvidia GTX1070Laptop, with Bionic Ubuntu18.4 installed with windows)

eth0: error fetching interface information: Device not found
eth1: error fetching interface information: Device not found
wlan0: error fetching interface information: Device not found
wlan1: error fetching interface information: Device not found

My $ ifconfig -a is:

enp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 10:7b:44:30:a7:11  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 127 scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 120396  bytes 4288597722 (4.2 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 120396  bytes 4288597722 (4.2 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.4  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::468d:211a:de70:2bfi prefixlen 64  scopeid 0x20<link>
        ether 34:f6:4b:5a:3f:e3  txqueuelen 1000  (Ethernet)
        RX packets 1767326  bytes 2539929595 (2.5 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 462672  bytes 72508967 (72.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

Assumed enp4s0 is my Ethernet interface and wlp3s0 is my Wireless interface: 
I tried to activate eth0 and eth1 by using: sudo ifconfig eth0 up (the same for wlan0 - 1) but I have the ERROR:  eth0: ERROR while getting interface flags: No such device. :(

I've two networks activate:

$ lshw -class network
  *-network                 
       description: Wireless interface
       product: Wireless 8299
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
**       logical name: wlp3s0**
       version: 3a
       serial: 34:f6:4b:5a:3f:e5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes ....
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8499 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
**       logical name: enp4s0**
       version: 10
       serial: 10:7b:44:30:a7:11
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp.... bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes ... #


How can I add:
eth0
eth1
wlan0
wlan1
on the top of what I have pls? :-)

Also, somebody can explain to me why I need Eth0 and Eth1  interfaces or wlan0 and wlan1 to run certain programs from terminal?

Help please? Thanks in advance

---

### Post by chili555 on 2018-07-29
> Assumed enp4s0 is my Ethernet interface and wlp3s0 is my Wireless interface: Quite correct.> Also, somebody can explain to me why I need Eth0 and Eth1 interfaces or wlan0 and wlan1 to run certain programs from terminal?I doubt that you do. Have you tried specifying the actual interface?```
sudo start some_program wlp3s0
```Can you please give us an example of the program you are attempting to run?

---

### Post by 83chivo on 2018-07-30
Hi chili555 

I'm attempting to run a Torch program.

I tried both logical network but it is doing nothing:  Ex: sudo mainDt.lua wlp3s0 or sudo mainDt.lua enp4s0 

To be more specific, its the neural network model boundaryMPr from [https://github.com/shuohangwang/SeqMatchSeq](https://github.com/shuohangwang/SeqMatchSeq) . I used to work with this model before from my Mac without any problem.

The sh executable command works perfectly,  and it runs well all python files. However, when I start running Torch file:  mainDt.lua , I've the Ethernet - Wireless issues below:

eth0: error fetching interface information: Device not found
eth1: error fetching interface information: Device not found
wlan0: error fetching interface information: Device not found
wlan1: error fetching interface information: Device not found

I am having this issue only while attempting to work with Torch.  I am working within multiple classes from different directories in the same device. For the issue, s that make sense ? 

More info: My network route table looks like this:
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

```

Also, my wireless is working ok. 
```

$ iwconfig
wlp3s0    IEEE 802.11  ESSID:"virginmedia[.....]"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: A0:21:B7:CF:[....]   
          Bit Rate=144.4 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:126   Missed beacon:0


lo        no wireless extensions.


enp4s0    no wireless extensions.

```


I have an Nvidia GTX1070 dual-boot running Linux-Ubuntu and Windows10, working perfect for around two weeks now. 

I'm learning Linux as I go, It's my 2nd week.

Thanks in advance

---

### Post by chili555 on 2018-07-30
I suspect strongly that the code you compiled contains a line somewhere that looks for the connected networking interface. Because of persistent interface naming, these are probably no longer eth0, eth1, wlan0 nor wlan1.

Ideally, I'd recommend contacting the authors of the code, Torch, probably and bring this to their attention. Hopefully, they will update the code and you can git pull and recompile.

However, as this may take a while, weeks, months, years or never, I suggest that you undertake this process: [https://askubuntu.com/questions/928084/how-to-rename-wlp2s0-to-wlan0-in-ubuntu-17-04](https://askubuntu.com/questions/928084/how-to-rename-wlp2s0-to-wlan0-in-ubuntu-17-04)

Post back if you get stuck or need further assistance.

---

