---
title: "Using a crossover cable to connect XP to Ubuntu"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by MauiWowee on 2011-03-02
I have laptop with XP and a pc with Ubuntu. I want to connect to the pc so that I can transfer files and if possible, connect to it in order to edit files since the pc does not have a monitor. And is there any way to "see" the other computer's screen, similar to a Virtual Machine?

The *connection between two computers* topic has been on here before but from what I found, it seemed to deal mostly with internet sharing which is not what I my goal is.

I have a crossover cable, and zero experience setting up networks, so I am not sure where to go from here.

---

### Post by turtle153 on 2011-03-02
You should just be able to use cat5 ethernet cable ad-hoc between the computers. You'll may also need to install Samba```
sudo apt-get install samba
``` to share with Windows.

For seeing the Windows screen from Ubuntu you'll need grdesktop. ```
sudo apt-get install grdesktop
```
To do the reverse you can use a VNC program such as [http://www.tightvnc.com/download.php](http://www.tightvnc.com/download.php)

Good luck!

---

### Post by The Cog on 2011-03-02
I assume this is an ethernet crossover cable, not a serial crossover cable:

You will need to configure both computers to have static IP addresses, different but in the same subnet. e.g. 10.0.0.1 and 10.0.0.2 with a subnet mask of 255.0.0.0. In Ubuntu, that's done by right-clicking the network connections widget in the system tray and editing auto eth0.

Remote desktop viewing can be enabled by allowing remote viewing under Settings->Remote Desktop on the PC.

For file sharing, the easiest is probably to install openssh-server on the PC and filezilla on the laptop. I remember struggling for many hours and failiing to get samba to work in the past.

---

### Post by MauiWowee on 2011-03-02
Awesome, thanks for the tips I will work on it tonight or tomorrow. And yes, it is an ethernet crossover cable.

The PC is not connected to the internet. Does that meet that the *apt-get install* commands will not work?

Also, turtle, I should clarify- I am trying to remote-in or otherwise access the Ubuntu computer, so I want to see the Ubuntu screen from Windows instead of the other way around.

---

### Post by The Cog on 2011-03-03
> **MauiWowee said:**
> The PC is not connected to the internet. Does that meet that the *apt-get install* commands will not work?
Yes it does. Apt-get is really aimed at fetching stuff from the Ubuntu repositories on the internet.

---

### Post by turiya on 2011-03-05
I am also trying to connect an XP machine to an Ubuntu machine using a crossover cable. I've set both of the machines to static IP addresses (Ubuntu laptop to 192.168.0.1 and XP desktop to 192.168.0.42) my main problem right now is that the XP machine just keeps saying "network cable unplugged". Any ideas on what might be going wrong?

---

### Post by turiya on 2011-03-05
I suppose I should also mention that the point of connecting the machines is to allow the XP desktop to connect to the internet through the Ubuntu laptop's wireless card. I have already found several sources on how to get that working, but until I can get the connection between the machines setup there's no point in worrying about that part.

---

### Post by The Cog on 2011-03-06
> **turiya said:**
> I am also trying to connect an XP machine to an Ubuntu machine using a crossover cable. I've set both of the machines to static IP addresses (Ubuntu laptop to 192.168.0.1 and XP desktop to 192.168.0.42) my main problem right now is that the XP machine just keeps saying "network cable unplugged". Any ideas on what might be going wrong?

My first reaction would be to wonder if the crossover cable was right. The connections should be:
1 --- 3
2 --- 6
3 --- 1
6 --- 2
When the cable is plugged in, the command ifconfig in Ubuntu should show the interface to be RUNNING. Try it with the cable out, then connected, then with the cable turned round - it should be symettrical. Beyond that, I'm running out of ideas.

---

### Post by turiya on 2011-03-07
> **The Cog said:**
> My first reaction would be to wonder if the crossover cable was right. The connections should be:
1 --- 3
2 --- 6
3 --- 1
6 --- 2
When the cable is plugged in, the command ifconfig in Ubuntu should show the interface to be RUNNING. Try it with the cable out, then connected, then with the cable turned round - it should be symettrical. Beyond that, I'm running out of ideas.

I've checked that three times, the cable is proper. I checked each individual wire using a multimeter and came up with .7 ohms of resistance for each.

I've also tried connecting both computers into my router 50+ feet away with my longest ethernet cable and both connected to the router.

Just now I remembered that the XBox 360 can swap the pin output for ethernet so that whether the situation would normally call for a crossover or a straight-through you can use either. Right now my 360 is downloading an update using that cable so the cable is fine.

I've also tried using a straight-through cable to connect the computers and what I've noticed is that the Ubuntu laptop's hardware connectivity lights (the lights on the port) flash (1 second long orange light, flash of green then 1 second of nothing, repeat) when the two computers are connected with the crossover, but not with the straight or no cable at all.

Regardless of whether there is a cable or what cable is plugged in the XP desktop has 2 possibilities for it's lights; if the crossover cable was plugged in when it turned on, or it had connection to the router at some point while it was on then it's lights are constant and green, if it didn't have the cable plugged in when it was turned on and hasn't connected to the router then it's lights are constantly off. I haven't checked it's lights when it's currently connected to the router.

This is probably the most confusing networking problem I've ever dealt with. I can't figure out if it's a hardware problem or a software glitch. Every experiment I come up with to determine where the problem is occurring gives me a result that indicates that nothing is wrong with anything, and yet it continues to fail.

Ubuntu (10.04 by the way) just keeps telling me that there's no connection on the ethernet. XP just keeps saying that a network cable is unplugged.

Edit:
   Just remembered that there is another XP computer in the house so as soon as the 360 finishes updating I'll try connecting that one to the Ubuntu laptop and see what happens.

Edit 2:
After moving computers so that I had the other XP desktop and the 2 I was trying to get connected to each other all in the same room I can get the two XP computers to talk to each other, but neither of them will talk to the Ubuntu machine. This tells me that the problem is most likely in the Ubuntu machine. Maybe it has some problematic drivers.

---

### Post by Paqman on 2011-03-07
You only need a crossover cable if the network interfaces are really, really old. NICs have been able to use a regular ethernet cable for this for a few years now, the card detects that it's plugged straight into another NIC and sorts the pin connections out automatically.

---

### Post by turiya on 2011-03-07
> **Paqman said:**
> You only need a crossover cable if the network interfaces are really, really old. NICs have been able to use a regular ethernet cable for this for a few years now, the card detects that it's plugged straight into another NIC and sorts the pin connections out automatically.

The two computers I'm trying to connect are both older model Dell computers but they do the jobs I need them for. The laptop is an Inspiron 600m purchased in 2005 and the desktop is a Dimension 3000 purchased in 2004. They're both old enough to need the crossover.

---

### Post by turiya on 2011-03-07
Not exactly sure what changed, but approximately an hour ago, about 5 minutes after I decided to give up on this ever working, the two finally started communicating with one another. Now my problem is that if I have the wired connection enabled the Ubuntu laptop tries to send all internet requests through the wired connection instead of the wireless.

Any ideas on how to fix this?

---

### Post by turiya on 2011-03-08
I realize at this point I'm getting beyond "absolute beginner talk" but is there a way in Ubuntu to specify which networking interface should be used to gain access to a specific IP address. Or can you specify that a specific interface should only be used to get access to a particular set of IP addresses.

I want to limit eth0 so it only sends packets bound for my desktop's IP address (192.168.0.42) or set up a list so that for every address except 192.168.0.42 it should use wlan0. That would fix the problem I'm having of every packet going out through eth0.

---

### Post by The Cog on 2011-03-09
I hope the two interfaces are configured to have different network numbers, meaning they don't both start with "192.168.0.". You will have nothing but trouble if it thinks both adapters are connected to the same network. 

Posting the output of these three commands would help is figure things out:
> ifconfig
route -n
cat /etc/resolv.conf

P.S.
I would suggest using networks 192.168.0 and 192.168.1.

---

### Post by turiya on 2011-03-23
> **The Cog said:**
> I hope the two interfaces are configured to have different network numbers, meaning they don't both start with "192.168.0.". You will have nothing but trouble if it thinks both adapters are connected to the same network. 

Posting the output of these three commands would help is figure things out:


P.S.
I would suggest using networks 192.168.0 and 192.168.1.

Sorry about the delay in responding, something else came up and this got put on the back burner.

The wireless connection is 192.168.1 and the wired is 192.168.0.

I was thinking it might have to do with the ARP caches on the different machines since they were both connected at some point through a wired connection to the router I'm trying to access via wireless. Aren't ARP caches supposed to be automatically cleared out every so often though?

Other than that I have no idea what it might be.

---

### Post by The Cog on 2011-03-23
Hah! I've lost track of how may half-finished projects I've got on my back burner.

ARP caches normally last for less than an hour. But unless you've been changing IP addresses, that shouldn't be a problem anyway.

Please post the output of these commands:
```
ifconfig
route
cat /etc/resolv.conf
```

Also, how are you configuring the address of the wired interface on Ubuntu?

---

### Post by turiya on 2011-03-24
```
agrajag@agrajag-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:f9:b4:56  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fef9:b456/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4200 (4.2 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:878 (878.0 B)  TX bytes:878 (878.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:8e:0b:50  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fe8e:b50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:566005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149284593 (149.2 MB)  TX bytes:3105745 (3.1 MB)
          Interrupt:11 
          
//route with the crossover unplugged
agrajag@agrajag-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

//route with the crossover plugged in
agrajag@agrajag-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.1     *               255.255.255.255 UH    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

//sciotowireless.net is my internet provider
agrajag@agrajag-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain sciotowireless.net
search sciotowireless.net
nameserver 69.43.24.2
nameserver 69.43.24.3

```

As to how I've been configuring the address of the wired interface I've been going into the Network Connections tool and setting it up manually with the address 192.168.0.1, netmask 255.255.255.0 and I've tried 3 different things for gateway since I'm not sure what to put in there and it seems to need it. I've tried gateway at 192.168.0.42, 192.168.0.1 and 192.168.1.1.

I went and did some tests and found that on the "route" command if the eth0 gateway is set to 192.168.0.42 the default destination changes to that instead of 192.168.1.1. Not sure if that means anything.

---

### Post by The Cog on 2011-03-24
Everything looks fine there with just one exception. When you plug the cable in, the default route changes (it shouldn't). It changes to say that the internet is reachable via 192.168.1.1 reachable on eth0. This is completely wrong. 

I presume that the default route when the cable isn't plugged in has been learned by DHCP from the wireless network, so that os very probably correct.

The default route is taken from the gateway entry in the network manager config. Since you don't have a connection to the internet via eth0, I think you should leave the gateway entry blank. This should then allow the correct default route over the wireless to remain in place.

Can you ping the XP desktop 192.168.0.42 when connected?

---

### Post by turiya on 2011-04-03
I've tried leaving the gateway for eth0 blank. It won't let me do that. As soon as I clear out the information from the gateway.

After I typed that I went to test it again and noticed something I hadn't before, there's a little button marked "Routes..." when that dialog pops up there's a check box "Use this connection only for resources on its network".

Now I can have them wired up together and still be connected to the internet on the laptop. Still need to see if I get connection to the internet on the Desktop though.

---

