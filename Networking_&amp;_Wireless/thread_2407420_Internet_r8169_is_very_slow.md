---
title: "Internet r8169 is very slow"
date: 2018-12-04
forum: Networking &amp; Wireless
---

### Post by maslobojik on 2018-12-04
[COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]Now I use kubuntu 18.04 and used ubuntu 16.04 [/COLOR][COLOR=#000000][FONT=Roboto]before[/FONT][/COLOR][COLOR=#000000], the same problem.
[/COLOR][COLOR=#333333][FONT=monospace]On linux the speed is 10Mb/s but o[/FONT][/COLOR][COLOR=#333333][FONT=monospace]n Windows 7 (dual boot) the speed of the link is 100Mb/s.[/FONT][/COLOR]
[COLOR=#000000]I read a couple of posts about my network interface issues with slow speed, nothing to help.[/COLOR]
[COLOR=#000000]Info :
[/COLOR]

```

[FONT=monospace][COLOR=#000000]sudo lshw -C network         [/COLOR]
  *-network                  
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 06
       serial: 4c:cc:6a:61:bf:a8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.21.46 latency=0 link=yes mul
ticast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:d000(size=256) memory:fe704000-fe704fff memory:fe700000-fe703fff

[/FONT]
```

```

[FONT=monospace][COLOR=#000000]lsmod | grep r81[/COLOR]
[COLOR=#FF5454]**r81**[/COLOR][COLOR=#000000]69                  86016  0[/COLOR]
mii        [/FONT] [FONT=monospace]            16384  1 [COLOR=#FF5454]**r81**[/COLOR][COLOR=#000000]69[/COLOR]
[/FONT]
```

```

[FONT=monospace][COLOR=#000000]sudo ethtool enp5s0[/COLOR]
Settings for enp5s0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full  
                                100baseT/Half 100baseT/Full  
                                1000baseT/Half 1000baseT/Full  
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  10baseT/Half 10baseT/Full  
                                100baseT/Half 100baseT/Full  
                                1000baseT/Half 1000baseT/Full                                                                                                                       
        Advertised pause frame use: Symmetric Receive-only                                                                                                                          
        Advertised auto-negotiation: Yes                                                                                                                                            
        Advertised FEC modes: Not reported                                                                                                                                          
        Link partner advertised link modes:  10baseT/Half 10baseT/Full                                                                                                              
                                             100baseT/Half 100baseT/Full                                                                                                            
        Link partner advertised pause frame use: Symmetric                                                                                                                          
        Link partner advertised auto-negotiation: Yes                                                                                                                               
        Link partner advertised FEC modes: Not reported                                                                                                                             
        Speed: 100Mb/s                                                                                                                                                              
        Duplex: Full                                                                                                                                                                
        Port: MII                                                                                                                                                                   
        PHYAD: 0                                                                                                                                                                    
        Transceiver: internal                                                                                                                                                       
        Auto-negotiation: on                                                                                                                                                        
        Supports Wake-on: pumbg                                                                                                                                                     
        Wake-on: g                                                                                                                                                                  
        Current message level: 0x00000033 (51)                                                                                                                                      
                               drv probe ifdown ifup                                                                                                                                
        Link detected: yes

[/FONT]
```

---

### Post by mitesh.agrwl on 2018-12-04
> **maslobojik said:**
> [COLOR=#000000]Hi,[/COLOR]
[COLOR=#000000]Now I use kubuntu 18.04 and used ubuntu 16.04 [/COLOR][COLOR=#000000][FONT=Roboto]before[/FONT][/COLOR][COLOR=#000000], the same problem.
[/COLOR][COLOR=#333333][FONT=monospace]On linux the speed is 10Mb/s but o[/FONT][/COLOR][COLOR=#333333][FONT=monospace]n Windows 7 (dual boot) the speed of the link is 100Mb/s.[/FONT][/COLOR]
[COLOR=#000000]I read a couple of posts about my network interface issues with slow speed, nothing to help.[/COLOR]
[COLOR=#000000]Info :
[/COLOR]

```

[FONT=monospace][COLOR=#000000]sudo lshw -C network         [/COLOR]
  *-network                  
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 06
       serial: 4c:cc:6a:61:bf:a8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       c[B]onfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.21.46 latency=0 link=yes mul
ticast=yes port=MII speed=100Mbit/s[/B]
       resources: irq:16 ioport:d000(size=256) memory:fe704000-fe704fff memory:fe700000-fe703fff

[/FONT]
```

```

[FONT=monospace][COLOR=#000000]lsmod | grep r81[/COLOR]
[COLOR=#FF5454]**r81**[/COLOR][COLOR=#000000]69                  86016  0[/COLOR]
mii        [/FONT] [FONT=monospace]            16384  1 [COLOR=#FF5454]**r81**[/COLOR][COLOR=#000000]69[/COLOR]
[/FONT]
```

```

[FONT=monospace][COLOR=#000000]sudo ethtool enp5s0[/COLOR]
Settings for enp5s0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full  
                                100baseT/Half 100baseT/Full  
                                1000baseT/Half 1000baseT/Full  
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  10baseT/Half 10baseT/Full  
                                100baseT/Half 100baseT/Full  
                                1000baseT/Half 1000baseT/Full                                                                                                                       
        Advertised pause frame use: Symmetric Receive-only                                                                                                                          
        Advertised auto-negotiation: Yes                                                                                                                                            
        Advertised FEC modes: Not reported                                                                                                                                          
        Link partner advertised link modes:  10baseT/Half 10baseT/Full                                                                                                              
                                             100baseT/Half 100baseT/Full                                                                                                            
        Link partner advertised pause frame use: Symmetric                                                                                                                          
        Link partner advertised auto-negotiation: Yes                                                                                                                               
        Link partner advertised FEC modes: Not reported                                                                                                                             
        **Speed: 100Mb/s**                                                                                                                                                              
        Duplex: Full                                                                                                                                                                
        Port: MII                                                                                                                                                                   
        PHYAD: 0                                                                                                                                                                    
        Transceiver: internal                                                                                                                                                       
        Auto-negotiation: on                                                                                                                                                        
        Supports Wake-on: pumbg                                                                                                                                                     
        Wake-on: g                                                                                                                                                                  
        Current message level: 0x00000033 (51)                                                                                                                                      
                               drv probe ifdown ifup                                                                                                                                
        Link detected: yes

[/FONT]
```

The 100Mb/s speed shown by Win is your LAN connection speed, i.e. connection speed between your PC and router/switch. This is also true for your Linux/Ubuntu/Kubuntu system, check highlighted portions in the code. To check the actual Internet speed, use an online too like [www.speedtest.net](www.speedtest.net)

---

### Post by maslobojik on 2018-12-04
> **mitesh.agrwl said:**
> The 100Mb/s speed shown by Win is your LAN connection speed, i.e. connection speed between your PC and router/switch. This is also true for your Linux/Ubuntu/Kubuntu system, check highlighted portions in the code. To check the actual Internet speed, use an online too like [www.speedtest.net]("http://www.speedtest.net")
I check on this [www.speedtest.net]("http://www.speedtest.net/") site. 
But why speed very fast on Windows. Something wrong with linux driver.

---

### Post by mitesh.agrwl on 2018-12-04
> **maslobojik said:**
> I check on this [www.speedtest.net]("http://www.speedtest.net/") site. 
But why speed very fast on Windows. Something wrong with linux driver.

Please post the interface speed and duplex details from windows.

---

