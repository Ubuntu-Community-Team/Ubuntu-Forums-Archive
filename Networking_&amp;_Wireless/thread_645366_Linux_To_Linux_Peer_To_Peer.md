---
title: "Linux To Linux: Peer To Peer"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by jkgoose937 on 2007-12-20
PLEASE NOTE THIS IS A LINUX TO LINUX PEER TO PEER NETWORK SITUATION!!!!
NO DOMAIN! NO SERVER! NO MICROSOFT SOFTWARE!

What is the best way to network 2 Ubuntu Linux machines??? And how???

I am a Linux Newbie with 6 yrs of experience so please be gentle with the wordage!

---

### Post by peitschie on 2007-12-20
Hi!

At 6 years experience you may not be totally newbie anymore :)

So, one question... are the computers just networked to each other or are they going to be connected to the internet?

Assuming it is a purely peer-to-peer network (i.e., only two computers connected together), the best way is to connect them with a cat5 crossover cable (looks like a big phone plug at either end in case you're not familiar with it), and set up a static ip address on each machine.

For example, the settings on computer one would be:
IP Address: 192.168.0.1
Net mask: 255.255.255.0

and on computer two:
IP Address: 192.168.0.2
Net mask: 255.255.255.0

Then just plug the crossover cable in, and you should be able to ping the other computer by opening up a terminal and typing:
```
ping 192.168.0.1
``` or ```
ping 192.168.0.2
```

---

### Post by TheWizzard on 2007-12-20
please don't shout.

for a local network use NFS

---

### Post by jonallport on 2007-12-20
There are some cool tools in the repositories for no-infrastructure networking. 

Google 'zeroconf' for more info or search in synaptic for 'zeroconf' and you'll find stuff like DNS multicast responders - oooo it makes me tingle all over!

P.S. that was sarcastic, I don't really derive physical pleasure from networking tools!!!!!

---

### Post by jkgoose937 on 2007-12-23
Ok I have a router that is connect to the internet suppleing my internet connection.

I tryed using SAMBA with Ubuntu but I keep getting firewall error messages (even when no firewall is installed), but that didn't work.

By default Ubuntu doesn't come with NFS server/client installed or a gui configure simple setup thingy and I don't want to mount IP addresses incase the IP addresses change. Thus back to Samba, which doesn't work because of the a firewall error message, even when no firewall is installed.

Is there a simple Linux to Linux file sharing system that is brain dead easy to use like MS has???

---

### Post by peitschie on 2007-12-23
> **jkgoose937 said:**
> Is there a simple Linux to Linux file sharing system that is brain dead easy to use like MS has???

Short answer:  not yet.  However, if you are willing to work for it a little bit then we can help guide you to a working system...

> **jkgoose937 said:**
> Ok I have a router that is connect to the internet suppleing my internet connection.

Okay, so am I correct in assuming BOTH computers plug into this router?  Can you mention the router type and model (e.g., Netgear WG311 or something.  It will be written on the outside of the box you got it in)?  This will help us ensure the router can do DHCP (i.e., automatically assign the IP addresses for the computer).

> **jkgoose937 said:**
> I tryed using SAMBA with Ubuntu but I keep getting firewall error messages (even when no firewall is installed)

Can you give more details about this problem?  I don't quite understand "firewall error messages"...  Whats the exact text you are seeing?  Do you know which program it is?  Does the issue occur on both computers?

> **jkgoose937 said:**
> By default Ubuntu doesn't come with NFS server/client installed or a gui configure simple setup thingy and I don't want to mount IP addresses incase the IP addresses change.

Fair enough.  I have the same concern at home :).  It is possible to make a working system, and not toooo difficult once you've had a little experience at it :)

So, the questions we need answered:
[LIST]
[*]Do both computers connect to the router?  What router type etc.?
[*]More information abou the "firewall error" please... like what was the exact text/program etc. that was complaining
[/LIST]

Cheers. <and almost merry christmas!>

---

### Post by theozzlives on 2007-12-31
> **jkgoose937 said:**
> Ok I have a router that is connect to the internet suppleing my internet connection.

I tryed using SAMBA with Ubuntu but I keep getting firewall error messages (even when no firewall is installed), but that didn't work.

By default Ubuntu doesn't come with NFS server/client installed or a gui configure simple setup thingy and I don't want to mount IP addresses incase the IP addresses change. Thus back to Samba, which doesn't work because of the a firewall error message, even when no firewall is installed.

Is there a simple Linux to Linux file sharing system that is brain dead easy to use like MS has???


I get the same message, Im using a Linksys Wireless Cable Gateway router but all of my connections are wired (I can have 4). Ubuntu & Kubuntu connect to my Windows XP box fine but I can't get them to connect to each other. Should I disable my router's Firewall or what?

---

### Post by peitschie on 2008-01-01
> **theozzlives said:**
> I get the same message, Im using a Linksys Wireless Cable Gateway router but all of my connections are wired (I can have 4). Ubuntu & Kubuntu connect to my Windows XP box fine but I can't get them to connect to each other. Should I disable my router's Firewall or what?

The router's firewall only affects traffic from the internet INTO the network, not between different computers on the internal network.  Can you ping the linux computers BY IP address?  (Let me know if you don't know how to find this btw :))

---

### Post by HermanAB on 2008-01-01
Use NFS, it is the most brain dead simple networking system available.  Configuration consists of about 3 lines in two text files: /etc/exports and /etc/fstab

A little bit of Googling and man page reading will get you going.  There is nothing simpler than this.

Cheers,

Herman

---

### Post by theozzlives on 2008-01-01
> **peitschie said:**
> The router's firewall only affects traffic from the internet INTO the network, not between different computers on the internal network.  Can you ping the linux computers BY IP address?  (Let me know if you don't know how to find this btw :))

no I can't ping the computer

---

### Post by wagoner on 2008-01-01
Does samba work between two linux computers?

I am working on an identical problem at the moment.  2 linux pc's both wired to a linksys router that connects to the internet.   One of the pc's dual boots Kubuntu 7.10 and Vista.  Occasionally someone brings a windows laptop over and plugs that in as well and I would like to be able to network and share files with all of these computers.  I haven't looked into nfs or zeroconf yet, but I guess I need to research all 3 of these and figure this out.  Can someone give me a recommendation?

After fumbling through the kde menus for awhile I was thinking I need to setup lisa.  What is that?  Do I need it?

I was able to ping, as above.  Router is linksys model RT31P2.

---

### Post by TheWizzard on 2008-01-01
> **wagoner said:**
> Does samba work between two linux computers?

yes

---

### Post by peitschie on 2008-01-01
Some links from the community wiki's which may be helpful:

How to set up samba:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Setting up NFS network shares (this is different from samba):
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

With the samba one, it is important to note the basic steps are: 
[LIST=1]
[*]install samba
[*]add a samba user (smbpasswd -h to see help messages)
[*]add a samba share (need to edit the /etc/samba/smb.conf file)
[*]restart the samba service (sudo /etc/init.d/samba restart)
[/LIST]

This will then allow you to connect to the computer from a windows XP computer using the newly added username/password combination.

---

### Post by jkgoose937 on 2008-01-11
The firewall message I get is:

Unable to find any workgroups in your local network. This might be caused by an enabled firewall.

Unless, by default, Ubuntu, enables a firewall without me knowing it, I am not able to browse my network with Samba.

---

### Post by peitschie on 2008-01-11
Ahh... that sounds like Windows being a pain :).  I get that often between just windows computers!  I do not know what causes this or makes it go away, I don't believe it is Ubuntu's fault however.

Still, some things to try:
[LIST=1]
[*]Make both the windows and ubuntu computer part of the same workgroup.  In Windows, this is changed by right-clicking on My Computer->Properties->Computer Name.  On Ubuntu you can change this by running 'gksu gedit /etc/samba/smb.conf' and changing the value of the "workgroup = " line.  Set both computers to the same workgroup
[*]Attempt to connect from the Windows computer straight to the Ubuntu computer by name.  Do this by opening up an explorer window, and typing in "\\computername" (without the "'s)
[*]Attempt to ping the ubuntu computer by IP address and see if you get a response.  You can do this by opening a dos prompt in Windows, and typing in "ping ubuntucomputerip" (without the "'s again).
[*]Attempt to ping the ubuntu computer by NAME not IP address and see if you get a response.  You can do this by opening a dos prompt in Windows, and typing in "ping computername" (without the "'s again)
[/LIST]

Have you tried connecting from Ubuntu to the Windows computer...?  If you need help on any (or all) of these steps, let me know and I'm happy to post more detailed instructions :)

---

