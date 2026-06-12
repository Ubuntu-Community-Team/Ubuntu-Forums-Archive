---
title: "Host-only network problems with VMware"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by ubuntuuser on 2006-07-24
Good evening,

this is the third day on which I try to setup host-only networking on my box between Dapper and WinXP inside VMware. I am running Dapper as host OS and VMware workstation 5.5.1 build-19175, and I installed WinXP SP1 as guest OS. It worked just fine, and all the different network adapters were created by running vmware-config.pl. The strange part is: Although /dev/vmnet1 and the virtual network adapter in XP are on the same subnet (192.168.38.0/24), they can't even ping each other. When I start a ping session in Win XP and capture packets with Ethereal, I can see that DHCP worked and the virtual interface got an IP (I can of cource also see that with ipconfig /all). But Ethereal only captures echo requests from my guest to the host, there are no replies sent. Strange thing is: from time to time  I can capture ARP requests, also initiated by the guest. These requests are answered correctly by the host. So why doesn't the host answer Ping echo requests? When I try to ping the guest from dapper, I get an error message: ```
ping: sendmsg: Operation not permitted
```Now, what's that supposed to mean? Doesn't ping run with suid bit set? So how can something be not permitted for root? Can anyone help me setting up host-only networking for my machine? I need an isolated network environment for, uhm, security testing purposes 8) So thanks for your help. I always thought I knew how to setup (basic) networks, but it just looks like I don't.

---

### Post by ubuntuuser on 2006-07-25
Can somebody please tell me what to do so I can fix that problem? I have  set up another virtual machine and let them run both at the same time. The can ping each other, but my host OS can't ping neither. What's wrong?

---

