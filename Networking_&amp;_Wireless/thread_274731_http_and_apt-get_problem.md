---
title: "http and apt-get problem"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by myso on 2006-10-10
Hi,
 i've got two problems.
1. i can't access any web pages. whatever I put in the mozzilla browser is timed-out. However, ping works, gaim works etc. It seems the 80 port is blocked somehow. But I can't find out what's wrong

2. sudo apt-get install doesn't work. when i looked at sources.list i found out it was full of comments -> that the installer couldn't verify something... i don't remember the exact comments and because i can't access this forum from linux, i can't post it. but every single line in the file was commented and the comments stated it was the work of the installer. I also remeber that during the installation there was an error message concerning some security updating, i think (i'm not sure of the exact problem). There was only one error throughout whole installation so I think it has something to do with all the apt-get and browsing problems.

I tried to google out some solutions but nothing worked.

something to add:
 - I don't have any firewall, i wanted to install firestarter, but since the apt-get install command doesn't work -> i couldn'
 - so all I've got is the basic Ubuntu just after installation

---

### Post by wieman01 on 2006-10-10
1. Disable ipv6 in Firefox: 

a. URL field: about:config
b. Search for ipv6.
c. Right-click->toggle

To disable ipv6 globally/system-wide, search the forum.

---

### Post by wieman01 on 2006-10-10
2. Source list:
> ### Repositories ###

## Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Ubuntu 'Backports' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

## Ubuntu Bug Fix Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Ubuntu Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse


There is also a nice source-list generator: [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by myso on 2006-10-10
i've tried that before:
doubleclick on "network-dns-IPV6-disable"
 so i set it to true, but it didn't help.

---

### Post by wieman01 on 2006-10-10
> **myso said:**
> i've tried that before:
doubleclick on "network-dns-IPV6-disable"
 so i set it to true, but it didn't help.
Can you ping [www.google.com?](www.google.com?) 

Have you installed a firewall (e.g. Firestarter)?

If all this is negative, disable IPV6 globally. The forum is full of howtos. That should help.

---

### Post by warden on 2006-10-10
sounds like a dns problem...

check your /etc/resolv.conf for "nameserver" entries
and try to ping them...

also try 72.14.221.147 (thats google) in your browser, if it works its definetly a dns problem

also, port 80 is not on your machine, its on the server side....

---

### Post by myso on 2006-10-10
i've used the source.list that was posted here, but it didn't work.
the apt update always gets timed out.
however ping for archive.ubuntu.com, security.ubuntu.com and [www.google.com](www.google.com) did work.

i haven't got any firewall -> only the pure ubuntu iso installation

---

### Post by wieman01 on 2006-10-10
> **myso said:**
> i've used the source.list that was posted here, but it didn't work.
the apt update always gets timed out.
however ping for archive.ubuntu.com, security.ubuntu.com and [www.google.com](www.google.com) did work.

i haven't got any firewall -> only the pure ubuntu iso installation
Then it's not a DNS issue. I reckon you need to disable "ipv6" globally: [http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6]("http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6")

---

### Post by puppy on 2006-10-10
Have you changed any of your networking hardware recently? If so, it *might* be a problem with the MTU setting - I'm having similar issues not being able to access my pop mail and some websites after switching to a wireless connection recently...

---

### Post by myso on 2006-10-10
ping of the nameserver in resolv.conf worked perfectly.
but trying to reach google through firefox by putting in the IP address didn't. so i guess it really isn't DNS. I'll try the global IPV6 disable thing.

I haven't changed any hardware recently.

THANKS for fast replies guys, I haven't seen that in other forums.

---

### Post by myso on 2006-10-10
bad news, the global disabling of ipv6 didn't help. i did this way:

----------------------------------------------------------------
So here are the changes I put in with the orginal comment out.
But the re-boot is required.

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6
----------------------------------------------------------------

it's from the link that was posted here.
i changed the file, saved, rebooted, but no browsing available.
any ideas?

I think it might have something to do with communication on port 80 -> both apt and browser use this http port. IS there any way to block it in the standard ubuntu installation? I don't have any firewall (i couldn't install any packages).

---

### Post by mips on 2006-10-10
What hardware are you using, modem/router model etc ???

1. Please post output of **lspci | grep Eth**
2. Please post output of **ifconfig eth0**  (Depends on your interface number)
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Who is your ISP and provide a web link.
[I]
If you are dual-booting install the **ext2ifs** driver in windows and access your ext2/3 partions in linux from windows if you want to transfer data across in order to paste here. Alternatively use a usb memory stick or stiffy disk.[/I]

---

### Post by warden on 2006-10-10
You DO have a firewall by the very fact that you installed Linux. It is included in the kernel itself. You can check if any filtering rules have been set by running "iptables -L" as a root (or sudo-ing). OUTPUT chain is the one you should be looking at to see if packets with outgoing port 80 are blocked. Although, I couldn't think of any reason why should such a thing exist on a fresh install, except because of an error in some of the installation scripts.... :-k

---

### Post by myso on 2006-10-10
> **warden said:**
> You DO have a firewall by the very fact that you installed Linux. It is included in the kernel itself. You can check if any filtering rules have been set by running "iptables -L" as a root (or sudo-ing). OUTPUT chain is the one you should be looking at to see if packets with outgoing port 80 are blocked. Although, I couldn't think of any reason why should such a thing exist on a fresh install, except because of an error in some of the installation scripts.... :-k

according to this I thought Ubuntu has no firewall in the standard installation:

1. UBUNTU

The actual installation was smooth, easy and provided an excellent desktop for a user who is new to Linux. Someone who wanted only basic options.
What I liked:
Simplicity: Give the user what they need, no more unless they want to add that themselves. Good idea!
Easy Install: Ok a distribution has to be easy for the user to install and one CD is about as easy as it gets. The steps of installation are quick effective and to the point. The network setup worked fine in the install!

I loaded the distro on a AMD desktop and a Fujitsu Siemens Amilo laptop and they both loaded with no problems. Detection of the laptop screen was flawless. Power Saving features worked with no problems.
USB Detection: My conclusion is that some of the cheap, USB1 drives will not work without some configuration changes, but the better USB2 drives will autodetect.
Network Tools: Gnome now offers a handy tool to use for networks. It is actually 8 tools in one interface. The tools are Devices,Ping, Netstat,Traceroute, Port Scan, Lookup, Finger and Whois. These are certainly handy tools and they are easy to use in the graphical interface.
What I did not Like:
My biggest complaint by far... no functional firewall exists on the system. I went to the website and found that the concept of the designers is that since you are not using a daemon by default so you do not need a firewall. PLEEEASE...don't let our Linux future put at risk security and force us all to return the constant hacks and fixes we all hated in Windows. Security is important and the system does need a simple to install firewall.

---

### Post by myso on 2006-10-10
requested outputs:

myso@myso-desktop:~$ lspci|grep Eth
0000:00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


myso@myso-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:50:8D:3A:02:25
          inet addr:10.23.3.68  Bcast:10.23.3.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe3a:225/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28368 (27.7 KiB)  TX bytes:1807 (1.7 KiB)
          Interrupt:201 Base address:0x6f00


myso@myso-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.23.3.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.23.3.1       0.0.0.0         UG    0      0        0 eth0


myso@myso-desktop:~$ cat /etc/resolv.conf
search roburnet.lan
nameserver 192.168.23.1


myso@myso-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


myso@myso-desktop:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#} 

I have a cable connection. I guess there is one router for whole flat building(is that what you call it? :) ). There are a few other families having the same provider( So there are about 5-8 loacl IPs connected to the router). Provider's homepage is in Slovak language, i guess you don't need it then. But if you want to know anything else, ask me and i'll try to find out. I've never had similar problem in Windows

---

### Post by warden on 2006-10-10
> **myso said:**
> according to this I thought Ubuntu has no firewall in the standard installation

Ahh... I see some of the GNU/Linux lore is needed:

Ubuntu is just one of the many distributions of the GNU/Linux operating system (the best one, IMHO). The main part, the core, of ANY Linux distribution, is the kernel. The kernel has, included in it, packet filtering capabilities (to put it simply, a firewall). It is called netfilter and one of the many tools to configure it is iptables, which is installed by default. There are other such tools available, like Firestarter. 

Unlike Windoze, you don't need special firewall rules unless you are running a server (security is much, much tighter in Linux when it comes to network connections). If you are interested in setting up firewall rules without a GUI tool, you can check [http://www.linuxguruz.com/iptables/howto/iptables-HOWTO.html](http://www.linuxguruz.com/iptables/howto/iptables-HOWTO.html), but this is beside the main issue, since you don't have web connection yet. 

So, try "sudo iptables -L", and you'll get the list of all firewall rules that have been set on your machine. If there is a rule under the "Chain OUTPUT" section that mentions port 80 (or http), then there is your problem. In that case, you can run "sudo iptables -F" to delete all rules. But as I said, a fresh install of Ubuntu should have all those sections empty...

---

### Post by myso on 2006-10-10
Warden,
 output of iptables looks like this:

sumyso@myso-desktop:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

so , there are obviously no restrictions on port 80.
The reason why I thought there's no firewall is the article i posted above. The whole thing is here [http://helpero.com/news/Computers/Linux/UBUNTU-vs-SUSE-vs-FEDORA_20.html](http://helpero.com/news/Computers/Linux/UBUNTU-vs-SUSE-vs-FEDORA_20.html)

---

### Post by warden on 2006-10-10
> **myso said:**
> [http://helpero.com/news/Computers/Linux/UBUNTU-vs-SUSE-vs-FEDORA_20.html](http://helpero.com/news/Computers/Linux/UBUNTU-vs-SUSE-vs-FEDORA_20.html)
Well, it is obviously written by "user who is new to Linux", as he puts it.....

---

### Post by mips on 2006-10-10
> **myso said:**
> 
myso@myso-desktop:~$ lspci|grep Eth
0000:00:06.0 **Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+** (rev 10)


I suspect the above might be your problem. Do a search here for **8139** and you will find many posts/threads on people having issues with the 8139 chipset.

---

### Post by wieman01 on 2006-10-10
> **warden said:**
> You DO have a firewall by the very fact that you installed Linux. It is included in the kernel itself. You can check if any filtering rules have been set by running "iptables -L" as a root (or sudo-ing). OUTPUT chain is the one you should be looking at to see if packets with outgoing port 80 are blocked. Although, I couldn't think of any reason why should such a thing exist on a fresh install, except because of an error in some of the installation scripts.... :-k
Yes, every Linux user has one. But as you have pointed out, it is never enabled by default. All ports are open by default.

---

### Post by myso on 2006-10-11
> **mips said:**
> I suspect the above might be your problem. Do a search here for **8139** and you will find many posts/threads on people having issues with the 8139 chipset.

If it was a hardware problem, why would ping and other basic commands work? I would suggest that no connection would be working.

---

### Post by myso on 2006-10-11
I did a search for **8139**, but i think all the issues concern a NIC that can't connect to the network at all. But, as mentioned before, I'm able to ping IPs.

---

### Post by wieman01 on 2006-10-11
You are not not only able to ping IP addresses, but also domains (such as [www.google.com](www.google.com)) as I recall, correct?

Can you do me a favor and run 2 more commands in order for us to see what going on there:
> sudo gedit /etc/resolvconf/resolv.conf.d/base
> route
Then post the output.

And you have got DHCP enabled, correct?

---

### Post by wieman01 on 2006-10-11
I suspect something is wrong with your DNS settings... That's common sense but the routing table looks odd. Please also post this one once again:
> sudo gedit /etc/resolv.conf
We are getting there.

---

### Post by myso on 2006-10-12
myso@myso-desktop:/etc$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.23.3.0       *               255.255.255.0   U     0      0        0 eth0
default         10.23.3.1       0.0.0.0         UG    0      0        0 eth0


myso@myso-desktop:/etc$ sudo gedit /etc/resolv.conf
search roburnet.lan
nameserver 192.168.23.1 

did you really mean
 "sudo gedit /etc/resolvconf/resolv.conf.d/base" ??
there is no such directory, or am I blind?

what exactly do you mean by DHCP enabled? is there a certain command for this or is it somewhere in the network settings?

and yes, i can ping google.

thanks

---

### Post by wieman01 on 2006-10-12
You enable DHCP in the router. 

What's your router's IP address, please? I reckon it's "192.168.23.1", is that correct?
[U][B]
EDIT:[/B][/U]
Also go to: Firefox->Edit->Preferences->General->Connection Settings. Do the "Proxy" settings say [COLOR="Red"]"Direct connection to the Internet"[/COLOR]?

---

### Post by myso on 2006-10-13
I don't have access to the router. It's for the whole building and taken care of by the provider company -> but I don't think it's a router problem, because I have no such problem with windows. I'm writing this on my computer from windose :).

---

### Post by wieman01 on 2006-10-13
A. _**Also go to:**_ Firefox->Edit->Preferences->General->Connection Settings. Do the "Proxy" settings say "Direct connection to the Internet"?

B. Plus, could it be that you have to have a chat with the administrator of the router? There is a chance that he has restricted the Internet access. Perhaps you need your own proxy as well. This does not seem to be a Linux problem anymore.

---

### Post by myso on 2006-10-13
BINGO!!!
wieman, you got me to the right point. The browsing problem is solved. I use a proxy server - I've thought of this before - one simply has to edit the settings manually. And so I did long ago in System -> Preferences -> Network Proxy. I thought this should work for whole system, but opbviously it didn't. Actually I thought that firefox might want it's own settings, but in windoze it's Tools -> Options etc. And so I searched for such thing in Linux firefox and there was no Options entry in the Tools menu (it's in the Edit menu as I see now) - that's why I thought the System -> Network proxy should work for whole system. Man, it's a pretty lama mistake. ](*,) 

Anywayz, I still can't make the apt-get command work.
The command I use is f.e.

"sudo apt-get install firestarter"

but it stops at

"E:Couldn't find package"

I've replaced my former messed-by-installer sources.list with thies one:

  # See sources.list(5) for more information, especially
     # Remember that you can only use http, ftp or file URIs
     # CDROMs are managed through the apt-cdrom tool.
     deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
     deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free
     deb [http://security.debian.org](http://security.debian.org) stable/updates main contrib non-free
     
     # Uncomment if you want the apt-get source function to work
     deb-src [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main contrib non-free
     deb-src [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main contrib non-free

---

### Post by wieman01 on 2006-10-13
Ok, try mine instead if you don't mind (and if you're running Dapper):
> ### Repositories ###

## Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Ubuntu 'Backports' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

## Ubuntu Bug Fix Updates
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Ubuntu Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

There is also a good source-list generator available here: [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

Piece of cake now that you have an Internet connection.

---

### Post by wieman01 on 2006-10-13
Myso, 

Just a comment... Watch out when you're installing Firestarter. Depending on what firewall policy you set, Firestart will disconnect you from the router/Internet/etc. first of all. You need to open the ports for DHCP and also allow port 80 to get it working again.

You open the graphical frontend for Firestarter by typing...
> sudo firestarter
This way you can configure your firewall. Let me know if this tool creates problems. I am running it so I can help you out.

---

### Post by myso on 2006-10-13
your list didn't help, the problem must be elsewhere.

---

### Post by wieman01 on 2006-10-13
> **myso said:**
> your list didn't help, the problem must be elsewhere.
Mmm... Could be the proxy again. Let me think for a while...

---

### Post by myso on 2006-10-13
> **wieman01 said:**
> Mmm... Could be the proxy again. Let me think for a while...

sure, think as long as you need ;)

---

### Post by wieman01 on 2006-10-13
You can set a proxy in Synaptic as well. See screenshot...

[COLOR="Red"]Settings->Preferences->Network[/COLOR]

---

### Post by myso on 2006-10-13
it didn't help.
i tried ports 3128 (and 8080 too - just in case)

myso@myso-desktop:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter

---

### Post by myso on 2006-10-13
the terminal command doesn't work, but I managed to get firestarter through Synaptic package man. Isn't that a bit wierd?
I would really like the terminal commands to work, too.

I ran the command you suggested, and the output looked like this:

myso@myso-desktop:~$ sudo firestarter
Error reading file /etc/firestarter/inbound/allow-from: No such file or directory
Error reading file /etc/firestarter/inbound/allow-service: No such file or directory
Error reading file /etc/firestarter/inbound/forward: No such file or directory
Error reading file /etc/firestarter/outbound/deny-to: No such file or directory
Error reading file /etc/firestarter/outbound/deny-from: No such file or directory
Error reading file /etc/firestarter/outbound/deny-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-to: No such file or directoryError reading file /etc/firestarter/outbound/allow-from: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Error reading file /etc/firestarter/outbound/allow-service: No such file or directory
Warning: External interface previously configured not found
Warning: Internal interface previously configured not found

However, the wizard worked and I set the firewall through the Firestarter GUI interface. There were no problems with disconnecting or blocking port 80 as you mentioned above.

---

### Post by wieman01 on 2006-10-13
Doesn't that work either?
> sudo aptitude install firestarter

---

### Post by shilliard on 2006-12-29
Did anyone ever find a solution for this?

I've the same problem, can't access repositories via http.  Works fine if I change my /etc/apt/sources.list repositories to use ftp instead of http.

I'm using a regular install of Dapper, nothing changed.  Router is a Netgear FVS318.

---

### Post by handy on 2006-12-30
[Try this DNS fix]("http://ubuntuforums.org/showthread.php?t=282034") ?

Hope it helps... :)

---

### Post by shilliard on 2007-01-03
As suggested I changed my DNS settings to use the OpenDNS servers but it didn't solve the apt-get problem with http.

Firefox works fine, and I can use apt-get with ftp but not http, it's weird.

---

### Post by shilliard on 2007-01-03
Found the solution on another thread, I removed the following line from /etc/apt/apt.conf:

Acquire::http::Proxy "false";

apt-get works fine now with http.

Thanks

---

