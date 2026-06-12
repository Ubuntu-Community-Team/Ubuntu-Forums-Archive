---
title: "I can get IP, but I can't ping myself"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by mohtasham1983 on 2007-06-05
After 1 year and half I rebooted the debian machine at my work which is using kernel 2.6.10.

Unfortunately, I was not able to connect to internet when it was rebooted. 

The most interesting part is that, I can see full information about my ethernet, IP address, broadcast and so on, when I issue ifconfig eth0.

I have tried to change /etc/network/interface to set IP manually and dynamically, but still I can't get ping myself. Although ping localhost works, ping 130.65.42.1 doesn't work.

Unfortunately, this machine is very old and I can't even use CD-ROM or my Flash Drive on it to upgrade the kernel to see if it helps.

I will appreciate your help.

Thanks

---

### Post by zackboarman on 2007-06-05
I have the same problem with my dial-up internet, I'll connect, get IP, dns, brodcast, etc, but it can't open up any webpages. I installed it ~ 1.5 years ago. What I do now is to: chroot into a copy of the Ubuntu Live CD on my harddrive. & when I connect there, regular ubuntu can get online, while when I try the same thing normaly, it won't work. So try using a chrooted copy & see if it works. if it does, then it is something deep in ubuntu, or just a linux thing.

---

### Post by kevdog on 2007-06-05
Is there a firewall on the machine that blocks ping requests??

Is the lo interface configured?? (loopback interface under /etc/network/interfaces)??

---

### Post by dyoung418 on 2007-06-05
> **mohtasham1983 said:**
> The most interesting part is that, I can see full information about my ethernet, IP address, broadcast and so on, when I issue ifconfig eth0.


I have a problem with the same symptoms.  I was actually in the middle of an ssh session with my Feisty Fawn box when the connection suddenly dropped.  Ever since then, I can't see anything on the network from that box even after multiple reboots and even though ifconfig shows that I have an IP address. 

When I run ifconfig, I get the following output:

[FONT="Courier New"]eth1      Link encap:Ethernet  HWaddr 00:1A:92:CB:5A:B0  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:fecb:5ab0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6236 (6.0 KiB)  TX bytes:35286 (34.4 KiB)
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18521 (18.0 KiB)  TX bytes:18521 (18.0 KiB)
[/FONT]

I'm not sure how to troubleshoot this problem.  Any help would be much appreciated.

---

### Post by geakMonkey on 2007-06-07
I am having a similar issue. I had the Ubuntu 6.06LTS online as a webserver, resest my firewall on my router, restarted the Ubuntu server and have not been able to get it to be seen on the internet since. I have used linux for ten years, and I think it is a configuration issue. 

As far as I can see, the ifconfig looks correct:

eth0      Link encap:Ethernet  HWaddr 00:14:2A:99:AF:DC
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fe99:afdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3001598 (2.8 MiB)  TX bytes:440976 (430.6 KiB)
          Interrupt:193 Base address:0xc000

See: [http://www.faqs.org/docs/linux_network/x-087-2-iface.ifconfig.html]("http://www.faqs.org/docs/linux_network/x-087-2-iface.ifconfig.html")

It seems there is a file that sets the ifconfig at boot:

auto eth0
iface eth0 inet dhcp

The first line specifies that the eth0 device should come up automatically when you boot.

See:[ https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-configuration.html]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-configuration.html")

Since all the issues started with a reboot, I think that settings are not being saved properly somewhere. When I made changes in System->Administration->Networking, the file ect/network/interfaces changes but I am not sure that the changes are correct.
 
I did have the same issue of not being able to get back on the internet some days ago. I unplugged the ethernet cards, the router, and dsl cables. Later, I plugged in the cable, then the booted the router to get a dchp ip, then booted the server. It seemed that I had to fiddle with activating the Networking again before that worked. Now, I just want my server back. Suggestions are helpful.

TIA

---

