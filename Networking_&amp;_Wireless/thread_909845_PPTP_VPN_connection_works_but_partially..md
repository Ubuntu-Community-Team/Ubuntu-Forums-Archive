---
title: "PPTP VPN connection: works but partially."
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by markys on 2008-09-03
Hi there,

I am working on a Lenovo T61 with an Intel 4965 wireless card. I am using package network-manager-pptp to connect to the VPN on the wifi network at school. Almost everything works great (surf, download, etc), but a couple of things just don't work.

For example, I can get on the login page for any google service (gmail, gcalendar, greader, etc), I try to log in, but then it just loads forever... Also, on my school web account (Horde IMP), I can log in and read mails, but sending does not work. Last but not least, trying to synchronize my Synaptic leads to the same result...

Since I am dual-booting, I tried in Vista and everything works fine. I also tried with a wired connection on Ubuntu and it works fine too. That means that is a software problem on my side... And just for the info, someone with almost the same setup as me is in the same situation.

I activated the debug mode in the VPN wizard, and here is the ppp related output: 
```
Sep  3 18:38:47 markys-laptop-ubuntu pppd[13554]: Script /etc/ppp/ip-up started (pid 13560)
Sep  3 18:38:47 markys-laptop-ubuntu pppd[13554]: Script /etc/ppp/ip-up finished (pid 13560), status = 0x0
Sep  3 18:38:48 markys-laptop-ubuntu NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 4. 
Sep  3 18:39:12 markys-laptop-ubuntu pppd[13554]: rcvd [CCP ResetReq id=0x3]
Sep  3 18:39:12 markys-laptop-ubuntu pppd[13554]: sent [CCP ResetAck id=0x3]
Sep  3 18:39:13 markys-laptop-ubuntu pppd[13554]: rcvd [CCP ResetReq id=0x4]
Sep  3 18:39:13 markys-laptop-ubuntu pppd[13554]: sent [CCP ResetAck id=0x4]
Sep  3 18:39:13 markys-laptop-ubuntu pppd[13554]: rcvd [CCP ResetReq id=0x5]
Sep  3 18:39:13 markys-laptop-ubuntu pppd[13554]: sent [CCP ResetAck id=0x5]
Sep  3 18:39:14 markys-laptop-ubuntu pppd[13554]: rcvd [CCP ResetReq id=0x6]
Sep  3 18:39:14 markys-laptop-ubuntu pppd[13554]: sent [CCP ResetAck id=0x6]
Sep  3 18:39:16 markys-laptop-ubuntu pppd[13554]: rcvd [CCP ResetReq id=0x7]
Sep  3 18:39:16 markys-laptop-ubuntu pppd[13554]: sent [CCP ResetAck id=0x7]
Sep  3 18:39:20 markys-laptop-ubuntu pppd[13554]: rcvd [CCP ResetReq id=0x8]
Sep  3 18:39:20 markys-laptop-ubuntu pppd[13554]: sent [CCP ResetAck id=0x8]
```

I keep getting these messages while the connection is active.

Finally, here is my VPN client configuration:
```
[main]
Description=Hermes
Connection-Type=pptp
PPTP-Server=sansfil.polymtl.ca
Use-Peer-DNS=yes
Encrypt-MPPE=yes
Encrypt-MPPE-128=yes
Encrypt-MPPE-Stateful=yes
Compress-MPPC=no
Compress-Deflate=no
Compress-BSD=no
PPP-Lock=yes
Auth-Peer=yes
Refuse-EAP=no
Refuse-CHAP=no
Refuse-MSCHAP=no
MTU=1416
MRU=1416
LCP-Echo-Failure=10
LCP-Echo-Interval=10
PPP-Custom-Options=
Peer-DNS-Over-Tunnel=yes
X-NM-Routes=
Use-Routes=no
```

Well that's it, I hope you can help me find the source of the problem!

Thanks a lot!

---

### Post by markys on 2008-09-05
Hi again,

After using the connection a little more, it seems that I am unable to do anything that implies upload of data.

-As I said before, I can access my web based school mail account, but I am unable to send a mail.
-When I make a connection speed test on [http://www.speedtest.net/](http://www.speedtest.net/) the download test goes fine, but the upload test does not start and it hangs forever.
-Sending mail through Evolution also doesn't work.

Since I had no problems with downloads yet, the problem is very probably something preventing the data from being uploaded.. However, it does not help me to figure out what does that, but that might ring someone's bell...

---

### Post by alazou on 2008-09-07
lol we are in the same school ;). 

I'm trying to set it up too, but I can't even surf on the internet. intranet works fine though (webct moodle etc). When I was using pptpconfig with fedora there was the option "client to lan" and "all to tunnel". for the wireless I just had to use the "all to tunnel" and it worked fine. But I can't find this option in the pptp plugin. maybe we have to add this option in the configuration file. where did you find yours ?

Try changing Refuse-CHAP=no to yes also. It's necessary for servers that use default configurations. not sure though.

---

### Post by alazou on 2008-09-07
Also have you tried accessing your hard drive (les ordinateurs des laboratoires de poly). when you're connected to the servers ? because I can't. I could when I was using fedora and pptpconfig, but now it's a no go. the techs told me that they upgraded to samba 3.2.3, and that was probably the cause. Just tough I would try asking you.

---

### Post by markys on 2008-09-08
Hey,

Actually it was very easy to set up the connection on a fresh install of ubuntu 8.04.

I simply installed package *network-manager-pptp*, connected to the wireless network hermes, and set up the VPN connection with the gui (you click the connection icon, and choose VPN configuration). You can check the configuration I use (which was given to me by another student, who has the same problem) in my first post.

Also, I do not even know how to access my hard disk space on the school server (I am new here), but i'll sure check that later.

---

### Post by alazou on 2008-09-09
yo !

Yeah thanks. in fact I had already used the pptp pluggin to connect. but for it to have total access to the internet you have to configure your options. I find the options on the pluggin too limited. as I said, with pptpconfig you could set "all to tunnel". With it all the communication went through the servers of polytechnique and you had all acces : download and upload. you can give this package a try, it works flawlessly. actually there is a how to here to set it up : [http://www.polymtl.ca/vpn/index-linux.html](http://www.polymtl.ca/vpn/index-linux.html). you don't need to follow the last steps explained in UTILISATION.

But the package is quite old you will have to compile it.

to connect to your hard drive you just have to follow this : [http://www.polymtl.ca/si/service/aireAccesLibre/Linux_acces_espace_disque.php](http://www.polymtl.ca/si/service/aireAccesLibre/Linux_acces_espace_disque.php)

replace codeacces by your actual acces code ex : alhurd

---

### Post by markys on 2008-09-09
Hi,

I read many things about pptpconfig, but did not try it since it is not supported anymore and it was replaced by the network-manager package. I'll try it this afternoon and give some feedback.

For the disk space, I tried to do as they say in the document, but it keeps asking me for my password. I don't have much time right now, so I'll give it another try later today.

---

### Post by markys on 2008-09-18
Hi,

There is apparently a bug in the network manager pptp package. Even if you set the MTU manually in the GUI, it won't apply it to the tunnel. You simply need to set it to 1300 using the command line, and it should work correctly.

Check this, especially the last post: [https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/151112](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/151112)

By the way, the one who published the last post on the launchpad page, Michel Dagenais, is the director of the Genie Informatique dept at Poly, if you want to thank him !

---

### Post by babaum on 2008-12-17
Im not sure if I should post it here or open a new thread, but I think there's an old (and serious) problem with the VPN support yet. As of this moment, I'm able to connect and use VPN perfectly in my thinkpad T43 with Intrepid. The only problem is, after I disconnect (couple of minutes), the system hangs, only the mouse moves... I tried to connect from another computer at home, ssh doesn't respond. The only solution seems to be a hard reset, and this is specially painfull for a notebook.

---

