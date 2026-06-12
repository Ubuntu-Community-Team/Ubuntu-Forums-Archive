---
title: "Internet (ethernet) problems on fresh install desktop"
date: 2015-07-09
forum: Networking &amp; Wireless
---

### Post by Excuse_Me on 2015-07-09
I just installed ubuntu 15.04 and internet is not working. I've restarted 8 times and once or twice internet has worked for a few seconds so I could start a download in software center and go on google but then it stops working again. I have tried different cables no difference. My other computers are fine. I think it must be some software problem so I was looking to install my drivers for the motherboard but they are all exe files and I found some information saying that Ubuntu should automatically find my drivers or something? Anyone know what might be wrong? 

Thankful for any help..

---

### Post by ajgreeny on 2015-07-09
I have moved your thread to Networking and wireless where it fits a bit better and may get more answers.

Forget about drivers in the way that windows might need them; the Linux kernel normally provides all you need for an ethernet cable connection, and the fact that it works for a few seconds suggests that yours is working but for some reason disconnects.

Can you please open a terminal and run commands
```
cat /etc/network/interfaces
lspci
``` one by one and copy the output back here, in code tags please.

There's a Code-tags how-to in my signature below if you don't know how to do that.

---

### Post by Excuse_Me on 2015-07-09
> **ajgreeny said:**
> I have moved your thread to Networking and wireless where it fits a bit better and may get more answers.

Forget about drivers in the way that windows might need them; the Linux kernel normally provides all you need for an ethernet cable connection, and the fact that it works for a few seconds suggests that yours is working but for some reason disconnects.

Can you please open a terminal and run commands
```
cat /etc/network/interfaces
lspci
``` one by one and copy the output back here, in code tags please.

There's a Code-tags how-to in my signature below if you don't know how to do that.
Ok, great! 

```
[COLOR=#000000][FONT=Verdana]s@server:~$ cat /etc/network/interfaces[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]# interfaces(5) file used by ifup(8) and ifdown(8)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]auto lo[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]iface lo inet loopback[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]s@server:~$ lspci[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:02.0 VGA compatible controller: Intel Corporation 4th Generation Core Processor Family Integrated Graphics Controller (rev 06)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:1f.0 ISA bridge: Intel Corporation B85 Express LPC Controller (rev 05)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]03:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)[/FONT][/COLOR]
```

Just now I installed windows on the same computer and internet was working fine but I don't want windows so I installed ubuntu again but same problem..

---

### Post by Excuse_Me on 2015-07-09
It says that there's a connection but I can't access internet through software center or browser. Any ideas?

---

### Post by ajgreeny on 2015-07-09
Can you always ping your router?

If you click on the network icon in your panel and choose "Information" you will see a window pop up showing what your router (if you have a router) or your "Default route" is; something like 192.168.1.1.

In terminal again run command ```
ping -c 4 192.168.1.1
```using the number string from your Direct route to make sure you're connected to that, then try ```
ping -c 4 216.58.208.46
``` and finally try ```
ping -c 4 google.com
``` which is the same as the previous ping command but using the name instead of IP address.

If the final command is a failure we know that there is a DNS (Dynamic Name Server) problem and can try to figure out why and find a solution for you, but let's move one step at a time.

---

### Post by praseodym on 2015-07-10
See here:

[http://ubuntuforums.org/showthread.php?t=2280309&p=13295166#post13295166](http://ubuntuforums.org/showthread.php?t=2280309&p=13295166#post13295166)

Same card.

---

### Post by Excuse_Me on 2015-07-11
> **ajgreeny said:**
> Can you always ping your router?

If you click on the network icon in your panel and choose "Information" you will see a window pop up showing what your router (if you have a router) or your "Default route" is; something like 192.168.1.1.

In terminal again run command ```
ping -c 4 192.168.1.1
```using the number string from your Direct route to make sure you're connected to that, then try ```
ping -c 4 216.58.208.46
``` and finally try ```
ping -c 4 google.com
``` which is the same as the previous ping command but using the name instead of IP address.

If the final command is a failure we know that there is a DNS (Dynamic Name Server) problem and can try to figure out why and find a solution for you, but let's move one step at a time.

Ok, thank you for the help here is the output:

```
s@server:~$ ping -c 4 192.168.1.7
PING 192.168.1.7 (192.168.1.7) 56(84) bytes of data.
64 bytes from 192.168.1.7: icmp_seq=1 ttl=64 time=0.058 ms
64 bytes from 192.168.1.7: icmp_seq=2 ttl=64 time=0.029 ms
64 bytes from 192.168.1.7: icmp_seq=3 ttl=64 time=0.035 ms
64 bytes from 192.168.1.7: icmp_seq=4 ttl=64 time=0.037 ms


--- 192.168.1.7 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.029/0.039/0.058/0.013 ms



``````
s@server:~$ ping -c 4 216.58.208.46
connect: Network is unreachable



``````
s@server:~$ ping -c 4 google.com
connect: Network is unreachable



```

I guess maybe DNS problem?

> **praseodym said:**
> See here:

[http://ubuntuforums.org/showthread.php?t=2280309&p=13295166#post13295166](http://ubuntuforums.org/showthread.php?t=2280309&p=13295166#post13295166)

Same card.
Thank you! I have now tried following the steps I downloaded the two packages and unpacked both of them and ran all the commands 

```
cd ~/Downloads/
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
and rebooted but it is still not possible to browse the internet through firefox or software center or any other software requiring internet.

---

### Post by Excuse_Me on 2015-07-12
I've been googling on DNS problems. My "interfaces" file look like this

auto lo eth0
iface lo inet loopback

I don't know if it can help. Any ideas why internet isn't starting? It is latest version of ubuntu

---

### Post by Excuse_Me on 2015-07-12
i ended up installing an earlier version of ubuntu and it worked

---

