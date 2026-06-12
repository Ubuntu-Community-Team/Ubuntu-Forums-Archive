---
title: "How to: Setup ICS / NAT under 8.04"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by NickZA on 2008-08-09
Hi All,

This is a guide I wrote for myself, next time I need to get this up and running. It's basically a sequence of steps specific to my situation but has explanations which should allow you to adapt it to your needs.

**How To: Get Ubuntu ICS running (Ubuntu 8.04 Server talking to Ubuntu 8.04 client or Windows XP Pro client)**

Based loosely on this documentation:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

[on server]

1. Get rid of network manager as it does not play nice with static IPs, which we need for ICS. Go to Synaptic and uninstall it. That means both the vanilla/unnamed version and the gnome version too. (2 packages, though there may be other related packages that synaptic will ask you to uninstall. Agree to this prompt.) Don't hesitate, you will note in synaptic if you read network-manager's description that it was never intended to run on servers, it is for clients which need automagic configurability.
2. Setup your network interfaces:
$ sudo gedit /etc/networking/interfaces

...and insert the following:

auto lo
iface lo inet loopback

#Your internet interface, change eth0 to whatever your internet interface name might be
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.up.rules

#LAN interface, change eth1 to whatever your LAN interface name might be
auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

...Note that your internet interface is "dhcp" (if you choose to even specify it at all), and LAN interface must be "static". This is because a DHCP server requires a static IP to be able to work (i.e. for it to assign addresses from, since it cannot assign an address to itself if it does not yet have an address!).

3. Install dnsmasq (already done by default for Ubuntu 8.04)

4. Make necessary changes to /etc/dnsmasq.conf:

interface=eth1
dhcp-range=192.168.0.100,192.168.0.250,72h

...This is likely all you will need in this file, on my 8.04 everything else was commented out by default.

5. Restart the networking daemon to take advantage of the new settings:
$ sudo /etc/init.d/networking restart

[on client]

6. $ dhclient eth0 
...to renew DHCP connection. May not be necessary, but strongly suggested so you can tell if you are now getting IPs successfully from your new DHCP server (as set up by DNSmasq). Read the output of the command to see if you're being assigned an IP in the correct range. At this stage, hostnames should resolve to IPs on the client (meaning DNS is also good to go) but IP forwarding is not yet enabled (as even direct IP address pings do not work). So next we get that going using iptables.

[back on server again]
7. Configure iptables for NAT translation so packets can be correctly routed through the Ubuntu server.

$ sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
$ sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
$ sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

(FYI: rule1 allows forwarded packets (initial ones), rule2 allows forwarding of established connection packets (and those related to ones that started), rule3 does the NAT.)

8. Enable routing

Configure the server for routing between two interfaces by enabling IP forwarding:

$ sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward" 

The above slightly odd syntax is required to get the correct permissions. FYI: There is a "Bug" in Ubuntu 7.10, and which I believe persists in 8.04 (At least, this fix didn't hurt in 8.04 so best to include it). So you will need to make a small edit in /etc/sysctl.conf

Add these lines :

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
If adding this in 8.04 note there is also a commented line in the default sysctl.conf which reads:
net.ipv4.ip_forward=1
...You can uncomment this as well as inserting the other two, just to make sure forwarding is enabled.

If you now attempt to ping, say, google.com on the client, you should be rocking. If any doubts, do:

[server]
$ sudo /etc/init.d/dnsmasq restart
$ sudo /etc/init.d/networking restart

[client]
dhclient eth0

---End Basic Setup.---

Step 9.
Now, if you want these features to persist beyond server reboot, there are is 1 step you need to make permanent. This is step 7, above.

First we need to issue the below three lines in the shell, thereby affecting the current iptables setup to get it into the correct state. If you have just executed steps 1-10 above, you can skip this as you'll have just done this (step 7). However if you've rebooted since then you'll need to issue these again:

$ sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
$ sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
$ sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

Once you've done this, save the current iptables configuration using:

sudo sh -c "iptables-save > /etc/iptables.up.rules"

(Note, you MUST use the above sh -c method as you cannot use default sudo (-s) with iptables-save -- you will get "permission denied". See here: [http://ubuntuforums.org/showthread.php?t=545296](http://ubuntuforums.org/showthread.php?t=545296) )

Now we can edit interfaces and bring everything together.

sudo gedit /etc/networking/interfaces

And modify the block/body of the main internet link (usually eth0) to contain the pre-up statement you see (uncommented) below:

#Loopback interface
auto lo
iface lo inet loopback

#Internet interface
auto eth0
iface eth0 inet dhcp
#<--pre-up firewall loading can be done here
pre-up iptables-restore < /etc/iptables.up.rules

#LAN interface
auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
#<--pre-up dnsmasq/ipmasq loading can be done here if you deem it necessary, purely optional though

"pre-up iptables-restore..." will restore the iptables settings we saved above, everytime we start up.

And that should be all there is. If you now reboot, everything ought to be bound correctly and you can get going on your LAN systems; irrespective of OS you are using on them, they should be able to see the each other and the internet.

SEE TROUBLESHOOTING IPTABLES FOR MORE INFO: 

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)


**end of How To**

I hope you have some luck with it! I find typically I have to use about 3 or 4 guides (good ones) together to get the answers I need for any specific middlingly-complex task like this. You might need to do the same.

-Nick

---

### Post by The Foz on 2008-11-18
Hi,

I have a question about your excellent How-To.

You have the following command:
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT

I saw the same command in the Community Documentation on how to set up Internet Connection Sharing.

Are you sure that it is the right way around? Reading the man pages on the iptables command, it says that "-i" is the input device, and "-o" is the output device. The command would therefore seem to say that NEW connection requests from eth0 (the Internet interface) should be forwarded to eth1 (the LAN interface). This seems wrong; I would have expected that requests from eth1 should be forwarded to eth0.

---

