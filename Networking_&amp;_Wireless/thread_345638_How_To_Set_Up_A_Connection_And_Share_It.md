---
title: "How To Set Up A Connection And Share It?"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by antiwindows798 on 2007-01-21
In Fedora you can choose to get network applications installed. After you install the Gnome desktop, you get under the System, Administration, Network menu a few menu items: DNS, Samba, Processes, etc. I have installed Ubuntu Server and it's not there. Why not? How should I get down to networking in Ubuntu?

---

### Post by DerHesse on 2007-01-21
Have you installed DNS, DNS, Samba etc?
):P

---

### Post by antiwindows798 on 2007-01-21
What? During the Ubuntu Server installation, I was asked whether I wanted to install a LAMP server or a DNS server, I have chosen DNS server.

Furthermore, I have looked what kind of packages were available and I haven't seen anything about DNS, except some DNS BIND or something like that application that looked nothing like the DNS application I'm got used to in Fedora.

---

### Post by antiwindows798 on 2007-01-21
:confused:

---

### Post by Bachstelze on 2007-01-21
Could you please be more precise ? What exactly do you want to do ?

---

### Post by antiwindows798 on 2007-01-21
I want to be do the following things:
[LIST]
[*]Be able to configure DNS settings.
[*]Be able to configure DHCP settings.
[*]Share an internet connection with a Windows computer.
[/LIST]

As I have said, I'm a little bit used to Fedora and the network applications it provides through the Gnome desktop, but I really want to stay in Ubuntu.

---

### Post by Bachstelze on 2007-01-21
Internet Connection Sharing can be done pretty easily. [Here](https://help.ubuntu.com/community/InternetConnectionSharing)'s how.

---

### Post by DerHesse on 2007-01-22
[FONT=monospace]So you would need:
[/FONT]```

$ sudo apt-get install bind9 bind9-doc gbindadmin dhcp3-server dhcp3-common samba samba-common
```[FONT=monospace]
and probably other dependencies which will be installed automatically.
[/FONT]

---

### Post by antiwindows798 on 2007-01-23
I have followed everything at [https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing) and everything went well, except that I have made on mistake, instead of using eth1, I have used eth0 (which in my case is the other way around than what page says).

So how can I undo the changes that I have made to eth0?

---

### Post by kidders on 2007-01-23
Hi there,

I took a quick look at the URL you posted. It's important to understand each of the steps involved in connection sharing ... ie setting your box up as a router.

**$sudo ifconfig eth0 192.168.0.1**: This assigns an IP to the eth0 interface manually. To reverse this setting, simply repeat the command to assign a different address. If eth0 used DHCP, the setting will probably be overrideen anyway, when you next restart the connection.

**$sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE**: This allows your PC to use eth0 to communicate on behalf of other PCs (presumably connected to eth1), and handle packets coming back into eth0 appropriately. To undo this, delete the appropriate iptables rule with a command that starts something like **sudo iptables -t nat -D PREROUTING...** Then, add your revised rule back into the firewall.

**$sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"**: This turns off a security feature designed to prevent your PC from being manipulated into handling packets it didn't create. You still want this feature off, so you don't need to worry.

---

### Post by antiwindows798 on 2007-01-24
Thank you, I will try that as soon as I get back home (I'm currently at work). And yes, I'm of course doing my best to understand what each step means.

---

### Post by antiwindows798 on 2007-01-24
Wait a minute, what about undoing the last steps?

$sudo ifconfig eth<x> <ip>
$sudo route add default gw <ip>

---

### Post by kidders on 2007-01-24
> **antiwindows798 said:**
> Wait a minute, what about undoing the last steps?

$sudo ifconfig eth<x> <ip>
$sudo route add default gw <ip>

These seem like client-side commands. Ordinarily, these are overridden when you restart the network interface, although you *might* need to manually remove the route. Take a look at route's man page for info about listing your current routes and removing ones you don't want. (Unwanted route settings can sometimes cause odd behaviour.)

---

### Post by antiwindows798 on 2007-01-24
I have two computers here: one with Ubuntu and one with Windows.

The Windows computer has one network card.

The Ubuntu computer has two network cards:

eth0 is the network card that connects to the Windows computer.

eth1 is the network card that connects to the internet.

What I want to do:

1. I want to connect to Ubuntu and Windows. I can't even ping to the Windows computer (nor can I ping to the Ubuntu computer from Windows), even if I give eth0 an IP address, like this: $sudo ifconfig eth0 192.168.0.1.

2. The most important part is to make Ubuntu share its internet connection with Windows.

In order to achieve that, I have find this link: [https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

I don't understand it. First of all, it says "first, configure the interface of your network card, for example using eth0 or eth0:0 like so:

$sudo ifconfig eth0 192.168.0.1"

In this case, eth0 means the network card that connects to the internet. What? I already have an internet connection! So I already have an IP address for eth1.

Secondly, it says: " then configure NAT on iptables:

$sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
$sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward""

Now I assume that "etho" in case refers to the network card that is connected to the internet.

Then it says "then move on to the clients". Clients? The Windows machine?

I have respect for the open source community and all but this is outrageous, FOR CRYING OUT LOUD DOCUMENT THESE THINGS! THAT'S WHY PEOPLE STAY IN WINDOWS OR RUN BACK TO WINDOWS! This is supposed to be easy, but how the **** should I get to know how to do these things if it isn't documented anywhere? Configuring my ATI driver took me 5 hours to do so, after 5 hours of research I finally found something that helped me find a solution. How pathetic is that? New ATI videocard + new Linux = 5 hours of having to waste my time trying to get it to work? Now I have wasted 5 more hours further trying to set up a network to share my internet connection to a Windows PC.

Does anyone know the solution?

---

### Post by antiwindows798 on 2007-01-24
??????

---

### Post by roger99 on 2007-01-24
How do you connect to the internet, do you use a router?  If so does it not have multiple ethernet ports on the back?

If you are using a router but it only has one ethernet connection, then the best soloution would be to get yourself an ethernet switch to share the router between the two computers.  If the only option you have is too connect the windows computer to the Ubuntu machine then make sure you have a cross-over ethernet cable as a straight through ethernet cable will not work in this instance.

---

### Post by antiwindows798 on 2007-01-24
I don't have a switch, router or anything unnecessary like that. I have two computers (one with Windows with one network card. And the other computer runs Ubuntu and has a network card to connect to the Windows computer (through a cross-over ethernet cable). In addition, the Ubuntu computer also has a network card to connect through the internet).

Before I decided to switch over to Ubuntu, I had Windows on both computers and I shared an internet connection through the computer that is now running Ubuntu.

I'm definitely not going to buy anything extra for this. I may be a Linux noob, but I'm by far not a computer noob (I'm a programmer) and from my experiences, I can say that this is something simple to configure.

If I'm not mistaking, my Ubuntu computer needs to serve as a DHCP server, through which the Windows computer gets its IP address. From there on, the Ubuntu computer has to share an internet connection back to Windows. End of story, right?

So can anyone tell me how to do it with the terminal?

---

### Post by kosmic on 2007-01-24
simply do this in your linux box :

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

After that your windows box should have access to the internet. also in your linux box do this :

sudo iptables -L and post the results so I can help you

---

### Post by antiwindows798 on 2007-01-24
thanks kosmic, but the thing is, I can't ping to my Windows PC, lol.

Whenever I run ifconfig eth0 <some address> eth0 gets that IP (eth0 = the network card that connects to Windows. eth1 = the network card that connects to the internet) but after the network has been restarted, eth0 looses its IP address.

---

### Post by kosmic on 2007-01-24
Hum the easy way is using a DHCP server, just follow this tutorial and if you need help just post here and I will help you

[http://doc.gwos.org/index.php/ServerGuide#Dhcpd](http://doc.gwos.org/index.php/ServerGuide#Dhcpd)

After following the guide do this and it should work ;)

sudo iptables -F
sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -j MASQUERADE
sudo echo "1" >/proc/sys/net/ipv4/ip_forward

---

### Post by antiwindows798 on 2007-01-27
I went to [http://doc.gwos.org/index.php/ServerGuide#Dhcpd](http://doc.gwos.org/index.php/ServerGuide#Dhcpd) and followed the instructions there.

I installed "dhcpd". Once you do that, I'm being told the following: > Then youll need to edit dhcp.conf in /etc to satisfy your needs. Additionally it will be nessecary to tell dhcpd which interface you want him to listen to, this is found in /etc/default/dhcp

Here's how my /etc/default/dhcp file looked like;

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES=""

So I changed INTERFACES to INTERFACES="eth0" because eth0 is the network card that I use to connect to Windows.

I edited /etc/dhcpd.conf as well, like I was told in the documentation.

So I ran  "/etc/init.d/networking restart" afterwards and got the following error message:

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Now what?

---

### Post by antiwindows798 on 2007-01-27
BTW, when I type in "ifconfig" I get the following information about eth0:

eth0      Link encap:Ethernet  HWaddr 00:17:31:2E:F9:C0  
          inet6 addr: fe80::217:31ff:fe2e:f9c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9227 (9.0 KiB)  TX bytes:2568 (2.5 KiB)
          Interrupt:233 

eth0 STILL doesn't have an IP address.

---

### Post by antiwindows798 on 2007-01-27
One more thing, in the documentation I was advised to add the following to  /etc/dhcpd.conf

default-lease-time 2100;
max-lease-time 8400;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name "somedomain.org";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.100;
range 192.168.1.150 192.168.1.200;
} 

I haven't added "option domain-name-servers" nor I have I added "option netbios-name-servers 192.168.1.1;" as I was stated later on if you wanted to add "WINS server". I don't need have a domain to add now and that's not needed. I don't really understand the purpose of a "WINS server"  but once again, that's also not very much needed.

---

### Post by antiwindows798 on 2007-01-27
I have two computers here: one with Ubuntu and one with Windows.

The Windows computer has one network card.

The Ubuntu computer has two network cards:

eth0 is the network card that connects to the Windows computer.

eth1 is the network card that connects to the internet.

What I want to do:

1. I want to connect to Ubuntu and Windows. I can't even ping to the Windows computer (nor can I ping to the Ubuntu computer from Windows), even if I give eth0 an IP address, like this: $sudo ifconfig eth0 192.168.0.1.

2. The most important part is to make Ubuntu share its internet connection with Windows.

What I don't want to do:

1. Buy unnecessary hardware ("routers" for example).
2. Install unnecessary software.

I have already tried to help for this: [http://www.ubuntuforums.org/showthread.php?t=345638](http://www.ubuntuforums.org/showthread.php?t=345638)

But nothing worked. Is it really that hard? What are you people using Ubuntu for? Playing games? Creating text files? Linux was made (or perhaps attempted) with networking in mind, that's one of the most important reasons to use Linux in the first place, at least, if it is able to do anything right for that matter (after 1.5 week I have yet to see Ubuntu do anything right).

Setting this up should be easy because as far as I know, all I have to do is configure eth0 to hae IP address and work, a DHCP server, add POSTROUTING to eth0 and that's about it, right? No need to configure anything on Windows or anything like that.

So does ANYONE here know how to do this?

---

### Post by kosmic on 2007-01-27
Hi, please can you post here what you have in the file ->/etc/dhcpd.conf.

Ok :) let's get this done.

1 - sudo apt-get remove dhcpd
2 - sudo gedit /etc/network/interfaces

then write 

```

 The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.100 (the adress when you did ifconfig adress)
        netmask 255.255.255.0
        network 192.168.1.0 -> (Also this should be in the range of adress)
        broadcast 192.168.0.255
        gateway 192.168.1.1 (this should be the same as the address)

```Now save and type :

**sudo /etc/init.d/networking restart**

OK now your eth0 will have allways this IP adress also if you reboot it will be there :)

Now

do this

```

sudo iptables -A POSTROUTING -s ***192.168.1.0/24*** -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

```NOTE 192.168.1.0/24 should be your Network adress :), DO NOT REBOOT then go to your windows BOX and configure it so it use and IP in the range of your network adress and put the GATEWAY IP in the Windows box to be the same as your eth0 network card, then try to connect.

IT SHOULD WORK, I hope ;)

Also sorry for telling you to install dhcpd and now telling you to unistall it, but is more easy for me to debug your problems if you use static ips :)

---

### Post by houstonbofh on 2007-01-27
This can be done, and is covered many places in this forum.  However, it is not trivial.  Additionally, since routers can be had for next to nothing, have built in firewalls for slightly more security, and draw less power than a computer, most people find them to be a better choice.  But if you want it, start searching "internet connection sharing" on this forum, and read a lot.  It will take some work.

---

### Post by antiwindows798 on 2007-01-27
> **kosmic said:**
> Hi, please can you post here what you have in the file ->/etc/dhcpd.conf.

Sure:

option domain-name "fugue.com";
option domain-name-servers toccata.fugue.com;

option subnet-mask 255.255.255.224;
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;

subnet 192.168.1.0 netmask 255.255.255.0 {
   range 192.168.1.10 192.168.1.100;
   range 192.168.1.150 192.168.1.200;
}

Those are the only things enabled.

> Now save and type :

sudo /etc/init.d/networking restart

OK now your eth0 will have allways this IP adress also if you reboot it will be there 

Not quite yet. This is what I wrote:

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1

After running 
sudo /etc/init.d/networking restart I got the following error message:

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 5408
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:04:76:21:7b:a6
Sending on   LPF/eth1/00:04:76:21:7b:a6
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 10.19.128.1 port 67
SIOCDELRT: No such process

---

### Post by kosmic on 2007-01-27
Adress and network should all be the same in your linux box, it should be

** address 192.168.1.100**
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
[B] gateway 192.168.1.100

[/B]Did you remove DHCPD ?? Reboot your computer and then type ifconfig it should have eth0 with the ip adress of 192.168.1.100

---

### Post by antiwindows798 on 2007-01-27
Dude, all that is needed is to configure Ubuntu, not WIndows. I will have to switch all the time between them. In IT, it's all about the most efficient solution.

---

### Post by antiwindows798 on 2007-01-27
Ooops, okay, I'm doing now what you have told me, be right back.....

---

### Post by kosmic on 2007-01-27
Also in your WINDOWS box what is the IP adress you have there it should be something like **192.168.1.101** or **192.168.1.150 **also Gateway should be ***192.168.1.100*** in your Windows Network card

Also after you reboot you Linux box dont forget to type this in a terminal :

sudo iptables -A POSTROUTING -s ***192.168.1.0/24*** -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

---

### Post by antiwindows798 on 2007-01-27
> **kosmic said:**
> Also in your WINDOWS box what is the IP adress you have there it should be something like **192.168.1.101** or **192.168.1.150 **also Gateway should be ***192.168.1.100*** in your Windows Network card

Also after you reboot you Linux box dont forget to type this in a terminal :

sudo iptables -A POSTROUTING -s ***192.168.1.0/24*** -j MASQUERADE
sudo echo "1" >/proc/sys/net/ipv4/ip_forward

It's 169.254.43.125.

Okay, the first part worked. I now have an IP on eth0 :). Now I will do the rest, brb.

---

### Post by antiwindows798 on 2007-01-27
I did:
sudo iptables -A POSTROUTING -s 192.168.1.0/24 -j MASQUERADE
And I got this error message back:

iptables: No chain/target/match by that name

BTW, what's / doing in 192.168.1.0/24 ? I assume that means "between 192.168.1.0 and 192.168.1.24"? Right?

---

### Post by antiwindows798 on 2007-01-27
And btw, I have rebooted.

---

### Post by kosmic on 2007-01-27
> **antiwindows798 said:**
> It's 169.254.43.125.

Okay, the first part worked. I now have an IP on eth0 :). Now I will do the rest, brb.

In Your windows Box you have to change that IP adress 169.254.43.125 to for example 192.168.1.101.

One question why the hell your Windows box network card have an ip like that ?? Is your Linux box that is directly connected to the Internet right ??

---

### Post by kosmic on 2007-01-27
> **antiwindows798 said:**
> I did:
sudo iptables -A POSTROUTING -s 192.168.1.0/24 -j MASQUERADE
And I got this error message back:

iptables: No chain/target/match by that name

BTW, what's / doing in 192.168.1.0/24 ? I assume that means "between 192.168.1.0 and 192.168.1.24"? Right?

Question 1  it means all ip adress in the range 192.168.1.*

Question 2 - give me a moment to see

---

### Post by kosmic on 2007-01-27
Hups my mistake i forget one command . IT should be

```

iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE      

```It more simple this way

---

### Post by antiwindows798 on 2007-01-27
I have done everything you have said, I have followed every step. And it still doesn't work.

However, eth0 does have an IP now and there is a connection between Windows and Ubuntu, but I can't access the internet on my Windows box.

---

### Post by kosmic on 2007-01-27
> **antiwindows798 said:**
> I have done everything you have said, I have followed every step. And it still doesn't work.

However, eth0 does have an IP now and there is a connection between Windows and Ubuntu, but I can't access the internet on my Windows box.

In your Windows Box do this :

Configure the Windows network card to be like this

[B]IP - 192.168.1.110
Netmask - 255.255.255.0
Gateway - 192.168.1.100
DNS - 192.168.1.100[/B]

---

### Post by antiwindows798 on 2007-01-27
Nope, nothing. But after I have set the DNS on Windows, trying to access the internet no longer gives me an error message in the browser now, it just hangs when you see the "connecting"  message in the browser.

---

### Post by kosmic on 2007-01-27
> **antiwindows798 said:**
> Nope, nothing. But after I have set the DNS on Windows, trying to access the internet no longer gives me an error message in the browser now, it just hangs when you see the "connecting"  message in the browser.

Ok we are almost there.

Go to you Linux box and install :

DNSMASQ and ipmasq
**sudo apt-get install dnsmasq ipmasq**

then Restart dnsmasq:

**sudo /etc/init.d/dnsmasq restart**

and then :

[B]sudo dpkg-reconfigure ipmasq
[/B]Reconfigure ipmasq to start after networking has been started

and hopefully it should start working.

TO BE IN THE SAFE SIDE :)

After doing that reboot your linux box, and type the following :
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE

AND IT SHOULD WORK NOW, I HOPE

---

### Post by antiwindows798 on 2007-01-27
Running sudo apt-get install dnsmasq ipmasq results in the following:

Setting up dnsmasq (2.33-1) ...
Starting DNS forwarder and DHCP server: dnsmasqdnsmasq: failed to create listening socket: Address already in use
 (failed).
invoke-rc.d: initscript dnsmasq, action "start" failed.

---

### Post by kosmic on 2007-01-27
Argh, dnsmasq is trying to start a DHCPD server. give me a minute

---

### Post by antiwindows798 on 2007-01-27
Wait, why can't I share an internet connection with Windows? Nothing went wrong, so isn't it working?

---

### Post by kosmic on 2007-01-27
If you rebooted your computer you need to type this again

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

also reboot your windows box and try acessing the net again.

if you want to make the forwarding permanet, do the following :
**sudo gedit /etc/sysctl.conf**
and add this line
[B]net.ipv4.ip_forward = 1

I'm cracking my head now, because you have everthing well configured, eth0 has a fixed ip adress like 192.168.1.100...WAIT
[/B][I]
Just tell me again your internet conection is coming from eth1 right ??
[/I]

---

### Post by antiwindows798 on 2007-01-27
> I'm cracking my head now

You almost now how I feel now! I have been trying to get this to work for days! ROFL!

> Just tell me again your internet conection is coming from eth1 right ??

Sure is.

Okay, I'm going to do what you have just told me to do. BRB.

---

### Post by antiwindows798 on 2007-01-27
> and add this line
net.ipv4.ip_forward = 1

Done, but shouldn't it be "forwarding" instead?

There are some of such things in that file:

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

Anyways, I'm going to reboot now.

---

### Post by kosmic on 2007-01-27
I think I found the solution.

In your linux box do :

**sudo iptables -t nat -D POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE**

and then

[B]sudo iptables -t nat -A POSTROUTING -s 192.168.1.110/32 -o eth1 -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"[/B]

[B]192.168.1.110 - SHOULD BE THE IP ADRESS OF YOUR WINDOWS NETWORK CARD

[/B] [I]Now in you windows box ensure that in your NetWork card in DNS Preferences you have the ip adress 192.168.1.100
and after that save and reboot your Windows box, and now it should work

[/I]***INSTEAD OF ADDING *** net.ipv4.ip_forward = 1 ***you can uncoment the following line***
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=1

---

### Post by antiwindows798 on 2007-01-27
Great, my internet connection is now no longer working in Ubuntu (I'm back in Windows now >:(). I have removed "net.ipv4.ip_forward = 1" but I still don't have an internet connection.

Should I proceed to do what you just said?

---

### Post by kosmic on 2007-01-27
[B]Yes just do what i've said in the topic above
[/B] 
I will be out for 15minutes, hope that you have internet now working, if not i will help you when I come back

---

### Post by antiwindows798 on 2007-01-27
Okay, be right back.

---

### Post by antiwindows798 on 2007-01-27
Running:

sudo iptables -t nat -D POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE

Results in the following error message:

iptables No chain/targer/match by that name

---

### Post by antiwindows798 on 2007-01-27
And not to forget that I don't have any internet connection anyone more on Ubuntu >:(.

---

### Post by kosmic on 2007-01-27
> **antiwindows798 said:**
> Running:

sudo iptables -t nat -D POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE

Results in the following error message:

iptables No chain/targer/match by that name

It is telling us that iptables doesn't have this rule, it is Ok you can continue with the rest of the commands

---

### Post by will61 on 2007-01-27
I haven't got much experience with Ubuntu but, However after reading all you have posted on this subject it seems the general direction you are working in is quite correct 

The only thing I might suggest that maybe causing you probs is the Ip address your trying to set 
I've checked my windows box from the command Prompt and it seems the Ip range for my local network runs from 192.168.2.1  through to 192.168.2.200 

If you make sure DHCP is enabled on your windows box it should assign Ip addresses in the 192.168.2 range if you set a fixed Ip address on your linux box within the 192.168.2 range it should work

To check the Ip settings on your windows box just go to the command prompt and type "ipconfig /all"

---

### Post by kosmic on 2007-01-27
> **will61 said:**
> I haven't got much experience with Ubuntu but, However after reading all you have posted on this subject it seems the general direction you are working in is quite correct 

The only thing I might suggest that maybe causing you probs is the Ip address your trying to set 
I've checked my windows box from the command Prompt and it seems the Ip range for my local network runs from 192.168.2.1  through to 192.168.2.200 

If you make sure DHCP is enabled on your windows box it should assign Ip addresses in the 192.168.2 range if you set a fixed Ip address on your linux box within the 192.168.2 range it should work

To check the Ip settings on your windows box just go to the command prompt and type "ipconfig /all"

Yes for this to work all the Boxes has to be in the same ip range.

So he's linux is with ip 192.168.1.100
and I hope is windows box is it ip - 192.168.1.110, gateway should be 192.168.1.100 and dns 192.168.1.100

if this is all correct, and IP FORWARDING is working it should give internet acess to both boxes

---

### Post by antiwindows798 on 2007-01-27
That doesn't work either.

Okay, this isn't going well. Is Linux capable of sharing an internet connection with Windows?

I'm not a network administrator (I'm a programmer) but I have been working with (Windows) network administrators for years now and this is by far the most retarded crap that I have seen. This should be easy.

First of all, the only thing that needs to happen is the following:

1. eth0 should be configured without screwing up my internet connection.

2. A DHCP server should be set up so that my Windows PC can get an IP address.

3. Ubuntu should be configured to (permanently) share an internet connection.

My Windows PC should NOT be modified in any way. Why not? Because it's simply not needed, if Ubuntu is misfitted to take care of business, then that is not the fault of Windows. I also have Windows XP installed on this computer and I will need to switch between Ubuntu and Windows XP now and then, and I totally don't feel like going every time to my (other) Windows PC to reconfigure its network settings every time I want to log on to Windows on this computer. That just doesn't make sense.

So what's the solution? How do I restore my internet connection and how do I do what I have just said above?

---

### Post by kosmic on 2007-01-27
1 - To Have ips assigned automatically you need to use a DHCP server or a router, in linux you have DHCPD.

2 - Also eth0 should be configured by DHCPD.

3 - if you do in your linux box ifconfig what it says about eth1 ? does it have an IP adress  ? if yes when it stop working ? for a cleaner answer please reboot linux and try to see if you have acess to the internet with linux

4 - if you have DHCP working it should be so simple as doing this :

[B]sudo iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

ethX should be the card that have acess to the internet.

Then reboot windows a it must work
[/B]

---

### Post by kosmic on 2007-01-27
Reboot and plug your internet cable to linux and then try to see if you can go to the internet, also post where the output of ifconfig ith the internet cable conected.

After what step did the internet on your linux box stopped working ?

Also post there the file [B]/etc/sysctl.conf

[/B]Those are the only files we modified, also do :

sudo iptables -F INPUT
sudo iptables -F OUTPUT

also sudo apt-get remove dnsmasq ipmasq

and edit the file /etc/network/interfaces

 and put this:

# The primary network interface
auto eth0
iface eth0 inet dhcp

SHOW ME ALSO THE FILE /etc/networks/interfaces

SEE YOU TOMOROW ;)

---

### Post by Zzl1xndd on 2007-01-27
Perhaps this thread will help you. [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) .

On another note this is not a common request on either Linux or Windows and most windows techs would tell you to by a router. Also as for your calling Microsoft comment you are charged to speak with them about windows issues such as this. You could call your computers manufatuer but they would also inform you to by a router as they dont support the software.

---

### Post by e_james on 2007-01-27
As a frustrated Windows to Linux potential convert I have been following this thread with some interest. I agree that the windows pc should not need to be rebooted in order to establish a connection. The most that should be necessary is to disable and re-enable the network adapter. The address 169.254.43.125 is a typical default address allocated by windows when it tries unsuccessfully to get an address by DHCP. I just noted that nobody commented on that.

My own experience goes back to 1900 FORTRAN, followed by 8060, 6502 and Z80 machine code, and then MSDOS (which is not case sensitive). In the last 15 years or so I have become so accustomed to working in a graphical environment with a mouse that the standard linux fix of the command line looks like a foreign language (encrypted). I have also learned that taking any configuration action, without a reasonable understanding of the consequences, is a good way to create a series of new problems. Please be patient with us ex wndows users. We do want to succeed.

---

### Post by aysiu on 2007-01-27
I've moved to the Jail the posts arguing about Linux and Windows.

This thread has been re-opened so that *antiwindows798* can get some help. *tweakedenigma* is absolutely correct, however, in saying that "this is not a common request on either Linux or Windows and most windows[sic] techs would tell you to by[sic] a router." I'm moving this thread to Networking & Wireless, in the hopes that, upon a re-open, it'll get the attention it deserves.

I will say, though, that *antiwindows798* should focus only on trying to solve the issue at hand and realizing that this is not a common request, that the forum is made up of volunteers (other Ubuntu users), and that it's expected that anyone asking for help should be polite. However, other users also need to realize it is not the job of Ubuntu users to rile up users who are frustrated with Ubuntu.

If people cannot be civil to each other, the offending parties will first be issued infractions and then possibly end up banned from the forums.

---

### Post by mips on 2007-01-28
Looking at your original request i believe the following will solve your problems if you follow the instructions:

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)
[http://ubuntuforums.org/showthread.php?t=89320](http://ubuntuforums.org/showthread.php?t=89320)

Your situation is actually less complicated. I started typing out a something here but changed my mind.

---

### Post by antiwindows798 on 2007-01-28
Okay, let's get this over with for once and all.

I have reinstalled Ubuntu now.

Let me explain again what I'm trying to do:

1. I want to connect my Ubuntu computer to my Windows computer first. On my Ubuntu box I have two network cards: eth0 = the network card used to connect to Windows and eth1 = the network card used to connect to the internet. First of all, I want to configure eth0 to work. Once I can ping from Windows to Ubuntu and vice versa, step 2 can be taken.

2. My Ubuntu box should be configured to permantely share its internet connection with my Windows box.

That's all!

Technically, what I'm trying to do, is to set up a DHCP server on Ubuntu so that my Windows box can get a IP and with that, Ubuntu can share an internet connection with Windows. Thus, no routers are needed and configuring my Windows box is also not needed.

When I type in "ifconfig" in the terminal, I get the following information:

eth1      Link encap:Ethernet  HWaddr 00:04:76:21:7B:A6
          inet addr:62.163.14.217  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::204:76ff:fe21:7ba6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29285 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60854678 (58.0 MiB)  TX bytes:2180938 (2.0 MiB)
          Interrupt:225 Base address:0x2400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

I don't know exactly what "lo"  means, but anyways, as you can see, etho is not listed here, I can go to System and Network settings to enable it, but I will need to configure it first before I can ping back and forth from Ubuntu and Windows.

In the file /etc/network/interfaces this is what I have:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

So what should I do?

---

### Post by kosmic on 2007-01-28
Ok this now is personall ;) ehhe

By the Way "lo" Loopback device or comon know by Localhost or 127.0.0.1


STEPS :

1 - sudo apt-get install dhcpd
2 - sudo gedit [B]/etc/dhcpd.conf
[/B]3 - Make it  look like this :
```

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc; 

#assign the remote dhcp server hostname/ip addresses 
option domain-name-servers 192.168.1.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS 
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth0 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}

```4 - Save and exit
5 - sudo gedit [B]/etc/default/dhcp (and make it look like the line below)
[/B]```

INTERFACES="eth0"

```Save and exit

6 - sudo /etc/init.d/dhcp restart

This will give your eth0 an automatic adress in the range 192.168.1.* also your windows box should also get an adress in the same range automaticly :)

when you get this done post here...

---

### Post by antiwindows798 on 2007-01-28
etc/dhcp3/dhcpd.conf doesn't exist on my computer. Did you mean /etc/dhcpd.conf instead?

---

### Post by kosmic on 2007-01-28
Yes I've made some errors in the configuration files but now it is correct, you can use it :)

---

### Post by antiwindows798 on 2007-01-28
After I have reinstalled Ubuntu, I couldn't get my video card driver to work (ATI). Without installing the ATI driver, Ubuntu looks extremely old and ugly and the windows aren't moving fast. So I have followed the instructions of a Ubuntu page (I have the link in Ubuntu, I'm now in Windows) and that totally ****ed up Ubuntu, I have followed the recovery instructions as well but that didn't work out as well. So I have reinstalled Ubuntu again and the same thing happen. One Ubuntu installation takes about 45 minutes at least. So I have already wasted 1 hour and 30 minutes on reinstalling Ubuntu and I don't feel like doing it again.

To be honest, I'm tired of Ubuntu. This is now the second week that I'm trying to do the most basic things in Ubuntu and at everything so far, Ubuntu has failed miserably. Ubuntu must be the worst operating system ever. I have lost my trust in Linux and Ubuntu but I'm not sure where to move on from here. Solaris? Linux is Linux, Linux is only the kernel, in every Linux distro you have KDE/Gnome, the Linux kernel, etc. So choosing another Linux distro is of course not going to give me a better OS. And since Sun doesn't support Java for BSDs, I can't switch to a BSD OS as well. I guess I will try Solaris but Solaris will probably suck worse.

So let me think for about 15 minutes about what I'm going to do next.

---

### Post by kosmic on 2007-01-28
1 - You can buy some books about linux (linux is not windows)
2 - You can buy Good hardware that is supported by linux and not some cheap cards like winmodems
3 - Read Read Read, dont try to make things without knowing what you are doing, I know ATI sometime gives troubles configuring but its a simple problem to care it out.
4 - So again Read and Read, when you understand how linux works you will see that it is miles ahead of M$ Windows

5 - Make Windows act like a DHCP Server to see if it is more simples than window
6 - Also make windows share its internet conection with linux to see if you can in simple steps.
7 - If you can do this in windows then stick with windows and not linux ;)

---

### Post by antiwindows798 on 2007-01-28
> - You can buy some books about linux (linux is not windows)

I have here, let me see, about 11 books about Linux. I could never find a normal Linux book that wasn't made for noobs. All they talk about in those books is OpenOffice and such crap, and the only thing they say about networking is wireless networking.

> 2 - You can buy Good hardware that is supported by linux and not some cheap cards like winmodems

The only hardware that works best with Linux is old outdated hardware. I'm int the IT business, and I have recently had to buy new hardware for an organization and install Fedora on them. So I did that, but the drivers didn't work so I simply left and told me to go get Red Hat instead because that way I can pick up the phone the bitch at them and hold them responsible.

I'm not going to buy "special" hardware for Linux. I have the newest hardware: AMD X2, 2 GB memory, ATI video card, etc, etc. If Linux can't handle that then it's not a worthy operating system.

> 4 - So again Read and Read, when you understand how linux works you will see that it is miles ahead of M$ Windows

Dude, I have ran some tests at the office on Ubuntu and Windows and let me tell you one thing, as much as I hate to say it, Windows has OWNED Ubuntu in every single test, ranging from memory to CPU tests. I was shocked but it's the truth. Windows is an extremely crappy operating system, but as far as I see it, Windows nevertheless is in every aspect superior to Linux. The best OS is probably Mac OS, every other OS out there is probably a bunch of bullshit.

And I'm reading constantly.

Anyways, I will be back in about 10 minutes. Thanks for your help so far, I will take a break away from Linux and everything about computers for a few minutes to think about this.

---

### Post by kosmic on 2007-01-28
98% of the cases it is now the hardware that dosn't work it is the User that doens't know how to make it work.

99% of the problems with linux is users that want linux to work like windows, but linux is not windows 

If Windows suits you best why do you bother work with linux ??

More than 60% of servers in the world use Linux or some variant of them like BSD, VAX, UNIX etc

I work for a TOP 500 enterprise and all our servers use BSD and linux and it is not old hardware we have, we have hardware that is a lot expensive, Also We use some workstations with ATI cards and all works flawlessy and with 3D desktops like Beryl.

So again I can do thing with linux that windows can't dream of, the only thing I can do in Windows best than linux is Playing some Games.

Also I'de like to see that benchmarks...

And by the way OSX is Based on Darwin and BSD :)

---

### Post by antiwindows798 on 2007-01-28
> 98% of the cases it is now the hardware that dosn't work it is the User that doens't know how to make it work.

That doesn't matter. Things have to work out of the box. If you buy a car will you find it acceptable to have to install the engine yourself? Paying a system administrator to install Windows on any computer will cost almost nothing because Windows already has all the drivers needed. Doing it on Linux will, as far as I see it, cost more than the entire Windows OS.

> 99% of the problems with linux is users that whant linux to work like windows, but linux is not windows

That's easy to say. I came into the Linux world with the intention to learn how to control the operating system with a command line, not with pretty windows. That's how I came in. I don't mind if I have to configure things myself, by for ****s sake, (to the Linux community) CREATE SOME DOCUMENTATION! Most of these Linux users seem to care only about browsing and sending emails, instead of using Linux for professional goals.

> If Windows suits you best why do you bother work with linux ??

Windows doesn't suit me best. It's easy to configure and everything works out of the box with Windows. As you can see from my user name, I'm not a fan of Windows.

I'm looking for an Unix like operating system to use it as a server and if possible, to use it as a desktop as well. I don't care whether it's an open source OS or not, I only care whether it works or not and whether it is not too expensive.

> More than 60% of servers in the world use Linux or some variant of them like BSD, VAX, UNIX etc

Yeah, that's true but you are forgetting one thing, are into making websites or anything like that? More than 60% of the web servers in the world run PHP. PHP!!! COMMON! How retarded is that? I have programmed in PHP for over a year and I couldn't wait to finally be able to switch to a real professional programming language for web programming. PHP is one of the biggest noob languages ever, web design and programming happens all at one in PHP and PHP doesn't care about any programming rules, basically everything you put in will work, regardless whether it should work or not. But why do people use PHP? Because most people want "easy"  things and they want it to be free. PHP, Ruby, Perl, Python, etc, all of that crap is so yesterday and so 90s. These days we have more professional solutions: ASP and JSP (but I must say that ASP is pretty *** too).

I have tried FreeBSD, just to learn more about it. So I have read a book about it and the author said that he has been using FreeBSD for about 11 years and during that time, he only saw FreeBSD crash once. Well FreeBSD crashed on me two times within 2 hours! And once I finally manged to set everything up, FreeBSD all of the sudden got a problem with my USB drive. How ****ed up is that?

I have tried Red Hat Linux in the late 90s. I took 3 hours to install on my computer and although it worked for the first 30 minutes, it crashed.

I have tried SuSE Linux before Novell took it over. I had to develop applications for it but SuSE failed on me, it crashed so often that I had to bitch at my employer and eventually he agreed and we unfortunately switched back to Windows.

A few months ago, a business parter of mine switched to Fedora. The drivers didn't work and nobody felt like paying me or the system administrators for an extra few hours to install Fedora on 20 computers and get the drivers working.

Now I'm personally trying out Ubuntu to use it as a server soon and during this whole week, I haven't seen anything right from Ubuntu (except that you cannot log in as root, that is, by default, I like that, lol). It's not faster than Windows, Linux does an amazingly bad job at swapping data and crashed too often.

> I work for a TOP 500 enterprise and all our servers use BSD and linux and it is not old hardware we have, we have hardware that is a lot expensive, Also We use some workstations with ATI cards and all works flawlessy and with 3D desktops like Beryl.

They have purchased the hardware with Linux/BSD in mind, otherwise Linux would have worked for me as well.

> And by the way OSX is Based in Darwin and BSD 

Yep.

Anyways, I have decided to give Ubuntu ONE MORE try. I have been way too much tolerant towards Ubuntu this week. Either it will work or not.

So I'm going to make a new post about the ATI driver issue before I can come back to you and finish networking issue.

---

### Post by antiwindows798 on 2007-01-29
> **kosmic said:**
> Also I'de like to see that benchmarks...

You mean like you see how we tested Ubuntu against Windows? Well, we created a small program and tested it using a database, both on Ubuntu and Windows but you know, here's a simple way to see which one is faster:

I have used a 64 bit computer with 4 GB of memory. Windows XP SP1 32 bit was installed on it and Ubuntu Server 6.10 64 bit was installed on that computer as well. Technically, Ubuntu has a huge advantage over Windows in this case because it's 64 bit whereas Windows is 32 bit and thus, Ubuntu should at least be 10% faster.

Now, you can run a simple test with Firefox for example. Firefox runs on both Windows and Ubuntu. So load some data into Firefox that is twice as much as you have memory and count how long it will take for Firefox to load everything into the memory and swap, and check how functional Ubuntu and Windows will remain.

The end results: Windows remained functional and it took Windows about 8 seconds to get everything straight. Ubuntu crashed 2 times during the test, 2 TIMES! Ubuntu wasn't functional at all during the test, after about 5 minutes we tried pressing on Ctrl + Alt + Delete but Ubuntu didn't respond to that.

The only excuse for that that I can think of is that Ubuntu was installed on a small and older hard disk, while Windows was installed on a much larger and newer hard disk. But then again, because Ubuntu was installed on a small hard disk, it should have been able to read the data at least as fast as Windows did on a big hard disk.

I must be crazy, but I'm willing to give Ubuntu another try. It's almost 8 in the morning here (I haven't slept) and I have been working on getting Ubuntu to work for over a week now. Once I get back home from work today I will go directly to bed, lol, so tomorrow or Wednesday, I will get back to installing the ATI driver in Ubuntu (I have just reinstalled Ubuntu for the 3rd time today to try yet another method to make the ATI driver work in Ubuntu and Ubuntu crashed again and I can't access the desktop AGAIN. So I will have to reinstall Ubuntu for the **fourth **time and that will be DEFINITELY the last time ](*,). If Ubuntu was a commercial product I would have definitely and seriously sued Canonical big time). Once that works out, I will do what you have said today and I will come back to it to configure Ubuntu to share its internet connection with Windows.

And yes, this time it's personal :x.

---

### Post by mips on 2007-01-29
> **antiwindows798 said:**
> After I have reinstalled Ubuntu, I couldn't get my video card driver to work (ATI). Without installing the ATI driver, Ubuntu looks extremely old and ugly and the windows aren't moving fast. So I have followed the instructions of a Ubuntu page (I have the link in Ubuntu, I'm now in Windows) and that totally ****ed up Ubuntu, I have followed the recovery instructions as well but that didn't work out as well. So I have reinstalled Ubuntu again and the same thing happen. One Ubuntu installation takes about 45 minutes at least. So I have already wasted 1 hour and 30 minutes on reinstalling Ubuntu and I don't feel like doing it again.

To be honest, I'm tired of Ubuntu. This is now the second week that I'm trying to do the most basic things in Ubuntu and at everything so far, Ubuntu has failed miserably. Ubuntu must be the worst operating system ever. I have lost my trust in Linux and Ubuntu but I'm not sure where to move on from here. Solaris? Linux is Linux, Linux is only the kernel, in every Linux distro you have KDE/Gnome, the Linux kernel, etc. So choosing another Linux distro is of course not going to give me a better OS. And since Sun doesn't support Java for BSDs, I can't switch to a BSD OS as well. I guess I will try Solaris but Solaris will probably suck worse.

So let me think for about 15 minutes about what I'm going to do next.

I honestly think you should move on and forget about it as everything will suck for you. Stick to windows. You have already expressed your views of it's superiority and how bad linux is.

If you want to carry on then I suggest you get eth0 working/enabled. Then follow the link I posted above. Alternatively enable remote desktop access and ask someone to assist you remotely with the configs.

You are going in circles here and you are just going to get annoyed & frustrated in the process.

This thread is becoming a waste of peoples time as it seems more like a rant than anything else.

---

### Post by Lil_Eagle on 2007-01-29
This is moving way off topic.  This is a thread on how to share internet, not a debate on Windows vs. Linux.  People who want to engage in that sort of conversation can better go elsewhere than on these forums in the first place.

Now, back on topic.

I'm having problems.  Here's my setup:

ADSL Router <-> Edgy <-> switch < - > Dapper, Network Printer.

Egdy can reach everything, but Dapper won't ping further than Edgy, however, it will look up DNS which is the ADSL, so I'm getting there.  The problem seems to be when I try the guides I've seen using the kernel's ip_forwarding, it kills Edgy's ability to reach anywhere.

On the edgy machine eth0 is the External and eth1 is the Internal.

I think the problem is with the subnets.  My switch by default gives 10.0.0.x addresses while the ADSL gives 192.168.1.x addresses.  I tried to reconfigure the switch to give 192.168.1.x addresses (higher range) but if I tell it to give anything other than the 10.0.0.x then it seems to get confused and won't answer DHCP requests.  Even if I tell the computers a static address . it doesn't seem to work.

In order for me to post here I have to disable eth1 on Edgy or I can't get anywhere.

Would a new switch/hub help?

I'm getting ready to pull my hair out.

---

### Post by mips on 2007-01-29
> **Lil_Eagle said:**
> This is moving way off topic.  This is a thread on how to share internet, not a debate on Windows vs. Linux.  People who want to engage in that sort of conversation can better go elsewhere than on these forums in the first place.

Now, back on topic.

I'm having problems.  Here's my setup:

ADSL Router <-> Edgy <-> switch < - > Dapper, Network Printer.

Egdy can reach everything, but Dapper won't ping further than Edgy, however, it will look up DNS which is the ADSL, so I'm getting there.  The problem seems to be when I try the guides I've seen using the kernel's ip_forwarding, it kills Edgy's ability to reach anywhere.

On the edgy machine eth0 is the External and eth1 is the Internal.

I think the problem is with the subnets.  My switch by default gives 10.0.0.x addresses while the ADSL gives 192.168.1.x addresses.  I tried to reconfigure the switch to give 192.168.1.x addresses (higher range) but if I tell it to give anything other than the 10.0.0.x then it seems to get confused and won't answer DHCP requests.  Even if I tell the computers a static address . it doesn't seem to work.


Could I suggest you read the two links in post #63.

What you want to do, configure the same subnet on all networks, will NOT work.

You have told us very little about what you have done to this point and what all your config files look like.

Setting up ICS is actually very simple. People tend to make it a lot harder than it actually is.

[http://ubuntuforums.org/showthread.php?t=269235&highlight=ICS](http://ubuntuforums.org/showthread.php?t=269235&highlight=ICS)
[http://ubuntuforums.org/showthread.php?t=89278](http://ubuntuforums.org/showthread.php?t=89278)
[http://ubuntuforums.org/showthread.php?t=88294](http://ubuntuforums.org/showthread.php?t=88294)
[http://ubuntuforums.org/showthread.php?t=76346](http://ubuntuforums.org/showthread.php?t=76346)

A 'switch' has nothing to do with IPs or assigning IPs as it a Layer two device. Some switches support multi layer but I doubt that for a home device.

You should actually start your own thread not hijack the OPs for various reasons.

---

### Post by Lil_Eagle on 2007-01-29
Perhaps I have been a bit unclear as to what I have tried.

Like I said in my last post, my current switch (which incently is also an ADSL Router, but that is beside the point) is a cheap piece of junk that doesn't like me telling it what its IP address is nor what addresses it should hand out via DHCP.

I have read all of those posts, followed the instructions and even tried a script that totally hosed my network.  I was about to give up when I thought, no wait, I can undo that.  I have tried many times and all looks good (no errors) but it still doesn't work.  Sometimes I manage to block eth0 from getting to the ADSL Router (192.168.1.1).  

I am doing my best to solve this problem without asking for help and feel foolish that I can't get it to work.  There are enough posts that I should be able to just read them and figure out what is best for me.  That is what I usually do, and feel foolish having to apply for help.  I tried firestarter and shorewall.  Shorewall is not as simple as I thought it should be (perhaps it is powerful) and firestarter didn't work.

The ADSL Router belongs to my ISP and I am not allowed to modify any of its settings.  To be honest I don't know if I am even allowed to share the connection.

Now I am back to square one.  There are no iptable chains nor is the kernel doing any forwarding.  

Let me clarify my setup:

Edgy machine:

joe@Box:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:F4:2E:F0:C9
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe2e:f0c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8098979 (7.7 MiB)  TX bytes:1745393 (1.6 MiB)
          Interrupt:193 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:13:D3:F4:5C:84
          inet addr:10.0.0.13  Bcast:255.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:d3ff:fef4:5c84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:103678 (101.2 KiB)  TX bytes:8280 (8.0 KiB)
          Interrupt:225 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53072 (51.8 KiB)  TX bytes:53072 (51.8 KiB)

Both cards dhcp aquired.

Dapper Machine:

papa@kim-desktop:$ifconfig
eth0    Link encap: Ethernet  HWaddr 00:10:DC:ED:60
          inet addr: 10.0.0.12 Bcast:255.255.255.255 mask 255.0.0.0
...

Am I right in thinking that the subnet is causing the problem?  I cannot change the switch to give a different mask, nor can I change which subnet it is on.  I have tried.

What I am trying to do it create internet access for the computer upstairs, for my 6 year old.  I don't want it to be permanent, I want to be able to turn it on and off from downstairs where my computer is (the Edgy machine).  My wife is totally against the idea that she has access to the internet, but she found some game sites and now she's always bugging me to use my computer so she can play games.

I am prepared to replace the switch.  That might be the easiest solution.  If I can get one dishing out 192.168.0.x, then it should work.  Right?

---

### Post by mips on 2007-01-29
Lil_Eagle,

Think about what you are doing here.

You are using an ADSL router between the two PC's. An ADSL router routes between it's WAN port (RJ-11 connector) and it's LAN port (RJ-45 switch ports). It will NOT route between the the switch ports as you are trying to do.

Think of it this way, internally that ADSL router looks like this WAN-Modem-Router-Switch. The switch part does not understand IP and leaves that up to the router. Each section can almost be seen as autonomous.

I do not know however whether the switch will function independantly from the router (My old netgear did not, it dropped the LAN side if you unplugged the RJ-11 WAN side). An easy test would be to connect two devices in the same subnet to the switch ports and see if each device can ping the other (Dont use 10. addresses though).  When the router assigns a IP address via DHCP it also specifies the gateway address which would be the routers internal LAN port connect to the switch. Traffic gets forwarded from this port to the WAN port and seeing nothing is connected to the wan port it ain't going anywhere.

If that can be done then we can carry on. If it uses the 10 subnet that is fine, you have to change the management interface ip address as well if you want to use say 192.168.2.x. The only problem is if the addresses change between devices because DHCP is used then it is going to be hard to specify a gateway as it will be constantly changing.

Is the network printer connected to the switch or the Dapper box ???

---

### Post by Lil_Eagle on 2007-01-29
You've summed up my thoughts.  But I do believe the switch (old ADSL router) WAN and LAN halves are independant.  I brought the computer from upstairs so I didn't have to keep running up to check it.

The printer is upstairs as well, designed to connect to the switch, hence the DHCP.  I suppose I could hook it up to the Dapper box, but the idea was that I could print to that printer even if my daughter's computer is off.  The printer is too big to fit here in the living room.

So, I have now the dapper and the edgy machine next to me.  The setup is still the same, the Dapper machine plugs into the switch and gets 10.0.0.12 and the Edgy machine plugs into it and gets 10.0.0.13 (eth1)   The numbers are consistant because the router keeps MAC addresses.  The Edgy machine's other NIC connects to the ADSL box (eth0) that belongs to the IP (with a cross cable no less). 

The two compuers can ping each other.  I thought if I got that far it would be a snap.  Not so.  Like I said, I'm willing to buy new hardware, but not run more cables.  There's only one cable going upstairs.

Like I said, the router won't accept the changes when I try to change the addresses.  I think I need to replace it and you've convinced me.  I'll buy a simple one. 

The ADSL box has two ports, so I could just connect the Dapper machine to the internet by crossing the cable and plugging it strait to the box, but that would leave the printer out of the loop.

Incently, when I try firestarter I loose eth0 on Edgy, therefore no internet.

Oh, and thanks for responding.  I am not about to give up.

---

### Post by mips on 2007-01-29
> **Lil_Eagle said:**
> 

So, I have now the dapper and the edgy machine next to me.  The setup is still the same, the Dapper machine plugs into the switch and gets 10.0.0.12 and the Edgy machine plugs into it and gets 10.0.0.13 (eth1)   The numbers are consistant because the router keeps MAC addresses.  The Edgy machine's other NIC connects to the ADSL box (eth0) that belongs to the IP (with a cross cable no less). 

The two compuers can ping each other.  I thought if I got that far it would be a snap.  Not so.  Like I said, I'm willing to buy new hardware, but not run more cables.  There's only one cable going upstairs.


First, do NOT buy another router. Rather just get a normal switch if you have to buy something.

Does the router have the option to specify the Defualt gateway ? My pos microcom has that option (not that i used it) maybe you can specify that to be the IP address of Edgy LAN interface connected to it ???

Another suggestion would be to statically configure the edgy machine ip address and run dhcp server on it. disable the dhcp server on the adsl router. this 'should' allow the edgy pc to serve up dhcp and the adsl router should ignore the dhcp requests.

Do you actually need dhcp at all seing it is only two devices, both the pc & printer could have static configs. it is not that much to configure ?

What brand/model is that router.

---

### Post by Lil_Eagle on 2007-01-29
I was thinking of a simple hub.  If I have a hub upstairs and run a DHCP server on Edgy, then the printer and the other computer SHOULD pick it up.  I'll still have to bridge, but at least I'll have contol of the ip addresses and the methods described earlier in this thread should work.  I wonder if this is secure, but for now I would rather have it work and work on security later.

I might be able to change the gateway on the switch.  I can reach it's web based configuration, but the problem I've been having is getting it to save the settings.  When I change the addresses and flash it's memory it doesn't come back and stops serving DHCP.  If I reset it back to the facory defaults (little button on the back) then I get the same 10.0.0.x IP addresses and 255.0.0.0 netmask and I think that's where the problem lies.  I'll play with it tonight since the stores are already closed here and then tomorrow I'll go shopping for a new hub.

Does this sound like a good idea?

---

### Post by mips on 2007-01-29
> **Lil_Eagle said:**
> I was thinking of a simple hub.  If I have a hub upstairs and run a DHCP server on Edgy, then the printer and the other computer SHOULD pick it up.  I'll still have to bridge, but at least I'll have contol of the ip addresses and the methods described earlier in this thread should work.  I wonder if this is secure, but for now I would rather have it work and work on security later.

I might be able to change the gateway on the switch.  I can reach it's web based configuration, but the problem I've been having is getting it to save the settings.  When I change the addresses and flash it's memory it doesn't come back and stops serving DHCP.  If I reset it back to the facory defaults (little button on the back) then I get the same 10.0.0.x IP addresses and 255.0.0.0 netmask and I think that's where the problem lies.  I'll play with it tonight since the stores are already closed here and then tomorrow I'll go shopping for a new hub.

Does this sound like a good idea?

A hub will work fine but if you are a stickler for performance it will be slower than a switch. Dunno if there is a big price difference. just make sure it supports at least 100Mb/s Full-Duplex.

No need to 'bridge' as you mentioned, you want to route as described in this thread.

---

### Post by antiwindows798 on 2007-01-29
I'm back, I have finally gotten everything to work. It turns out that I have downloaded Ubuntu 6.06 LTS instead of Ubuntu 6.10 (I have had actually downloaded them both, but I forgot to remove Ubuntu 6.06 LST), so the installation procedure for my ATI video card didn't work under Ubuntu 6.06 LTS for some reason.

Anyways, kosmic, I'm back now. I apologize for any inconveniences it may have caused, I didn't know that you have to work your *** off (apparently) every time after each new or so version of Ubuntu to get the drivers to work correctly.

I really want to get this to work. I'm by far not ready to give up on Ubuntu, even if Ubuntu appears to give up on me.

Here's what you have told me to do:

> **kosmic said:**
> Ok this now is personall ;) ehhe

By the Way "lo" Loopback device or comon know by Localhost or 127.0.0.1


STEPS :

1 - sudo apt-get install dhcpd
2 - sudo gedit [B]/etc/dhcpd.conf
[/B]3 - Make it  look like this :
```

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc; 

#assign the remote dhcp server hostname/ip addresses 
option domain-name-servers 192.168.1.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS 
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth0 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}

```4 - Save and exit
5 - sudo gedit [B]/etc/default/dhcp (and make it look like the line below)
[/B]```

INTERFACES="eth0"

```Save and exit

6 - sudo /etc/init.d/dhcp restart

This will give your eth0 an automatic adress in the range 192.168.1.* also your windows box should also get an adress in the same range automaticly :)

when you get this done post here...

Now, I don't understand one thing about that. How is my eth0 network card configured by doing that? The only place where I see "eth0" in /etc/dhcpd.conf is between comments. Sure, in /etc/default/dhcp INTERfACES is set to "eth0" but nevertheless, how is eth0 configured to work doing that?

Anyways, I will do what you have just said. BRB.

---

### Post by antiwindows798 on 2007-01-29
Things have apparently changed after this last installation, all of the sudden eth0 = network card that is connected to the internet and eth1 = network card that is connected to Windows XP.

ifconfig results in the following:

eth0      Link encap:Ethernet  HWaddr 00:04:76:21:7B:A6  
          inet addr:62.163.14.217  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::204:76ff:fe21:7ba6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3914012 (3.7 MiB)  TX bytes:438962 (428.6 KiB)
          Interrupt:217 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

---

### Post by kosmic on 2007-01-29
In the configurations just substitute eth0 for eth1.

Now to answer you question, your card will now because we define it in this step

 5 - sudo gedit [B]/etc/default/dhcp (and make it look like the line below)
[/B]     Code:
     [LEFT]INTERFACES="eth0" <- HERE WE ARE ALOCATION THE CARD TO DHCP ON  THAT NETWORK  ;)[/LEFT]

---

### Post by Lil_Eagle on 2007-01-30
It works!

I didn't have to buy a new switch after all.  I managed to reprogram that one to disable it's DHCP service and have Dapper statically bound to use Edgy as the gateway, then with dnsmasq and ipmasq and a few iptables commands and turning on the ip_forwarding.  I knew that it SHOULD work.  It just took me a few days (and a lot of reading) to get it going.

I probably shouldn't have jumped into this thread and throw my problem in.  If I just had of tried a little longer I would have got it.

The problem arises because there are too many ways to skin a cat, and if one has never tried it, how does one know where to begin.

Mips, thanks for the tips.  The best thread that I found was this one:

[http://ubuntuforums.org/showthread.php?t=159661]("http://http://ubuntuforums.org/showthread.php?t=159661")

---

### Post by antiwindows798 on 2007-01-30
Okay, I have done what you have told me to do.

Running sudo /etc/init.d/dhcp restart results in the following:

```
Starting DHCP server: dhcpd failed to start - check syslog for diagnostics.
```

So I have ran cat /var/log/syslog:

```
Configuration file errors encountered -- exiting
```

This is how my /etc/dhcpd.conf looks like (completely):

```
# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc; 

#assign the remote dhcp server hostname/ip addresses 
option domain-name-servers 192.168.1.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS 
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth0 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}
```

---

### Post by antiwindows798 on 2007-01-31
kosmic?

---

### Post by dsegarra on 2007-01-31
Antiwindows798

My setup is similar to yours only difference is that I have a router but do not have a 
DSL/Cable modem connected to it. My wireless pci is doing the work. Did you have
any luck?.  I am trying to put it to work as well.

---

### Post by antiwindows798 on 2007-02-01
> **dsegarra said:**
> Antiwindows798

My setup is similar to yours only difference is that I have a router but do not have a 
DSL/Cable modem connected to it. My wireless pci is doing the work. Did you have
any luck?.  I am trying to put it to work as well.

No, I'm not having any luck, I'm trying to do it myself, though, lol.

---

### Post by mips on 2007-02-02
Do you have a **eth1** yet ?

---

### Post by dsegarra on 2007-02-02
well I found this:

[http://ubuntuforums.org/showthread.php?t=349954&referrerid=190182](http://ubuntuforums.org/showthread.php?t=349954&referrerid=190182)

Found interesting what RandomJoe posted. I want to try it that way and see but havent had the chance. If I get it to work, I will post my way or wathever way I use..

---

### Post by dsegarra on 2007-02-03
Antiwindows798

I got it working using the link I previously posted. No DNS server nothing. If you can ping from/to both machines, then you should be able to connect. I was hitting my head to then find out under firefox connection settings. I had to enable Automatically detect proxy and bingo. It worked..try that.


thanx

---

### Post by antiwindows798 on 2007-02-06
dsegarra, no, I have started to do it myself because these *snip* weren't, obviously, helpful (except to encourage newbies to quit and go back to Windows and to run away *snip*).

So I will have to do it myself. And so far I have configured my network card properly. So that's outta the way, I haven't spend much time on it so far because I'm trying to get Samba to work first on it before I go back at trying to make Ubuntu share its internet connection with Windows.

Thanks again to the Ubuntu community, I'm left on my own. When you post a message about bookmarks in Firefox or anything of that level, you have got a hot thread coming up, expect noobs to reply like crazy to it. Finally a chance to impress fellow noobs! But when you ask a serious question (I still haven't had a good reply to ANY of my threads/questions so far, in this forum), nobody replies of course.

And of course, the worst thing of all, documentation of anything related to Linux is so poor it makes even Windows look good, ROFL. And most of the time when installing software you end up being required to actually know what the developer(s) of the software you are trying to install, wants you to know about insides of the software, like you have written it yourself(!). *snip* But of course, it's not for nothing that Linux is free.

---

### Post by koenn on 2007-02-06
I don't know how things work in your part of the world, but where I'm from, calling people ASSTARDED NOOBS while you're asking them for help does not work well. You might want to keep that in mind.  

If you keep bragging on about how good Windows is, what advice can we give you other then  "use Windows, it's really good, or so I hear" ?

> But when you ask a serious question (I still haven't had a good reply to ANY of my threads/questions so far, in this forum), nobody replies of course.
You've had a couple of replies that probably would have solved your problem if you'd cared to read them. (I could also assume you read them but didn't understand any of it, but i won't)
> 
And of course, the worst thing of all, documentation of anything related to Linux is so poor it makes even Windows look good,
Linux (and the software that comes with it) is just aout the best documented OS I've ever come across. Everything you'd ever want to know had been described in HOWTO's, discussed on forums and written about in books. And if that's not sufficient, you can actually see how it was written. The only thing you got half right is that some documentation requires some previous knowlegde. Which dowumentation doesn't ?

> it's not for nothing that Linux is free
Explaining the meaning of the word 'free' in this context is going to be lost on you. In any case, you got your money's worth, wo what are you complaining about ? 

------------------

Now, to return to the matter at hand : as mips already said: having Linux share an internet connection is trivial. Most people manage to set it up in 20 minutes. Forum time included. 

If you want to have another go at it I'll have a look. 
First, give me the info again - you seem to change it between posts and I don't want to be scrolling back and forth in this thread all the time or make guesses about it.  

- the Ubuntu machine will be connected to the internet, right ?
- it has 2 NIC's, correct ? 
- how does it connect to the internet : adsl router/modem ? cable modem ? dialup ? ...

for the windows machine : is it configured with dhcp (automatically get network config) or manually ?  If manually : give ip address, subnet mask, default gateway (from network connection : properties)

same questions for ubuntu. The easiest way to do this is to post the contents of /etc/network/interfaces and the output of the command ifconfig (as before) and route -n

---

### Post by kidders on 2007-02-07
Your o/p has already been _thoughrally_ answered. If you are still having trouble with your network configuration, or you have a new question, feel free to post the relevant configuration files/system logs. Perhaps someone (whom you haven't succeeded in alienating) will take a look at them for you.

I would also suggest that you identify a suitable connection sharing HOWTO, follow it, and identify any parts of it you don't understand or can't get to work properly. If you're looking for specific answers, it helps to start with a specific question.

If you are not happy with either the quality of the responses to your queries on this forum, or your Ubuntu experience in general, you should stop using them. While they're certainly entertaining, posts in the style of your latest one are of limited value to the community. Ubuntu alternatives from the Linux world include Mandriva, Gentoo, Debian, and others, all of which provide excellent support. I'm sure their users would all enjoy reading about how everything you don't quite understand is crap.

---

### Post by mips on 2007-02-07
> **antiwindows798 said:**
> 
Sure, that's why people keep asking it over and over again.

No it's because many people fail to use the search function or fail to read or don't want to read.

> **antiwindows798 said:**
> 
Good idea but there is one problem: THERE IS NO (GOOD/LOGICAL) HOWTO ON THIS SUBJECT.


There are MANY,
[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
[http://ubuntuforums.org/showthread.php?t=335465](http://ubuntuforums.org/showthread.php?t=335465)
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)
[http://ubuntuforums.org/showthread.php?t=76346](http://ubuntuforums.org/showthread.php?t=76346)
[http://ubuntuforums.org/showthread.php?t=269235](http://ubuntuforums.org/showthread.php?t=269235)

You call people rude names yet you yourself cannot get something so trivial to work. You try and get Samba working yet you don't even have basic networking configured properly. You must crawl before you can walk or run.

You have also been asked questions and you bluntly ignored them.

The way I see it the help is for free and people generously volunteer their time yet you act like a little spoiled brat.

---

### Post by mips on 2007-02-07
First, just do this:

sudo gedit /etc/network/interfaces

```
auto eth1
iface eth1 inet dhcp

iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.0.255
        gateway 62.163.14.217  #(Assuming it stays the same)
```

Windows PC:
```
       address 192.168.1.11
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.0.255
        gateway 192.168.1.1
```

Disable any firewalls etc you might have installed and just try to ping between the two machines. The first thing to establish & test is connectivity. Also try and ping to the eth1 address and see what happens.

Post output of:
```
ifconfig -a
route -n
```

---

### Post by koenn on 2007-02-07
- edit : posted too soon -

---

### Post by koenn on 2007-02-07
> **antiwindows798 said:**
> the advice that you should give me is how the **** I can do what the **** I have asked for, how is that for an advice?
I was going to do just that, as soon as you'd given me the info I need to get a handle on the problem. In stead, you've choosen to pick a fight. No problem. _My_ internet connection sharing is working. 

> then why the **** haven't you answered this thread when I asked the question about sharing an internet connection?
I didn't spot this thread until yesterday. And what gives you the idea that I (or anyone else around here) is under any obligation to answer questions ? 

> Yes. That's funny, you criticize me for not have read what the repliers have said, while I have explained my settings in great detail.
As I don't like to be misquoted : When I asked for your config, I  explained that it was because you seem to change it every now and then, and I'd rather not go looking in 100 posts for what *might* be the current config of your computers.


Apparently you prefer having an argument over having your network problem fixed.
Fine.
Bye.

---

### Post by kidders on 2007-02-07
> **koenn said:**
> Apparently you prefer having an argument over having your network problem fixed.
Fine.
Bye.

None of the details I requested have been provided either.

Cya guys.

---

### Post by mips on 2007-02-07
Maybe we should ask the mods/staff to close this thread as I honestly don't believe we are going to help this individual or meet his expectations ever..

I mean so many people have gone out their way to try and help him but there is zero gratitude. Others have hijacked this thread and were sorted out in no time.

This is really a easy thing to do, no argument.

---

### Post by koenn on 2007-02-07
mips, you have a point. 
I suggested to the mods this might be a troll and would leave it up to them - but whatever the outcome, I "m not planning on posting in this thread anymore.  

nice job with the hijackers btw.

---

### Post by mips on 2007-02-07
> **antiwindows798 said:**
> Okay, let's see what you have.



I don't want to install FireStarter. Why? Because it's not needed to do so to share an internet connection.



That sets up TEMPORARY settings, which are not valid after a reboot.



That's about wireless networking, it includes also temporary crap.



I have no router.



Router + Firestarter crap.



Wireless router + XBox crap.

***Looks like you have failed to proof your point.***


If you cannot take the above links and make them work for you then I'm sorry to say that there is absolutely no hope in hell that you will ever get this right.

I would honestly suggest that you stick to windows. It's seems suited to your needs.

On other forums you would have been blown off a long time ago.

My time on this thread is over & I'm adding you to my ignore list which is a 1st ever.

---

### Post by K.Mandla on 2007-02-07
Keep the thread on-topic and civil, or it will be locked.

---

### Post by ihatecommies on 2007-02-07
I have the same problem and none of these solutions worked for me. I can share files between Windows and Linux but I can't figure out how to share an internet connection between the two (I have two Windows boxes here but I only need internet on one of them and I only have access to the internet on my Linux box).

---

### Post by mips on 2007-02-07
> **ihatecommies said:**
> I have the same problem and none of these solutions worked for me. I can share files between Windows and Linux but I can't figure out how to share an internet connection between the two (I have two Windows boxes here but I only need internet on one of them and I only have access to the internet on my Linux box).

Start your own thread and post the link to it here. you will be helped.

In your new thread post output of 
/etc/network/interfaces
ifconfig -a
/etc/resolv.conf
your IP address parameters
what setup you have etc.

Why does your username give me a sense of dejavu ?

---

### Post by ihatecommies on 2007-02-10
Okay, I will make a post "ICS on Ubuntu".

---

### Post by ciroberts on 2007-02-10
Well, not sure if this message should go here but everyone else has posted whatever they feel like here so before this thread hits the dumps, I'd like to say that the labours of the helpful souls involved didn't go in vain for I was able to do exactly what the guy who started this thread was trying to do. I installed Ubuntu on a old laptop I had and made up a crossover cable from an ethernet cable I bought. I'm studying to get my certification so I like doing things the hard way instead of just buying a router, it will help me in the real world. So my task was to make the Ubuntu laptop act like a router so the two computers both could surf the net.

[COLOR="Red"]**So thanks to all who contributed their info, this thread now has an ABUNDANCE of good, well, actually GREAT tips to get something like this working. Good can come out of all things!** [/COLOR]

Special thanks to **KOSMIC** though, his advice to add the line 

"sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth(x) -j MASQUERADE"

*- where x indicates the adapter connected to the Internet

did the trick for me I think. 

After that I was able to ping websites by their IP address but not Domain name because I'm not running DNS software on the laptop I'm using as the router. *Therefore*, all I did was run the DIG command and at the end it gives the IP address of the network DNS server that it gets its info from (I connect using a cable modem by the way). I put that in for the preferred DNS server on the Windows computer and everything is working perfectly. It's actually the same computer I'm using to submit this message!

I'd like to make a quick suggestion that can ease frustration for the Noobs trying to do this, because I'm a Noob too I know!!

*Instead of retyping commands over and over, it's easier to make a simple script file and give it root execute permissions so you can run the entire script via the sudo command. My script was called "becomerouter" so whenever I had to alter code and restart the network afterward I simply typed "sudo /<full path to script>/becomerouter" to run the commands again to give the interfaces their IP addresses and configure IPtables etc...*

*Another tip, watch out which sites you use to ping to test your connection, some servers don't respond to Ping requests so you may think your connection isn't working when that particular IP address just doesn't respond to any pings. I used yahoo and hi5.com to test. Or better yet, just use a browser to test!!!

---

### Post by koenn on 2007-02-10
:)

---

### Post by antiwindows789 on 2007-02-10
After having configured my network car and a DHCP server MYSELF, I realized that Kosmic was ether giving me either WRONG or INCOMPLETE information.

But that doesn't matter, apparently because obviously you MUST talk happy here at a Disney level, regardless if it's wrong or not, for as long as you talk in a way that will be perceived as "positive" (no criticism or anything like that) by the noob community (in order to make keep them in believing that they are not noobs) of Ubuntu and its moderators, it's okay. There is actually a word for that: communism.

Networking in Linux is probably done well, but the documentation for the applications that run on it is a disaster and even worse is the Linux community to which you are directed for any questions you have.

Anyways, I'm still a Linux noob because I'm new to Linux (but not to computer technology in general) and I'm still trying to set this up but I will do it on my own. I will not use this communist noob forum anymore.

---

### Post by antiwindows789 on 2007-02-10
Before I leave, one thing I have noticed is that nothing has worked out to get this internet sharing crap working (I know, there is almost nothing about this on the internet but still). I have done EVERYTHING so far to get it to work, the only thing I got to work is a DHCP server but that's it.

So it is even possible? I mean, I know that nobody really knows how to do it, and from my short experience with Linux, I bet that if it is possible, it will be some half baked ICS, there will be probably a billion things you can't do on the Windows PC. So my question is: can a normal fully working ICS be set up with Ubuntu?

---

### Post by pay on 2007-02-10
Can't you just use a router?

---

### Post by Bil-E-daKid on 2007-02-10
Hello antiwindows,

Can you please go into a little detail about what bits of hardware you have, how they are connected, and how you connect to the internet?

Many thanks
Bil-E-daKid

---

### Post by meng on 2007-02-10
> **antiwindows789 said:**
> Before I leave, one thing I have noticed is that nothing has worked out to get this internet sharing crap working (I know, there is almost nothing about this on the internet but still). I have done EVERYTHING so far to get it to work, the only thing I got to work is a DHCP server but that's it.
You're leaving? Sorry to see you go.
> So it is even possible? I mean, I know that nobody really knows how to do it, and from my short experience with Linux, I bet that if it is possible, it will be some half baked ICS, there will be probably a billion things you can't do on the Windows PC. So my question is: can a normal fully working ICS be set up with Ubuntu?
You ask the question but you also answer it. So I'm not sure what you want to hear, since you already seem to know the answer.

Ubuntu/Linux is not for everyone. Perhaps it's not for you.

---

### Post by Bil-E-daKid on 2007-02-10
Very good point meng - I wondered that myself.  I wondered if I am perhaps falling prey to some kind of pro-MS troll?  There seems to be quite a few around at the moment eh...

---

### Post by antiwindows789 on 2007-02-10
> **pay said:**
> Can't you just use a router?

Because I don't feel like paying $ 80 dollars to get a router when my computer can serve as one.

> **Bil-E-daKid said:**
> Hello antiwindows,

Can you please go into a little detail about what bits of hardware you have, how they are connected, and how you connect to the internet?

Many thanks
Bil-E-daKid

Thanks dude, for trying to help me out. But I really don't feel much for another thread with 100+ replies, another "infraction" and having it end in a fight because nothing has worked to get my ICS to work. If you really know enough about ICS, networking and so on, I will be happy if you could help me out.

> **meng said:**
> You ask the question but you also answer it. So I'm not sure what you want to hear, since you already seem to know the answer.

No, not really. Reread what I have written.

> **meng said:**
> Ubuntu/Linux is not for everyone. Perhaps it's not for you.

Hmmmmm, well, let's see. I have worked for about 7-8 years as a programmer, 2 years as a database administrator and I often work as a Windows system administrator (at which I'm still new and I hate it). If Linux is not for me, then it's for no one.

> **Bil-E-daKid said:**
> Very good point meng - I wondered that myself.  I wondered if I am perhaps falling prey to some kind of pro-MS troll?  There seems to be quite a few around at the moment eh...

I'm realistic and definitely not in support of Microsoft.

---

### Post by Bil-E-daKid on 2007-02-11
Hey there again antiwindows,

I'm glad you're not a troll - I'd hate to be wasting my lazy Sunday afternoon helping one!  ;-)

Anyways, to be honest, I'd most likely not be the very best person to help you but I'm willing if you are.

I have set up a Dapper box as an internet firewall, web proxy filter for a local non-profit (which is basically a router on the edge of their network - between the LAN and their adsl router) so I may be able to help if you're situation is similar.

The reason I asked for more info is that, if you are connecting via a modem or some such, then I've not done anything like that before so may not be of much help.

If it's the first one around, then there's an IP routing option somewhere you need to turn on to get the linux box to be able to foward IP traffic (act as a router).   See [http://www.rohansheth.com/2006/06/27/building-a-simple-router-using-iptables/]("http://www.rohansheth.com/2006/06/27/building-a-simple-router-using-iptables/") for more details.

The rules of what gets routed and what doesn't is configured in your iptables ruleset.  (Do a google for iptables rule generator and you'll find a couple of resources online to assist with configuring that side of things). 

Fair enough though given you've already tried everything.  May it go well with you whatever way you decide to go.

Regards
Bil-E-daKid

---

### Post by esaym on 2007-02-11
Ubuntu really isn't made to be a router.

Perhaps try smoothwall or something.  There are tons of router style distros out there.  I been using smoothwall for 4 years now

---

### Post by ihatecommies on 2007-02-11
Bil-E-daKid you can help me out! [http://www.ubuntuforums.org/showthread.php?p=2136578](http://www.ubuntuforums.org/showthread.php?p=2136578)

I have the same problem!

> **esaym said:**
> Ubuntu really isn't made to be a router.

Why not?

---

### Post by kidders on 2007-02-11
Users on this thread may be interested in taking a look here before posting ... [http://www.ubuntuforums.org/showthread.php?t=345638](http://www.ubuntuforums.org/showthread.php?t=345638)

---

### Post by ihatecommies on 2007-02-11
> **kidders said:**
> Users on this thread may be interested in taking a look here before posting ... [http://www.ubuntuforums.org/showthread.php?t=345638](http://www.ubuntuforums.org/showthread.php?t=345638)

That post is useless, I have been looking at that thread for 3 days now.

---

### Post by aysiu on 2007-02-11
> **kidders said:**
> Users on this thread may be interested in taking a look here before posting ... [http://www.ubuntuforums.org/showthread.php?t=345638](http://www.ubuntuforums.org/showthread.php?t=345638)

> **ihatecommies said:**
> That post is useless, I have been looking at that thread for 3 days now. I've merged the two threads, since they're basically the same thing.

---

### Post by houstonbofh on 2007-02-11
> **antiwindows789 said:**
> Hmmmmm, well, let's see. I have worked for about 7-8 years as a programmer, 2 years as a database administrator and I often work as a Windows system administrator (at which I'm still new and I hate it). If Linux is not for me, then it's for no one.
Talk about arrogance...  Anyway, I know that Linux **can** do this.  However, I am not sure it can be done in Ubuntu.  I tried to make an Ubuntu server a switch for sniffing purposes, and failed.  It may be the wrong tool for this job.  In the past few years I have been using m0n0wall for this, as it is a better tool, and runs on anything.  You can get a used router for $15, so why do this?

Let me put this in words you can understand.

I want to run my e-commerce web application.  I want to use Microsoft Personal Web Server, and use DCOM to tie it to an Access database.  I have read the guide at [http://www.webwizguide.com/asp/tutorials/installing_pws_win98.asp](http://www.webwizguide.com/asp/tutorials/installing_pws_win98.asp) but can't get the web application to talk to Access.  This documentation sucks!  Can you even run an e-commerce app on Windows?
:lolflag:

---

### Post by K.Mandla on 2007-02-11
This thread has deviated enough and devolved more than enough to warrant closing. It is unfortunate that the goodwill of our members was abused by a troll, but the honest people who attempted to help deserve a generalized note of thanks for their efforts.

If you're still having problems with networking and your issue resembles the problems described here, please feel free to post a new thread asking for help with a link back to this one. 

And now, I get to use my favorite smilie. 

[IMG]http://xs312.xs.to/xs312/07056/sabdfl-anim.gif[/IMG]

THREAD CLOSED! :D

---

