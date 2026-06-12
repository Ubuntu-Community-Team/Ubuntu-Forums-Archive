---
title: "connected to network but cannot use!!"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by vladuz976 on 2007-07-11
sony vaio type C 
wireless and wired network connect.
for wireless I get a full signal, the wired network also says connected.
i cannot use the internet however. 
all windows computers in the office are somehow working.
another person had a similar issue with a macbook and wireless network. 
problem is that all the office computers are in japanese so its hard to figure out the settings.
the all say DHCP but then a default gateway is also entered.

any idea what could be wrong, or what I can try to fix it.
any help would be greatly appreciated. I am in the office and cannot work.


thanks

---

### Post by vladuz976 on 2007-07-11
so all computers have some IP entered where it says default gateway in windows network settings.
when I type that ip into my browser I noticed that thats the IP of one of the routers in the office.
so is it possible that dhcp is used to assign an IP to each computer but to reach out I need to get through that gateway?
if so, how would I change my settings?

thanks

---

### Post by kevdog on 2007-07-11
Boot with only the wired connected or wireless connected.

Assuming you have the wired only connected, and you are still not connected, what happens when you do the following:

Assuming eth0 is the interface name
sudo eth0 down
sudo eth0 up
sudo route add default gw 192.168.1.1  <---use correct gateway/router address here
sudo dhclient

---

### Post by vladuz976 on 2007-07-11
how to i find out what the interface name is?
I forgot that command and I can:t look anything up online right now.

---

### Post by vladuz976 on 2007-07-11
i get 
command not found

---

### Post by kevdog on 2007-07-11
lshw -C network

Look for "Logical name"

---

### Post by vladuz976 on 2007-07-11
yeah that says eth0
but what do you mean by 

sudo eth0 down ?

the command "eth0" doesnt seem to exist.
could it be something else?

---

### Post by vladuz976 on 2007-07-11
can anybody please help me?
at this point I dont even have a copy or windows to fall back on.
any ideas are welcome.

thanks

---

### Post by vladuz976 on 2007-07-11
i am sure that this is something that can be fixed if I knew more about networking and linux.
but the sad thing is that with os x and windows you really just turn on the computer and connect to the internet. with my ubuntu laptop i am the only person in the office who cannot do anywork without at the same time being a networking expert. I really love using free software, but it seems as if ubuntu is still not ready for use in office.

thanks anyways.

---

### Post by fredj on 2007-07-12
sudo eth0 down means
1 the sudo command makes you an admin or root user and will ask for your password.

2. eth0 is the name of a network interface, in this case probably the wired network card.
3. down means disconnect eth0

Please open a terminal and type
lshw -class network
Post the result so that we can get an accurate idea of the name of your wired network card and the 
name of the driver that it is using.

---

### Post by kevdog on 2007-07-12
Sorry, that was a typo on my part (I hate when I do that)

Its supposed to be the following

sudo ifconfig eth0 down

Sorry

---

### Post by vladuz976 on 2007-07-12
i have to copy this manually but here it goes:

description: ethernet interface
product: 88EE8036 pci-e fast ethernet controller
physcical id:0
bus info:pci@02:00.0
logical name:eth0
version:16
serial:00:13:a9:a7:f8:2b
size:100MB/s
capacity:1Gb/s
width:64bits
clock 33MHz
capabilities: bus_master cap_list ethernet physcial tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotioation
configuration: autonegotioation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=n/a letency=0 link=yes multicast=yes port=twisted pair speed=100Mb/sec


there are 3 routers  in the office,

yamaha remote router RT57i net volante IP:192.168.1.254
NTT webcaster 7000 IP:192.168.1.1
another one without name just a white box

the yamaha is connected to the white box and the NTT webcast. one of the desktops is directly connected to the yamaha. my laptop is wired to the NTT webcast.

I think printers are also hooked up to the network somehow.

thanks

---

### Post by kevdog on 2007-07-12
It sounds like all the "routers" are on the same LAN so in actuality I think only one is functioning as a true router, with the other ones most likely acting as a hub.

Anyway it would be helpful if you knew if the router had a dhcp server in play.  The method described below is only for wired connections -- not wireless

Try
sudo iifconfig eth0 down
sudo ifconfig eth0 up
sudo route add default gw 192.168.1.1
sudo dhclient

Now if that doesnt work, try assigning your computer a static IP address
sudo ifconfig eth0 down
sudo ifconfig 192.168.1.100 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1


See if the above worked with
ifconfig
Try pinging the router ping 192.168.1.1

---

### Post by vladuz976 on 2007-07-12
one more thing is that under DNS it had an IP starting with 33. something
that`s also what`s in /etc/resolv.conf
is it possible that I put the IP of the router I connect to as the nameserver in /etc/resolv.conf
is it possible that it`ll forward it. because the 33. thing doesn`t work. 
and the interesting thing is that my wireless connection shows 95% signal strength and the wired connection also seems to be fine as far as the connection goes. 
so i am wondering if the reason why I cannot reach any site is because it cant translate the domain to an IP.

---

### Post by vladuz976 on 2007-07-12
i tried all suggestions above, nothing works.
dns is assigned automatically by dhcp.
i can ping both routers but nothing else. 
i tried to ping google by using the IP instead of the domain name to see if it is the nameserver what causes trouble. but even so i cannot ping anything.
again, with another windows laptop all it took was plugging in the cable.
what could be going on here?

thanks

---

### Post by Arpan Chakrabarti on 2008-01-11
I have windows xp & ubuntu 7.04 os.In xp i can use my internet service.But in linux i cannot use it.I think ubuntu 7.04 cannot detect my ethernet card,because when i working in linux the light of the network card if off.Please help me for use the internet in ubuntu.

---

