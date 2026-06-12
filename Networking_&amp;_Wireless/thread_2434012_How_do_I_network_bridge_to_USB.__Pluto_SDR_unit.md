---
title: "How do I network bridge to USB.  Pluto SDR unit?"
date: 2019-12-29
forum: Networking &amp; Wireless
---

### Post by adrian-h on 2019-12-29
I will try and describe my situation the best I can, I have two Linux (Ubuntu 18.04 LTS) computers, one is 192.168.1.40 (Normal desktop), and the other 192.168.1.30 (This is a headless unit and does not run X server).

Now 192.168.1.30 is typically remote at the end of a long CAT5 cable, I will typically ssh into the computer to update it, run the odd script, and send a TS stream to it for amateur radio use.

I have obtained a Pluto SDR from Analog devices and when I plug this in to a Ubuntu computer it will assign the PlutoSDR an address of 192.168.2.1 and the host pc 192.168.2.10.  (I did not realise you could pass TCP/IP via USB before, but as it is all serial data, I could see the possibility!).  I can change these IP's if required.

What I would like to achieve is to have 192.168.1.40 stream to the PlutoSDR which means the TCP/IP packets need to be 'bridged' in the headless computer and sent out via USB to the PlutoSDR.  Can anyone tell me how to achieve this if possible.  

I could as mentioned above change the IP addresses to be in the same subnet if required and that helps.

Thanks in anticipation.

Adrian

---

### Post by adrian-h on 2019-12-29
In case it helps anyone answer, on the 192.168.1.30 computer that is remote.  

In /etc/netplan/ there are two files: 01-netcfg.yaml  and 50-cloud-init.yaml

01-netcfg.yaml is as follows:
```

network:
         version: 2
         renderer: networkd
         ethernets:
             enp0s25:
               dhcp4: no
       addresses: [192.168.1.30/24]
               gateway4: 192.168.1.254 
       nameservers:
                    addresses: [192.168.1.254]
```

and 50-cloud-init.yaml is as follows:

```
# This file is generated from information provided by                                                                                                                                                     
# the datasource.  Changes to it will not persist across an instance.                                                                                                                                     
# To disable cloud-init's network configuration capabilities, write a file                                                                                                                                
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:                                                                                                                                
# network: {config: disabled}                                                                                                                                                                             
network:                                                                                                                                                                                                  
    ethernets:                                                                                                                                                                                            
        enp0s25:                                                                                                                                                                                          
            dhcp4: true                                                                                                                                                                                   
    version: 2
```

The 192.168.1.40 desktop computer is managed by netmanager at present, the only file in /etc/netplan/ is 01-network-manager-all.yaml

and contains the following:

```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

Adrian

---

