---
title: "Wireless card working, but cannot ping/connect to router or Internet"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by ssalman on 2005-11-22
Hi, let me start by saying I’m a Linux newbie, but have good Windows experience. I have installed Suse 9.3 and 10.0 on my laptop successfully, and had most of my hardware up and running, and now I’m trying Ubuntu out, so far looks good, but with some hiccups. :(
    
I’m able to connect to the Internet and my local network through my two other boots: XP and Suse, but with Ubuntu, I’m having a very stubborn problem: if I use DHCP I don’t have a connection, and when I manually setup a static IP address/subnet/gateway I get a connection but still cannot ping or connect to my router or Internet. I have tried with and without WEP, same results. What I find strange is that if I use DHCP, my laptop recives a IPV6 address instead of the IP4 address. Did some Googling and search on this forum but found no answer.
    
   Below is some information about my setup.
    
   I would appreciate any help.:razz:
    
   My router ip: 192.168.2.1
   My desktop ip: 192.168.2.3
    
   ifconfig output
   ```
 
   $ ifconfig
   eth1      Link encap:Ethernet  HWaddr 00:0E:35:66:E1:FE
             inet6 addr: fe80::20e:35ff:fe66:e1fe/64 Scope:Link
             UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
             RX packets:28 errors:0 dropped:0 overruns:0 frame:0
             TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:243 (243.0 b)  TX bytes:2028 (1.9 KiB)
             Interrupt:10 Base address:0x8000 Memory:e0200000-e0200fff
    
   lo        Link encap:Local Loopback
             inet addr:127.0.0.1  Mask:255.0.0.0
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING  MTU:16436  Metric:1
             RX packets:336 errors:0 dropped:0 overruns:0 frame:0
             TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:28140 (27.4 KiB)  TX bytes:28140 (27.4 KiB)
   
```     
   iwconfig output 
   ```

   $ iwconfig
   lo        no wireless extensions.
    
   eth0      no wireless extensions.
    
   eth1      IEEE 802.11g  ESSID:"NetOpen"
             Mode:Managed  Frequency:2.417 GHz  Access Point: 00:11:50:35:5F:A9
             Bit Rate=54 Mb/s   Tx-Power=20 dBm
             Retry limit:7   RTS thr:off   Fragment thr:off
             Power Management:off
             Link Quality=91/100  Signal level=-37 dBm  Noise level=-89 dBm
             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:0  Invalid misc:0   Missed beacon:0
    
   sit0      no wireless extensions.
   
```     
   iwlist output 
   ```

   $ iwlist scan
   lo        Interface doesn't support scanning.
    
   eth0      Interface doesn't support scanning.
    
   eth1      Scan completed :
             Cell 01 - Address: 00:11:50:35:5F:A9
                       ESSID:"NetOpen"
                       Protocol:IEEE 802.11g
                       Mode:Master
                       Channel:2
                       Encryption key:off
                       Bit Rate:54 Mb/s
                       Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                       Quality=89/100  Signal level=-40 dBm
                       Extra: Last beacon: 1292ms ago
    
   sit0      Interface doesn't support scanning.
   
```     
   route output 
    ```

   $ route -n
   Kernel IP routing table
   Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
   
```     
   ping when using DHCP
   ```

   $ ping 192.168.2.1
   connect: Network is unreachable
   
```     
   ping when using static IP
   ```

   $ ping 192.168.2.1
   PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
   From 192.168.2.2 icmp_seq=2 Destination Host Unreachable
   From 192.168.2.2 icmp_seq=3 Destination Host Unreachable
   From 192.168.2.2 icmp_seq=4 Destination Host Unreachable
    
   --- 192.168.2.1 ping statistics ---
   6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4999ms
   , pipe 3
   
```

---

### Post by ranf on 2005-11-22
What brand is your router?

I read on some other thread that some routers have probs with ipv6. Disabling ipv6 should resolve this.

---

### Post by ssalman on 2005-11-22
Thanks for your reply, ranf!

I have a Belkin 802.11G wirless router (model:F5D7230-4), and I think you are on to something, but could you please walk me through (or point me to a how-to) disabling IPV6 support, I would like to test it and see if it will help.

---

### Post by h3avyarms on 2005-11-22
I have the exact same router as you and I was having the same problem you are. I've got it fixed now but I'm unsure exactly what done it as I tried everything under the sun. The last thing I did was turn on WEP and set a password then rebooted and it was working.

---

### Post by ranf on 2005-11-22
[QUOTE=ssalman]
I have a Belkin 802.11G wirless router (model:F5D7230-4), and I think you are on to something, but could you please walk me through (or point me to a how-to) disabling IPV6 support, I would like to test it and see if it will help.[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=87798&highlight=%22disable+ipv6%22](http://ubuntuforums.org/showthread.php?t=87798&highlight=%22disable+ipv6%22)

And post if that helped.

---

### Post by ssalman on 2005-11-25
I tried turning off the IPV6 support, but it didn’t help. I had to reinstall Ubuntu to fix a separate problem (Grub started going crazy on me by getting stuck in an endless rebooting cycle). And this time I skipped the network setup during install, and when I finished the install and booted in Ubuntu, I setup the wireless network and it just worked!!! I have no idea what have happened, but it worked with just few steps, right out of the box.
    
   I guess this post is no help to anybody:(, I wish I had a better answer, but at least I can surf the net now! :cool:

---

