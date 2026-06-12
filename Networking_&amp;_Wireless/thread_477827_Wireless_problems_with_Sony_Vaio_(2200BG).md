---
title: "Wireless problems with Sony Vaio (2200BG)"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by chrisgeller on 2007-06-18
Hi

Just installed Ubuntu and very new to all this.

I've installed Feisty Fawn on my Vaio TR2MP - I can't get the wireless to work. If I plug in the computer via ethernet, it works, and wireless worked with XP so it's a Ubuntu software issue.

I can get up a list of available networks, and apparently connect (it's hard to tell?), but Firefox can't open anything.

I've read around on the forums but it seems like most people had problems after an upgrade. Can anyone point me in the right direction?

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"RReynolds"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:C6:FE:B8   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-32 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:3045  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:4



ipconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:CC:26:A9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:57124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55259773 (52.6 MiB)  TX bytes:11525405 (10.9 MiB)

eth1      Link encap:Ethernet  HWaddr 00:0E:35:02:F6:E0  
          inet6 addr: fe80::20e:35ff:fe02:f6e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3505 errors:3106 dropped:3106 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1276 (1.2 KiB)  TX bytes:45320 (44.2 KiB)
          Interrupt:9 Base address:0x2000 Memory:e0201000-e0201fff 

eth0:avah Link encap:Ethernet  HWaddr 08:00:46:CC:26:A9  
          inet addr:169.254.6.214  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth1:avah Link encap:Ethernet  HWaddr 00:0E:35:02:F6:E0  
          inet addr:169.254.8.183  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Base address:0x2000 Memory:e0201000-e0201fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:733341 (716.1 KiB)  TX bytes:733341 (716.1 KiB)


I'm very new to all this; let me know if there's any more info that would be useful, thanks

---

### Post by charleseddy on 2007-06-18
Right click the network icon in the tray and click "Connection Information." Let me know what it says.

---

### Post by chrisgeller on 2007-06-18
"Could not find ....(the glade file)"

Sorry, didn't remember that exactly.

It's strange, I've found I can connect (illegally) to my neighbours unsecured wireless, and of course my wired connection still works.

If I connect to my own network - it looks connected, little bars etc, but either works *extremely* slowly, loading up files incompletely or usually not at all.

But I suspect it is not connected, as it repeatedly flashes up asking for my password. Entering it doesn't seem to work.

Any ideas? Thanks

---

### Post by fdrake on 2007-06-18
what kind of key protection do u use on your network. wep ?

try this:
sudo iwconfig eth1 essid ESSID key s:PASSWORD
ESSID=your essid's name
PASSWORD=your pass

---

### Post by chrisgeller on 2007-06-19
Hi

I'm using WEP 64bit hexadecimnal

When I type:

sudo iwconfig eth1 essid MYESSID key MYKEY

into terminal, it doesn't display anything differently at all, just gives me another prompt. But I think this does seem to make the internet work? 

Is that what you expected? How can I make this permanent?

---

### Post by fdrake on 2007-06-19
> **chrisgeller said:**
> Hi

I'm using WEP 64bit hexadecimnal

When I type:

sudo iwconfig eth1 essid MYESSID key MYKEY

into terminal, it doesn't display anything differently at all, just gives me another prompt. But I think this does seem to make the internet work? 

Is that what you expected? How can I make this permanent?

u mean that ur connected now??
to make it permanent just use the same password and esiid in your network configuration and use whose to create a new network place, and save it. next time it should be automatic when you select the right network place.

---

### Post by chrisgeller on 2007-06-19
It still seems to come and go. Last time it worked for about 2 minutes. Then I couldn't do anything to fix it.

Would you expect writing
sudo iwconfig eth1 essid MYESSID key MYPASSWORD
to fix the problem?

Do you mean I need to make permanent changes to my /etc/network/interfaces file?

---

### Post by fdrake on 2007-06-19
no . just go to system>administration>network>select wireless connection>properties
essid:RReynolds
password type:WEP key hexadecimnal (you said you's usnig WEP 64bit hexadecimnal right?)
configuration: automatic configuration DHCP

just make sure that your router is configuret properly. what kind of router do u have? if u have an option of "Authentication Type" between open and shared select automatic. 	
under "Encryption Strength" select 64 bit (like u said before"
remeber that the network configuration prog doesn't handle Passphrase just key
click ok , check the wireless connection to activate it (if it wasn't activated) and above press the floppy disk icon to save the new configuration as home-network

to be sure reboot and see if it works

---

### Post by chrisgeller on 2007-06-19
I've made those changes. Previously I had it set to roaming.

When I reset it doesn't appear to search for wireless networks at all. I have the icon with the two overlapping computer screens, but it doesn't connect at all. It will connect to an available wired connection though.

I have a Buffalo Airstation G54 router. I couldn't actually find the router settings part -- is that in the system/administration/network?

---

### Post by fdrake on 2007-06-19
> **chrisgeller said:**
> I've made those changes. Previously I had it set to roaming.

When I reset it doesn't appear to search for wireless networks at all. I have the icon with the two overlapping computer screens, but it doesn't connect at all. It will connect to an available wired connection though.

I have a Buffalo Airstation G54 router. I couldn't actually find the router settings part -- is that in the system/administration/network?

don't check the roaming mode just click ok.
to see your router settings u have use a wired connection and use the browser usually at the address 192.168.1.1(not sure for ur modem)
another thing when u see the icon with the two screen on the bar click on it and under connection name write eth1 (for wireless. eth0=wire connection)

---

### Post by chrisgeller on 2007-06-19
I was able to access my router through that IP and my settings were as you suggested.

When I click on the two windows I'm currently only offered

Wired network (greyed out)
and manual configuration.

---

### Post by fdrake on 2007-06-19
on the bar right click on an empty spot . select add to panel>under system and hardware select "Network Monitor"

---

### Post by chrisgeller on 2007-06-19
Hi

I've added that.

At the moment the wireless is working.

When I left click on Network manager it says my current (wireless) connection is eth1, and the other connection is lo. It says my signal strength is 100%.

I thought wireless was meant to be eth0?

---

### Post by fdrake on 2007-06-19
> **chrisgeller said:**
> Hi

I've added that.

At the moment the wireless is working.

When I left click on Network manager it says my current (wireless) connection is eth1, and the other connection is lo. It says my signal strength is 100%.

I thought wireless was meant to be eth0?

you have to check your ifconfig and iwconfig they tell you which one is wired and wireless. in your case eth1 is wireless and eth0 wire

---

### Post by chrisgeller on 2007-06-19
Below are my current ifconfig and iwconfig - you're right about the eth1/eth0 of course.

My wireless stopped working again so I plugged in my ethernet. I noticed that both eth1 and eth0 seem to be sending and received at the moment, but very slowly.

If I set a youtube video downloading, my wired connection can download it, but if I remove the cable then whilst it says it is send/receiving, it does it so slowly as to stop video altogether.

ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:CC:26:A9  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fecc:26a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99115 (96.7 KiB)  TX bytes:20905 (20.4 KiB)

eth1      Link encap:Ethernet  HWaddr 00:0E:35:02:F6:E0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe02:f6e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4028087 (3.8 MiB)  TX bytes:635747 (620.8 KiB)
          Interrupt:9 Base address:0xe000 Memory:e0201000-e0201fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17003 (16.6 KiB)  TX bytes:17003 (16.6 KiB)


 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"RReynolds"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:C6:FE:B8   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-27 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:873  Invalid misc:0   Missed beacon:0

---

### Post by chrisgeller on 2007-06-24
Hi, does anyone have any other ideas please?

---

