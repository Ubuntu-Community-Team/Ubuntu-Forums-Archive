---
title: "Ubuntu 18.04.1 LTS shows connected Wifi, but it wont work"
date: 2018-12-17
forum: Networking &amp; Wireless
---

### Post by hashs on 2018-12-17
Hello,

I have Lubuntu (Ubuntu 18.04.1) installed on an old computer. It used to work fine, but now I can't connect to the internet, although Lubuntu shows the internet connected on the botton right. When I try browsing stuff on Firefox, it does not work. How can I solve it?

Thanks

---

### Post by mitesh.agrwl on 2018-12-18
Please post the output of ```
$ip address
$ping -c 5 -i 0.5 8.8.8.8
$ping -c 5 -i 0.5 www.google.com
```

---

### Post by hashs on 2018-12-20
Hello, sorry for my delay and thanks for helping out.

Output of iwconfig

enp0s7    no wireless extensions.

lo        no wireless extensions.

wlx20e917028640  IEEE 802.11  ESSID:"Cabral"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: C0:25:E9:D7:61:38   
          Bit Rate=13 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1088   Missed beacon:0


$ ping -c 5 -i 0.5 8.8.8.8
connect: A rede está fora de alcance
(Network out of reach)

ping -c 5 -i 0.5 [www.google.com](www.google.com)
ping: [www.google.com:](www.google.com:) Falha temporário na resolução de nome
(Temporary failure in name resolution)

---

### Post by hashs on 2018-12-20
As I have said, the computer shows the internet connected to the wifi network in the botton right of the Lubuntu interface, but I cannot access websites or make any updates. I use an wireless adapter. 

I am not experiencied with networking problems, so I would gladly accept some help. Thanks

IPV4

IP address 10.42.0.1
Broadcast address 10.42.0.255
Sub-network mask 255.255.255.0

IPV6
IP address fe80::88ca:85c9:450d:3e13/64

---

### Post by hashs on 2018-12-20
Can someone please help?

---

### Post by chili555 on 2018-12-20
> IP address 10.42.0.1Where did you get that interesting IP address? By DHCP, that is, automatically from the router? How does it compare to the address for other connected devices, such as phones, iPads, etc.? Are they also in the 10.42.0.xx range?

Old Chili smells a big fat rat.

---

### Post by hashs on 2018-12-21
What do you mean by big fat rat?

Command 'ip address' won't work on the Lubuntu computer (the one with connection problems), I got the IP address through the UI. This is the output of command 'ip address' from another computer on the same network:

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether b4:b5:2f:71:09:bd brd ff:ff:ff:ff:ff:ff
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 84:4b:f5:a9:a5:71 brd ff:ff:ff:ff:ff:ff
    inet 192.168.11.4/24 brd 192.168.11.255 scope global dynamic noprefixroute wlo1
       valid_lft 6998sec preferred_lft 6998sec
    inet6 fe80::a046:a0c3:fb92:64ad/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

Honestly, I don't quite get it. All of those are connected on the same network and used to work fine. I haven't changed anything on the Lubuntu computer, it simply stopped working misteriously (to me). Other machines connected to the same network work just fine.

---

### Post by chili555 on 2018-12-21
> I got the IP address through the UI. Do you mean that the Network Manager sees your router and you clicked on it and connected? Or do you mean that you clicked the user interface and selected the option to set up a new network connection? That is a computer-to-computer connection, not computer to router. I doubt that is what you intended.

Please note that the other computer is on the 192.168.x.y network, not 10.42.0.x. That is a big fat rat!

Please clarify.

---

### Post by hashs on 2018-12-21
The network manager shows my network and I just clicked and connected.

---

### Post by hashs on 2018-12-21
I have deleted the old Wifi connections and made a new one, using info from the other computer connected to the same network. Now it works fine

Thanks

---

### Post by wildmanne39 on 2018-12-21
Please allow 12 hours between bumps if you do not receive a reply.

Thanks

---

### Post by chili555 on 2018-12-21
Let's remove all the existing connections:```
sudo rm /etc/NetworkManager/system-connections/*
sudo service network-manager restart
```Now does it see your network? Can you click on it and supply the password and connect?

It might take a reboot.

---

