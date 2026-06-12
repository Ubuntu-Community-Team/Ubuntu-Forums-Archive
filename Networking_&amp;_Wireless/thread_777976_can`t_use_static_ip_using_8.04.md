---
title: "can`t use static ip using 8.04"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by mbdriver on 2008-05-01
I`m on a network where we have to use static ip. I can find the other computers in my network, but I can`t connect to internet, while the others can. I have found out that my dns can`t be changed with network manager. only ip and gateway. I have tried changing dns in the config file and using the terminal, but I`m not allowed to save changes. so what do I do now? :confused:

---

### Post by superprash2003 on 2008-05-01
you can change DNS servers and save the changes this way [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by mbdriver on 2008-05-02
not working for me. :confused:

---

### Post by helgman on 2008-05-02
If I understand you right you don't have a DHCP giving out addresses (and info) on your network so you want to set everything up manualy and you are having trouble with specifying DNS server?

Do you have access to root (sudo) and what have you done so far?

Regards,
Helgman

---

### Post by njparton on 2008-05-02
Please post your /etc/network/interfaces file.

---

### Post by mbdriver on 2008-05-02
I`ll post it when I come home. I think that it`s strange that I can see my shared files in my mediasenter pc, and play music and movies via the lan, but I can`t go to any websites. I have ubuntu installed beside windows xp pro. And in xp everyting works fine. let me xplain our network. it`s me and 3 more households that share one internet connection in lan. there is a wireless router in all houses, that are connected with cat5 cabel. my router is the router that is connected to the internet. I`ve taken some sceenshots of everything, but I don`t know where to upload it. one more thing. when I go to network tools and mark my device, and press configure, I get: **The interface does not exist**. Don`t realy understand anything. :confused:

---

### Post by mbdriver on 2008-05-04
> **njparton said:**
> Please post your /etc/network/interfaces file.


auto lo
iface lo inet loopback


iface eth1 inet static
address 192.168.2.116
netmask 255.255.255.0
gateway 192.168.2.1
wireless-key xxxxxxxxxx
wireless-essid HEIM

auto eth1


wconfig

mrb@mrb-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"HEIM"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:5C:24:D5   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:xxxxxxxxxx   Security mode:open
          Power Management:off
          Link Quality=88/100  Signal level=-41 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mrb@mrb-laptop:~$ 

ifconfig

mrb@mrb-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:ef:03:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:15:00:3f:05:e1  
          inet addr:192.168.2.116  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe3f:5e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:30492 (29.7 KB)  TX bytes:4434 (4.3 KB)
          Interrupt:22 Base address:0x2000 Memory:c0001000-c0001fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59720 (58.3 KB)  TX bytes:59720 (58.3 KB)

mrb@mrb-laptop:~$ 



now what? I`m getting fed up now. I was thinking og getting rid of windows, but they have something that works at least. And I see that it isn`t just me that are having problems. some of my usb devices don`t work eather.

---

### Post by mbdriver on 2008-05-05
*bump*

---

### Post by subzero316 on 2008-05-05
> I`m on a network where we have to use static ip. I can find the other computers in my network, but I can`t connect to internet, while the others can. I have found out that my dns can`t be changed with network manager. only ip and gateway. I have tried changing dns in the config file and using the terminal, but I`m not allowed to save changes. so what do I do now? 




Did you try saving as a SuperUser(sudo)?

---

### Post by mbdriver on 2008-05-05
Yes. when I open the config file, I`m not allowed to save it. I`ve looked on every guide I`ve found, and no luck so far.

---

### Post by zdude on 2008-05-05
Try:

gksudo gedit /etc/resolv.conf

Then type in your dns ip as:

nameserver xxx.xxx.xxx.xxx


Then save!

---

### Post by chili555 on 2008-05-05
When you ```
sudo gedit /your/config/file
```and make changes, it won't let you save and close? Please let us see the result of:```
ping -c3 192.168.2.1
ping -c3 74.125.45.147
ping -c3 www.google.com
```Can you get to the administration pages of your router? [http://192.168.2.1](http://192.168.2.1) perhaps? Does it have DNS addresses? If so, jot those down carefully and we'll proceed.

---

### Post by mbdriver on 2008-05-05
Could not save the file /ect/resolv.conf
Unexpected error: File not found :confused: wery strange since when I see in the file exlporer, it`s there. When I had typed the code. a window opens. but there isn`t any text there. I opend the file in explorer, and there it says:

ipaddres 192.168.2.116
nameserver 192.168.0.1 

ping router 192.168.2.1 ok
everything else fails.

---

### Post by Dalej on 2008-05-05
I have not yet found a way to use the file manager in root (super user) but if you use the terminal and type 
sudo gedit <file location and name> 
you can save without a problem.  I hope this helps

---

### Post by mbdriver on 2008-05-05
> **Dalej said:**
> I have not yet found a way to use the file manager in root (super user) but if you use the terminal and type 
sudo gedit <file location and name> 
you can save without a problem.  I hope this helps

nope. can`t save. have tried: sudo gedit ect/resolv.conf, gksudo gedit ect/resolv.conf, sudo gedit /ect/resolv.conf and gksudo gedit /ect/resolv.conf. always getting error message.

---

### Post by chili555 on 2008-05-05
> sudo gedit /ect/resolv.confIt's not **ect**, it's **etc**.> ipaddres 192.168.2.116
nameserver 192.168.0.1What is the address of your router? Your *interfaces* file says it's 192.168.2.1. */etc/resolv.conf* thinks it's 192.168.0.1. If it is actually 192.168.2.1, and I think it is, because it responds to pings, then *sudo gedit /etc/resolv.conf* and make it look exactly like this:```
nameserver 192.168.2.1
```Then try the ping commands I gave you before. Let us know.

---

### Post by mbdriver on 2008-05-05
> **chili555 said:**
> It's not **ect**, it's **etc**.What is the address of your router? Your *interfaces* file says it's 192.168.2.1. */etc/resolv.conf* thinks it's 192.168.0.1. If it is actually 192.168.2.1, and I think it is, because it responds to pings, then *sudo gedit /etc/resolv.conf* and make it look exactly like this:```
nameserver 192.168.2.1
```Then try the ping commands I gave you before. Let us know.

Wow. its working. I have internet and everything. Thanx a lot.:popcorn: everything because of dyslexia.:lolflag: I used cut and paste, and I got in. I am so happy now.

---

### Post by chili555 on 2008-05-05
I *love* copy and paste! Fortunately for me, you can copy and paste from a forum page to a terminal and from a terminal to a reply page! Saves me a lot of typing and more than a few mistakes.

Glad it's working for you.

---

