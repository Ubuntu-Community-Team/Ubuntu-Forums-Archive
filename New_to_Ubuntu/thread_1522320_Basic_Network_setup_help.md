---
title: "Basic Network setup help"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by netwidget on 2010-07-02
Please help.

I am new to Linux, ubuntu, and I only know a little about networking.  I am very, very, very, frustrated with IP addressing, hostnames, file sharing, etc.

I trying to setup up a network in my house that has the following pieces to it.  File server, printer server, access to the internet;  Client computers: wireless laptops, desktops (with eternet and wireless), apple TV with XBMC (ethernet).

I have DSL through Qwest (netopia router, ISP DNS settings) and another wireless router (set up on netopia as pass through) acting as a DHCP server to wireless and cabled computer (cable to router). 
 
server is named servermain. It is running Ubuntu Server 10.04 AMD64. I have set up directories on servermain and set them (the folders) to exported with read write privileges.  

The exports file on servermain has this line in it for mounting folder '/':

/  laptop1(rw)  

  ;where 'laptop1' is the name of the client computer to be given rights to '/' on servermain.

in laptop1's fstab file it reads:

servermain:/  /home/username/server nfs

The nfs-kernel-server is installed on servermain and nfs-common is installed in laptop1.

when I type $ sudo mount -a, I get the following message:

"mount.nfs; DNS resolution failed for servermain: Name or service not known"

My questions are does the DHCP server resolve computer names? I did not setup a domain when I installed and setup servermain does it need one?  Does the domain have to be FQDN or can it be anything made up that does not resolve anywhere except to the internal DHCP server on the LAN?  What is the hostname vs the DNS name vs the domain name?  How does my computers on the LAN know to look for each other?

Everything I have read on these forums and in the ubuntu tutorials and setup pages makes HUGE assumptions as to the basic understanding of network terminology and setup jargon.  Where do I go to use ubuntu as a novice and to learn networking terms to have an understanding of what I am doing.

I know this is long but I have been surfing for days to get simple general questions answered with no luck.

Thank in advance for any help/answers

---

### Post by gzarkadas on 2010-07-03
Try to give a permanent IP address to your server (from your internal network range). This most likely will have to be performed through the web interface of your DHCP server.

Then in each client computer, edit its `/etc/hosts' file, adding a line:
```

<server-IP-address>    servermain

```If your clients' `/etc/host.conf' has a line of the type `order hosts,bind' (or similar if hosts is present there), then this will allow your clients to see the server irrespectivelly of your dns settings.

---

### Post by netwidget on 2010-07-03
Thank you, but my DSL ISP is not a static IP address.  It is dynamic.  The WAN side of my router is setup with DHCP,  The LAN side of the both of my routers are setup as DHCP as well.

If all of the routers are set to DHCP settings and the computers in the LAN will be set to DHCP, how do I use computer names in (any, all)config files to create mount-points, priveledges, etc...

I don't know the difference between nameservers, hostnames, DNS, DNS client DNS services, and domain names.

Please help.

---

### Post by gzarkadas on 2010-07-04
The hosts mechanism can work independently from dhcp. The only thing you need to do is assign a static IP (one that does not change if the server is rebooted and is always the same) to the server. Then any client with a modified as described /etc/hosts will be able to resolve the name of the server to an IP address.

To do this, per those guides: [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html), [http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html#ASSIGNIP](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html#ASSIGNIP), all you have to do is:

1. Add (do not delete the other lines) the following lines to the server's `/etc/network/interfaces' file. The following assumptions are made:
-- Your network as created by your router / dhcp server has the address: 192.168.1.0
-- Its netmask is 255.255.255.0 (true for any network starting with 192.168....)
-- Your gateway (the WAN/LAN router) has the address: 192.168.1.254
-- The address you assign to your server is: 192.168.1.240
-- Your server connects to the network with an ethernet cable, and it has only one network card, so that its active interface is `eth0'.
If something of the above is different in your case, simply change the example to your real value(s).

```

auto eth0
iface eth0 inet static
        address 192.168.1.240
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        gateway 192.168.1.254

```

Save the file and then restart your server. 

After the server has started again, open a terminal window and type:
```
sudo ifconfig | less
```

Scroll the output of the command until you see a line starting with `eth0'. If the values reported in that section of output match the above, then you are ok.

Now go to your clients, edit their `/etc/hosts' file (the line with the specific values of this example becomes:```
192.168.1.240  servermain
```) and restart them too.

---

### Post by evermooingcow on 2010-07-04
In this case your server will need a similar setting if you want to be  able to export your share
```
/  laptop1(rw)
``` as you have above. Otherwise your server  won't know where "laptop1" is.

You would need a static IP for your laptop in addition to the server as  in the example above and a below entry in the /etc/hosts file of your *server*:
```
ip_of_laptop laptop1
```Alternatively you can export your share  to your entire subnet as
```
/ 192.168.1.0/24(rw)
``` so that any computer on your local  network will have full access (including laptop1).

If you want to take the manual entry aspect out of this and retain  dynamic addressing but have all of your computers still addressable by  name you would need to set up a dynamic DNS server.

---

### Post by netwidget on 2010-07-05
gzarkada:, Thank you for follow up information, 

evermooingcow:  Thank you for your response... are you saying that gzarkadas' information will not work unless there are static ip addresses assigned? And that the only way to get my LAN to work completely inside DHCP is to configure it using dynamic DNS?  Let me clarify the architecture in hopes that your help can be confirmed:

[LIST]
[*]DSL modem/router gets IP address (WAN) from ISP:  Method, DHCP.
[*]servermain gets IP address (LAN)from DSL modem/router: Method DHCP.
[*]Wireless router gets IP addresses(LAN)from servermain: Method, DHCP.
[*]laptop1 gets IP address (nested LAN) from wireless router: Method, DHCP.
[/LIST]

Assuming that the above architecture and configuration is working correctly with ip ranges, etc., for the nested LAN requirements, is dynamic DNS going to keep track of and allow all the networked computers to resolve servermain.  And, will the server be able to resolve all computers on the network so that file services, and printer services will work?

I really appreciate the help that both of you have given me.  And I know that this is all volunteer based.  It would be extremely helpful to have a complete "exhaustive" guide for installing, configuring and maintaining Ubuntu Server.  I have followed one snippet of instructions on one website only to run into a big question or a problem with my particular system.  Then I find and follow another snippet of info from another website only to run into another problem.   And yes I have gone to Ubuntu's main server installation guide in an effort to follow a step by step approach to installing.  It is not exhaustive, and is easy to get stuck quickly with too many questions unanswered and no link or sidebar for clarification.   I am insanely typing into these config files exactly what is typed in the snippet not knowing 65% of the time what I am typing, what it does, and how it works.

I installed Ubuntu server 10.04 over 2 weeks ago and it is still not configured.  I have changed the various config files as many as 8 times.  Both routers have crashed 2 twice and I have had to  reset and then reconfigure them. My ISP has zero support for Linux systems. So I am feeling really alone here.  

I fear that it is impossible to install and build a Linux server based on the "one sentence" answers provided here and on the web.

Thank you

---

### Post by gzarkadas on 2010-07-07
> **netwidget said:**
> ...

[LIST]
[*]DSL modem/router gets IP address (WAN) from ISP:  Method, DHCP.
[*]servermain gets IP address (LAN)from DSL modem/router: Method DHCP.
[*]Wireless router gets IP addresses(LAN)from servermain: Method, DHCP.
[*]laptop1 gets IP address (nested LAN) from wireless router: Method, DHCP.
[/LIST]
...

This seems overly complicated and also inconsistent with your first post. 

The network topology that you now describe is [[this]("http://ubuntuforums.org/album.php?albumid=1938&pictureid=6498")]. It has the server as intermediate between the two routers, thus with the need for two network cards, a running dhcp server and network translation between the clients and the DSL router. It really is useful only if you want to operate a firewall/proxy on your server to enforce policy for your entire network (such as to forbid internet access to certain network applications, etc.) It is also, usually, a pain to set up.

The network topology described in your first post is [[that]("http://ubuntuforums.org/album.php?albumid=1938&pictureid=6499")]. The server is just another host in the subnet which is (since the second router is configured as pass-through) just one, and with one dhcp server (at the DSL router). For a home network with a simple file/print server this is an adequate network topology.

Now if your actual network is like the second case (which I believe it is, else your laptops could not access the Internet before you configured your server), then I believe the instructions I posted should work. 

If it is not, then you definitely need to provide the true setup of your network, else no-one here (or elsewhere) will be able to really help you. As a bare minimum, post the output of `sudo ifconfig' for your server and a couple of the clients, as well as the IP addresses of your two routers, as seen by the internal network.

---

### Post by netwidget on 2010-07-08
I the past 5 days as I have been trying to get an answer and a direction to my problem.  I have come across so many variations of server configurations, and different server applications.  I have looked at moving the server in front of the second router and using the server as the main router and setting up the Linksys as a nested LAN for wireless devices only.  All cabled would go through a switch.  

I have also since 5 days ago upgraded my DSL to a static address in the hopes that this would make things simper.  Also I want to use VPN or another remote access application to be able to access my home server remotely.

This has posed some new challenges for the DSL router which is not capable of completing a RFC-1483 Bridge to the second router (according to Qwest tech support). In any event I will for lack of any other alternative list the devices available to me and which will be part of the LAN, and list the desired functions of the LAN:

**Device 1**
Motorola Netopia 3347-2 DSL-modem/router (wireless g)
WAN is static ip address
Wan mask 255.255.255.255
Router IP 192.168.0.1
Network 192.168.0.0
netnask 255.255.255.0

**Device 2 **
Linksys WRT300N Wireless router
router default ip address 192.168.1.1

**Device 3**
Gigabit 8 port switch

**Device 4**
Server:
AMD64 Athlon X3 435
2GB RAM
3- 1TB SATA HDD in configured in RAID5 (1.9 TB logical space with 32GB swap)
RAID5 basic setup in CMOS software controlled by Ubuntu Server
eth0 (on-board Ethernet)
not other peripherals
OS Ubuntu Server 10.04 64amd

**Device 5,6,7**
Desktop computers
Pentium 4 2-@1.7Ghz, 1-@2.3GHz,
1GB RAM all
500 GB SATA HHD, DVD-RW
OS: Ubuntu Desktop 10.04 32BT i386

**Device 8**
HP Pavillion 9000 Laptop
Intel Celeron Duo 1.7GHz 
1GB RAM
120 SATA HDD
OS: Ubuntu Desktop 10.04 32BT i386

**Device 9**
Gateway Laptop
AMD Athlon 64BT
320GB SATA HDD, Partitioned for dual boot
OS 1: Ubuntu Desktop 10.04 64amd 
OS 2: Windows 7

**Device 10**
DELL Laptop
Pentium 4, 1.7GHZ
2GB RAM, 80 GB HDD
OS: Windows XP Professional

**Device 11**
Apple TV 
OS: Dual Boot with XBMC
Ethernet

**Device 12**
WII
Wireless

**Device 13**
Canon Imageclass MF5750
4:1 printer
no Ether USB only

**Device 14**
Canon MP250 coloer printer /scanner 
4:1 USB only

Plan for LAN
The server (Device 4)is planned to hold all of the shared files from all users on the LAN. Also it will be the main respository for the XBMC media center operated from Apple TV (device 11).  Printer (Device 13) will be connected to this server.  This server will also need to function as a LAMP server for Web development testing.

Device 14 smaller Canon printer will be connected to another desktop with print services activated to all users.

WII, Device 12 simply needs wireless internet access.

Future expansion of the system (or a parallel system) to include web server to host for small websites developed, maintained at home.  So how should I set up these devices with the given equipment given the uses and future plans of the system.  Frankly I have read so many different ways to do this that I'm just at a total stand still until someone can pose a solution that will make sense.

Thanks for the help.

---

### Post by gzarkadas on 2010-07-09
The best network configuration is the one that you can understand and easily manage. If you don't really understand what you are doing the chances to setup properly (ie securely) your network are small. I would thus suggest to abandon the ideas to partition your network in subnets and / or setup a DMZ and the like and simply:

1. Use your main router as firewall, wireless access point and dhcp server. Set aside the 2nd router; it only adds in complexity without any real benefit. Put all your computers in the same network.

2. Configure your server to have a static internal ip address within the (one) network range, as described in my previous posts.

3. Use the /etc/hosts file (windows machines have also a hosts file inside c:\system32\drivers\etc) in all client machines to avoid the need to setup a DNS server; it's hard to setup DNS right when you are a beginner.

4. Configure your router, server and hosts firewalls. It is not that hard because all hosts will have the same settings, so you basically need to define three sets of rules (router, server, host).

It is easy to later modify this setup to allow vpn connections from outside (just a new rule to your router firewall to tunnel requests to the server and a rule in the server to accept them) and in no way less secure than the alternatives (you have to, in any case, protect each host individually if you want to have a secure network; a firewall is never enough).

---

### Post by kendallp on 2010-07-09
I am sorry in advance for slightly hijacking this thread but I have been contemplating a similar scenario.

My home network is currently setup like this (my pictures aren't as good as gzarkadas):

[[Current Setup]]("http://ubuntuforums.org/picture.php?albumid=1939&pictureid=6501")

I use Arno's Firewall to handle the firewall and NAT, along with Samba for file sharing.  I am not using print sharing but probably should.  My clients are setup as static IP addys to keep from running DHCP on my linux box.


I am interested in moving to this:

[[Proposed Setup]]("http://ubuntuforums.org/picture.php?albumid=1939&pictureid=6502")

For the most part, this is so I can have wi-fi for my iPhone and also a wireless connection for my work laptop.  It would also give me the ability to move my HTC without worrying about cabling.

If I am currently working, are there problems I should expect if I was to add a Linksys WRT54GL ( [http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190) )?  

I am guessing I would have to config the router to act solely as a router and not also a gateway but otherwise it seems a fairly simple change.



Thanks in advance,
-Kendall


P.S. - To keep this from being a total hijack, if no one sees an issue with my proposal; Net you could switch to a static IP for your wireless router (you could still use its internal DHCP for the clients that connect to it) and then you could skip using DHCP/DNS on your server and let that all be handled via your ISP with the server only serving as a NAT.  

The NAT is easy to setup with many of the packaged firewalls.  As I said above, I personally use Arno's because it is easy to setup and seems to be well regarded.

---

### Post by gzarkadas on 2010-07-09
I don't see any problems; the linksys router has a rich configuration interface and the manual also looks comprehensive. In your server you will just have to consolidate the rules for the two "internal" NICs to one set, which is straightforward.

The point is -and this explains my previous post's theses- that today's routers are advanced (they usually are embedded linux systems with statefull firewall, nat, dhcp and all the like) and there is usually no point to add yet another piece in the chain by placing your server in between. You get a slower network throughput, added complexity because you have to setup (again) NAT and forwarding rules, less security actually -because you run unneeded services in your server (the nat/forwarding layer) and you are thus vulnerable to bugs in their code- and less cpu/IO/bandwidth available for your core services. 

IMO the server-in-the-middle  setup can only be justified if you run on your server an IDS such as snort or some other content-inspecting proxy, or software such as MoBlock and you want (in the later two cases) to enforce policy for your entire network. For simple networks with a simple file/print server it is not worth the effort.

---

### Post by QLee on 2010-07-09
[QUOTE=kendallp]
I am guessing I would have to config the router to act solely as a router and not also a gateway but otherwise it seems a fairly simple change.[/QUOTE]

Looking at your picture of what you want, it can be achieved easily. You want to configure that gateway (the linksys) to not do NAT or DHCP  (not a router) and just plug the LAN  output from your existing firewall into one of the hardwired ports of the linksys. That way you are just using it as an access point for the wireless, let your existing firewall manage NAT and DHCP for the LAN. 

[QUOTE=kendallp]P.S. - To keep this from being a total hijack, [/QUOTE]

Sorry dude, it is a hijack, look, now we are answering you not the OP.

---

### Post by gordintoronto on 2010-07-09
> **netwidget said:**
> Please help.

I am new to Linux, ubuntu, and I only know a little about networking.  I am very, very, very, frustrated with IP addressing, hostnames, file sharing, etc.

I trying to setup up a network in my house that has the following pieces to it.  File server, printer server, access to the internet...


What you want to do is MUCH simpler than you are making it. You don't need to worry about IP addressing, hostnames, etc. You do need to understand a little bit about file sharing and printer sharing. It's a lot easier than you think it is!

---

### Post by kendallp on 2010-07-09
> **QLee said:**
> Sorry dude, it is a hijack, look, now we are answering you not the OP.

Yup, busted.  Sorry netwidget.


Thanks for the responses gzarkadas and QLee.  Based on your post gzark, once I buy the wireless router I think I'll take your advice and stop routing everything through my linux box.


-Kendall

---

### Post by netwidget on 2010-07-17
Quote: gordontornto

> What you want to do is MUCH simpler than you are making it. You don't need to worry about IP addressing, hostnames, etc. You do need to understand a little bit about file sharing and printer sharing. It's a lot easier than you think it is!

Well I'm all ears.  I agree that in today's advanced applications things in Linux should be superior to Windows.  And maybe the term "easy" should be placed in context.  I have been working on computers for 25 years and I have been setting up computers on Windows for the last 15.  

In Windows you can "share a file on a networked computer", and "map a network drive" and to link to that shared file in 4 steps without ever opening a text editor.  While I may have the ability to do this in Linux (desktop, dont' know for sure), I do not have the Gnome GUI installed on the server so I am trying to set this up using command line and nano, or vi.

So I absolutely agree that it should be as easy and as straight forward as fixing a few things. However I am stuck in Linux jargon that I don't know, Networking terms that however universal they may be, are still fuzzy to me, and the lack of a GUI on my server.

So let me simplify my setup as much as possible. Forget the previous setup.  Here is the new simple set up for now until I understand NFS, etc: 
DSL modem/router is set to Static IP address on WAN side (from ISP). 
Network is 192.168.0.0, 
netmask is 255.255.255.0, 
Gateway is 192.168.0.1, 
Broadcast address is 192.168.0.255, 
DHCP range is 192.168.100-254, 
LAN server (name is servermain) has static ip of 192.168.0.2, 
desktop computer (desktop1) on LAN (cabled to router) has static IP address of 192.168.0.3
APPLE TV (cabled to router) will have static IP address if 192.168.0.4

Servermain (file server) is to be the central file server for clients on the LAN.  It needs to store user files for users using client computers, central media files for media system controlled by XBMC on Apple TV as a client to the server.  Media content to XBMC needs to be be able to be added by other client computers in LAN and recognized by Apple TV and all other client computers that have XBMC installed on them.

So please by all means if this is so easy than give me the simple step by step procedures to set up NFS and file sharing on the server and to configure it with the permissions and uses outlined above.  If this is not the right forum to get real help then please tell me where the "Ubuntu for absolute monkeys" is and I will be happy to join.](*,)

---

### Post by gzarkadas on 2010-07-17
I am packing my luggage for vacations write now, so I will not be able to follow in depth for some time, but I have a little time for some general remarks:

1. Don't use NFS on the server, use Samba (CIFS). Samba is supported by all of XBMC (see [http://wiki.xbmc.org/index.php?title=Types_of_Media_Sources#Generic_Network_Sources](http://wiki.xbmc.org/index.php?title=Types_of_Media_Sources#Generic_Network_Sources)), Windows (you said you have a couple of that OS clients) and also out of the box by Ubuntu (at least as a client - you just select the server from the network, or use an `smb://server-name/shared-folder' url in nautilus bar to use it).  

2. Thus, you only difficulty will be to configure Samba at the server, along with user information. Now this is something I have not yet done, because I use a ReadyNAS as my file server and it came pre-configured, but the Samba documentation is rich. See [http://www.samba.org/samba/docs/](http://www.samba.org/samba/docs/) and in particular [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/).

3. Regarding the users issue: 

3a. If you have a small number of distinct users in your network the best solution is to create them with standard unix tools (the adduser  command) in the server and assign permissions as usual (at the server) in the to-be-shared directories. Then on each client supply the credentials for the desired user when trying to connect to the server. Both Ubuntu and Windows offer the ability to permanent store them at the client side, so that they need not been entered more than once.

3b. If you have a large or a dynamic set of users, you should consider setting up an LDAP server also at your fileserver box. In that way you will effectively set up a domain with your server as Primary Domain Controller. This is definitely more work, and also something that I haven' t done yet so I can only point to the official LDAP documentation, Admin Guide: [http://www.openldap.org/doc/admin24/](http://www.openldap.org/doc/admin24/), and FAQ: [http://www.openldap.org/faq/data/cache/1.html](http://www.openldap.org/faq/data/cache/1.html). This thread: [thread]640760[/thread] will also be of help.

And finally, setting up a server has never been (under any OS) an easy thing; there are always some fine details to tackle and unanticipated dificulties. In your case (I know because we have more or less the same origins, as it shows out :)) it is a bit more difficult, because the decision -a very good one IMHO - to switch platform has put you back to the beginning. For a while you will get frustrated when things that used to be easy (the other way) are suddenly not. But this is a once-paid tax; once you learn the way to do it, it will become as easy and natural as it became some years ago when you were making the first steps on your old platform. So, be patient and exercise the read-test-verify loop; this has always been the way to succeed at the end.

---

### Post by QLee on 2010-07-17
[QUOTE=gzarkadas]...
And finally, setting up a server has never been (under any OS) an easy thing; there are always some fine details to tackle and unanticipated dificulties. In your case (I know because we have more or less the same origins, as it shows out :)) it is a bit more difficult, because the decision -a very good one IMHO - to switch platform has put you back to the beginning. For a while you will get frustrated when things that used to be easy (the other way) are suddenly not. But this is a once-paid tax; once you learn the way to do it, it will become as easy and natural as it became some years ago when you were making the first steps on your old platform. So, be patient and exercise the read-test-verify loop; this has always been the way to succeed at the end.[/QUOTE]

+1, I certainly agree with that.

@netwidget

Here are some links that may help you:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking)

---

### Post by netwidget on 2010-07-17
gzarkadas:  Thanks for the heads up about samba and XBMC I will look into it.

QLee:  Thank you for the links,  I am going there right now to check them out.

---

