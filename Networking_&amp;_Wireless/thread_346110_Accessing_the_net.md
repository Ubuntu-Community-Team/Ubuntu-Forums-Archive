---
title: "Accessing the net"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by drich290195 on 2007-01-25
Im new to this and have a problem, i have a network card and ubuntu see's it and it is active. However firefox wont connect to the net. 

How do i get Ubuntu to connect to my netgear router. I know my dfefault gateway for the router is 192.168.0.1 and i have reserved an ip for my machine. Hoiw do i set up UBuntu to connect to the net. Any help would be greatly apreciated thanks.

---

### Post by Jussi Kukkonen on 2007-01-25
Have you taken a look at System --> Administration --> Networking?

If yes (or if you can't make sense of it) and things still don't work,  please paste the output of these commands
```
ifconfig
cat /etc/network/interfaces 
```

---

### Post by drich290195 on 2007-01-25
Ok been into networking tools my network card is set too enabled, and is set to dhcp is also set as active , yet firefox still wont eork i am running of the cd it is not installed to hard drive will this affect it do i need to enter any settings or anyrthing

---

### Post by Jussi Kukkonen on 2007-01-25
Running from the livecd shouldn't be any different. 

Do you know that there is a dhcp server in the network? Your router probably does that, I'm just checking...

Can you run the commands I posted and paste the output here? You can do that in a terminal (which is in Applications/Accessories I think). Also a third command for you to run:
```
dmesg | grep eth
```

---

### Post by drich290195 on 2007-01-26
Please help it's doing my head in.

I cant put those commands in cause i cant save the results and open them in windows to post here.

I have tried putting the ip gateway and everything from windows into the network tools section.

The funny thing is if i open firefox type in [www.google.co.uk](www.google.co.uk) it says it is searching for  the page if i open up network tools and enter the ip details while firefox is open and click apply, it will then open google, but then once the network tools is shut firefox wont open any other page.

So i know it is seeing the wrouter what is wrong, it also wont work if it is set to dhcp. Its really doing my head in i want to het using the thing please help.

---

### Post by Jussi Kukkonen on 2007-01-26
Sounds really weird.
> 
I cant put those commands in cause i cant save the results and open them in windows to post here.
A USB-memorystick might save the day. Alternatively just copy  a few things to paper and then write them here in windows:
1. the contents of /etc/network/interfaces (you can forget the lines that start with #),
2. run this command: ***tail -f -n0 /var/log/messages***, then apply your network settings like you've done before. You should get a couple of lines (the dates and series of numbers aren't important)

> if i open up network tools and enter the ip details while firefox is open and click apply,
Can you be a little more specific -- I am not sure where you are inputting the details (e.g. I couldn't find an "apply"-button in either *Networking* or *Network Tools* windows...). If you could tell exactly what information you are inputting and where and how, I could (maybe) tell if that's correct.

---

### Post by Cyberbayne on 2007-01-26
> **drich290195 said:**
> I cant put those commands in cause i cant save the results and open them in windows to post here.

I've been having a similar problem, and what has helped is a utility I installed in Windows that allows you to view the Ubuntu file directory. 

So when I'm troubleshooting I can copy and paste the console results into a text file (see Accessories/Text Editor) on the desktop. Then when I return to Windows I find the desktop and click and drag the file to the windows desktop. Now you can copy/paste the info into the forum.

I'm not at home so I don't remember the name of the Windows ext3 reader utility, but knowing there is one should set you on the path to finding it. I think I found it in Sourceforge.

---

### Post by Cyberbayne on 2007-01-27
Its called Explore2FS.

[http://sourceforge.net/project/showfiles.php?group_id=182608](http://sourceforge.net/project/showfiles.php?group_id=182608)

---

### Post by drich290195 on 2007-01-28
Write these are the results of the commands you gave me, these are the valiues i have set up for eth0 in networking, cause manual dhcp wont do anything. 

They are exactly the same as my windows settings and they work. IP 192.168.0.2 subnet 255.255.255.0 Default Gateway. 192.168.0.1

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0A:E4:42:03:11
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe42:311/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:904 (904.0 b)  TX bytes:1170 (1.1 KiB)
          Interrupt:233 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by Jussi Kukkonen on 2007-01-28
According to your interfaces file, your connection was set to use dhcp when you ran the command (no static connections were defined)...

The TX and RX packet counts indicate that there has been little traffic (like you said yourself) -- so your setting are probably correct. This is a problem I've never seen before, and I have no ide what goes wrong. The only thing that I can think of that could help debug this is the logs, particularly ***dmesg | grep eth***.

---

### Post by drich290195 on 2007-01-28
Couldnt do that command that you gave on the last post, but here are the other results with the ip settings in.

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

I have a netgear DG384G could their be any settings on their i am missing

---

### Post by drich290195 on 2007-01-29
Here are the latest results to the command dmseg | grep eth

[4294714.322000] eth0: RealTek RTL8139 at 0xf8a06000, 00:0a:e4:42:03:11, IRQ 233[4294714.322000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294716.716000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294727.667000] eth0: no IPv6 routers present

 Can anyone please help me it is doing my head in anyone offer any advice

---

### Post by drich290195 on 2007-01-30
Anyone Please HElp

---

### Post by Jussi Kukkonen on 2007-01-30
dmesg output looks just as it should...  As far as I can see your operating system thinks everything is as it should be and that the connection is up. 

I'm pretty much out of ideas now. Changing hardware (the network card in this case) could help, but I'm not promising anything.

---

