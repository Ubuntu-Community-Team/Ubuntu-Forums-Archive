---
title: "Cannot connect to wireless network on Ubuntu 11.04"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by asdfgh1 on 2011-07-20
Hello,

I'm new to ubuntu, as in I've never used it before. I recently installed the ubuntu 11.04 *Natty Narwhal* release and I cannot connect to my wireless router. Whenever I click on the wireless network in the Networking Panel to connect to it, I get the following:

> Authentication required by wireless network
Passwords or encryption keys are required to access the wireless network...

Underneath the text is the "Wireless security:" field, but I cannot choose any of the options or type in the network's password.

What should I do? :(

For reference, this is the ifconfig and iwconfig from terminal:

> 
mok@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:9b:88:66:e1  
          inet6 addr: fe80::20e:9bff:fe88:66e1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:345 dropped:0 overruns:0 frame:345
          TX packets:16 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3343 (3.3 KB)
          Interrupt:11 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:11:25:80:51:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11376 (11.3 KB)  TX bytes:11376 (11.3 KB)



mok@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-97 dBm
          Rx invalid nwid:660  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14216   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-97 dBm
          Rx invalid nwid:660  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14216   Missed beacon:0



Your help is greatly appreciated!

---

### Post by fractalman on 2011-07-20
sorry misread the output.

---

### Post by dyrvere on 2011-07-20
Read through Part II: Wireless management about Manual Setup on the Arch-Wiki.
[https://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_management](https://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_management)
hope it helps!
Skip all sections about load/probe-modules and /etc/configurations unless really sure it could work! :)

---

### Post by roger_1960 on 2011-07-20
Hi

On the ouput from the OP the signal levels are really low - too low to work I think.  Perhaps too far from the wifi source?

Roger

---

### Post by amjjawad on 2011-07-20
Hello and Welcome :)

Are you able to connect directly to your router via LAN Cable?

Do you have any Wireless Security on your Router? if yes, what type?

How far are you from the router? is it N-Router? G-Router?

---

