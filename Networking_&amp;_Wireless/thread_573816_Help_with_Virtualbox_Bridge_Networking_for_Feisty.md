---
title: "Help with Virtualbox Bridge Networking for Feisty"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by jdogzilla on 2007-10-12
Hello all, I am struggling to get bridge networking to work with Virtualbox. 

I am using Feisty 7.04, have both Virtualbox and Vmware Server installed. 
I have followed the instructions from below:
[http://ubuntuforums.org/showthread.php?t=346185&highlight=virtualbox+bridge+network](http://ubuntuforums.org/showthread.php?t=346185&highlight=virtualbox+bridge+network)

I can ping the Virtualbox from my host Linux box, but I cannot ping the Linux box or browse the web with WinXP in the Virtualbox.  Where am I going wrong, and what can I check?  I have a firewall running on my Linux box.  Do I need to do something to configure this?  ANy help will be appreciated. 

Thanks

---

### Post by Jorge on 2007-10-12
Have you installed the VirtualBox additions?

---

### Post by jdogzilla on 2007-10-12
Yes I did ... this is what I have in my rc.local file at this point:

# For Network Bridging/TAP to enable Virtual Box
#Add a bridge, add eth0
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
dhclient br0
# Create tap1
tunctl -t tap1 -u <myusername>
# Enable tap1
brctl addif br0 tap1
ifconfig tap1 192.168.1.80 up
# Change tun permissions
chmod 0666 /dev/net/tun
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap1/proxy_arp'

and I am statically assigning an IP address within the Virtual Machine's network connections.
I can ping my guest from my host, but not my host from my guest. 

My router does not show that it has assigned the 192.168.1.80 address out to anyone. 

Additionally, do I need to do anything on my host firewall?

---

### Post by Jorge on 2007-10-12
As far as I know, VirtualBox uses NAT to manage the guest network. In my case, my LAN uses the 192.168.x.x range of addresses, so my Linux host takes the 192.168.x.Y, while the WinXP guest takes a 10.x.x.Y address. The network requests from the guest are managed by VirtualBox, so there is no LAN-group address asigned to the guest. Therefore, I can not ping from one to another.

---

