---
title: "[SOLVED] Broad band"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by podianu on 2009-01-08
I am usin BSNL Broadband with a Seimens C2110 modem. I get the following error when trying to connect after reconfiguring ppoeconf. Could not connect due to eth0
  "Check-Item Failed for NAS-Port-Id"
      Could anybody help pl.
                Thanks

---

### Post by theinnercityhippy on 2009-01-08
> **podianu said:**
> I am usin BSNL Broadband with a Seimens C2110 modem. I get the following error when trying to connect after reconfiguring ppoeconf. Could not connect due to eth0
  "Check-Item Failed for NAS-Port-Id"
      Could anybody help pl.
                Thanks

Do you have NAS storage on your network? I would suggest using the automatic setup feature of the network manager applet as this is a vast improvement over previous versions for auto detection and configuration of PPP connections.

-JimDog-

---

### Post by superprash2003 on 2009-01-08
go to the terminal and type ifconfig and post output here..

---

### Post by podianu on 2009-01-10
A more detailed input
   I have a Seimens C2110 modem, with Ubuntu installed. The modem works fine in XP but is a no go in Ubuntu. I have the following outputs after doing the ppoe config and giving the appropriate user name and password.
Plog:
ppo<--->eth0
Chap aunthetication failed
Check-Item Failed for NAS-Port
connection terminated

Output of:
/sbin/ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:47:7d:2e:50  
          inet6 addr: fe80::203:47ff:fe7d:2e50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13700 (13.3 KB)  TX bytes:7540 (7.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:133544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6711956 (6.4 MB)  TX bytes:6711956 (6.4 MB)
Output of
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

Output of
lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)

Output of sys log:
Jan 10 02:14:39 podi kernel: [   59.073936] eth0: no IPv6 routers present
Jan 10 02:14:39 podi NetworkManager: <info>  starting...
Jan 10 02:14:39 podi NetworkManager: <info>  Found dial up configuration for dsl-provider via Modem: dsl-provider
Jan 10 02:14:39 podi NetworkManager: <info>  Found dial up configuration for ppp0 via Modem: ppp0
Jan 10 02:14:41 podi pppd[4291]: PPP session is 9762
Jan 10 02:14:41 podi pppd[4291]: Using interface ppp0
Jan 10 02:14:41 podi pppd[4291]: Connect: ppp0 <--> eth0
Jan 10 02:14:41 podi pppd[4291]: CHAP authentication failed: Check-Item Failed for NAS-Port-Id
Jan 10 02:14:41 podi pppd[4291]: CHAP authentication failed
Jan 10 02:14:41 podi pppd[4291]: Connection terminated.
   Any ideas please.
Pl note:
 I also tried to reset the modem to PPPoE_0_35 settings but it does not seem to work. Pl do respond

---

### Post by podianu on 2009-01-11
I found I had my password fed wrongly. Problem resolved. Sorry for the boo boo.

---

