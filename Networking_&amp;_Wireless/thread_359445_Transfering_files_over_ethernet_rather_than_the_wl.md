---
title: "Transfering files over ethernet rather than the wlan"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Eschatokyrios on 2007-02-12
I have a laptop running Ubuntu 6.06, and a desktop running SuSE 10.1. The SuSE computer has several Samba shares set up, and I can see these from the ubuntu computer under smb://. The problem is that when I try to transfer large files, they go very slowly, less than 100 kbps. 

Both the desktop and the laptop are linked with a cat 5 crossover cable, which is eth0 on the laptop. Both computers are also connected to my wireless lan, on wlan0. I only want to use the wlan to get an internet connection, but I suspect that the files are also being transferred on the wlan. I want the samba share files to be transferred over the ethernet cable only. How do I ensure that that happens?

---

### Post by ciscosurfer on 2007-02-12
> **Eschatokyrios said:**
> I have a laptop running Ubuntu 6.06, and a desktop running SuSE 10.1. The SuSE computer has several Samba shares set up, and I can see these from the ubuntu computer under smb://. The problem is that when I try to transfer large files, they go very slowly, less than 100 kbps. 

Both the desktop and the laptop are linked with a cat 5 crossover cable, which is eth0 on the laptop. Both computers are also connected to my wireless lan, on wlan0. I only want to use the wlan to get an internet connection, but I suspect that the files are also being transferred on the wlan. I want the samba share files to be transferred over the ethernet cable only. How do I ensure that that happens?Let me be the first to welcome you to Ubuntu Forums!  We are a happy community of users that like helping people out.  If you have any questions at all, someone will be able to tackle them and get back to you with comments and/or solutions :-)

As for your question, I doubt the packets are being sent over both connections, but you can make sure of this by installing iptraf and checking that way  (open a terminal session and enter in the following code):```
sudo aptitude install iptraf
```Open a terminal and enter in **sudo iptraf** to get it started.  Iptraf is a comprehensive tool and you can check many things.  In your case, you can select the first options on the first two screens, and then try sending files between your machines...the monitor will show you which connections are being used, etc.  Post back your results.

---

### Post by Eschatokyrios on 2007-02-15
> **ciscosurfer said:**
> Let me be the first to welcome you to Ubuntu Forums!  We are a happy community of users that like helping people out.  If you have any questions at all, someone will be able to tackle them and get back to you with comments and/or solutions :-)

As for your question, I doubt the packets are being sent over both connections, but you can make sure of this by installing iptraf and checking that way  (open a terminal session and enter in the following code):```
sudo aptitude install iptraf
```Open a terminal and enter in **sudo iptraf** to get it started.  Iptraf is a comprehensive tool and you can check many things.  In your case, you can select the first options on the first two screens, and then try sending files between your machines...the monitor will show you which connections are being used, etc.  Post back your results.

Wow, the Ubuntu forum posters are so much friendlier than the SuSE forum posters! :D Thanks for the welcome.

Iptraf shows everything I'm trying to do over the network as going through wlan0, as I suspected. I'm getting absolutely no traffic on eth0. I suspect I'm just not looking in the right spot in the file system to get onto eth0. Can someone explain what I need to be doing?

---

### Post by gradedcheese on 2007-02-15
Is the WiFi on the same network and subnet as the LAN?  If so, you shouldn't have two interfaces up on the same subnet...  For example, when you run "ifconfig", what are the IP addresses for eth0 and wlan0?  If they're on the same subnet, you don't have much choice as to which one will be used (and other issues will come up).  Stop the WiFi interface ("sudo ifdown wlan0") and eth0 will be the only choice.

---

### Post by Eschatokyrios on 2007-02-18
ifconfig doesn't give any ip address, just a ipv6 address with a bunch of hex numbers. I assume I have to set the ip address myself in Networking or something, but I don't know what IP I should pick. Is it alright to just pick one arbitrarily?

---

### Post by gradedcheese on 2007-02-18
you have DHCP though, right?  You can ask for an IP:

sudo ifconfig eth0 dhcp
sudo ifup eth0

or you can manually run dhclient:

sudo dhclient eth0

---

### Post by Eschatokyrios on 2007-02-19
I don't think I have the DHCP client installed on the desktop, unless suse does it automatically. I tried dhclient and it didn't get anything eth0, so I'm inclined to believe I don't have it. But do I really need it for a network with just two computers on it?

---

### Post by gradedcheese on 2007-02-19
You have a dhcp client on every PC, you just don't have a DHCP **server** apparently.  For just two computers, that's fine.  Assign them different static IPs (on the same subnet).  Use a hub or switch or one crossover cable.

---

### Post by Eschatokyrios on 2007-02-24
Okay, I manually assigned different IPs to eht0. I don't entirely understand the concept of subnets, but I'm fairly sure that eth0 and wlan0 are on different ones. ifconfig lists the mask of eth0 as 255.255.255 with an IP of 172.16.20.3, while wlan0 has a mask of 255.255.0.0 and the ip that DHCP gave it. But when I try to transfer something iptraf still shows all the traffic as going over wlan0, and going slowly.

---

### Post by RandomJoe on 2007-02-24
Did you set an IP for the wired port on the other machine as well?

Subnets tell what range of IPs is directly reachable for a given port.  (More or less, in a nutshell...)  It isn't the subnet that needs to be different from the WLAN port, rather the IP address.  The subnet is a function of the overall network architecture, which in your case isn't a big deal - just be sure the subnets are set the same on either side of the wired link.

What I would do in your situation, is set one computer's wired port to:
IP: 192.168.1.1
Subnet: 255.255.255.0

And the other's wired port to:
IP: 192.168.1.2
Subnet: 255.255.255.0

Assuming your wireless connection doesn't use 192.168.1.x.  If it does, for the above settings change the third number to something higher.  (192.168.123.x for example.)  You can use any of 2-254.

Then be sure you use the other computer's wired IP when browsing the share - smb://192.168.1.1 - if you use the hostname odds are it's going to resolve to the wireless IP and once again go over the WLAN.

---

### Post by Eschatokyrios on 2007-02-25
RandomJoe: that worked! Thanks.

---

