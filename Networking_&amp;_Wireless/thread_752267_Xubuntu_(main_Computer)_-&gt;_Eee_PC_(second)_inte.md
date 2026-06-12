---
title: "Xubuntu (main Computer) -&gt; Eee PC (second) internet connection LAN"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by alphajean@gmail.com on 2008-04-11
Today bought Eee PC.

On the main computer I have Xubuntu OS.
How should I connect my new Eee PC to the internet via main computer?

Please HELP

---

### Post by alphajean@gmail.com on 2008-04-11
Please help.

---

### Post by superprash2003 on 2008-04-11
you need to have two ethernet cards on the main computer for this .. then follow the ICS=internet connection sharing guide.. like this one [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by alphajean@gmail.com on 2008-04-11
what is “ifconfig” ? 

There written:
You should setup your second Ethernet wired or wireless card and set its IP address to something like “192.168.10.1&#8243; via “ifconfig” utility as follows:
$ ifconfig eth1 192.168.10.1 netmask 255.255.255.0

---

### Post by alphajean@gmail.com on 2008-04-11
should I copy ifconfig to terminal and press OK?

---

### Post by alphajean@gmail.com on 2008-04-11
I writed lnconfig in terminal and pressed Enter. Result is:

eth0      Link encap:Ethernet  HWaddr 00:50:04:0F:71:D5  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33088 (32.3 KB)  TX bytes:13994 (13.6 KB)
          Interrupt:10 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0D:87:B8:CD:32  
          inet addr:78.84.247.117  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::20d:87ff:feb8:cd32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204422914 (194.9 MB)  TX bytes:7797950 (7.4 MB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22286 (21.7 KB)  TX bytes:22286 (21.7 KB)

---

### Post by alphajean@gmail.com on 2008-04-11
friends, what should i do next?

---

### Post by alphajean@gmail.com on 2008-04-11
superprash2003,

I have two internet cards in main pc and one in Eee pc, everything is fine in hardware, but I'm new in Linux.
Please, help me.

Step by step. Please.

---

### Post by Iowan on 2008-04-11
First, be patient - sometimes it takes more than 10 minutes to get a response.  Then, it looks like **eth1** is being interpreted as the internet connection.  > ifconfig eth0 192.168.10.1 netmask 255.255.255.0  Personally, I'd prefer to edit the**/etc/network/interfaces** file..  How is the eeePC configured?  If it defaults to DHCP, it may need some tweaking, too.

---

### Post by alphajean@gmail.com on 2008-04-11
When I configure Eee pc there written:

Select type of address your computer will use to identify itself on the LAN:
1) Dynamic IP address (DHCP) (default)
2) Static IP address

What should I chose? What did you mean how eee pc is configured? Configuration is:


	ASUS Notebook
ASUS Eee PC
Display 7"
CPU & Chipset Intel Mobile CPU & chipset
Operating System Linux System/ Hardware Compatible with Windows XP
Communication 10/100 Mbps Ethernet
WLAN WiFi 802.11b/g
Memory 512MB, DDR2
Storage-Flash 4GB
Web-Cam 0.3 Mega Pixel Video camera
Audio Hi-Definition audio CODEC, Built-in stereo speaker, Built-in microphone
Battery Life 3.5 hrs (4 cells 2.6Ah)
IO ports "3x USB 2.0
1x VGA
1x SD/MMC card reader
1x Audio in
1x Audio out"
Dimension & Net Weight 22.5 x 16.4 x 2.15~3.5 cm, <1 kg

---

### Post by alphajean@gmail.com on 2008-04-11
I open file etc/network/interfaces

Text in the file is:

auto lo
iface lo inet loopback

---

### Post by alphajean@gmail.com on 2008-04-11
As I understood, I should open file etc/networks/interfaces

Then I should delete all the strings and write in this file:

# The extended interfaces
auto eth1
iface eth1 inet static
address 78.84.247.117
netmask 255.255.224.0

And then I should:
Check if the previous command worked by typing the following:
$ ifconfig

Am I right?

---

### Post by Iowan on 2008-04-11
Leave these:```
auto lo
iface lo inet loopback 
```

Also, to edit you *might* need **sudo**:```
sudo nano /etc/network/interfaces
``` and you will probably need to restart networking.

---

### Post by alphajean@gmail.com on 2008-04-11
Ok, now I have in terminal as follows
auto lo
iface lo inet loopback

# The extended interfaces
auto eth1
iface eth1 inet static
address 78.84.247.117
netmask 255.255.224.0


 question is HOW to save? What combination of keys?


^G Ieg&#363;t Pal&#299;^O WriteOut  ^R Read File ^Y Iepriekš&#275;j^K Cut Text  ^C Cur Pos
^X Iziet     ^J Justify   ^W Where Is  ^V N&#257;kam&#257; lap^U UnCut Text^T To Spell

---

### Post by Iowan on 2008-04-11
> ^O WriteOut
That's CRTL-O (letter, not zero)

But, I wonder if **eth1** needed the edit - **eth0** is the one without an IP address...

---

### Post by alphajean@gmail.com on 2008-04-11
...

---

### Post by alphajean@gmail.com on 2008-04-11
...

---

### Post by alphajean@gmail.com on 2008-04-11
...

---

### Post by alphajean@gmail.com on 2008-04-11
...

---

### Post by alphajean@gmail.com on 2008-04-11
....

---

### Post by alphajean@gmail.com on 2008-04-11
YES!!! At last. This thing is work.

In terminal I wrote:
su
password
sudo nano /etc/network/interfaces

Then I add this text:

auto lo
iface lo inet loopback

# The extended interfaces
auto eth0
iface eth0 inet static
address 78.84.247.117
netmask 255.255.224.0

then:
ifconfig eth0 78.84.247.117 netmask 255.255.224.0


what next should I do to create connection between these PCs?

---

### Post by alphajean@gmail.com on 2008-04-11
eth0      Link encap:Ethernet  HWaddr 00:50:04:0F:71:D5  
          inet addr:78.84.247.117  Bcast:78.84.255.255  Mask:255.255.224.0
          inet6 addr: fe80::250:4ff:fe0f:71d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74953 (73.1 KB)  TX bytes:64605 (63.0 KB)
          Interrupt:10 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0D:87:B8:CD:32  
          inet addr:78.84.247.117  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::20d:87ff:feb8:cd32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:284459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:222892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:358915598 (342.2 MB)  TX bytes:17267911 (16.4 MB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60970 (59.5 KB)  TX bytes:60970 (59.5 KB)

---

### Post by alphajean@gmail.com on 2008-04-12
I reinstalled system ..... I still can't connect...Think Windows XP will choose, i cant operate in Xubuntu normally...

Bue people

---

