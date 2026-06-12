---
title: "Howto ISDN NetMod USB Modem share connection and Wireless Router WRT54G"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by riomacho on 2008-06-11
I live in Costa Rica and the only semi-decent connection I can get is ISDN, since I live outside the coverage area for real broadband.  I had shared the connection between 2 PCs using a crossover cable and their ethernet cards.  However I purchased a laptop, a printer and a Wii and got a hankering to implement a wireless home network.  Apparently it is now working, so here is a guide.   

The problem with the wireless routers is that none in Costa Rica came with USB or serial cables for connecting to the Internet.  If you can find one that does, and will dial your ISP, then you can probably bypass the tutorial.  If you can't, then you have to use one PC as a gateway to dial up and to share the connection.  I thought of using the gateway PC as a router, but was unable to get any set up to work in conjunction with the router.  So I now have the following set up:
ISP -- RJ11--> Netmod Modem (ppp0) &#8211; - USB cable --> Gateway PC (eth0 10.0.0.1) ---> WRT: Internet Port (10.0.0.2) + Router IP (192.168.1.1) ---> LAN (DHCP clients)

Download the attached diagram (Open Office Presentation file)  if you like. 

The key breakthrough was realizing that the router could be fooled into thinking that the gateway PC was the ISP.  The Internet Port on the router is an Ethernet port, so it can connect to the gateway PCs eth0 card.  Basically I have two separate networks 10.0.0.0 on subnet 255.255.255.0 and 192.168.1.0 on subnet 255.255.255.128.  I am able to tell the WRT54G the &#8220;ISP's&#8221; (gateway PC) static network information.   

**Step 1 &#8211; Configure PC connected to Internet. **
This PC must be in a static configuration and configured first, before connecting anything to the router.   I found it helpful to uninstall Network-Manager on this PC using Synaptic GUI (Adept in Kubuntu). 

In a terminal type or paste (you can also use gedit in Ubuntu or kate in Kubuntu):
sudo nano /etc/network/interfaces

Some configuration will be set, alter the file to match:
auto lo
iface lo inet loopback
	address 127.0.0.1
	netmask 255.0.0.0
# use if you have one network card eth0 should work.  
# If you have a wireless or second card, then it might be different. 
auto eth0
iface eth0 inet static
	address 10.0.0.1
	netmask 255.255.255.0
Save (ctrl+o, then enter) and Exit (ctrl+x)

**Step 2 &#8211; Configure Router WRT54G version 8**
Connect a cable to a second PC that is setup to get an IP address via DHCP (default in Ubuntu). Connect a normal ethernet cable to the router's Internet port.  Power on the router.  Log in to the router's admin using the default address (192.168.1.1) in Firefox, Konqueror or other.  If you can't log in, then hit the reset button on the back of the router for 5 seconds.  No user name is needed and the default password is admin.  There are several menu items to adjust.  
a)Basic Set Up tab &#8211; Change Internet connection type to Static IP, new fields will appear.  Internet IP Address = 10.0.0.2 Subnet Mask = 255.255.255.0 Gateway = 10.0.0.1   Static DNS1= XXX.XXX.XXX.XX Static DNS2 = XXX.XXX.XXX.XX ***** Network Set up section, change Subnet mask to 255.255.255.128 (Save changes)
b)After saving the changes, you will get a message to renew your lease.  Good!  Go into a terminal and type sudo ifdown eth0, wait for the confirmation message (ie: DHCPRELEASE on eth0....) Now type sudo ifup eth0 and wait again for confirmation  You can reconfirm your success with the ifconfig eth0 command
1.yourprompt:~$ ifconfig eth0
2.eth0   Link encap:Ethernet  HWaddr 00:13:D3:97:75:DC
3.          inet addr:192.168.1.100  Bcast:192.168.1.127  Mask:255.255.255.128
4.          inet6 addr: fe80::213:d3ff:fe97:75dc/64 Scope:Link
5.          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
6.          RX packets:896 errors:0 dropped:0 overruns:0 frame:0
7.          TX packets:1734 errors:0 dropped:0 overruns:0 carrier:0
8.          collisions:0 txqueuelen:1000
9.          RX bytes:763502 (745.6 KiB)  TX bytes:156304 (152.6 KiB)
10.          Interrupt:16 Base address:0xc000
c)Now you can confirm your physical set up, go to the gateway PC and repeat the ifdown, ifup process in part b) above. (not necessary?) In this case you will not get confirmation, because it is a static IP.  You can now ping all devices on your network go back to the DHCP PC, from a terminal run this command:  ping 10.0.0.2 -c 5  This is the router, now ping  10.0.0.1 -c 5  That is the gateway PC!

But you still can't surf the web, you have to tell the gateway PC to forward packets and allow masquerading.  Depending on what use you may have for the gateway PC, you can make it a DMZ &#8211; which means it is open to the web and forwards all packets.  This is what I will explain in Step 4.  However if you need to use the PC and keep any documents or information on it, then you will want to set up addition policies and rules.  You may do this directly in IP tables, or using a firewall front end like Firestarter or Arno IP tables.  I have not had success with Firestarter but Arno was easy to configure and worked right away. 
**Step 3 &#8211; Iptables set up (Basic)**
Run the following commands in a root terminal (Ubuntu type sudo -i in a normal terminal. Kubuntu choose a new root terminal from the terminal menu) (each line separately)
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
# Set up IP FORWARDing and Masquerading
iptables --table nat --append POSTROUTING --out-interface ppp0 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
exit

Now try from your wired PC, you should be able to visit web sites ! 
**Step 4 - Client Set up **
Now you can set up your other devices to connect to the wireless router, either with a wired or wireless connection.  You should be able to use the system settings in Kubuntu (Kmenu&#8594; System Settings &#8594; Network Settings + admin mode) or the Network Settings in Ubuntu (System &#8594; Administration &#8594; Network) In a terminal type or paste (you can also use gedit in Ubuntu or kate in Kubuntu):
sudo nano /etc/network/interfaces

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

#iface ppp0 inet ppp
#provider ppp0

**Step 5 &#8211; Advanced Router Configuration**
There are some other items you must configure on your router.  Look at the documentation or online, but the main one is SECURITY.  Wireless security is very important, so make sure to go to the wireless  tab in the web browser and set up your network name and password.  (see router manual) WPA2 Personal or WPA Personal are the recommended security levels, since WEP is easy to hack.  

Good Luck!

---

### Post by matt.cohenprice on 2009-03-27
Riomacho,

thank you - this is about to be really helpful. I am also in Costa Rica (Monteverde area) and a friend has a coffee shop where she has internet but can't offer wifi because she has the same unfortunate NetMod ISDN modem. Right now, we're looking for an old computer nobody needs (not quite as easy to find here as in the States) I can throw ubuntu on for the sole purpose of trying to make your Howto work for us. 

SO, I'll probably be hitting you up with some questions once I get a hold of that machine and start trying this.

I do have a few questions right off the bat, though.

Step two, you say: "Connect a cable to a second PC that is setup to get an IP address via DHCP (default in Ubuntu). Connect a normal ethernet cable to the router's Internet port." Should the daisy chain be set up at this point (gateway computer eth0 --> router's internet port, and router's LAN port --> personal computer's eth0)?
 
Why is the network subnet mask 255.255.255.128, as opposed to the typical 255.255.255.0?

Step 3, re ARNO - is ARNO a program I would need to install onto the gateway machine, or do I just follow those terminal steps and that's all I need? I would like to use the machine to access internet and store files, if possible.

Thanks for the Howto!

---

