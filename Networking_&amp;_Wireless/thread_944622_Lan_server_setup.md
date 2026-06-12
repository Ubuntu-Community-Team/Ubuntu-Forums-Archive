---
title: "Lan server setup"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by zidane on 2008-10-11
Hello All

I am a newbie to linux, although have been using ubuntu 8.04 since it came out. I wonder if you could assist me with the following ( I have had a look at the threads but did not find the info i think i needed?)

I am looking to setup a Home network.

I have a old dell PC which I would like to make my home network server. 

I want to install unbuntu on this and then share my Internet from it to my other pc's which will have a mix of windows and linux. The dell pc has 2 nic cards. I am hoping to have some files/photos/music on the dell server for sharing to the other pcs's.

One nic (eth0) is connected to a router which provides adsl internet. The internet address is dhcp starting with;
 inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0

I then want to connect my other pc's using private address 10.0.0.x/255.255.255.0 which will be a mix of winXP and linux.

Can someone explain how I go about completing the complete setup. 

That is setting up the dell pc as the LAN server which get internet on one of the NIC cards and then I am able to get the other PC's on the internet using the other NIC card in the dell pc.

Do I attach a switch to the second NIC card and then attach all the other pc's to that switch using patch cables. Also do attach patch cable from the second NIC card to the switch. also the switch has dhcp so any computer plugged into the switch should have ip address dynamically assigned. 

I hope someone can assist me with this matter or point me in the direction of documents that are to explain the methods thoroughly.

I thankyou for you assistance ion this matter an apologise if the question appears dumb

---

### Post by Iowan on 2008-10-11
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a link on Internet connection sharing.  You might also check the [Perfect Server]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") How-To at howtoforge.com.

---

### Post by cariboo on 2008-10-11
You should also include a switch if you want to connect to more than one computer on you network.

Jim

---

### Post by zidane on 2008-10-12
Hello jim

thanks for reply. Should I connect the switch to the 2nd NIC card or connect the switch to the router and then the other computers to the switch. 

My ip address is set dynamically by the ISP and I want to set the IP on my 2nd NIC using possibly 10.x.x.x which would then be able to dhcp IP addresses to the other computers on my network

---

### Post by Iowan on 2008-10-13
> **zidane said:**
>  also the switch has dhcp so any computer plugged into the switch should have ip address dynamically assigned.  I doubt it... but I suppose it's possible.  The router, on the other hand, is probably capable of handling the DHCP duties - and the 192.168.0.3 is probably an address assigned by the router.  Attaching the switch to one of the router's ports would *probably* get IP addresses assigned to other network machines in the 192.168.0.x range. The 10.x.x.x is another of the private IP ranges.  If you prefer it, the router could probably be changed to use these instead.  Or, you *could* have the server assign DHCP addresses via the 2nd port - and attach the switch to that second port.  Confused yet? :)

---

