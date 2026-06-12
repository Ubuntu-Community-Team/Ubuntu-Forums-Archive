---
title: "Raspberry Pi cluster - 2 machines, static eth0, 1 with wifi and other with AP"
date: 2020-05-13
forum: Networking &amp; Wireless
---

### Post by andrewsawyer on 2020-05-13
Hi,

It's been a while since I've posted here, and I'm definitely stuck.

I've installed Ubuntu 20.04 on some Raspberry Pi 4's, with root mounted on SSD's. It's all working well from that perspective, however I'm less than competent when it comes to networking and I've hit a road block. Hoping someone can help.

The basic plan is as follows:

Machine 1 - Ubuntu Desktop, Wifi with DHCP, eth0 as a static IP 10.10.10.1
Machine 2 - Ubuntu Server, Access Point, eth0 as static IP 10.10.10.2

Both headless machines.

If I'm on a known wifi network, Machine 1 will connect and I'll be able to remote desktop or ssh into it. If the wifi network is unknown, I'll be able to connect to Machine 2 via it's access point, and link across to Machine 1 to add the wifi network, or just get on with whatever through the access point.

Given that at any time, the only connection that the machines will have to 'the outside world' will be through the wifi network on Machine 1, both machines will need to share this connection.

If I make any changes to the file in /etc/netplan/ on Machine 1, then while I can still connect to the wifi, and ssh between the machines on the ethernet, I can no longer access the Internet for some reason (I can access other computers on the home network though), and Ubuntu Desktop says the wifi is unavailable and I can't do anything with it.

Please help!

---

### Post by andrewsawyer on 2020-05-13
By the way, if anyone is interested, below is the plan, and I'm documenting all the steps so that anyone else can follow in the future:

There are actually 4 machines, however the above simplifies it somewhat by just calling out two. The other two will simply be Ubuntu Server 20.04 with eth0 set as static - 10.10.10.3 & 4, using the wifi network on 10.10.10.1 (Machine 1) to access the Internet. I'm going to have Docker Swarm running across them (it's way easier to set up than K8s) with Jupyter Labs, PostgreSQL and potentially pySpark. The standard python will also be configured with MPI so I can do parallel compute with it. 

I'm currently studying a Master of Data Science, Strategy & Leadership, and this is a bit of a hobby project to get something set up that I can actually use (although to be honest a 4x Raspberry Pi set up still probably doesn't even compete performance wise with my laptop).

---

### Post by andrewsawyer on 2020-05-14
Ok - I've managed to progress.

Rather than using the default GUI, I used nm-connection-editor. When I used this and shared my ethernet connection, it didn't update my IP address like the default GUI did. So it's now shared and everything seems to be working :-)

---

