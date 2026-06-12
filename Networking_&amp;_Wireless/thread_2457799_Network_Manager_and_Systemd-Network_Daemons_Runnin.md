---
title: "Network Manager and Systemd-Network Daemons Running"
date: 2021-02-09
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2021-02-09
Having installed some kvm guests that are NAT connected I would like to have them in bridge mode.  I have followed a number of instructions and believe I have now created and enabled a bridge on my host and all is working well.  Except ..... I seem to have both systemd-networkd and network manager up and running.   Is this a conflict - should both be running or just systemd-networkd?

```
dad@dadubuntu:~$ systemctl status systemd-networkd
&#9679; systemd-networkd.service - Network Service
     Loaded: loaded (/lib/systemd/system/systemd-networkd.service; enabled; ven>
     Active: active (running) since Tue 2021-02-09 18:53:43 GMT; 50min ago
TriggeredBy: &#9679; systemd-networkd.socket
       Docs: man:systemd-networkd.service(8)
   Main PID: 481 (systemd-network)
     Status: "Processing requests..."
      Tasks: 1 (limit: 18943)
     Memory: 5.5M
     CGroup: /system.slice/systemd-networkd.service
             &#9492;&#9472;481 /lib/systemd/systemd-networkd

Feb 09 18:53:43 dadubuntu systemd-networkd[481]: rtnl: received neighbor for li>
Feb 09 18:53:43 dadubuntu systemd-networkd[481]: virbr0-nic: Link UP
Feb 09 18:53:43 dadubuntu systemd-networkd[481]: virbr0-nic: Gained carrier
Feb 09 18:53:43 dadubuntu systemd-networkd[481]: virbr0: Link UP
Feb 09 18:53:43 dadubuntu systemd-networkd[481]: virbr0-nic: Link DOWN
Feb 09 18:53:43 dadubuntu systemd-networkd[481]: virbr0-nic: Lost carrier
Feb 09 18:53:46 dadubuntu systemd-networkd[481]: eno1: Gained carrier
Feb 09 18:53:46 dadubuntu systemd-networkd[481]: br0: Gained carrier
Feb 09 18:53:47 dadubuntu systemd-networkd[481]: br0: DHCPv4 address 192.168.1.>
Feb 09 18:53:48 dadubuntu systemd-networkd[481]: br0: Gained IPv6LL

```

```
dad@dadubuntu:~$ systemctl status network-manager
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendo>
     Active: active (running) since Tue 2021-02-09 18:53:43 GMT; 51min ago
       Docs: man:NetworkManager(8)
   Main PID: 779 (NetworkManager)
      Tasks: 3 (limit: 18943)
     Memory: 14.6M
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;779 /usr/sbin/NetworkManager --no-daemon

Feb 09 18:53:43 dadubuntu NetworkManager[779]: <info>  [1612896823.7154] device>
Feb 09 18:53:43 dadubuntu NetworkManager[779]: <info>  [1612896823.7157] device>
Feb 09 18:53:43 dadubuntu NetworkManager[779]: <info>  [1612896823.7158] device>
Feb 09 18:53:43 dadubuntu NetworkManager[779]: <info>  [1612896823.7165] device>
Feb 09 18:53:43 dadubuntu NetworkManager[779]: <info>  [1612896823.7326] device>
Feb 09 18:53:43 dadubuntu NetworkManager[779]: <info>  [1612896823.7329] device>
Feb 09 18:53:43 dadubuntu NetworkManager[779]: <info>  [1612896823.7329] device>
Feb 09 18:53:45 dadubuntu NetworkManager[779]: <info>  [1612896825.4657] agent->
Feb 09 18:53:46 dadubuntu NetworkManager[779]: <info>  [1612896826.9113] device>
Feb 09 18:53:46 dadubuntu NetworkManager[779]: <info>  [1612896826.9121] device>
lines 1-20/20 (END)

```

```
dad@dadubuntu:~$ networkctl status -a
&#9679; 1: lo                                                         
             Link File: /usr/lib/systemd/network/99-default.link
          Network File: n/a                                     
                  Type: loopback                                
                 State: carrier (unmanaged)        
                   MTU: 65536                                   
  Queue Length (Tx/Rx): 1/1                                     
               Address: 127.0.0.1                               
                        ::1                                     

&#9679; 2: eno1                                                              
             Link File: /usr/lib/systemd/network/99-default.link       
          Network File: /etc/systemd/network/1-br0-bind.network        
                  Type: ether                                          
                 State: enslaved (configured)
                  Path: pci-0000:00:1f.6                               
                Driver: e1000e                                         
                Vendor: Intel Corporation                              
                 Model: Ethernet Connection (7) I219-V                 
            HW Address: 2c:f0:5d:92:6d:9e (Micro-Star INTL CO., LTD.)  
                   MTU: 1500 (min: 68, max: 9000)                      
  Queue Length (Tx/Rx): 1/1                                            
      Auto negotiation: yes                                            
                 Speed: 100Mbps                                        
                Duplex: full                                           
                  Port: tp                                             

Feb 09 18:53:43 dadubuntu systemd-networkd[481]: eno1: Link UP
Feb 09 18:53:46 dadubuntu systemd-networkd[481]: eno1: Gained carrier

&#9679; 3: br0                                                                    
               Link File: /usr/lib/systemd/network/99-default.link          
            Network File: /etc/systemd/network/2-br0-dhcp.network           
                    Type: bridge                                            
                   State: routable (configured)   
                  Driver: bridge                                            
              HW Address: 2c:f0:5d:92:6d:9e (Micro-Star INTL CO., LTD.)     
                     MTU: 1500 (min: 68, max: 65535)                        
           Forward Delay: 15s                                               
              Hello Time: 2s                                                
                 Max Age: 20s                                               
             Ageing Time: 5min                                              
                Priority: 32768                                             
                     STP: no                                                
  Multicast IGMP Version: 2                                                 
    Queue Length (Tx/Rx): 1/1                                               
                 Address: 192.168.1.146 (DHCP4)                             
                          2a00:23c8:4182:ba00:2ef0:5dff:fe92:6d9e           
                          fdaa:bbcc:ddee:0:2ef0:5dff:fe92:6d9e              
                          fe80::2ef0:5dff:fe92:6d9e                         
                 Gateway: 192.168.1.254 (Sagemcom Broadband SAS)            
                          fe80::7a65:59ff:fe7b:dd5d (Sagemcom Broadband SAS)
lines 1-52

```

The output of /etc/netplan/01-network-manager-all.yaml reads:

```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

I have (managed?) to delete the network manager gui from my host machine panel so I'm not sure where I am.  My kvm machine says its **Network Source is Bridge br0: Host device eno1**  - which looks OK to me - and within the guest machine it says it's ip address is 192.168.1.148 which is the same as my host range. The kvm guest interface is **Ethernet (enp1s0)**. So what is my question?  It looks OK to me in that the kvm guests are now 192.168.1.x instead of 192.168.122.x but is it right that both systemd-networkd and Network Manager are both running?

---

