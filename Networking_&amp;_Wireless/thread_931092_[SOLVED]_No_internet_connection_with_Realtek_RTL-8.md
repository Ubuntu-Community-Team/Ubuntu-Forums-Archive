---
title: "[SOLVED] No internet connection with Realtek RTL-8139/810x family NIC"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by fidamehran on 2008-09-26
Dear All,
I have been facing the problem for quite some time now. The problem started after I changed my IP settings from DHCP to Static IP Setting.

At first my ISP had given me a Static IP address, then after a few days changed it to direct connection type (DHCP). I changed the setting myself from the Administration options (GUI). Then the ISP changed the address again to a Static IP address. But now as I changed the Network settings again, the internet connection does not work anymore. No Ping reply, no web page loading.. nothing.

I have a network card of "Realtek RTL-8139/810x family", and I dual boot with Windows XP.

I went through several forums and got suggestions like:

1. From inside Enable Wake-up-on-lan.

2. Keep network cable plugged in while logging in. Then shutdown, disconnect cable and power, wait for 15 sec and turn back power on.

3. Keep the power button pressed for several seconds when PC is off.

4. Through Terminal Turn Networking Off, Then Turn Networking On (commands were provided to put into Terminal).

Nothing worked.

What can I do?

---

### Post by fidamehran on 2008-09-28
I know you all have received such problems a lot, but I really don't know what to do. I am relatively new to Ubuntu and didn't have such problem before. Please can anybody help.. !!!???

---

### Post by superprash2003 on 2008-09-28
does it work currently in xp?are you setting the ips in the router or in the pc?

---

### Post by fidamehran on 2008-09-28
In XP, it works ok. No problems. I am setting the IP in my PC. I have an internet connection provided through a LAN connection. A LAN cable is all I got connected to my LAN card. No router.
Thanks again for replying.

---

### Post by superprash2003 on 2008-09-29
have you done an ifdown and ifup in the terminal or atleast rebooted?? in your terminal type ifconfig and post output here..

---

### Post by fidamehran on 2008-09-29
fida@fida-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:37:02:96:bf  
          inet6 addr: fe80::218:37ff:fe02:96bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17067 (16.6 KB)  TX bytes:468 (468.0 B)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84400 (82.4 KB)  TX bytes:84400 (82.4 KB)

fida@fida-desktop:~$

---

### Post by fidamehran on 2008-09-29
I'm not sure if I did ifup and ifdown. Reboot? If you are asking about PC reboot, yes, I did lots of times.

---

### Post by fidamehran on 2008-09-29
Is this page giving right instructions?
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")
My IP address, DNS address and others show okay in outputs. About the other outputs, I had no idea what they meant. Any suggestions on that?

---

### Post by Dotakon on 2008-09-29
I have the same card and till two weeks ago it was working better than in windows xp.
From then to now, i am not able to get connected to Internet and i do not find any solution for the moment.
I was not thinking that this would be a card problem, but after your post........
If i find any solution i will inform you.

---

### Post by puppywhacker on 2008-09-29
Hi,

strange provider, changing settings constantly, how can you keep up?

I have the same interface so I'll post step by step my settings. I think you only lost your ip-address settings in the interfaces file.

btw your 4 steps sound a lot like voodoo practices =) goodluck

```

bassie@sneezy:/$ lsmod | grep 8139
8139too                31104  0 
8139cp                 27776  0 
mii                     7552  2 8139too,8139cp
```

```

bassie@sneezy:/$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok
```

```

fida@fida-desktop:~$ cat /etc/network/interfaces
auto lo eth0
iface lo inet loopback

iface eth0 inet static
        address 88.222.174.68
        netmask 255.255.240.0
```

```

fida@fida-desktop:~$ sudo ifup eth0
```

```

fida@fida-desktop:~$ ifconfig eth0
```

---

### Post by fidamehran on 2008-09-29
Yeah, Voodoo indeed. I guess, your situation was a little better than mine. This is what my outputs say:

fida@fida-desktop:~$ lsmod | grep 8139 
8139too                27520  0  
8139cp                 24704  0  
mii                     6400  2 8139too,8139cp 
fida@fida-desktop:~$ sudo mii-tool eth0 
[sudo] password for fida:  
eth0: **autonegotiation failed,** link ok 
fida@fida-desktop:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
 
 
iface eth0 inet static 
address 172.16.4.5 
netmask 255.255.255.0 
gateway 172.16.1.3 
 
 
 
 
 
 
fida@fida-desktop:~$ sudo ifup eth0 
SIOCADDRT: **No such process** 
**Failed to bring up eth0.** 
fida@fida-desktop:~$ ifconfig eth0 
eth0      Link encap:Ethernet  HWaddr 00:18:37:02:96:bf   
          inet addr:172.16.4.5  Bcast:172.16.4.255  Mask:255.255.255.0 
          inet6 addr: fe80::218:37ff:fe02:96bf/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:850 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:82612 (80.6 KB)  TX bytes:3985 (3.8 KB) 
          Interrupt:20 Base address:0xe800  
 
fida@fida-desktop:~$  
 
--
P.S: However, the IP address, gateway and the Subnet Mask is showing ok here. That I changed through Manual Configuration of network.

---

### Post by fidamehran on 2008-09-29
Sorry for the badly aligned paragraphs. I have to log out of Windows and restart to Ubuntu everytime I get an instruction from you, do the stuffs, and copy-paste the outputs in a Word file, log out and restart into Windows XP to post you the outputs (coz there is no internet in my Ubuntu). :-(
Paragraphs get out of line through this process.

---

### Post by puppywhacker on 2008-09-29
AHA!

address 172.16.4.5
netmask 255.255.255.0

your ip-address and netmask combined say that your ip-address can reach all ip-address 172.16.4.* but the gateway is in a different subnet 

To reach 172.16.1.3 you need to use netmask 255.255.248.0

Alternatively you could temporarily make a new route, something like
sudo route add -host 172.16.1.3 gw 172.16.4.5

From the ifconfig you posted first didn't have an ip-address and now you do. So celebrate those little victories! That the "autonegotiation failed" is OK. it just means that the linespeed wasn't negotiated, but the ethernet link is still OK (you coul see that from the orange light at the back).

If it still wouldn't work you could show the route table and try to ping the gateway and look at the arp-cache to see which ip-addresses your computer already knows.

```

route
ping 172.16.1.3 -c 4
arp -a
route

```

P.S. I think your word copy/pasting is pretty resourceful.

---

### Post by fidamehran on 2008-09-29
First, A Big THANKS.
I am writing from Ubuntu.

"
route
ping 172.16.1.3 -c 4
arp -a
route"

gave:

fida@fida-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
fida@fida-desktop:~$ ping 172.16.1.3 -c 4
connect: Network is unreachable
fida@fida-desktop:~$ arp -a
fida@fida-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
"

Ok.

Then,
"sudo route add -host 172.16.1.3 gw 172.16.4.5"
gave:
fida@fida-desktop:~$ sudo route add -host 172.16.1.3 gw 172.16.4.5
[sudo] password for fida: 
SIOCADDRT: No such process

Then I changed the Subnet Mask (As soon as I read that in your post, I had a feeling, it was going to work.

Dear Friend, please tell me how the Subnet Mask thing was botching things up? What is a Subnet Mask and how did changing it solved the problem?

And why does the LAN card work in Windows when the Subnet Mask is wrong?

Thanks again and again.

---

### Post by Dotakon on 2008-09-29
Fixed. I have reseted the router and now it works. I do not know why it works now, but it does. Would be good to find out about the origin of the error...

---

