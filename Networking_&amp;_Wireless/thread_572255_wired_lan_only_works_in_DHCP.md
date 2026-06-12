---
title: "wired lan only works in DHCP"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by bedwetter on 2007-10-10
I have an Asus F3SV laptop and am having some issues with the wired LAN connection.  If I use DHCP, I can connect no problem.  However, if I try and use a static ip, nothing works.  Other linux boxes on my network are fine with static ip.  Any ideas what the problem might be?

Thanks in advance

---

### Post by kevdog on 2007-10-10
How are you trying to set up your static IP??  Can you post whatever file you have altered?

---

### Post by bedwetter on 2007-10-10
I am doing it through network manager, just selecting staticip and then specifying the ip and gateway I want.  I am a newbie to linux so  I dont know what files are being modified.

---

### Post by kevdog on 2007-10-10
Please do the following and post the output:

cat /etc/network/interfaces

---

### Post by bedwetter on 2007-10-10
Here it is when dhcp is enabled:

```
# The loopback network interface
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

```

and when I try to set static ip
```
auto lo
iface lo inet loopback



iface eth0 inet static
address 192.168.0.7
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

```

Thanks for your help

---

### Post by kevdog on 2007-10-10
Ok here is the general format I follow -- you are mostly correct:

auto wlan0
iface wlan0 inet static
address 192.168.168.40
gateway 192.168.168.230
dns-nameservers 192.168.168.230
netmask 255.255.255.0

The dns-nameserver is in your case the gateway.

Try editing your /etc/network/interfaces file (gksu gedit /etc/network/interfaces) and adding the dns-nameservers line

You have to be more specific in saying it doesnt work!! Does that mean you dont get assigned a dhcp address, or your router or gateway isnt working.

After trying to connect with network manager please troubleshoot with
ipconfig
route -n

---

### Post by bedwetter on 2007-10-10
I got it to work.  I used the network manager to set the static ip, then checked ifconfig and it was still saying I was using the address previously assigned my dhcp.  I manually changed the ip with ifconig and it is now working.

Thanks for your time.  Sorry about the vague question.

---

