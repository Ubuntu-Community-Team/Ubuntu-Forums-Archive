---
title: "eth0: error fetching interface information: Device not found"
date: 2016-09-19
forum: Networking &amp; Wireless
---

### Post by andriin on 2016-09-19
Hi, I have had the Ubuntu OS on my laptop for almost 5 months now. Before it was always connected via wifi but recently i had gotten it switched over to an ethernet cable connection. This is where the problem starts. If i were to type in ifconfig i would see this 
```
enp1s0    Link encap:Ethernet  HWaddr 78:e3:b5:61:ca:3b  
          inet addr:192.168.1.244  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:ce05:58f0:9d51:481:fda7:2c2f/64 Scope:Global
          inet6 addr: fe80::70d5:8d4f:e089:3f2a/64 Scope:Link
          inet6 addr: 2602:306:ce05:58f0:8258:7e89:7fd2:4c05/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86911261 (86.9 MB)  TX bytes:4510686 (4.5 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:293596 (293.5 KB)  TX bytes:293596 (293.5 KB)

```
if i were to type in ifconfig eth0 i get this error:
eth0: error fetching interface information: Device not found

Now unfortunately i dont know what the problem is at all and i have spent about 2 hours trying every fix i can find or attempt to do on this but what is frustrating is that i can not get eth0 to be usable in the sense that the device is found and there is no error. I checked multiple times to see if it was my driver or if i was missing it but it is clearly there. Hopefully someone can tell me a fix to this problem

---

### Post by wildmanne39 on 2016-09-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by jeremy31 on 2016-09-20
Use enp1s0 instead of eth0 as this is the predictable naming scheme used in Ubuntu 16.04

---

### Post by JKyleOKC on 2016-09-20
jeremy31 gave you the right answer, but he didn't mention that you'll need to do this everywhere that you now have "eth0" in your configuration files. This name change of interfaces sent me right up the wall for almost a week before I finally comprehended what has happened. Fortunately, most configuration files do NOT mention the interface's name, so the correction isn't as tedious as it might sound.

---

### Post by jeremy31 on 2016-09-20
If someone needs to disable the renaming it can be done for PCI devices do ```
sudo -H gedit /etc/default/grub
```
Find the line that starts with GRUB_CMDLINE_LINUX_DEFAULT and add ```
net.ifnames=0
```
inside of the quotes, mine currently is ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash net.ifnames=0"
```
Then save the file, exit gedit
```
sudo update-grub
```
Reboot and the renaming is gone
If you need to disable renaming of USB wireless devices also do ```
sudo ln -s /dev/null /etc/udev/rules.d/80-net-setup-link.rules
``` before rebooting

---

