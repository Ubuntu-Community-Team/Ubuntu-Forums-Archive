---
title: "Simple network help"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by Armor on 2007-02-01
Alright, here's my situation:
Main PC has Edgy, works fine. Small tweaks I need to figure out how to do but otherwise works fine. It dual boots XP/Ubuntu (Keep XP for games). This machine connects through a standard cable modem.
I just installed Ubuntu (6.10) on my notebook. I has an internal 11g wireless card. No dual booting here, straight up Edgy. 
I have a wireless router, a WRT54G.

What I want to do is this:
Cable modem to wireless router, and use cat5 to connect the main machine through the router (of course)
THEN, wirelessly connect the notebook to the router, so both machines can be online at same time. I also want a shared network folder, so that if I want to move a file from one PC I can just drop it in the network folder, then browse the network folder with the notebook in order to open up files I place there.

Is this possible?

Total Linux noob here

---

### Post by koenn on 2007-02-01
> Is this possible?
Theoretically, yes. 
I suppose the connections you describe are physically possible ? ie you can plug both the cable modem and a computer into youre routert ?
Your router shiould be able to de NAT for this to work. Can you check that ?

> I also want a shared network folder, so that if I want to move a file from one PC I can just drop it in the network folder, then browse the network folder with the notebook in order to open up files I place there.
Where do you think this shared network folder will be located ?

---

### Post by mips on 2007-02-01
Yes it will work.

---

### Post by punx45 on 2007-02-01
yep.   the only thing that complicates the sharing matter is the desktop is dual booting.
my suggestion would be to make the share area a separate partition/drive on the dual boot desktop.   enable sharing with windows, and sharing via NFS in ubuntu, then configure the laptop for both SAMBA and NFS.
also, it will help to give the desktop a static IP in both OSes.

---

### Post by Armor on 2007-02-01
> my suggestion would be to make the share area a separate partition/drive on the dual boot desktop. enable sharing with windows, and sharing via NFS in ubuntu, then configure the laptop for both SAMBA and NFS.
also, it will help to give the desktop a static IP in both OSes.
Linux noob here man...I have no idea what any of that is you're talking about...
I tried plugging the cable modem into the router then the router into the main PC and got nowhere with that. Internets wasn't workin. So I guess the FIRST step would be to figure out how to get Internet working on my main PC when booted in Ubuntu by just going through cable modem > router > main PC then I can figure out later how to get wireless working with the notebook and the shared folder

---

### Post by koenn on 2007-02-01
> cable modem > router > main PC 
OK ....
connect them all, turn them of (wait 5 minutes) ,  turn them on one by one :
1- modem  (and wait until its completely started - look for indicator lights,  )
2- router (again, give it a few minutes)
3- PC (boot Ubuntu, so we can easily check network stuff)

If you're lucky, it will be OK already. 
If not, run ifconfig and post output.

---

### Post by Armor on 2007-02-01
Thank you! 1, 2, 3 steps rocks for Ubuntu noobs like me. I'll do just that when I get home tonight. 

What are the odds that it will be ok and good to go? Is it hard to fix it and make it work if it's not and I have to run ifconfig?

PS - by "run ifconfig" you mean go to a terminal and type just that "ifconfig" ?

---

### Post by koenn on 2007-02-01
past bedtime on this side. I'll come and have a look tomorow evening

odds : 70% ?

ifconfig  : yes, just type it in a terminal & hit enter
It just shows a bit of network configuration, but it's a good start to find out where to look next if networking isn't working. 

Thousands of people have home networks like the one you're trying, so it's not all that hard to setup and there'll be plenty of people to give directions

(and with my luck, having said all that, it might just turn out that your router - cable modem - network card are one of these "pain in lower part of back" combinations  :) )

---

### Post by punx45 on 2007-02-02
my bad. i thought the network was already up and running.

but yes, the physical layout you described is right on.

usually the power cycle trick noted above works with cable modems and routers.  also you can check the router status page to make sure it is getting a good IP from the ISP too.  also if you are still having troubles after a power cycle, make sure the router is using the correct method to get service from the ISP.   since its cable, it should probably be set to automatic configuration or DHCP (two ways of describing the same thing).   i would focus on getting networking going on the desktop first, then tackle the wireless on the laptop. (hope you got your learning cap on :-D )

---

### Post by Armor on 2007-02-02
I did just that. Shut down computer, unplugged all, then plugged cable modem in, then router, turned computer on, and no luck. I ran ifconfig when it was setup that way (I have the router unplugged now just cable modem so I have internets) and it came back with this:

> leigh@leigh-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7D:F1:50  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe7d:f150/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:207695 (202.8 KiB)  TX bytes:86260 (84.2 KiB)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

Helllllp

---

### Post by punx45 on 2007-02-02
have you used the router successfully before now?

---

### Post by Armor on 2007-02-02
Yes

---

### Post by Armor on 2007-02-02
Anyone?

---

### Post by punx45 on 2007-02-02
when you browse to the router to do the configuration, what is its IP?
and, 
is the desktop set up for automatic configuration (DHCP)?

oh.. and make sure the cat5 cable coming from the modem to the router is plugged into the WAN port on the router, and not one of the regular switch ports (1-4).

---

### Post by Armor on 2007-02-02
[IMG]http://lhbox.com/files/Screenshot.png[/IMG]

---

### Post by koenn on 2007-02-02
At least you got an ip address (net addr:192.168.1.100), presulmably from (a dhcp service on) your router so we can assume the pc and the router can communicate. (we'll thest that later). 
The modem and the PC work together also, but what we need is the modem to talk to the router. 


Here's a few things you can do to figure out how your network is set up

1/ connect router to PC directly, and run 
ifconfig
route -n

you could also surf to [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) 
scroll down to to bottom, there's some text there that tells you your "public" ip address. 
Is it the same as the one you got from ifconfig ?


2/ set up modem > router  > PC again, as before
run ```
ifconfig
```. Result should be the same as in your earlier post. If not, let us know.
als, run ```
route -n
``` again, and post result.

---

### Post by Armor on 2007-02-02
Ok, with router directly to computer (obviously no internet here, modem isn't involved) and running ifconfig in terminal, I get this:
> leigh@leigh-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7D:F1:50  
          inet6 addr: fe80::250:8dff:fe7d:f150/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10692 (10.4 KiB)  TX bytes:2222 (2.1 KiB)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

leigh@leigh-desktop:~$ 


When I run route -n I get this:
> leigh@leigh-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
leigh@leigh-desktop:~$ 


When I shut down computer and have modem > router > computer, after running ifconfig I get this:

> leigh@leigh-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7D:F1:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

leigh@leigh-desktop:~$ 


When I run route -n I get this:

> leigh@leigh-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
leigh@leigh-desktop:~$ 


---

### Post by koenn on 2007-02-02
> 1/ connect router to PC directly, and run 
sorry, my mistake, that should have been modem to PC direcly. Can you do it again ? 

note you're not getting ip addresses anymore, while your router should provide that service, judging from that screenshot. 

With (some) cable modems / ISP's, swapping devices the way you're doing now (router, PC, ...) doesn't sit well - use the 1-2-3 routine as before - it helps to avoid problems caused by attaching differet devices to the modem all the time.

---

### Post by Armor on 2007-02-02
Modem to PC (internet works)
ifconfig
> leigh@leigh-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7D:F1:50  
          inet addr:66.67.167.124  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::250:8dff:fe7d:f150/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37175 errors:2423 dropped:0 overruns:0 frame:0
          TX packets:15689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2615 txqueuelen:1000 
          RX bytes:32389089 (30.8 MiB)  TX bytes:1641805 (1.5 MiB)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

leigh@leigh-desktop:~$ 


route -n
> leigh@leigh-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
66.67.160.0     0.0.0.0         255.255.248.0   U     0      0        0 eth0
0.0.0.0         66.67.160.1     0.0.0.0         UG    0      0        0 eth0
leigh@leigh-desktop:~$ 


---

### Post by koenn on 2007-02-02
ok, now the modem - router - pc again

---

### Post by Armor on 2007-02-02
Why? I already did that

---

### Post by koenn on 2007-02-03
because that's the setup you want to get working, right ? So how you're going to troubleshoot something that isn't there? 
Also, the last time you had it set up that way, ([http://ubuntuforums.org/showpost.php?p=2097451&postcount=17](http://ubuntuforums.org/showpost.php?p=2097451&postcount=17) ) your computer did not pick up an IP address - nothing is going to work if your computer doesn't have an IP address, so it would be wise to see if this is a recurrent problem or just a one time glitch. 

Anyway, skipping a few steps and making lots of assumptions - just to avoid you having to set up things one way, then another, you could try this

- if you have the time/patience, shut down (unplug the power chord) the modem for 20-30 minutes. This sometimes helps to have it reset its config ang get rid of leftovers from the 'modem to PC directly' setup (like : it rememvers the MAC address of the PC, and refuses to work with the router because that has a different MAC address)
- do that modem-router-pc thing again, in the corect order, 
- run ifconfig, and verify that your PC has an IP address. 
- if it does, test it by pinging it; eg
```
ping 192.168.1.100 -c 4
```
- run route -n to check that you have a gateway, it should show a line  like
```
leigh@leigh-desktop:~$ route -n
...
0.0.0.0   192.168.1.1  0.0.0.0 UG 0 0 0 eth0
```

- you could then ping the router's public IP address to verify that it routes. Problem is that this address may have changed in the mean time so it only gives relevant info info if it works

```
ping 66.67.167.124 -c 4
```

Alternatively you could look around in the configuration pages of the router to find anything that looks like 66.67.167....  (except 66.67.167.1) or "public IP", "internet', "WAN IP", ... and use that address for the ping command 

- you could also try to detect the route to the internet with
```
traceroute 66.67.167.1
```
you may have to install 'traceroute' first (synaptic or 'sudo apt-get install traceroute', i think) - it's just a small package but i'm not sure it's installed by default. 

-with whatever output you've gathered we should be able to know what sort of trouble you're having, but for good measure, also do
```
ping 66.67.167.1 -c 4
```


for all these commands : copy/paste the results in a text file (applications : Accessoires : Text Editor) so you can refer to them later or post them here


-----------------------
After you've done all this, have a look at your router, the 'Clone MAC address' page. See if there's anything there that looks like you could "fake" the MAC address of the router. That might provide a possible workaround to trick the modem in to believing it's talking to your PC (which it is willing to do) while in fact it's talking to the router

---

### Post by Armor on 2007-02-03
Alright, gimme a little bit and I'll post all that stuff up

---

### Post by Armor on 2007-02-03
Here are the results from Modem > Router > PC

> leigh@leigh-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8D:7D:F1:50  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe7d:f150/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30132 (29.4 KiB)  TX bytes:30064 (29.3 KiB)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

leigh@leigh-desktop:~$ ping 192.168.1.100 -c 4
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=0.022 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=64 time=0.010 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=64 time=0.017 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=64 time=0.015 ms

--- 192.168.1.100 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 0.010/0.016/0.022/0.004 ms
leigh@leigh-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
leigh@leigh-desktop:~$ ping 66.67.167.124 -c 4
PING 66.67.167.124 (66.67.167.124) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable
From 192.168.1.1 icmp_seq=2 Destination Net Unreachable
From 192.168.1.1 icmp_seq=3 Destination Net Unreachable
From 192.168.1.1 icmp_seq=4 Destination Net Unreachable

--- 66.67.167.124 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3000ms

leigh@leigh-desktop:~$ 

Here's a screen shot of the MAC Address page:

[img]http://lhbox.com/files/Screenshot2.png[/img]



I've restarted my computer about 30 times, plugged this in plugged that in rout -n here and route -n I'm really, really getting frustrated here. Do we have any solutions??

---

### Post by koenn on 2007-02-03
Ok, it's clear that the trouble is on the segment from your router to the ISP. 
Probably because your router is not getting an IP address from your ISP. 

Suggestion:
Enable the "MAC Clone" with "get conncted pc's MAC"

You may have to reboot the router etc to make it effective - follow the instructions on your screen, if any. 

see if you can get to a website. If not, try to ping something on the internet (66.67.167.) or run that whole diagnostic sequence (ifconfig, route -n, ping ...) again and see if anything has changed.

---

### Post by punx45 on 2007-02-04
ooh good point, i hadn't thought of the mac cloning.

i do recall now that when i got cable ISP (comcast) I set up the connection with the PC connected directly to the modem, and then when i attached the router, i had to set mac cloning to the PCs MAC.  ive been told that if you leave the connection for a while this problem resolves itself, but I have never had the patience, so i went straight for MAC cloning and it worked.

---

### Post by Armor on 2007-02-05
Well, it's working - but not quite how I have been trying. 

I just ended up setting the damn thing up in XP. The only reason I wanted the wireless was for me to use when my girlfriend wanted to use the main computer, and she doesn't like Ubuntu because she's used to XP. So, as long as I have this thing working in XP, I can try to hop on the wireless network from my notebook

---

