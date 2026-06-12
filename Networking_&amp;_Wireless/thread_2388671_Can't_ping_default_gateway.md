---
title: "Can't ping default gateway"
date: 2018-04-06
forum: Networking &amp; Wireless
---

### Post by datuttlejr on 2018-04-06
I'm slowly learning terminal but I can't figure out what is wrong here. I did a restart after some updates and now I can't reach the default gateway. I'm on my phone trying to figure out how to attach a picture of the screen to this.

---

### Post by wildmanne39 on 2018-04-06
Hello and welcome to the forums! You did not say if you are using wired or wireless connection? 

Please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created. 

Someone should be able to help after you post the information.

---

### Post by datuttlejr on 2018-04-06
[https://drive.google.com/file/d/1yNDE3E9WeBstrz5krk3HeRe3Hip0AJYOfQ/view?usp=drivesdk]("https://drive.google.com/file/d/1yNDE3E9WeBstrz5krk3HeRe3Hip0AJYOfQ/view?usp=drivesdk")

---

### Post by datuttlejr on 2018-04-06
Yes I'm using wireless

---

### Post by chili555 on 2018-04-06
How is it that the ethernet and the wireless both seem to be connected and that both have the *same* IP address?? No wonder your system is confused!

Where and how did you configure this? Surely the normal Network Manager didn't do this to you.

---

### Post by datuttlejr on 2018-04-08
[https://paste.ubuntu.com/p/Y8TYF5cfyQ/](https://paste.ubuntu.com/p/Y8TYF5cfyQ/)

This will help hopefully.

---

### Post by datuttlejr on 2018-04-08
Like I said, I've been playing with terminal while watching Eli the computer guy. Trying to learn but may have taken some foolish steps.

---

### Post by chili555 on 2018-04-09
It appears that you let Network Manager connect the wireless and then set up /etc/network/interfaces for the ethernet. First of all, your file contains a bit of un-necessary entries and omits one that is vital. Thanks, Eli!

First, you cannot have two interfaces connected at the same time with the exact same address. Your router is, undoubtedly, rejecting both. If you want to set a static IP address for the ethernet, select an address outside the DHCP pool in the router. Please check here: [https://www.voipmechanic.com/dlink_pics/dlink-airwireless1.jpg](https://www.voipmechanic.com/dlink_pics/dlink-airwireless1.jpg)  In this example, the router will assign DHCP addresses from x.100 to x.199. If you wanted to use a static IP in this router, an address outside this range, say x.50, would work well.

If you have administrative privileges for this router, have a look in the administration pages and see what the DHCP range is; select an address outside it.

If you do not have administrative privileges for this router, you'll have to guess. I'd probably use x.150.

I suggest that you revise /etc/network/interfaces to something like:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.150
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8

```Now click the Network Manager icon and ask the wireless to disconnect. Next:

```
sudo ifdown eth0 && sudo ifup -v eth0
```

Did you connect?

```
ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by datuttlejr on 2018-04-09
I changed my file like you asked. Then I disconnected, copy and pasted the command you said to run, reconnected but still can't ping.

Yes I have admin rights on my router so I changed DHCP to use just .2 - .50. Then I set static to 51.

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


#The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.51
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8

---

### Post by chili555 on 2018-04-09
>  #The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.51
netmask 255.255.255.0
[COLOR="#FF0000"]network 192.168.0.1
broadcast 192.168.0.255[/COLOR]
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8   But that is not what I suggested. Please try again.

Are there any clues here?```
dmesg | grep eth
```

---

### Post by datuttlejr on 2018-04-10
I made the changes to the interface folder to exactly what you suggested. I have a question though. You have me changing the eth0 connection and I believe the issue is with my wlan0 connection?

I ran the other code you asked:

```
dennis@juniors-laptop:~$ dmesg | grep eth
[    0.405983] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.406598] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.515711] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.552081] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0xffffc90000ca2000, 68:f7:28:76:c1:94, XID 10900800 IRQ 35
[    1.552088] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   37.455996] r8169 0000:02:00.0 eth0: link down
[   37.456156] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.457843] r8169 0000:02:00.0 eth0: link down
[   37.517551] promethean: loading out-of-tree module taints kernel.
[   37.517639] promethean: module verification failed: signature and/or required key missing - tainting kernel
[   37.518078] usbcore: registered new interface driver Promethean ActivDriver
[   44.035460] r8169 0000:02:00.0 eth0: link up
[   44.035479] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[32639.532867] r8169 0000:02:00.0 eth0: link down
[32697.413110] r8169 0000:02:00.0 eth0: link down
[32697.413374] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[32754.214789] r8169 0000:02:00.0 eth0: link up
[32754.214818] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[34199.420435] r8169 0000:02:00.0 eth0: link down
[34612.560018] r8169 0000:02:00.0 eth0: link up
[34861.281599] r8169 0000:02:00.0 eth0: link down
[34861.281628] r8169 0000:02:00.0 eth0: link down
[34861.282329] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[34867.663932] r8169 0000:02:00.0 eth0: link up
[34867.663967] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[35016.707768] r8169 0000:02:00.0 eth0: link down
[35057.000408] r8169 0000:02:00.0 eth0: link up
```

---

### Post by datuttlejr on 2018-04-10
I have another thing to add. I connected to a different wifi and everything worked well there, so it seems just to be my home wifi....

---

### Post by wildmanne39 on 2018-04-10
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chili555 on 2018-04-10
> You have me changing the eth0 connection and I believe the issue is with my wlan0 connection?
Yes, indeed. I wanted to get the ethernet away from the same IP address that the router gave out for the wireless. Now that it is, evidently, fixed, let's proceed. Please detach the ethernet cable, activate the wireless and run: ```
iwconfig
```Does it show an SSID, namely your router? Next, run:```
route -n
```What is the IP address associated with your wireless, wlan0? Is it 192.168.0.1? What is the exact reply when you try to ping it?```
ping -c3 192.168.0.1
```How about these?```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```In all cases, we need to see the exact response from the terminal, not just 'it didn't work.'

---

### Post by datuttlejr on 2018-04-10
```
dennis@juniors-laptop:~$ iwconfig

lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Northwood RV"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 14:AB:F0:53:E5:F0   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0


eth0      no wireless extensions.


dennis@juniors-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0
dennis@juniors-laptop:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.51 icmp_seq=1 Destination Host Unreachable
From 192.168.0.51 icmp_seq=2 Destination Host Unreachable
From 192.168.0.51 icmp_seq=3 Destination Host Unreachable


--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2001ms
pipe 3
dennis@juniors-laptop:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.51 icmp_seq=1 Destination Host Unreachable
From 192.168.0.51 icmp_seq=2 Destination Host Unreachable
From 192.168.0.51 icmp_seq=3 Destination Host Unreachable


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2007ms
pipe 2
dennis@juniors-laptop:~$ ping -c3 www.ubuntu.com
ping: unknown host www.ubuntu.com
dennis@juniors-laptop:~$ 
```

I see an ESSID, is that the same thing as an SSID? I know I'm very new at this and hope I am responding correctly and thank you for your time and effort.

---

### Post by datuttlejr on 2018-04-10
I just had an epiphany that I should have seen MUCH earlier. When I log onto my router for admin purposes, I always used a bookmark and didn't notice that the address is: 192.168.100.1:8080/?wifi_basic

I have enclosed my LAN settings page to show settings there...

:confused: And I wonder why my system is confused..... I think it is mainly operator error.


[IMG]https://drive.google.com/file/d/1EGOkx2TysW41qxL5_NyiPjKPTmFvoRhx/view?usp=sharing[/IMG][IMG]https://drive.google.com/file/d/1EGOkx2TysW41qxL5_NyiPjKPTmFvoRhx/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/1EGOkx2TysW41qxL5_NyiPjKPTmFvoRhx/view?usp=sharing](https://drive.google.com/file/d/1EGOkx2TysW41qxL5_NyiPjKPTmFvoRhx/view?usp=sharing)

---

### Post by chili555 on 2018-04-10
Are other devices on the network, iPads, phones, etc., able to connect? What IP address do they show once connected?> 
the address is: 192.168.[COLOR="#FF0000"]100[/COLOR].1:8080/?wifi_basic

Very confusing indeed.

---

### Post by datuttlejr on 2018-04-10
Here is a copy of my phone screenshot:

[Screenshot]("https://drive.google.com/file/d/0B93TZGAzG2pQZ243cmdnTjJRODdxaUU3RkFZTHl6THhPcWNB/view?usp=sharing")

and iPad:

[iPad]("https://drive.google.com/open?id=0B93TZGAzG2pQMlRpdEtUa1B2RlM4VXJ0Wl9OSm45dEFLUkxj")

---

### Post by chili555 on 2018-04-10
> **datuttlejr said:**
> Here is a copy of my phone screenshot:

[Screenshot]("https://drive.google.com/file/d/0B93TZGAzG2pQZ243cmdnTjJRODdxaUU3RkFZTHl6THhPcWNB/view?usp=sharing")

and iPad:

[iPad]("https://drive.google.com/open?id=0B93TZGAzG2pQMlRpdEtUa1B2RlM4VXJ0Wl9OSm45dEFLUkxj")Both in the 192.168.0.1 network. If you put 192.168.0.1 in your browser address bar, do you reach the router setup page?

Did you configure wireless in Network Manager as a static IP address or just DHCP, therefore letting NM and the router do all the work?

[https://i.stack.imgur.com/5wZ09.png](https://i.stack.imgur.com/5wZ09.png)

May we see:```
dmesg | grep wlan
```

---

### Post by datuttlejr on 2018-04-10
> **chili555 said:**
> Both in the 192.168.0.1 network. If you put 192.168.0.1 in your browser address bar, do you reach the router setup page?

Did you configure wireless in Network Manager as a static IP address or just DHCP, therefore letting NM and the router do all the work?

[https://i.stack.imgur.com/5wZ09.png](https://i.stack.imgur.com/5wZ09.png)

May we see:```
dmesg | grep wlan
```

Yes I do reach the router setup page at 192.168.0.1

I'm not 100% sure how I set it up.  Here are my versions of the pictures you sent though. 

[General]("https://drive.google.com/open?id=1mQ_7NXe8Fm4o_i6PF24MC0qg6N-uuhrp")

[IPv4]("https://drive.google.com/open?id=1U5Ysr4Ah7c1aEeM0PRBtEhj-gI85keZX")

[IPv6]("https://drive.google.com/open?id=1U5Ysr4Ah7c1aEeM0PRBtEhj-gI85keZX")

```
dennis@juniors-laptop:~$ dmesg | grep wlan[   44.440849] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.452811] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.521671] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  498.988824] wlan0: authenticate with 14:ab:f0:53:e5:f0
[  499.005869] wlan0: send auth to 14:ab:f0:53:e5:f0 (try 1/3)
[  499.007867] wlan0: authenticated
[  499.011865] wlan0: associate with 14:ab:f0:53:e5:f0 (try 1/3)
[  499.028324] wlan0: RX AssocResp from 14:ab:f0:53:e5:f0 (capab=0xc11 status=0 aid=5)
[  499.028440] wlan0: associated
[  499.028468] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[34062.657705] wlan0: deauthenticating from 14:ab:f0:53:e5:f0 by local choice (Reason: 3=DEAUTH_LEAVING)
[34063.528948] wlan0: authenticate with d8:b6:b7:d4:d8:50
[34063.545894] wlan0: send auth to d8:b6:b7:d4:d8:50 (try 1/3)
[34063.547858] wlan0: authenticated
[34063.551987] wlan0: associate with d8:b6:b7:d4:d8:50 (try 1/3)
[34063.555529] wlan0: RX AssocResp from d8:b6:b7:d4:d8:50 (capab=0x411 status=0 aid=2)
[34063.555630] wlan0: associated
[34400.950327] wlan0: deauthenticating from d8:b6:b7:d4:d8:50 by local choice (Reason: 3=DEAUTH_LEAVING)
[34415.949539] wlan0: authenticate with 14:ab:f0:53:e5:f0
[34415.966973] wlan0: send auth to 14:ab:f0:53:e5:f0 (try 1/3)
[34415.969051] wlan0: authenticated
[34415.972459] wlan0: associate with 14:ab:f0:53:e5:f0 (try 1/3)
[34415.988786] wlan0: RX AssocResp from 14:ab:f0:53:e5:f0 (capab=0xc11 status=0 aid=5)
[34415.988888] wlan0: associated
[34844.579181] wlan0: deauthenticating from 14:ab:f0:53:e5:f0 by local choice (Reason: 3=DEAUTH_LEAVING)
[34957.291768] wlan0: authenticate with 14:ab:f0:53:e5:f0
[34957.308479] wlan0: send auth to 14:ab:f0:53:e5:f0 (try 1/3)
[34957.310567] wlan0: authenticated
[34957.314310] wlan0: associate with 14:ab:f0:53:e5:f0 (try 1/3)
[34957.330991] wlan0: RX AssocResp from 14:ab:f0:53:e5:f0 (capab=0xc11 status=0 aid=5)
[34957.331092] wlan0: associated
[49338.037670] wlan0: authenticate with 14:ab:f0:53:e5:f0
[49338.053739] wlan0: send auth to 14:ab:f0:53:e5:f0 (try 1/3)
[49338.055696] wlan0: authenticated
[49338.059516] wlan0: associate with 14:ab:f0:53:e5:f0 (try 1/3)
[49338.075807] wlan0: RX AssocResp from 14:ab:f0:53:e5:f0 (capab=0xc11 status=0 aid=4)
[49338.075920] wlan0: associated
[49805.234279] wlan0: deauthenticating from 14:ab:f0:53:e5:f0 by local choice (Reason: 3=DEAUTH_LEAVING)
[49806.133257] wlan0: authenticate with 14:ab:f0:53:e5:f0
[49806.150088] wlan0: send auth to 14:ab:f0:53:e5:f0 (try 1/3)
[49806.154044] wlan0: authenticated
[49806.155643] wlan0: associate with 14:ab:f0:53:e5:f0 (try 1/3)
[49806.171990] wlan0: RX AssocResp from 14:ab:f0:53:e5:f0 (capab=0xc11 status=0 aid=4)
[49806.172088] wlan0: associated
[70887.591331] wlan0: deauthenticating from 14:ab:f0:53:e5:f0 by local choice (Reason: 3=DEAUTH_LEAVING)
[70894.913893] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[70894.929393] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[70895.075539] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[70896.790350] wlan0: authenticate with 14:ab:f0:53:e5:f0
[70896.806774] wlan0: send auth to 14:ab:f0:53:e5:f0 (try 1/3)
[70896.808743] wlan0: authenticated
[70896.812710] wlan0: associate with 14:ab:f0:53:e5:f0 (try 1/3)
[70896.829011] wlan0: RX AssocResp from 14:ab:f0:53:e5:f0 (capab=0xc11 status=0 aid=4)
[70896.829116] wlan0: associated
[70896.829212] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
dennis@juniors-laptop:~$
```

---

### Post by chili555 on 2018-04-10
Your settings in Network Manager appear correct.

We see this in the log:> [  498.988824] wlan0: authenticate with 14:ab:f0:53:e5:f0
[  499.005869] wlan0: send auth to 14:ab:f0:53:e5:f0 (try 1/3)
[  499.007867] wlan0: authenticated
[  499.011865] wlan0: associate with 14:ab:f0:53:e5:f0 (try 1/3)
[  499.028324] wlan0: RX AssocResp from 14:ab:f0:53:e5:f0 (capab=0xc11 status=0 aid=5)
[  499.028440] wlan0: associated
[  499.028468] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[34062.657705] wlan0: deauthenticating from 14:ab:f0:53:e5:f0 by local choice (Reason: 3=DEAUTH_LEAVING)At timestamp 499 it connected and all appears perfectly normal. At timestamp 34062, roughly 23 hours later, it is disconnected. It appears that, for at least that time, you had a connection.

Let's try a few things.> Yes I have admin rights on my routerWe have seen a few cases in this and other Ubuntu Q&A sites where a space in the name of the SSID was not helpful. Please try changing the name from Northwood RV to NorthwoodRV or Northwood_RV or some such, without a space in the name.

Now lets remove the old connection:

```
sudo rm /etc/NetworkManager/system-connections/Northwood*
```And reboot.

You should see the renamed network and be challenged for the WPA2 password. Did you connect? How about:```
ping -c3 192.168.0.1
```

---

### Post by datuttlejr on 2018-04-10
I did all you asked and restarted my computer. 

```
dennis@juniors-laptop:~$ ping -c3 192.168.0.1PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.


--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms


dennis@juniors-laptop:~$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"NorthwoodRV"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 14:AB:F0:53:E5:F0   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:58   Missed beacon:0


eth0      no wireless extensions.

```

---

### Post by chili555 on 2018-04-10
One last thing before I give up my computer and go back to the third grade:```
ip addr show
```

---

### Post by datuttlejr on 2018-04-10
```
dennis@juniors-laptop:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 68:f7:28:76:c1:94 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.51/24 brd 192.168.0.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::6af7:28ff:fe76:c194/64 scope link 
       valid_lft forever preferred_lft forever
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether ac:e0:10:17:79:b5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.7/24 brd 192.168.0.255 scope global dynamic wlan0
       valid_lft 3032sec preferred_lft 3032sec
    inet6 fe80::6cd2:43e8:d56c:c73b/64 scope link 
       valid_lft forever preferred_lft forever
dennis@juniors-laptop:~$ 



```

---

### Post by chili555 on 2018-04-10
This is the weirdest problem I've faced so far this week!!! You have both ethernet and wireless connected and still can't ping!

Please download this file on some other computer: [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)  Transfer it on a USB drive or similar to the Ubuntu computer. Drag and drop it to the desktop. Now, in the terminal:

```
cd  ~/Desktop
chmod +x wireless-info
./wireless-info

```It will produce a big report named wireless-info.txt. Transfer it to the USB and, on another computer, paste it here and give us the link: [http://paste.ubuntu.com](http://paste.ubuntu.com)

We hope we will spot the problem and suggest the fix from the data.

---

### Post by datuttlejr on 2018-04-10
I have a confession..... I can ping with eth0 with wire hooked up. I was disconnecting to test wireless.....

```

dennis@juniors-laptop:~/Desktop$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.17 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.19 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.782 ms


--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.782/1.050/1.190/0.191 ms
dennis@juniors-laptop:~/Desktop$ 

```

---

### Post by datuttlejr on 2018-04-10
[http://paste.ubuntu.com/p/pn47wR6bzm/](http://paste.ubuntu.com/p/pn47wR6bzm/)

---

### Post by chili555 on 2018-04-10
> I have a confession..... I can ping with eth0 with wire hooked up. I was disconnecting to test wireless.....
And then did you reboot? I wonder if ping is attempting to use the now unavailable ethernet. 

So far, I see nothing unusual in your data.

---

### Post by datuttlejr on 2018-04-10
I did reboot. why is ethernet unavailable? I plugged it back in.

---

### Post by chili555 on 2018-04-10
> **datuttlejr said:**
> I did reboot. why is ethernet unavailable? I plugged it back in.Why???

Why do you need both? Please detach the ethernet, leave it detached, reboot, still leaving it detached. Detach.

Connect with wireless. Can you ping detached?

---

### Post by datuttlejr on 2018-04-10
I need both because it is the only computer I have and I cannot respond when I detach the ethernet. I suppose I can respond simply with my phone.... OR connect via the other wireless I can attach to and respond.

---

### Post by datuttlejr on 2018-04-10
> **chili555 said:**
> Why???

Why do you need both? Please detach the ethernet, leave it detached, reboot, still leaving it detached. Detach.

Connect with wireless. Can you ping detached?

I need both to respond here. I did detach and rebooted. 

I connected to NorthwoodRV. I could not ping.

I connected to fairpoint07904 and had these results:

```

dennis@juniors-laptop:~/Desktop$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=11.4 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.20 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.32 ms


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.206/4.669/11.480/4.816 ms
dennis@juniors-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"fairpoint07904"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: D8:B6:B7:D4:D8:50   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:101   Missed beacon:0


eth0      no wireless extensions.


dennis@juniors-laptop:~/Desktop$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.51 icmp_seq=1 Destination Host Unreachable
From 192.168.0.51 icmp_seq=2 Destination Host Unreachable
From 192.168.0.51 icmp_seq=3 Destination Host Unreachable


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
pipe 3
dennis@juniors-laptop:~/Desktop$ 

```

Then I reconnected eth0 so I could respond easier. So right now I am connected to NorthwoodRV via cable and fairpoint07904 via wireless.

---

### Post by chili555 on 2018-04-10
> dennis@juniors-laptop:~/Desktop$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From [COLOR="#FF0000"]192.168.0.51[/COLOR] icmp_seq=1 Destination Host Unreachable
From 192.168.0.51 icmp_seq=2 Destination Host Unreachable
From 192.168.0.51 icmp_seq=3 Destination Host UnreachableThat is the IP address of the ethernet.

> #The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.51
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1 8.8.8.8

We are, once again, unable to pin down the wireless.

I am not sure how I can help you if you, again, reject my suggestions.

---

### Post by datuttlejr on 2018-04-10
> **chili555 said:**
> That is the IP address of the ethernet.



We are, once again, unable to pin down the wireless.

I am not sure how I can help you if you, again, **reject my suggestions**.

I am trying my best to follow your instructions. I'm sorry if it sounds like I am not. 

I detached the eth0. I rebooted and I ran the following. my LAN cable was not connected and I ran these.

```
dennis@juniors-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 68:f7:28:76:c1:94  
          inet addr:192.168.0.51  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:18598 (18.5 KB)  TX bytes:18598 (18.5 KB)


wlan0     Link encap:Ethernet  HWaddr ac:e0:10:17:79:b5  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6cd2:43e8:d56c:c73b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9599 (9.5 KB)  TX bytes:22044 (22.0 KB)


dennis@juniors-laptop:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.51 icmp_seq=1 Destination Host Unreachable
From 192.168.0.51 icmp_seq=2 Destination Host Unreachable
From 192.168.0.51 icmp_seq=3 Destination Host Unreachable


--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2008ms
pipe 2
dennis@juniors-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 68:f7:28:76:c1:94  
          inet addr:192.168.0.51  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:32390 (32.3 KB)  TX bytes:32390 (32.3 KB)


wlan0     Link encap:Ethernet  HWaddr ac:e0:10:17:79:b5  
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f0ac:b6f:7126:5210/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16204 (16.2 KB)  TX bytes:33284 (33.2 KB)


dennis@juniors-laptop:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.01 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.70 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.75 ms


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.709/2.159/3.017/0.608 ms
dennis@juniors-laptop:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
From 192.168.0.51 icmp_seq=1 Destination Host Unreachable
From 192.168.0.51 icmp_seq=2 Destination Host Unreachable
From 192.168.0.51 icmp_seq=3 Destination Host Unreachable


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2009ms
pipe 2
dennis@juniors-laptop:~$ 
```

Again the LAN cable was not connected. 

I then reconnected the LAN to be able to post to this forum.

---

### Post by datuttlejr on 2018-04-10
I connected to NorthwoodRV. I can't ping 192.168.0.1 while connected

I connected to fairpoint07904. I **can** ping 192.168.1.1 while connected to it but can't ping 8.8.8.8

---

### Post by chili555 on 2018-04-12
First of all, as I have tried to suggest, it is not at all helpful to have both wireless and ethernet connected at the same time as we run tests. If ping fails, then we haven’t any idea whether the issue is isolated to wireless or ethernet or both.

As we are making tests from now on, detach the ethernet, reboot and run, in the terminal:```
 sudo ifdown eth0 
``` Run the tests that are requested and capture the terminal output by highlighting it, selecting ‘copy’ and then paste it into any text document like text editor or even LibreOffice. Then, after you reconnect with ethernet, copy and paste the text you saved in the text document into your forum reply.

First, please confirm that you *are* able to ping and access the internet with ethernet. Please confirm that, even though you appear to be connected with wireless, after the reboot process I described above, you are *NOT* able to ping and access the internet with wireless.

Please reboot, as above, and show us:

```
iwconfig
route -n
ping -c3 8.8.8.8
sudo ufw status verbose
sudo dpkg-reconfigure resolvconf

```When you re-attach the ethernet to reply, you will need to do:  ```
sudo ifup eth0
```
I look forward to your results.

---

### Post by datuttlejr on 2018-04-12
[QUOTE][COLOR=#000000]First of all, as I have tried to suggest, it is not at all helpful to have both wireless and ethernet connected at the same time as we run tests.[[/COLOR]/QUOTE]

I'm sorry for my inexperience. I thought unplugging and rebooting was enough. I wasn't grasping the concept yet that I had to disable the eth0. If I had known this we might have got done quicker.:redface:

April 12 6:15 pm

Yes I was able to ping and use internet with ethernet but could not when I unplugged it.


Unplugged cable
reboot


```
dennis@juniors-laptop:~$ sudo ifdown eth0


	ifdown: waiting for lock on /run/network/ifstate.eth0
	Killed old client process
	Internet Systems Consortium DHCP Client 4.3.3
	Copyright 2004-2015 Internet Systems Consortium.
	All rights reserved.
	For info, please visit https://www.isc.org/software/dhcp/


	Listening on LPF/eth0/68:f7:28:76:c1:94
	Sending on   LPF/eth0/68:f7:28:76:c1:94
	Sending on   Socket/fallback
	DHCPRELEASE on eth0 to 192.168.0.1 port 67 (xid=0x2b618608)



```

AHA!! this was different and it took several minutes time to do it.

Then the ping tests you asked for:

```
dennis@juniors-laptop:~$ ping -c3 192.168.0.1	PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
	64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.44 ms
	64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.29 ms
	64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.38 ms
	
	--- 192.168.0.1 ping statistics ---
	3 packets transmitted, 3 received, 0% packet loss, time 2003ms
	rtt min/avg/max/mdev = 1.299/1.377/1.445/0.060 ms


dennis@juniors-laptop:~$ ping -c3 8.8.8.8
	PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
	64 bytes from 8.8.8.8: icmp_seq=1 ttl=57 time=19.2 ms
	64 bytes from 8.8.8.8: icmp_seq=2 ttl=57 time=20.3 ms
	64 bytes from 8.8.8.8: icmp_seq=3 ttl=57 time=19.7 ms
	
	--- 8.8.8.8 ping statistics ---
	3 packets transmitted, 3 received, 0% packet loss, time 2003ms
	rtt min/avg/max/mdev = 19.205/19.797/20.392/0.484 ms
```

OMG It worked. I could use access the internet as well.

However I continued with your instructions because I'm trying to show you I am trying to follow your instructions.

```
dennis@juniors-laptop:~$ iwconfiglo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"NorthwoodRV"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 14:AB:F0:53:E5:F0   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-21 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0


eth0      no wireless extensions.


dennis@juniors-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0
dennis@juniors-laptop:~$ sudo ufw status verbose
[sudo] password for dennis: 
Status: inactive
dennis@juniors-laptop:~$ sudo dpkg-reconfigure resolvconf
dennis@juniors-laptop:~$ 
```

It gave me a warning about making new file and replacing old. 
I said yes since you told me to run this command plus it said if I replied no, it wouldn't do it again.
Then it told me I needed to reboot. So I did.

I am responding to you now via wireless. I have not turned on last command yet.
```
sudo ifup eth0
```

Should I run this? Or do you have different instructions?

---

### Post by chili555 on 2018-04-12
It appears that the issue is fixed and very likely caused by the confusion in the system which was evidently trying to ping through the ethernet which was detached but not 'downed.' > Should I run this? Or do you have different instructions?Only run it if you wish to disconnect the wireless at the Network Manager icon and then use ethernet.

Frankly, the best way to dynamically switch between the two is Network Manager. I'd probably remove all the eth0 settings from /etc/network/interfaces and rely on NM alone. Moreover, I see from your paste that you travel quite a bit and connect to many different networks. In that instance, I'd just use wireless, even at home. I do.

---

### Post by datuttlejr on 2018-04-12
Thanks for your help. What started all these changes was my traveling. When I am in the Middle East there are a lot of restrictions on internet. I was trying to learn how to set up a server here at my house so that I could VPN through it. 

Also maybe set up my own web server. I know I need a dedicated computer to do these things but I was just in the learning stages.......

I have a LONG way to go.

---

### Post by chili555 on 2018-04-12
Glad it's working.

---

