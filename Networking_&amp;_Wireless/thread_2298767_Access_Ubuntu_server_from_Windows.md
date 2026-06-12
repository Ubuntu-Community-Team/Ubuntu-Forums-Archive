---
title: "Access Ubuntu server from Windows?"
date: 2015-10-13
forum: Networking &amp; Wireless
---

### Post by ash_law on 2015-10-13
Hi Ubuntu Gurus,

Having been a windows techie for years and having only dabbled with  unix/linux the last couple of weeks have been a massive learning curve. I  appreciate that there is a huge amount of information about ubuntu  server on forums such as these and various other sites also but for some  reason I am unable to connect the windows box to the ubuntu server.

I have gone through [https://help.ubuntu.com/community/In...nectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")  and set it up as per with a few changes in the ip addresses for my  system but although I can see the server from the windows box I still  cannot connect to the internet.

I have now re-installed ubuntu server - installed via dos dhcp server -  installed desktop - uninstalled network manager as I intend to setup the  network via iptables and have installed webmin.

I have also previously gone through the webmin setup that internet shares but to no avail.

I know both the nics in the server work as do both the nics in the windows box (although only one is used).

I am running BT Infinty - although this should not cause a problem.

(previously I have had untangle and suse linux enterprise server setup  and running perfectly as a server (file server, gateway, etc) without  issue)).

Any ideas anyone?

---

### Post by TheFu on 2015-10-13
How do you want to connect to Linux from Windows? 
Which protocols? 
Did you install those services?  
Did you open the firewall ports for each service?

Can the systems ping each other by IP and by name?  Linux uses IP networking which doesn't use a broadcast "here I am" method like Windows.

---

### Post by joe.koenig on 2015-10-14
> **TheFu said:**
>  which doesn't use a broadcast "here I am" method like Windows.

  Could you please elaborate?  What other methods of broadcast are there that are unique to the Windows operating system?  I'm blissfully ignorant to none.

 @OP: Really?  That's all all the info you're willing to provide?  In a networking matter, nonetheless?

---

### Post by ash_law on 2015-10-14
hi TheFu,

I have been going around in circles for days with this.

I have several issues from the start:

1. On setup ETH0 (outside world to server) is set to DHCP; when I change the router to use a static ip and do the same with ETH0 - I get no internet connection; change back to DHCP and it works again;

2. When I set up ETH0 to "share to other computers" - then I have no internet connection for the server (is there more to this?, such as setting up an ad-hoc network i.e. as per wireless connection);

3. The suggested way to connect is windows to ubuntu is SSH/VNC/Putty? - SSH is installed on the server.

4. The server needs to act as a gateway for the windows 10 box and as a secure fileserver / backup for windows 10.

regards

> **TheFu said:**
> How do you want to connect to Linux from Windows? 
Which protocols? 
Did you install those services?  
Did you open the firewall ports for each service?

Can the systems ping each other by IP and by name?  Linux uses IP networking which doesn't use a broadcast "here I am" method like Windows.

---

### Post by michi1983 on 2015-10-14
> **ash_law said:**
> 
1. On setup ETH0 (outside world to server) is set to DHCP; when I change the router to use a static ip and do the same with ETH0 - I get no internet connection; change back to DHCP and it works again;

You seem to mix here some expressions up.
Lets clarify this a little bit.
You have 2 NICs on your Ubuntu Server, right?
Can you please post the output of ```
ifconfig -a
``` and ```
cat /etc/network/interfaces
``` from your server.
Your ISP provided you with a router/modem which connects to the internet and from this router you connect to ONE of your 2 NICs of your server, right?
What do you do with the 2nd NIC of your server? Will you create a LAN for your clients there?

> **ash_law said:**
> 
2. When I set up ETH0 to "share to other computers" - then I have no internet connection for the server (is there more to this?, such as setting up an ad-hoc network i.e. as per wireless connection);

Where do you make these settings? Where can you tell eth0 to "share to other computers"?

> **ash_law said:**
> 
3. The suggested way to connect is windows to ubuntu is SSH/VNC/Putty? - SSH is installed on the server.

SSH etc. are just examples how to access a server. But to configure a server it is very common to use a SSH connection that you don't have to sit in front of the server the whole time.
But therefore the 2 NICs of the server need to be configured correctly.
And then there is the iptables firewall which needs to be configured correctly if you have 2 NICs and your server should act like a gateway for the clients.

> **ash_law said:**
> 
4. The server needs to act as a gateway for the windows 10 box and as a secure fileserver / backup for windows 10.

Important things first... see above ;-)

Regards

---

### Post by TheFu on 2015-10-14
There must be 2 NICs for a Linux machine to act as a router/gateway if there is any hope of being secure.
Sounds like eth0 is your "red" network - connected to the internet.
eth1 would be connected to the "green" side - connected to the LAN - normally a switch that connects to other systems.

There are lots of details to make this into a network gateway. For most people, it is much easier AND more secure to use a router distro rather than rolling your own.

Personally, I wouldn't have any storage anywhere near a network gateway. On the commercial routers which have storage, there have been a number of security flaws that allowed the storage to be accessed by internet connections.

Linux/Unix is very different from Windows. About 20% is similar, though 80% seems similar until you look under the covers.

@joe - if you have issues, please create your own thread. Don't want to mix information.

---

### Post by bab1 on 2015-10-14
> **TheFu said:**
> ...

@joe - if you have issues, please create your own thread. Don't want to mix information.

You made a statement that at best is murky>  Linux uses IP networking which doesn't use a broadcast "here I am" method like Windows. 

@ joe.koenig is asking for clarification on that point.  Both Windows and Linux use (and have always used) IP addressing for *networking* connectivity.  In fact, TCO/IP connectivity does use IP broadcasts.  So what do you mean by what you have said?  Try and be a little more precise and document the statement when you are making a statement like that.

---

### Post by TheFu on 2015-10-14
This is about system to system discovery. Linux doesn't "automatically" find other Linux systems on a subnet where we can just wait a few minutes and a list of other systems show up. At least I've never seen that work. Either /etc/hosts or DNS is needed to use names instead of IPs.

Windows Network Discovery: [http://windows.microsoft.com/en-us/windows/what-is-network-discovery#1TC=windows-7](http://windows.microsoft.com/en-us/windows/what-is-network-discovery#1TC=windows-7)  - not sure how this helps the OP.

---

### Post by ash_law on 2015-10-14
Hi,

I have completed a fresh install of Ubuntu Server today - installed updates, dhcp server and then desktop.

ifconfig -a:

eth0 is the primary NIC (outside world to Server)
eth1 is secondary NIC (server to Windows box)

```
eth0      Link encap:Ethernet  HWaddr 00:40:f4:59:3b:4d  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe59:3b4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1685753 (1.6 MB)  TX bytes:100130 (100.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:19:66:0b:d5:2c  
          inet6 addr: fe80::219:66ff:fe0b:d52c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:201970 (201.9 KB)  TX bytes:7195 (7.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81819 (81.8 KB)  TX bytes:81819 (81.8 KB)
```

cat /etc/network/interfaces

```
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

The router has been set to use a static IP which the server is on.

There is a ubutu forum post that relates to sharing a connection and according to that post you go into network manager and set eth0 to share with other computers.

regards,

---

### Post by bab1 on 2015-10-14
> **TheFu said:**
> This is about system to system discovery. Linux doesn't "automatically" find other Linux systems on a subnet where we can just wait a few minutes and a list of other systems show up. At least I've never seen that work. Either /etc/hosts or DNS is needed to use names instead of IPs.
This is not the point that @ joe.koenig is talking about.  To be blunt,  your statement of...> IP networking which doesn't use a broadcast "here I am" method like Windows. ...seems to be in misspoken.  A newbie would not know that however.> 

Windows Network Discovery: [http://windows.microsoft.com/en-us/windows/what-is-network-discovery#1TC=windows-7](http://windows.microsoft.com/en-us/windows/what-is-network-discovery#1TC=windows-7)  - not sure how this helps the OP.
Actually none of it relates to your statement that implies that Windows does not use TCP/IP.

NetBIOS (NBT) does use IP networking as much as any other Linux application that needs network connectivity.  I feel that if you are going to talk about various applications that work with IP addressing you should be more to the point.  NBT uses TCP but does not replace it.  The link you provided does not explain TCP/IP or NetBIOs over TCP (NBT).  

My quibble is with your "sorta, close to, almost like" descriptions without really either explaining or giving precise instructions (assistance) to the OP or the poster that asks you to explain what you mean in your statement, that appears on the surface to be erroneous.

---

### Post by TheFu on 2015-10-14
Who said that Windows doesn't use IP?  I didn't. I said that name resolution for Windows is different than for Linux systems. This is common point of confusion from people new to Unix networking. They expect to see a list of all the systems on the network, but it doesn't work that way. At least that was what I was trying to say. Sorry if it wasn't clear.

The OP didn't ask and I felt that the explanation would take this thread way off-topic for what the current replies showed was needed. Judgment call. It could have become an unnecessary rabbit hole about DNS, mDNS, zeroconf, dnsmasq, /etc/hosts ... plus  that was  yesterday and I've slept since then. Don't  recall what other tasks were taking my attention at the time.

Until about 60 min ago, we didn't know the system had 2 NICs. I'm still unclear how the network fits together.  Is there a separate router or is that THIS system?  Why doesn't eth1 have an IP and subnet assigned? We don't know. Lots of questions and a few answers so far. I can see 3 different network setups with the information provided/suspected at this point.

As is common, we don't know what level of knowledge the other people in the thread have either. I want to tailor the response for the OP's knowledge level.

We are mostly volunteers here after all.

Ok  -  seems we've been sidetracked since post #4 and post #9 reset everything to zero.

Is there a router device on this network?
Is eth0 connected to it or to some WAN modem/bridge?
How is eth1 connected to the windows machine? Through a switch?
A list of LAN IPs for the Linux  and Windows machines would clarify much. Please.
Gateway can mean many things. Can you please be more specific?  Is this a pure network gateway/router or is it a proxy server for web traffic and other specific protocols?
ssh is  the common way that Unix systems communicate - ssh provides scp, sftp too. There are 50 other commonly used protocols. Some can be proxied easily. I don't know whether every protocol needed from Windows is easily proxied or not. From Windows, putty is the normal ssh client.

---

### Post by bab1 on 2015-10-14
> **TheFu said:**
> Who said that Windows doesn't use IP?  I didn't. 

Sure you did.  Reread your own statement.
> 
I said that name resolution for Windows is different than for Linux systems. 

You didn't quite say that either.  Windows since Win95 used both DNS and NetBIOS for name resolution.
> 
This is common point of confusion from people new to Unix networking. They expect to see a list of all the systems on the network, but it doesn't work that way. At least that was what I was trying to say. Sorry if it wasn't clear.

Reread the OP's posts.  It is a TCP/IP problem.
> 
The OP didn't ask and I felt that the explanation would take this thread way off-topic for what the current replies showed was needed. Judgment call. It could have become an unnecessary rabbit hole about DNS, mDNS, zeroconf, dnsmasq, /etc/hosts ... plus  that was  yesterday and I've slept since then. Don't  recall what other tasks were taking my attention at the time.
You don't need to make it so complicated.  It really is not a name service issue at all.> 
Until about 60 min ago, we didn't know the system had 2 NICs. 
[QUOTE]Look at post #4.  That was long before just an hour agin.
I'm still unclear how the network fits together.  Is there a separate router or is that THIS system?  Why doesn't eth1 have an IP and subnet assigned? We don't know. Lots of questions and a few answers so far. I can see 3 different network setups with the information provided/suspected at this point.
[/QUOTE]I know.  The OP was finally directly asked about the network topology.> 

As is common, we don't know what level of knowledge the other people in the thread have either. I want to tailor the response for the OP's knowledge level.
So ask, don't just spew opinions.> 

We are mostly volunteers here after all.


Ok  -  seems we've been sidetracked since post #4 and post #9 reset everything to zero.

Uh huh.

---

### Post by QIII on 2015-10-14
There has been quite enough of wetting on each other's shoes now.

Back on task.  Let's get OP squared away.

---

### Post by ash_law on 2015-10-15
Hi,

System Config:

```
BT Infinity router located in lounge (I work from home);
BT Powerline adapter connected from router to office;
RJ45 connection into Ubuntu Server with 2 x NICs;
ETH0 NIC (Internet to Server);
Secondary NIC (ETH1) via RJ45 from Server to Windows Box.
```

```
Latest version of OpenSSH installed on Windows Box.

```

Previously when Suse was installed this configuration worked perfectly - however SSH was not required on the Windows Box (saying that though the Windows Box was running Windows 7 and not Windows 10).

regards,

---

### Post by ash_law on 2015-10-15
I understand that I am a newbie to Ubuntu forums but it seems to me that there is a lot of in-fighting and disagreements as to what works and what does not.

There are 4 useful posts out of 14 on this thread (and 2 are mine) and I am no closer to even getting the server / windows box sorted.

I know from past history that there is a "love/hate" relationship with unix/linux and windows - there will probably always be - but for practical reasons I require a windows box for business and a secure linux server for everything else.

Us windows techies have always admired the linux forums as the "gurus" on these forums know their stuff. However at the moment I am unimpressed.


Rant over!

---

### Post by bab1 on 2015-10-15
> **ash_law said:**
> I understand that I am a newbie to Ubuntu forums but it seems to me that there is a lot of in-fighting and disagreements as to what works and what does not.

There are 4 useful posts out of 14 on this thread (and 2 are mine) and I am no closer to even getting the server / windows box sorted.


I know from past history that there is a "love/hate" relationship with unix/linux and windows - there will probably always be - but for practical reasons I require a windows box for business and a secure linux server for everything else.

Us windows techies have always admired the linux forums as the "gurus" on these forums know their stuff. However at the moment I am unimpressed.

Rant over!
It's not because you are a newbie that you haven't moved forward with your network problems.  The your needs (as expressed by you) are not very clear.  All of the 14 posts are useful and are related related to your situation; even if not directly.  

Since you have reinstalled the Ubuntu OS you will have to start over.

Are you trying to place the Windows host in a separate secure network with the Ubuntu host serving as that network's router/firewall/NAS?  By your previous posts it sure seems like it.  If so I would configure the Ubuntu host for IP connectivity to the router first.  Then deal with the Windows to Ubuntu connectivity.  Most folks use a static IP address (configured on the Ubuntu host) for the WAN side (e.g. connected to the ISP's modemrouter).  Then you can configure the LAN side NIC for the Windows IP connectivity.

If this is what you want to do, post the output of these commands```

ifconfig -a

cat /etc/network/interfaces

cat /etc/resolv.conf

cat /etc/hosts 

cat /etc/hostname

```
What is the IP network range for the ISP NAT'd side?  Something like 192.168.1.0 /24.   With a subnet mask of 255.255.255.0.  What IP address range do you want to use for the Windows side?  Maybe something like 10.0.1.0 /24?

Out of curiosity; have you installed a DE for the Ubuntu host yet?  If this host is going to be a router/firewall/NAS you really don't need a DE.  If you want the convenience of  having a file manager and a graphical text editor (i.e. gedit or some such), you can install the minimal file manager and X-server bits.  I would not install the full DE for what you have proposed.

---

### Post by ash_law on 2015-10-15
It is possible that what I think is clear and precise is probably not.

When the company was in its infancy (while I was developing our products and pre-server requirements) we were hacked. It was a windows 7 PC which was secure (but actually not secure enough)

From that point onwards, I built a server and installed and configured suse linux enterprise server. I got shot of suse as it became too expensive to run.

suse was pretty straightforward to set up - the manual that I ordered from the USA made that job easy.

Fast forward to now:

I have reinstalled ubuntu server - in this order - installed updates; dhcp server; clamtk; gufw; desktop; webmin.


The server at the moment is connected to the internet via dhcp - with a reserved ip static ip address assigned to the BT router for it; everytime I assign a static ip to eth0 (BT router to server) i get no internet. I have asked this question but no answer is forthcoming as to a solution and the help pages re: ubuntu seem to suggest that this should not happen.

What I am trying to do is assign eth0 to a xxx.xxx.1.xxx ip and eth1 (server (gateway) to windows box) on xxx.xxx.2.xxx ip; so in answer to your question: "*Are you trying to place the Windows host in a separate secure network  with the Ubuntu host serving as that network's router/firewall/NAS?*" - Yes I am.

I understand the use of static IP's; I also understand that windows 10 seems to be unlike any other windows OS in that connectivity has led me to install the latest version of openssh onto windows 10.

---

### Post by bab1 on 2015-10-15
> **ash_law said:**
> It is possible that what I think is clear and precise is probably not.

When the company was in its infancy (while I was developing our products and pre-server requirements) we were hacked. It was a windows 7 PC which was secure (but actually not secure enough)

From that point onwards, I built a server and installed and configured suse linux enterprise server. I got shot of suse as it became too expensive to run.

suse was pretty straightforward to set up - the manual that I ordered from the USA made that job easy.

Fast forward to now:

I have reinstalled ubuntu server - in this order - installed updates; dhcp server; clamtk; gufw; desktop; webmin.


The server at the moment is connected to the internet via dhcp - with a reserved ip static ip address assigned to the BT router for it; everytime I assign a static ip to eth0 (BT router to server) i get no internet. I have asked this question but no answer is forthcoming as to a solution and the help pages re: ubuntu seem to suggest that this should not happen.

What I am trying to do is assign eth0 to a xxx.xxx.1.xxx ip and eth1 (server (gateway) to windows box) on xxx.xxx.2.xxx ip; so in answer to your question: "*Are you trying to place the Windows host in a separate secure network  with the Ubuntu host serving as that network's router/firewall/NAS?*" - Yes I am.

I understand the use of static IP's; I also understand that windows 10 seems to be unlike any other windows OS in that connectivity has led me to install the latest version of openssh onto windows 10.
We are not going to move forward unless you provide the information I asked for.  From the Ubuntu hosts viewpoint you only need to concentrate on the IP connectivity.  To tell me "everytime I assign a static ip to eth0 (BT router to server) i get no internet"  is nice but it isn't really the whole picture.  ***What did do to configure the interface?  What were the steps and what was the actual configuration?***

How about the other information.

There is no need to obscure the IP addresses.  The addresses are used only on the inside of a LAN.  They are used by millions of uses for their own networks.

In the end you will need to configure each interface and turn on packet forwarding on the Ubuntu host so that the Windows side data will be sent to and from the Internet.

OpenSSH is nice but not really needed.  You can use PuTTY or ICMP ping to check continuity. If you want to use SSH you need to have OpenSSH-server installed on Ubuntu also.  I have not heard of any Win10 changes that would cause any IP traffic problems.

---

