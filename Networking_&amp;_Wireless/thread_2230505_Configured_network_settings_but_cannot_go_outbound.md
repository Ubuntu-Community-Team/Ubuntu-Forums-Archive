---
title: "Configured network settings but cannot go outbound **Networking Issue**"
date: 2014-06-19
forum: Networking &amp; Wireless
---

### Post by numan2 on 2014-06-19
Hi all,

I stood up my first Ubuntu Server 14.04 and added the following network settings:
sudo vim /etc/network/interfaces
auto eth 0
iface eth 0 inet static
address 10.4.1.103
netmask 255.255.255.0
network 10.4.1.0
broadcast 10.4.1.255
gateway 10.4.1.1
dns-nameservers 10.4.1.1

When I run the following command to restart the network sudo /etc/init.d/networking restart
nothing happens.  I did do sudo restart but I'm sure if that restarts networking...

I can't reach the Internet... I wanted to do an apt-get for gnome GUI.  

The server is in a DMZ and I'm looking at the Palo Alto logs and it's not reaching.  

Any ideas?

Thanks!

---

### Post by numan2 on 2014-06-23
Anyone??? Do I have the basic settings under network for me to reach the internet?

Thanks

---

### Post by steeldriver on 2014-06-23
I assume 'eth 0' is a typo?

What have you done so far to diagnose it? Can you ping the gateway? what's in the dmesg log for eth0?

---

### Post by numan2 on 2014-06-23
Sorry, 'eth 0' was a typo I have it correct on the server.

I cannot ping the gateway and I did a dmesg | grep eth0 but i didn't see anything for ipv4 listed.. I'm not sure if I was suppose to.

I see the following under dmesg... ipv6 eth0 link not ready, bnx2 using msi, bnx2 nic copper link is up, 1000 mbps full duplex

I going to try to ping the server from the firewall.

---

### Post by numan2 on 2014-06-23
I connected a laptop to the dmz switch and gave it a IP on the 10.4.1.0/24 network.  I can ping the server 10.4.1.103.  However on the laptop I was not able to ping the gateway.

---

### Post by SeijiSensei on 2014-06-23
Some routers have ping disabled.  On the laptop, can you browse to websites or ping other machines offsite?  Did you build the gateway?

---

### Post by numan2 on 2014-06-23
On the laptop I cannot reach the internet.  Wireless is disabled and I cannot ping other machines.  I'm thinking is has to be a rule on the palo alto that is not allowing me to go out to the Internet.  But when I check the logs for the server's IP address it doesn't reach there...

---

### Post by numan2 on 2014-06-24
I'm going to blow this server away and reinstall ubuntu and setup network settings during install.

---

### Post by numan2 on 2014-06-24
Question, if I want to reinstall ubuntu server do I need to delete the old image or can I just pop in the CD?

Thanks

---

### Post by numan2 on 2014-06-24
I just reinstalled Ubuntu by putting the in the live CD and configured the networking setting again but I'm having the same issues as before.  I cannot go out to the Internet from the server nor do I see any logs on the palo alto fw.    

I added more name server dns:  10.4.1.1, ISP Cox, 8.8.8.8 to see if it is a dns issue... doesn't look like it.

Everything is on a 10 network.  Below is how it's setup:

Using a PA-200 FW and it has 4 ports...

Port 1 is connect to the ISP for external.  Port 2 is the DMZ (10.4.1.0/24).  The DMZ is connect to to a dmz switch.  From the switch it's connected to the server on eth0.  

I know it shouldn't be this hard but this is driving me crazy.

---

### Post by John Chambers on 2014-07-24
So has anyone found any good answers to this question?  I've been experimenting with (k/x)ubuntu 14.04, and found the same problems every time.  The installation always fails to find network access, and it's difficult to find useful information on how to set it up.  I can't imagine that any novices could solve the problems, and would conclude that ubuntu simply doesn't allow Internet access.

The most annoying part is that googling for things like "beginner ubuntu install" turns up lots of guides, but all seem to start with instructions to use apt-get to install and start various useful things.  But this totally fails, because the newly-installed system can't see the Internet.  

I haven't found any set of keywords that turns up a coherent guide to how to get the Internet access up and running.  I've installed 14.4 on a number of machines, each time stumbling around, finding that what I did to get the previous one working doesn't work on the current installation.  It'd be really useful if we had a good "troubleshooting" guide for solving these basic installation problems that are being asked about all over.  A guide that assumes you have internet access is not useful, though, since that seems to be one of the first things that always fails.

One thing I've found is that "network-manager" seems to be running by default, and you need to edit /etc/network/interfaces (and apparently reboot, though there may be some way to test changes without a reboot).  The problem here is that everything I've found about it has examples that aren't explained, and they're all different.  Thus, do you need a "gateway" address?  If so, what address should it be?  What's the correct syntax to tell it about nameservers?  How is a novice to figure these things out?  What do you ask your ISP to get the correct values?

(It's likely that there are good answers to such questions somewhere, but I haven't found them, and they really should be included with the startup stuff in a way that the installer can easily find them.)

---

