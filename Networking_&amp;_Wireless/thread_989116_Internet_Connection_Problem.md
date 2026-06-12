---
title: "Internet Connection Problem"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by jovigeorge on 2008-11-21
After installing Ubuntu, I am not able to connect to the internet. I am using a wired connection with a ADSL 2+ Modem.
Tried connecting using pon dsl provider but nothing happens. The output of lspci is as follows-
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139
Even tried to connect through my Motorolla E6. The system is detecting the phone but not connecting.
Please help me.

---

### Post by superprash2003 on 2008-11-21
post output of ifconfig.. which ISP are you connected to?

---

### Post by jovigeorge on 2008-11-22
The following is the output of ifcong-
jovi@jovi-desktop:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:66:16:ed:6c   
          inet6 addr: fe80::219:66ff:fe16:ed6c/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:300 (300.0 B)  TX bytes:2016 (2.0 KB) 
          Interrupt:22 Base address:0xb800  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB) 
I also tried pppoeconf. it detected eth0 & pan0 and after the scanning i got the following error - 
Sorry, I scanned 2 interfaces, but the Access            &#9474;  
          &#9474; Concentrator of your provider did not respond. Please    &#9474;  
          &#9474; check your network and modem cables. Another reason      &#9474;  
          &#9474; for the scan failure may also be another running pppoe   &#9474;  
          &#9474; process which controls the modem.   
My connection is Airtel Broadband connected throught Beetel ADSL2+ Modem model 220BX.
I dont have any problem in connecting through XP. (THe PC is dual boot)

---

### Post by madverb on 2008-11-22
Does the modem authenticate the connection with your ISP?

---

### Post by jovigeorge on 2008-11-22
> **madverb said:**
> Does the modem authenticate the connection with your ISP?

In XP i just switch on the modem and it gets connected. In Ubuntu no lick till now.

---

### Post by madverb on 2008-11-23
What is the modem brand and model?

---

### Post by jovigeorge on 2008-11-23
beetel 220bx. isp airtel

---

### Post by madverb on 2008-11-23
On the modem do you have a steady green light for the DATA/WAN connection?
Can you ping the modem?
```
ping 192.168.1.1
```
Basically you need an IP in the range of 192.168.1.2 - 192.168.1.254. It does seem like you aren't automatically receiving an IP from the modem. You could try manually setting up an IP in that range as follows:
```
sudo gedit /etc/network/interfaces
```
> iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
```
sudo gedit /etc/resolv.conf
```
> nameserver 192.168.1.1
```
sudo /etc/init.d/networking restart
```

---

### Post by jovigeorge on 2008-11-24
All the lights on the modem are on. Tried pinging and got the following message- ping &#8211; network unreachable
Tried sudo gedit /etc/network/interfaces. Got the following message -
** (gedit:5621): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.ZG18KU': No such file or directory 
I/O error : No such file or directory 

The following message was for sudo /etc/init.d/networking restart
jovi@jovi-desktop:~$ sudo /etc/int.d/networking restart 
sudo: /etc/int.d/networking: command not found

What should I do now?

---

### Post by superprash2003 on 2008-11-24
which ubuntu version are you running?

---

### Post by jovigeorge on 2008-11-24
8.10

---

### Post by madverb on 2008-11-25
> **jovigeorge said:**
> All the lights on the modem are on. Tried pinging and got the following message- ping – network unreachable
Tried sudo gedit /etc/network/interfaces. Got the following message -
** (gedit:5621): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.ZG18KU': No such file or directory 
I/O error : No such file or directory 

The following message was for sudo /etc/init.d/networking restart
jovi@jovi-desktop:~$ sudo /etc/int.d/networking restart 
sudo: /etc/int.d/networking: command not found

What should I do now?

That first error is unusual... what you could do is try
```
gksu nautilus
```
and browse to /etc/network and double click on the interfaces file.

The problem with the second one is that you did missed the "i" in init.d

---

### Post by jovigeorge on 2008-11-25
Errors and more errors. Thats all I get.
jovi@jovi-desktop:~$ gksu nautilus 
Initializing nautilus-share extension 
 
** (nautilus:5549): WARNING **: Unable to add monitor: Operation not supported 
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory 
Please ask your system administrator to enable user sharing. 
 
 
--- Hash table keys for warning below: 
--> file:///root 
 
(nautilus:5549): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above) 
 
(nautilus:5549): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time 
Shutting down nautilus-share extension 
seahorse nautilus module shutdown 

In the interface I got the error "could not display network:/// Nautilus cannot handle network locations.

I corrected the spelling of etc/init.d/networking restart and it restarted without any error message.
Can you please tell me why this is happening?

---

### Post by superprash2003 on 2008-11-25
from your ifconfig , it shows that you have an ip problem. you arent getting an ip. so follow this to setup a static ip so that you would be able to connect to the internet and in turn connect to 192.168.1.1 [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by madverb on 2008-11-26
That's some weird errors. Do you know how to use vim? You can use that instead of gedit in the previous guide I gave you.

---

### Post by jovigeorge on 2008-11-26
errors again. I was able to create the static IP as told by you.
When i tried the sudo /etc/init.d/networking restart, i got the following message - if down: interface eth0 not configured.
i am still getting the following error- 
jovi@jovi-desktop:~$ pon dsl provider connect 
The file /etc/ppp/peers/dsl does not exist. Please create it or use 
a command line argument to use another file in the /etc/ppp/peers/ directory. 
Any ideas?

---

### Post by madverb on 2008-11-27
You don't need to authorise to ppp... your modem does that.

In Windows it seems like you are receiving your IP from the modem automatically... but for some reason DHCP isn't working in Ubuntu. Maybe you could try reinstall DHCP client.

```
sudo apt-get purge dhcp-client
sudo apt-get install dhcp-client
```

---

### Post by jovigeorge on 2008-11-27
I got the following error- 
jovi@jovi-desktop:~$ sudo apt-get purge dhcp-client 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Package dhcp-client is not installed, so not removed 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
jovi@jovi-desktop:~$ sudo apt-get install dhcp-client 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Package dhcp-client is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 
E: Package dhcp-client has no installation candidate
In the Synaptic the DHCP client is shown as installed.

---

### Post by superprash2003 on 2008-11-28
after you made those changes to the interfaces file, could you please post the file here again..

---

