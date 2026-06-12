---
title: "hello, in Lenovo netbook (4 years old), in Windows 8.1 works the  WiFi in ubuntu late"
date: 2016-01-13
forum: Networking &amp; Wireless
---

### Post by spi2 on 2016-01-13
hello, in Lenovo netbook (4 years old), in Windows 8.1 works the  WiFi in ubuntu latest version not working, what can I do?

---

### Post by Bucky Ball on 2016-01-13
*Thread moved to **Networking & Wireless**.*

Welcome. Plug in an ethernet cable so you are online, open a terminal and put these commands in, one after the other hitting 'enter' after each. 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

You will be asked for your password. It will be invisible when you type it. That is normal.

Pull the ethernet cable out and reboot the machine. Any luck? If it works you should be notified of available networks. If not, please provide the output of this command:

```
sudo lshw -C network
```

---

### Post by spi2 on 2016-01-14
Hello, apology from my English...


I run 
sudo apt-get update
sudo apt-get dist-upgrade
I pull the ethernet cable out and I reboot, but nowhere is there WiFi..
I run 
sudo lshw -C network
and display 20-30 lines, but most important: 
Ethernet... 
Hardware Controller...
Nowhere is there WiFi...
What else can I do?

---

### Post by Bucky Ball on 2016-01-14
Please run:

```
sudo lshw -C network
```

... again and post the result between code tags, thanks. We can not help you with no information. What you've provided tells us nothing useful. ;)

See my signature link for how to create code tags.

---

### Post by spi2 on 2016-01-14
[LIST]
[*][INDENT]Hello,

I don't understand where is "See my signature link for how to create code tags." and "code tags" , I know what is WiFi and Nowhere is there WiFi, only Ethernet Controller...

thanks a lot...[/INDENT]

[*]
[LIST]
[*]

[*]
[/LIST]

[/LIST]

---

### Post by Hadaka on 2016-01-14
Hi, please open a terminal ctrl/alt/t then COPY and paste this command
```
 lspci -nnk | grep -iA2 net
```
copy the ENTIRE output..this means the ethernet information as well
then post the output with your reply.
thanks.

---

### Post by spi2 on 2016-01-15
hello,

```
eva@eva-fili:~$ sudo lspci -nnk | grep -iA2 net 
[sudo] password for eva: 
01:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: Lenovo Device [17aa:3805]
    Kernel driver in use: alx
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0611]
    Kernel driver in use: bcma-pci-bridge
eva@eva-fili:~$ 
```


and other PASTE

eva@eva-fili:~$ sudo lspci -nnk | grep -iA2 net 
[sudo] password for eva: 
01:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: Lenovo Device [17aa:3805]
    Kernel driver in use: alx
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0611]
    Kernel driver in use: bcma-pci-bridge
eva@eva-fili:~$ 
eva@eva-fili:~$ sudo lshw -C network
[sudo] password for eva: 
  *-network               
       description: Ethernet interface
       product: QCA8172 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 20:1a:06:99:47:0c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:81 memory:f0900000-f093ffff ioport:2000(size=128)
  *-network
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:36 memory:f0800000-f0807fff
eva@eva-fili:~$ 

thanks a lot, I wait for your answer...

---

### Post by Bucky Ball on 2016-01-15
> **Bucky Ball said:**
> post the result between code tags, thanks.

If you wouldn't mind. :) See the link in my signature at the bottom of this post for how to (I've done one block in your last post as an example).

---

### Post by Hadaka on 2016-01-15
Hi, please COPY and post the output of..
```
lsb_release -a
```
```
lsmod |egrep "b43|bcma|wl"
```
```
rfkill list all
```
*post the output of each command in code tags.
To use code tags..copy your output then click the **# symbol **on the reply page.center row
click the **#** and it will generate [ CODE] [ /CODE]
put your output between the codes ...^..
thanks

---

### Post by spi2 on 2016-01-15
hello,

I don't understand...

my English is not good and I have one hand...(brachial plexus)

PASTE one - one

1)
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

2)
bcma

3)
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

I wait for your answer...

thanks a lot...

---

### Post by Hadaka on 2016-01-15
Hi, from a working,connected wired connection please COPY
and paste one line at a time,Ignore any file not found or warning
error,this is sometimes normal. Copy and paste,one line at a time.
```
sudo modprobe -rf bcma
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
```
```
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo -e "blacklist b43\nblacklist ssb\nblacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
boot,disconnet wired connection,test wireless

---

### Post by spi2 on 2016-01-15
thanks a lot! WiFi on! after 1 year!:D

---

### Post by Hadaka on 2016-01-15
You are welcome,glad that worked for you.
Please mark your thread SOLVED by going to
your first post and clicking **TOOLS**
then choose **SOLVED**
thanks

---

