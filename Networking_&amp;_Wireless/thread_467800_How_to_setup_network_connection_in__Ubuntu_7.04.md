---
title: "How to setup network connection in  Ubuntu 7.04"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by sreenivas1234 on 2007-06-08
Today i installed ubuntu but no internet, DHCP setting detected and fine. but mozilla says not conected to server. when i set the ip address and default gate way, subnet mask, it not connecting 

the network icon says network not established,

in xp TCP IP setting there are two things extra which my service provider gave

IP  : ***.**.***.***	
SUB : ***.***.***.***
GAT : ***.**.***.***	


DNS : ***.***.***.15
      ***.***.***.12

but in linux there is no DNS
is this a problem??

but am using fine with windows XP no problem atall,
am pretty new to linux, i just saw the graphic of linux and i istalled in my computer, which f*** vista doesnt support because of graphic card.

my system. 
intel pentium 4
1.8MHz
1GB RAM
intel 82845 Chipset

HP desktop D220 model
monitor Samsung satron45Bn

internet cnnection
Cable connection with Motorola SB5100 Modem
Network adaptor:
Broad com 440x10/100 integral contrll

---

### Post by Astraion on 2007-06-08
I have Motorola SB5101 Modem and i have a static IP ... therefore i assign IP, Subnet, Gateway manually...
But i didnt manage to connect to the net...why ?
Cuz my freaking ISP has set the Subnet Mask not 255.255.255.0, but 255.255.248.0 
So i think you should try this, and change the Subnet mask, put either 255.255.248.0 or 255.255.252.0.

Maybe you experience the same problems like i did...

---

### Post by sreenivas1234 on 2007-06-08
my subnet mask which ISP provided is 

255.255.255.224

Gat way: 219.91.252.129

not working

---

### Post by Andra on 2007-06-08
if you suspect dns, type
[http://82.211.81.158](http://82.211.81.158)
in browser, and see whether it works now.

It's ip address for [www.ubuntu.com](www.ubuntu.com). If you trust it...

Other thing is it's not clear whether your network settings are changed from dhcp to manually set. In console window if you type:
ifconfig
what's the output?

---

