---
title: "Ubuntu 8.04 on HP 6720s: Ethernet and other problems"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by abhishekbawkar on 2008-09-01
Hi there…
 
I am new to Ubuntu. I have HP6720s laptop with following configuration:
Processor:         Intel Core 2 Duo T5470
RAM:             1GB 
Chipset:         Intel GME965 Express
HDD:             120GB (12GB allocated for Ubuntu (10GB ext3 partition + 2GB Swap area))
Network Interface:     Intel Fast Ethernet Integrated Controller (10/100 NIC)
Wireless:        Intel 802.11a/b/g, Bluetooth 2.0
 
I have installed **Ubuntu 8.04 (64-bit version)** and liked it very much. Everything went well during the installation. Now I am facing following problems:
 
1.    **Ethernet is not working.** After setting IP address, subnet mask, gateway, DNS, it shows that the LAN is connected, I can see the packets being sent/received, but I cannot open any web page neither I can ping any IP. I have tried almost everything mentioned on the forum **“Ubuntu 8.04 Hardy and HP 6720s (a hopefully complete guide)”** and other too to make my Ethernet work, but none of them worked. And because the Ethernet is not working I am **not able to do** **“aptget”** for anything. 
2.    **build-essential is not getting installed.**
3.    not able to compile any of the software packages like AWN, Compiz settings manager etc. It shows **“C compiler could not create executables”**. When I checked on forums I came to know that g++ is not installed. So I tried to install **g++-4.2** (debian package, the one which is there on ubuntu CD (ordered from ubuntu website)), but it says **“Dependency not satisfiable: libstdc++6-4.2-dev”** and when I try to install **libstdc++6-4.2-dev** it says **“Dependency not satisfiable: g++-4.2”.** I didn’t understand this, **g++-4.2 and libstdc++6-4.2-dev** both showing dependency not satisfiable for each others (C’on at least one should be independent of other).
 
Just to mention that, I have tried all the above things on Ubuntu 8.04 (32 bit version) and Ubuntu 7.10 (32 bit version) also, none of them worked there too. Would like to know whether Ubuntu 8.04 (64 bit version) is the correct installation for my notebook. 
 
Please let me know if anyone has got solution for these, at least the Ethernet problem. I guess, once my Ethernet problem gets solved then everything else will be solved by “aptget”.
 
Thanks in advance!!
 
Abhishek

---

