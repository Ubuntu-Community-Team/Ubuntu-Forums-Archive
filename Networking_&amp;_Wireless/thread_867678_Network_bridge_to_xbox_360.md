---
title: "Network bridge to xbox 360?"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by Hazer on 2008-07-23
Hi,

My problem is that I am trying to bridge my wireless laptops connection (wlan0) to my xbox 360 (eth0) I have used ICS which worked but my NAT setting was strict, so i am trying to make a bridge.  I have tried to do:

sudo brctl addbr br0
sudo brctl addif br0 wlan0
sudo brctl addif br0 eth0
sudo ifconfig wlan0 0.0.0.0 promisc
sudo ifconfig eth0 0.0.0.0 promisc
sudo dhclient br0

But I just get a "no DCHPOFFERS received" message so i try to assign it a static address but then my computer loses its wireless connection!

Also could you tell me what settings to use on the xbox.

(PS my first post and I'm only 13 so make it easy to understand for a newbie:lolflag:)

---

### Post by kielanmatt on 2008-07-23
hi my fellow 13 year old i see ur problem and i must say i had it for the last 3 days but i solved it, it is completely do-able for a 13 year old (cause im 13 as well) you just have to pay attention to what you read in this reply

IF YOU REALLY WANT TO DO A BRIDGE THEN DO THIS (but i did summink along the lines of ICS and i got moderate NAT)

```
sudo brctl addbr br0
sudo brctl addif wlan0
sudo brctl addif eth0
sudo ifconfig wlan0 0.0.0.0
sudo dhclient wlan0
sudo ifconfig eth0 192.168.111.1 netmask 255.255.255.0 #if it cannot assign the netmask use ifconfig eth0 192.168.111.1
sudo dhclient br0
sudo ifconfig br0 up
```

then go on your XBOX360 and edit the IP setting manually to 192.168.111.2 , then the netmask to 255.255.255.0 (or leave it to automatic 0.0.0.0 if you couldn't assign a netmask previously on ubuntu) and then set the gateway to 192.168.111.1 . Then you edit the DNS settings and change the Primary DNS to 192.168.111.1 and leave the socondary automatic (0.0.0.0) 

If you want to do it the working way (GUARANTEE) and get moderate NAT, look below

ICS STEP BY STEP

1) remove any bridging software like firestarter
2) type this (you might skip it if you havent made any attempts on bridging your internet by BRCTL)

```
brctl show
```

IF THERE IS ANY BRIDGE (after you wrote the command) LISTED TYPE

```
sudo ifconfig **THE NAME OF THE BRIDGE** down
sudo brctl delbr **NAME OF THE BRIDGE**
```


it is important that we have no internet sharing or bridges before we begin, because you will get very nasty ****

3) type this to come into the root terminal
```
sudo su
```
then it will ask you for your password and if this has been done correctly the command line will say root@(name of you computer)

**NOTE :** on my computer it poped up with account expired but my command line was root@kielanmatt-desktop: /home/kielanmatt# so i recognised it was ok

4)IF you have static IP on your network that supplies you with internet (i am talking about router--->PC not ISP's IP for your house) so step 4.1

IF

YOU HAVE DYNAMIC IP WHICH MOST PEOPLE HAVE ON WIRELESS DO STEP 4.2

BUT DONT DO BOTH

4.1)
```
ifconfig wlan0 **your.static.ip.address** # i wrote wlan0 because i assume the device that supplies your ubuntu box is wireless internet if not change it to what ever device is the internet one like eth0 or summink
```

4.2)
```
ifconfig wlan0 0.0.0.0 # i wrote wlan0 because i assume the device that supplies your ubuntu box is wireless internet if not change it to what ever device is the internet one like eth0 or summink
```
then to enable DHCP
```
wlan0 dhclient #then again if your internet device is not wlan0 substitute it with the one that you have
```

5) you can do this via command line but i dont like it that way
if you do it by command line type this

```
ifconfig eth0 192.168.111.1 netmask 255.255.255.0 #eth0 is your wired card that you connect to xbox if it cannot assign the netmask use ifconfig eth0 192.168.111.1
```

6) now copy all this block of text into terminal and execute all lines

```
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
apt-get install dnsmasq ipmasq
/etc/init.d/dnsmasq restart
dpkg-reconfigure ipmasq
```

then you allow that ppp thing (if you dont get that message dont worry) and SET ipmasq to start after networking has been started

7)then edit a file to enable sharing ```
gedit /etc/sysctl.conf
```
IT SHOULD READ and you remove the # MARKED IN BLUE next to net.ipv4.ip_forward=1

```

# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.  (Added in kernel 2.6.22.)
kernel.maps_protect = 1

# Increase inotify availability
fs.inotify.max_user_watches = 524288

# protect bottom 64k of memory from mmap to prevent NULL-dereference
# attacks against potential future kernel security vulnerabilities.
# (Added in kernel 2.6.23.)
vm.mmap_min_addr = 65536

##############################################################3
# Functions previously found in netbase
#

# Comment the next two lines to disable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling (http://lkml.org/lkml/2008/2/5/167)
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
[COLOR="Blue"]**#**[/COLOR]net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net/ipv4/icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net/ipv4/icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net/ipv4/conf/all/accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net/ipv4/conf/all/secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net/ipv4/conf/all/send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net/ipv4/conf/all/accept_source_route = 0
#
# Log Martian Packets
#net/ipv4/conf/all/log_martians = 1
#
# Always defragment packets
#net/ipv4/ip_always_defrag = 1
```

and then youre done on your PC and you switch on the XBOX 360 and edit the IP setting manually to 192.168.111.2 , then the netmask to 255.255.255.0 (or leave it to automatic 0.0.0.0 if you couldn't assign a netmask previously on ubuntu) and then set the gateway to 192.168.111.1 . Then you edit the DNS settings and change the Primary DNS to 192.168.111.1 and leave the socondary automatic (0.0.0.0)


here you go!

---

### Post by Hazer on 2008-07-23
Thanks,

But i still get a strict NAT with your ICS method (bridge failed at dhclient br0 with a "no dhcpoffers received error:( )

I would really like a bridge to get an open NAT

Your help is much appreciated

---

### Post by kielanmatt on 2008-07-23
well the bridge is not the way (or maybe you could give the bridge static IP) but try to find out how to change NAT settings on ICS or in worst case your NAT might be the fault of your wireless connection (router or the settings on ubuntu or eth0)

---

### Post by Hazer on 2008-07-24
Yeah I try to assign a static IP to the bridge but the computer loses its internet connection:( (I used sudo ifconfig br0 192.168.111.1)


When I was using windows I enabled ICS and initially the NAT was open when i deactivated the firewall but doing so was not preferable because of the hideous security of windoze (Im using it now:() so I created a network bridge in windows which was super trivial and I got an open nat.

Might just make a stripped down windows OS and turn my crappy old laptop into a piece of dedicated networking hardware!:)

P.S could I use firestarter for ICS and do port forwarding on the firewall to improve the NAT?

---

### Post by kielanmatt on 2008-07-24
NAT means Network Address Translation baby, so i dont think port forwarding would help (although i mite be wrong like in most cases)
also keep in mind that firestarter is a piece of firewall and it didnt work out for me same like with the bridge!

just stick to ICS trust you will just waste valuable playing time on live

---

### Post by kielanmatt on 2008-07-24
i think summink like that would open up your NAT

```
sudo su
echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
/sbin/iptables -A FORWARD -i wlan0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o wlan0 -j ACCEPT

```

---

### Post by Pasedaddy on 2008-07-26
Great post since it is one of the only helpful information in this topic. 

One big problem!

ICS is just making another router out of your computer. This does make opening your NAT very hard and it is very tough to configure this network because of all the routers. 

Anyways it would be nice if there was a network bridge wizard like there is in windows.

---

### Post by kielanmatt on 2008-07-26
hehe on linux there is nothing like windows dont even hope for that wizard

---

### Post by Pasedaddy on 2008-07-26
Well I'm just saying it would be great for Linux since if people see things easy on Linux then they are more likely to make the switch. Personally I think the command line is great but if you don't know where to look for a solution to your problem that needs the command line (like what we are doing) and sometimes people don't help you out a wizard would help a lot. I asked twice how to do this an both told me to use firestarter which didn't help me.

---

### Post by Belistner on 2008-09-29
Hi,

I have been trying to do exactly the same thing as Hazer but not getting very far. I will try the advice in this post when I get home tonight, thanks kielanmatt.

One thing I'd like to ask, is anyone using a cross over cable or just a regular ethernet cable (e.g. the one that came with the xbox). I read somewhere it may have to be a cross over cable which got me thinking, I'm not sure if it would.

Lewis

---

### Post by Tom--d on 2008-09-29
I'm using Iptables and ICS from wlan0 to eth0 (360 connected to eth0) and I get modrate NAT. How? Well, I found out that I need a Static IP on my wlan0 (connected to the internet) and a static IP on eth0. Then its moderate. Otherwise its strict. 
I can play Live perfectly :)

---

### Post by saint-takeshi on 2008-10-14
> **Pasedaddy said:**
> Well I'm just saying it would be great for Linux since if people see things easy on Linux then they are more likely to make the switch.

more users who don't like using the command line isn't "great for Linux" because then developers have to spend more time designing user interfaces and making things easier for non-geeks, which leaves them with less time for what they're good at; writing programs to do things, and do them well. i don't know about now, but it certainly used to be the case that linux/open source developers made programs that they needed to use, and if other people found a use for them, then great, but it's not like proprietary software, where maximizing the number of users means more money, so is a priority, from a development point of view.

you're right that a wizard for ICS would be great, and when i have time, i might work on making just such a thing 

(don't hold your breath, i'm still teaching myself C++ and Java, then i'll need to learn to use GTK for making the interface, and by then it'll probably already have been done by someone who actually knows what they're doing)

i'm sure there's a "request a thing" forum where you could suggest the wizard, and developers might take it seriously, if it looks like there's a lot of demand for it or whatever. god, i've gone really far from my original point, haven't i?

i'll stop writing now and go drink more coffee.

---

### Post by novaki on 2009-01-19
I followed this guide and got it working, but now, after I\ve restarted my computer and disconnected it from the xbox, my internet has stopped working. My computer will say that I\m connected to the wireless (or wired) network, but I\m not able to access any websites...

Do you have any idea how this happened? (p.s. I\m pretty new at linux)

---

### Post by nes125 on 2009-12-18
Hello, i have a problem. the steps used here word perfectly the first time i used them but ever sins then my xbox logs out when 1 start a game or somthing. does anyone know what the problem is here ?

---

### Post by chromechipmunk on 2010-04-11
guys if you have an xbox 360, a laptop, a Ethernet cable and you want to use your laptop to get xbox live and you are using Ubuntu, there is a really simple way to achieve it.

Step 1. All you have to do it go to the signal sign thing in the top right corner between sound and battery life and right click it.

Step 2. Click edit connections.

Step 3. When the box titled Network Connections pops up click on wired, then Auto eth0, then click edit.

Step 4. On the box that pops up click IPv4 Settings.

Step 5. Click on the drop down box next to method and select Shared to other computers.

Step 6.  Click apply, then click close and thats its now just plug the Ethernet cable into your xbox 360 then the back of your laptop and then go on your xbox and connect to live. And its as easy as that.

---

### Post by TheHammer23 on 2011-05-05
If you guys want the NAT to be completely open you need to configure port forwarding on your router. You need to forward the ports for xbox live to the wireless address assigned to your laptop (or whatever PC your using as the bridge). You then need to forward these ports to the XBOX from the PC. For this reason I use Firestarter, configuration takes only a minute or two. I forward ports 80, 88, 3074, and 53 as recommended at [Microsofts Xbox Support Site]("http://support.xbox.com/en-us/pages/xbox-live/troubleshoot/connection-issues/nat-type-strict.aspx"). You really don't need to have NAT open to play online, I think it just allows your XBOX to host games and helps matchmaking. Just make sure you forward the ports both on the router and on the PC being used as a bridge.

---

