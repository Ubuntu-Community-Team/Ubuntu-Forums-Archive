---
title: "Ubuntu 8.0.4 LTS (hardy) on Dell R310 Server: Network Card  Issues"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by chyanga on 2010-11-04
**Ubuntu 8.0.4 LTS (hardy) on Dell R310 Server: Network Card  Issues** 			
 			 			 		   		 		 		I have Dell R310 sever. I  tried to install Ubuntu 8.0.4 LTS (hardy) using the CD ROM. 

I couldn't  install using the cdrom. It gave driver not found message at  the middle of the install and aborted (but CDROM hardware works fine  with live CD). 



Then, I used the usb boot drive and installed the Ubuntu from there. I came up with some issues: 



  
2.       After, I installed the image , couldn’t bring the network  interfaces up.I checked the /etc/inetwork/interfaces files. It looks  good as :


# The loopback interface
auto lo
iface lo inet loopback

# The static network for internal network

auto eth0

iface eth0 inet static
   address 10.120.16.22
   netmask 255.255.255.0
   gateway 10.120.16.21



I tried couple of commands :

ifconfig -a --> only shows loopback

I tried --> /etc/init.d/networking restart

gave this errors: 

eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device: ls 



 Sudo ifup eth0
Sudo ifup eth1
It didn’t bring the interfaces up;
Gave some errors :    
  eth1: ERROR while getting interface flags: No such device 
  SIOCSIFADDR: No such device
   
   
  I also run the command, 
                  
   lshw –C network 



gave :

   
  *-network:0 UNCLAIMED
                  Description: Ethernet controller
                  Product: NetXtreme II BCM5716 Gigabit Ethernet 
                  Vendor:Broadcom Corporation
                  Physical id:0
                  Bus info: pci@0000:02:00.0
                  Version:30
                  Width :64 bits
                  Clock: 33MHz
                  Capabilities: pm vpd msi msix pciexpress bus_master cap_list
                  Configuration: latency =0
   
  Same for the another network card. 
   
  Note: I read somewhere that Dell R310 comes with newest Broadcom  Ethernet card, but the Ubuntu 8.0.4 LTS (hardy), comes with older  version of the driver, so the OS doesn’t detect the Network card. I am  struggling little bit to figure out this, spend some time , but couldn’t  figure how to update the drivers. 



Any help would be greatly appreciated. 





Regards, 

Chyangba

---

### Post by irv on 2010-11-04
First, I ask why you are using an old version of Ubuntu? 8.04 is so out dated. Wouldn't you be better off using the latest release?

---

### Post by ibizatunes on 2010-11-04
Is there any reason you have to have 8.04? 
why not 10.04 as it a LTS as well, and you may have a easier time getting this issue resolve?

---

### Post by chyanga on 2010-11-04
Thank you for response. 

I used the 8.0.4 LTS version to keep all the servers at work consistent with only one version of Ubuntu servers.

---

### Post by irv on 2010-11-04
> **chyanga said:**
> Thank you for response. 

I used the 8.0.4 LTS version to keep all the servers at work consistent with only one version of Ubuntu servers.

Remember when you do this as new hardware is released the OS might not support or work well with it. There are no more security updates available for out dated OS's. This might be a problem on a server platform. I don't know how many servers you are dealing with, but if it is only a few, I would conciser bringing them all up to speed. This is just a suggestion and may help in the long run. (maybe less problem). 

I personally only have one server, but I keep it up to date by installing the latest LTR. I am running 10.04 on it now. My desktop and laptop is running 10.10.

---

