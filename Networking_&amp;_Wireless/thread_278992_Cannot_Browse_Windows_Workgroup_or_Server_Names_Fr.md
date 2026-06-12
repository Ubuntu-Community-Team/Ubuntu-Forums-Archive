---
title: "Cannot Browse Windows Workgroup or Server Names From Nautilus"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by mac_an_ultaigh on 2006-10-17
I can access Ubuntu from Windows Explorer but can't access Windows workgroup or servers from Ubuntu Nautilus without using IP addresses.

Network comprises:
- D-Link Wireless Modem Router
- box1 - Laptop running Ubuntu + Samba with wireless connection
- box2 - Desktop running Win XP Pro with wireless connection
- box3 - Desktop with Win 2000 with wired ethernet connection to router
- box4 - Laptop running Win XP Home with wireless connection

All interfaces configured to obtain IP and DNS server addresses automatically.

On Ubuntu box, 'General Windows sharing settings' of shared folders are set to 'Do not use WINS server'

From Windows boxes, My Network Places -> Entire Network -> Microsoft Windows Network -> Mshome shows all boxes and full access to all shares.

From Ubuntu box, Places -> Network Servers -> Windows Network -> mshome returns:

The folder contents could not be displayed.
Sorry, couldn't display all the contents of 'Windows Network: mshome

Typing the IP address of each machine in Nautilus toolbar using smb://192.168.1.x works with absolutely no problem.

Typing the server/machine name of the Ubuntu box smb://box1 works fine too.

But typing the names of the Windows boxes smb://box2 etc. returns the could not be displayed message.

My grasp of networking is not great, but, as far as I understand it, this suggests that the DNS on the Ubuntu box is failing to resolve the server names. Is this correct? If so, how do I fix it?

I've read as much of the Samba HowTos, CheckLists, Fault Trees and Troubleshooting Guides as I can digest and tried as many variations in smb.conf as I can think of, but so far no luck.

I've browsed the forums and know this issue has been raised several times before, but so-far haven't been able to find a solution.

Any guidance would be much appreciated.

---

### Post by tompicking on 2006-10-27
I have the same problem. Typing the name of the computers on my network works a treat. However, I am unable to browse any of the networks under "Windows Network" (aka smb:///).

I use Edgy, but I had the problem in Dapper. Was hoping the update would fix problem.:-k

---

### Post by dbott67 on 2006-10-27
Have you installed samba and smbfs?
```
sudo apt-get install samba smbfs
```

---

### Post by dbott67 on 2006-10-27
Also try this thread:
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by mac_an_ultaigh on 2006-10-30
> **dbott67 said:**
> Also try this thread:
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)OK. So LinNeighborhood description says it is "a browser for SMB (Microsoft Windows) networks. It allows you to browse the available SMB shares and mount/unmount them via the smbfs filesystem, similarly to Network Neighborhood on Microsoft platforms."

Does that mean that Nautilus can't browse Windows networks and we have to use LinNeighborhood instead?

If so, how? Help only contains About... No other help at all!

I've installed and run LinNeighborhood but it only shows the machine/server name of the Linux box it's running on. No Windows boxes!

I've tried Options -> Browse entire network but nothing happens!

What do I do next?

---

### Post by dbott67 on 2006-10-30
> **mac_an_ultaigh said:**
> OK. So LinNeighborhood description says it is "a browser for SMB (Microsoft Windows) networks. It allows you to browse the available SMB network browser for Linux and X11."

Does that mean that Nautilus can't browse Windows networks and we have to use LinNeighborhood instead?


No... you can use Nautilus (verify that you have 'libgnomevfs2-extra' installed) or LinNeighborhood or the command line:```
dbott@thedrake:~$ smbtree
Password:
MSHOME
        \\THEDRAKE                      thedrake server (Samba, Ubuntu)
                \\THEDRAKE\print$               Printer Drivers
                \\THEDRAKE\dbott-P4
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
        \\DAPPER                        dapper server (Samba, Ubuntu)
                \\DAPPER\print$                 Printer Drivers
                \\DAPPER\ndis
                \\DAPPER\IPC$                   IPC Service (dapper server (Samba, Ubuntu))
                \\DAPPER\ADMIN$                 IPC Service (dapper server (Samba, Ubuntu))

```

> What do I do next?

1. Make sure all computers have the same WORKGROUP name.

2. Windows uses WINS service to allow users to browse by computer name (also known in Windows-speak as Netbios name).  WINS binds the computer name to the IP address.  For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address.  The problem is that DNS resolution requires that:

a) You're running a DNS server
b) Each client is registered in the DNS server

The problem here is that most people don't run their own DNS server and if you have any Windows computers on the network, you really should have a WINS server or 'winbind' installed.

There is a package in the repositories called 'winbind' that will allow you to browse by computer name.

This info is provided by 'featherking' from [this thread]("http://www.ubuntuforums.org/showthread.php?t=288022"): 

```
sudo gedit /etc/nsswitch.conf
```

find this line (it may not be exactly that)

```
hosts:          files dns mdns
```

and add wins, so now it looks like

```
hosts:          files dns mdns wins
```

then install winbind
```

sudo apt-get install winbind
```

Now trying pinging XP-COMP (or whatever your xp box's name is), All that should allow you to ping a windows machine name by installing the Windows Internet Naming Service (WINS), perhaps that will solve your workgroup issue because now you can see their names?

-Dave

---

### Post by mac_an_ultaigh on 2006-11-05
Hi Dave,

Thanks for your time and advice. Apologies for the delay in replying. Working Windows all week :( so only have time to play with Ubuntu at weekends.  > **dbott67 said:**
> No... you can use Nautilus (verify that you have 'libgnomevfs2-extra' installed) or LinNeighborhood Sure do :)
> **dbott67 said:**
>  ```
dbott@thedrake:~$ smbtree
Password: 
``` Tried that. This is what I get:
```
MSHOME
    \\WINDOWS_BOX_NAME
timeout connecting to 82.101.8.47:445
timeout connecting to 82.101.8.47:139
Error connecting to 82.101.8.47 (Operation already in progress)
cli_start_connection: failed to connect to WINDOWSBOX<20> (80.101.8.47)
    \\UBUNTU_BOX_NAME
        \\(shows all shares as in your example)
``` Have no idea why it's looking for 82.101.8.47 Tried pinging it, but it ain't there :-?
> **dbott67 said:**
> 1. Make sure all computers have the same WORKGROUP name. Done.> **dbott67 said:**
>  WINS binds the computer name to the IP address.  For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address...

The problem here is that most people don't run their own DNS server and if you have any Windows computers on the network, you really should have a WINS server or 'winbind' installed. I don't understand. My understanding was - as you say - that WINS had been superceded by DNS. We have a router. From the Windows boxes I can ping the machine/server names of both Windows and Ubuntu boxes no problem. None of our boxes have WINS installed. Doesn't that mean there's a DNS server working somewhere?> **dbott67 said:**
> There is a package in the repositories called 'winbind' that will allow you to browse by computer name.

This info is provided by 'featherking' from [this thread]("http://www.ubuntuforums.org/showthread.php?t=288022"): ........

Now trying pinging XP-COMP (or whatever your xp box's name is) Done that. No difference. ping WINDOWS_BOX_NAME doesn't work. As a n00b this is all new territory. There's a limit as to how many threads I can follow without completely losing the plot.  > **dbott67 said:**
>  All that should allow you to ping a windows machine name by installing the Windows Internet Naming Service (WINS) OK. So I could try installing WINS on all the Windows boxes. But the question is: why should this be necessary?

All Windows boxes network no probs without it. With Samba, libgnomevfs2-extra, LinNeighborhood and winbind all installed on the Ubuntu box, why is it necessary to load the Windows machines with outdated technology so Ubuntu can communicate with them? It all seems a bit archaic to me. If Ubuntu wants to be useable straight out of the box, then this would seem to be one glaring omission where there is considerable room for improvement :-k

Ian

---

### Post by nickmcg on 2006-11-05
I run a mixed network and all I have needed to do is add samba and winbind (either sudo apt-get install or synaptic - both work equally well), and modifying the file /etc/nsswitch.conf, changing the hosts line to include 'wins'
e.g hosts: files wins dns
and edit  /etc/samba/smb.conf to change the 'workgroup = MSHOME' to the name of my Windows network.

This will allow you to browse the network from Nautilus. I didn't have to make any changes to the windows machines.
The only other wrinkle is setting the samba permissions for accessing Ubuntu shares from Windows (I haven't bothered).

My understanding of wins is that windows stations will 'elect' the wins server on the network, so that the users in a home network don't need to worry. As far as I know, wins is is link between netbios and dns name resolution.

At this point, I'll stop before I demonstrate that I really don't know what I'm on about!

HTH

Nick

---

### Post by mac_an_ultaigh on 2006-11-05
Thanks Nick. > **nickmcg said:**
> I run a mixed network and all I have needed to do is add samba and winbind (either sudo apt-get install or synaptic - both work equally well), and modifying the file /etc/nsswitch.conf, changing the hosts line to include 'wins'
e.g hosts: files wins dns
and edit  /etc/samba/smb.conf to change the 'workgroup = MSHOME' to the name of my Windows network. Been there. Done that. Still haven't managed to get the T-shirt :roll: > **nickmcg said:**
>  
The only other wrinkle is setting the samba permissions for accessing Ubuntu shares from Windows (I haven't bothered). No problem there. I've been able to browse Ubuntu shares from Windows since the start. > **nickmcg said:**
>  HTH Every little bit does :)

---

### Post by dbott67 on 2006-11-05
> **mac_an_ultaigh said:**
> Hi Dave,

Thanks for your time and advice. Apologies for the delay in replying. Working Windows all week :( so only have time to play with Ubuntu at weekends.   Sure do :)
 Tried that. This is what I get:
```
MSHOME
    \\WINDOWS_BOX_NAME
timeout connecting to 82.101.8.47:445
timeout connecting to 82.101.8.47:139
Error connecting to 82.101.8.47 (Operation already in progress)
cli_start_connection: failed to connect to WINDOWSBOX<20> (80.101.8.47)
    \\UBUNTU_BOX_NAME
        \\(shows all shares as in your example)
``` 
Have no idea why it's looking for 82.101.8.47 Tried pinging it, but it ain't there :-?
A few things look odd to me.  You mention that you're behind a firewall/router, yet your IP addresses are all 'valid' (i.e. not in the non-routable, private range - 192.168.x.y or 10.x.y.z).  This could be the root of all of the problems.  If you could post a little diagram with the network layout (names & IPs of all devices) that would be helpful.  IF you are behind a firewall, the machines would be unreachable by any hackers.

Secondly, are you running a software firewall on any of the machines?  If so, disable it while we troubleshoot.  To confirm in Windows, open the Network control panel, select the interface (there might be a little 'lock' on it and perhaps 'Firewalled' appears in the details.  If so, open the properties, click on ADVANCED and disable it.

For Ubuntu, post the output of
```
sudo iptables -L
```

Can you post the output of the following commands from each computer:

**_For the IP address:_**
```
ifconfig -a
``` (**ipconfig -all** from Windows)

**_For the Nameserver:_**
```
cat /etc/resolv.conf
``` (in Windows, **ipconfig -all** reveals it)

**_Routing Table:_**
```
route -n
``` (for Windows, it's **route print**, I think)

> **mac_an_ultaigh said:**
> I don't understand. My understanding was - as you say - that WINS had been superceded by DNS. We have a router. From the Windows boxes I can ping the machine/server names of both Windows and Ubuntu boxes no problem. None of our boxes have WINS installed. Doesn't that mean there's a DNS server working somewhere? 

The only DNS server is at your ISP.  Your router forwards all lookups to it, and they do not have any registered entries for your home computers.  The little Linksys/D-Link/Netgear cannot provide the FQDN information to any clients on the network (as far as I know).

By installing winbind on your computers, each computer will 'register' the other computer's Netbios name and IP address.  AS Nickmcg mentioned, one of the computers running 'winbind' will be 'elected' to be the 'browse master' (aka the authority that the other computers will look to).  In the event that the 'browse master' is off, one of the other computers running wins/winbind will take over.

> **mac_an_ultaigh said:**
> 
Done that. No difference. ping WINDOWS_BOX_NAME doesn't work. As a n00b this is all new territory. There's a limit as to how many threads I can follow without completely losing the plot.   OK. So I could try installing WINS on all the Windows boxes. But the question is: why should this be necessary?

You shouldn't need to install WINS on the Windows boxes (WINS is the actual server, which you might want to use if you were running a corporate LAN).  The underlying technology is 'Netbios over TCP/IP', which is already there (for legacy reasons, so that it can communicate to Windows NT networks, etc).

> **mac_an_ultaigh said:**
> 
All Windows boxes network no probs without it. With Samba, libgnomevfs2-extra, LinNeighborhood and winbind all installed on the Ubuntu box, why is it necessary to load the Windows machines with outdated technology so Ubuntu can communicate with them? It all seems a bit archaic to me. If Ubuntu wants to be useable straight out of the box, then this would seem to be one glaring omission where there is considerable room for improvement :-k

Ian

As mentioned, you should'nt have to load anything on the Windows computers... they should already work (you mention that they can see each other).  In order to get Ubuntu & Windows talking we need Ubuntu to have some packages installed, namely samba, smbclient, smbfs and winbind.

As to why or why not certain packages aren't installed by default, I don't know.  Windows has the same issues with regards to 'default installations', but of course, they include everything required to talk to other Windows machines, but if you want to connect to Netware or Unix (natively), lookout! :)

-Dave

---

### Post by nickmcg on 2006-11-05
> **mac_an_ultaigh said:**
> 
From Ubuntu box, Places -> Network Servers -> Windows Network -> mshome returns:

The folder contents could not be displayed.
Sorry, couldn't display all the contents of 'Windows Network: mshome


I've just tried this on my machine, and found a different problem:
Places -> Network Servers -> Windows Network shows an empty document, and gives "Couldn't display "smb:///mcgill". The location is not a folder."
If I then hit the reload button, the network icon shows up, and I can browse that, although I have to hit the reload button at least once to browse the servers.

I did not have this problem under Dapper!

Interestingly, Places->connect to server->[select windows network], Browse does not exhibit this problem .

Nick

---

### Post by mac_an_ultaigh on 2006-11-05
Thanks Dave. > **dbott67 said:**
>  If you could post a little diagram with the network layout (names & IPs of all devices) that would be helpful.  Click to enlarge: [ATTACH]18917[/ATTACH] > **dbott67 said:**
>  Secondly, are you running a software firewall on any of the machines?  If so, disable it   Done
> **dbott67 said:**
>  For Ubuntu, post the output of
```
sudo iptables -L
```  ```
ian@UBUNTU1:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target    prot opt source    destination

Chain FORWARD (policy ACCEPT)
target    prot opt source    destination

Chain OUTPUT (policy ACCEPT)
target    prot opt source    destination
``` > **dbott67 said:**
>  Can you post the output of the following commands from each computer:

**_For the IP address:_**
```
ifconfig -a
``` (**ipconfig -all** from Windows)  

DHCP in operation so IPs are assigned in order of boot up.

I only need to enable graphic browsing between UBUNTU1 and WIN2 so have only included outputs from those below for simplicity:
```
ian@UBUNTU1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:90:96:1F:A6:DA
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x1c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3238 (3.1 KiB)  TX bytes:3238 (3.1 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:A9:3E:09
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2677 errors:45 dropped:45 overruns:0 carrier:0
          collisions:537 txqueuelen:1000
          RX bytes:68067 (66.4 KiB)  TX bytes:173219 (169.1 KiB)
          Interrupt:11 Base address:0x8000

``` And for the WIN2 machine: ```
ipconfig -all

Windows IP Configuration

    Host Name . . . . . . . . . . . . . : WIN2
    Primary Dns Suffix  . . . . . . . . :
    Node Type . . . . . . . . . . . . . : Unknown
    IP Routing Enabled. . . . . . . . . : No
    WINS Proxy Enabled. . . . . . . . . : No

Ethernet adapter Wireless Network Connection 2:

    Connection-specific DNS Suffix  . . :
    Description . . . . . . . . . . . . : D-Link AirPlus G DWL-G122 Wireless USB Adapter(rev.B)
    Physical Address. . . . . . . . . . : 00-13-46-6B-A3-5E
    Dhcp Enabled. . . . . . . . . . . . : Yes
    Autoconfiguration Enabled . . . . . : Yes
    IP Address. . . . . . . . . . . . . : 192.168.1.2
    Subnet Mask . . . . . . . . . . . . : 255.255.255.0
    Default Gateway . . . . . . . . . . : 192.168.1.1
    DHCP Server . . . . . . . . . . . . : 192.168.1.1
    DNS Servers . . . . . . . . . . . . : 192.168.1.1
    Lease Obtained  . . . . . . . . . . : 05 November 2006 17:02:31
    Lease Expires . . . . . . . . . . . : 05 November 2006 18:02:31

```  > **dbott67 said:**
>  **_For the Nameserver:_**
```
cat /etc/resolv.conf
``` (in Windows, **ipconfig -all** reveals it)  ```
ian@UBUNTU1:~$ cat /etc/resolv.conf
nameserver 62.24.199.13
nameserver 62.24.199.23
nameserver 192.168.1.1

``` > **dbott67 said:**
>  **_Routing Table:_**
```
route -n
``` (for Windows, it's **route print**, I think)  
```
ian@UBUNTU1:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ra0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ra0
``` Click to enlarge: [ATTACH]18918[/ATTACH] > **dbott67 said:**
> 
The only DNS server is at your ISP.  Your router forwards all lookups to it, and they do not have any registered entries for your home computers.  The little Linksys/D-Link/Netgear cannot provide the FQDN information to any clients on the network (as far as I know).  Now I'm even more confused. ipconfig on Windows outputted: ```
DNS Servers . . . . . . . . . . . . : 192.168.1.1
``` which I assumed meant that 192.168.1.1 (the router) was a DNS Server.
> **dbott67 said:**
>  You shouldn't need to install WINS on the Windows boses (WINS is the actual server, which you might want to use if you were running a corporate LAN).  The underlying technology is 'Netbios over TCP/IP', which is already there (for legacy reasons, so that it can communicate to Windows NT networks, etc).  That's what I thought. :) > **dbott67 said:**
>  As mentioned, you should have to load anything on the Windows computers... they should already work (you mention that they can see each other).   They certainly can. And they can all see UBUNTU1 too. So no probs with Windows Networking at all.

Where now?

Ian

---

### Post by dbott67 on 2006-11-05
Ian,

Further to my previous post about IP address, network layout, etc., you mention that you are able to connect to the Windows computers from Ubuntu using the IP address --- what is the IP address that you are using?

I whipped up a little diagram in OpenOffice's Presentation Software (Impress) and plugged in some arbitrary names & numbers.  Then I pressed F5 to start the presentation & took a screenshot to attach to this post as a PNG file.

I'm including the original file so that you can plug in the real values for the computer names & IP addresses,  Just unzip the file (Ians_LAN.zip), make the necessary modifications & re-post (you'll need to re-zip the file to post it back here).

Thanks,
-Dave

---

### Post by nickmcg on 2006-11-05
> Now I'm even more confused. ipconfig on Windows outputted:
Code:

DNS Servers . . . . . . . . . . . . : 192.168.1.1

which I assumed meant that 192.168.1.1 (the router) was a DNS Server.
If your sytem is like mine, the router is a DNS server for your local network (and is also a DHCP server) , but will forward any unknown names to the DNS servers it then knows about.
DNS covers IP adressing, but not wins (if I'm wrong about this, I'm sure someone will correct me)

Nick

---

### Post by mac_an_ultaigh on 2006-11-05
Dave > **dbott67 said:**
>  Further to my previous post about IP address, network layout, etc., you mention that you are able to connect to the Windows computers from Ubuntu using the IP address --- what is the IP address that you are using?  Whatever IP is assigned by the router on bootup for that session. That's why I'd like to enable graphic browsing from Nautilus. Otherwise, each time I want to browse from Ubuntu I have to go to each Windows box and run ipconfig to find out what IP they're using for that session. > **dbott67 said:**
>  I whipped up a little diagram in OpenOffice's Presentation Software (Impress) and plugged in some arbitrary names & numbers.  Then I pressed F5 to start the presentation & took a screenshot to attach to this post as a PNG file.  Thanks. I'll certainly be using that next time, but for now I presume the diagram I knocked-up earlier contains all the info you asked for?

Ian

---

### Post by mac_an_ultaigh on 2006-11-05
Nick > **nickmcg said:**
>  If your sytem is like mine, the router is a DNS server for your local network (and is also a DHCP server) , but will forward any unknown names to the DNS servers it then knows about.  So the router IS a DNS server - even if only a very limited one. Which ought to mean it can handle those names it DOES know about. i.e. names on the LAN. > **nickmcg said:**
>  DNS covers IP adressing, but not wins (if I'm wrong about this, I'm sure someone will correct me)  I wouldn't expect a DNS server to cover WINS, but would expect it to translate Names to IP addresses. >  From Wikipedia:
The **domain name system** (**DNS**) stores and associates many types of information with [domain names]("http://en.wikipedia.org/wiki/Domain_name"), but most importantly, it translates domain names (computer [hostnames]("http://en.wikipedia.org/wiki/Hostname")) to [IP addresses]("http://en.wikipedia.org/wiki/IP_addresses"). Otherwise, why wouldn't it be called something like IPS rather than DNS?

Ian

---

### Post by nickmcg on 2006-11-06
I did notice that before I had winbind installed, the ubuntu box was not broadcasting its name to the router, despite the fact that dhcp was allocating an ip address.

Nick

---

### Post by mac_an_ultaigh on 2006-11-06
> **nickmcg said:**
> I did notice that before I had winbind installed, the ubuntu box was not broadcasting its name to the router, despite the fact that dhcp was allocating an ip address. That sounds about right. I seem to remember noticing something similar myself. I'm starting to suspect that winbind may be the answer but the problem is that Nautilus doesn't know that!

---

### Post by dbott67 on 2006-11-06
Hi Ian (and Nick),

Sorry for the delay... life gets in the way of being a geek sometimes! :)

Ian --- the LAN diagram you provided is fine... I was whipping that one up just as you were posting your reply.

As for the DNS issue: According to the D-Link 'Help Menu' *When DNS Relay is enabled, the router will play a role as DNS server that [COLOR="Red"]send request to ISP DNS server and cache the information for later access[/COLOR]. When DNS relay is disabled, [COLOR="Red"]the computer will pull information from ISP DNS server[/COLOR]*.

My interpretation of this is that your router does not know anything (DNS-wise) about your local network, as all of the information is being pulled from the ISPs DNS server.  It is not functioning as a DNS server, other than to forward requests to the ISP DNS server (and possibly cache the result to increase performance).

The **iptables -L** indicates that no firewall is running on your Ubuntu box.

The output of **ifconfig/ipconfig/route** indicate that the machines in question are getting the correct DHCP information from the router (IP, Subnet Mask & Gateway are all 192.168.1.x, 255.255.255.0 & 192.168.1.1.

The one thing that is odd is the inclusion of the ISPs nameservers in your **/etc/resolv.conf** file.  My home network is very similar to yours:

1. D-Link DI-624 Wifi Router - 192.168.1.1
2. NexStar LX NAS 160 GB (SMB, FTP) - 192.168.1.2
3. HP JetDirect EX Plus Print Server - 192.168.1.10
4. Toshiba Tecra 8000 (Dapper) wifi - 192.168.1.100
5. Dell Inspiron 5160 (XP Home) wifi - 192.168.1.101
6. Windows XP Pro (Kids) wired - 192.168.1.102
7. Mac OSX - 192.168.1.103
8. HP iPAQ 4250 (PocketPC) wifi - 192.168.1.104
9. Dell Inspiron 6400 (multiboot: Dapper, XP Pro, XP MCE, Win2003) wifi - 192.168.1.105
10. Desktop PC (Dapper) wired - 192.168.1.106

My output of smbtree is:
```
dbott@thedrake:~$ smbtree
Password:
WORKGROUP
        \\PIII-600
        \\NAS-160GB
                \\NAS-160GB\IPC$
                \\NAS-160GB\Music
                \\NAS-160GB\Archive
                \\NAS-160GB\Data
                \\NAS-160GB\PUBLIC
MSHOME
        \\THEDRAKE                      thedrake server (Samba, Ubuntu)
                \\THEDRAKE\print$               Printer Drivers
                \\THEDRAKE\dbott-P4
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
        \\DAPPER                        dapper server (Samba, Ubuntu)
                \\DAPPER\print$                 Printer Drivers
                \\DAPPER\ndis
                \\DAPPER\IPC$                   IPC Service (dapper server (Samba, Ubuntu))
                \\DAPPER\ADMIN$                 IPC Service (dapper server (Samba, Ubuntu))

```

When you ran this command, you got:
```
MSHOME
    \\WINDOWS_BOX_NAME
timeout connecting to 82.101.8.47:445
timeout connecting to 82.101.8.47:139
Error connecting to 82.101.8.47 (Operation already in progress)
cli_start_connection: failed to connect to WINDOWSBOX<20> (80.101.8.47)
    \\UBUNTU_BOX_NAME
        \\(shows all shares as in your example)
```

The problem is that it shouldn't be trying to connect ot 82.101.8.47 --- it's not even on your subnet.  Looking back at your resolv.conf, yours has 2 nameservers listed from your ISP (I'm assuming).  Mine does not have anything except the Ip of my D-Link router.  Let's try commenting out the first 2 entries:
```
**#** nameserver 62.24.199.13
**#** nameserver 62.24.199.23
nameserver 192.168.1.1 
```

Now, cross your fingers.  You shouldn't require a reboot, but if this doesn't work, try re-booting the system.  Post the output of **smbtree**.

The only other difference between your network & mine is that I use 'static' DHCP (basically, I reserve the same IP for each computer so that I can use port-forwarding to SSH/VNC/whatever to my home computers from work (or wherever).  On your router, the [static DHCP setting]("http://support.dlink.com/Emulators/dslg604t/home_dhcp.html") is under the DHCP button.  If you look at the bottom of the screen, you should be able to get the MAC address & current IP address to plug into the 5 available fields.

-Dave

---

### Post by mac_an_ultaigh on 2006-11-06
Dave
> **dbott67 said:**
>  The **iptables -L** indicates that no firewall is running on your Ubuntu box.  True. You said to disable it for troubleshooting. > **dbott67 said:**
>  The output of **ifconfig/ipconfig/route** indicate that the machines in question are getting the correct DHCP information from the router (IP, Subnet Mask & Gateway are all 192.168.1.x, 255.255.255.0 & 192.168.1.1.  Also true. > **dbott67 said:**
>  The one thing that is odd is the inclusion of the ISPs nameservers in your **/etc/resolv.conf** file.   Not odd at all. I configured it to work that way. For an explaination see below. > **dbott67 said:**
>  The problem is that it shouldn't be trying to connect ot 82.101.8.47 --- it's not even on your subnet.   Absolutely. Where are these IPs coming from is what I'd like to know?
> **dbott67 said:**
>   Looking back at your resolv.conf, yours has 2 nameservers listed from your ISP (I'm assuming).  No. They are the IPs of my ISP's nameserver. But they're not listed from  it. They are listed there because I prepended them in  /etc/dhcp3/dhclient.conf. I did this after several very frustrating days of trying every-which-way to get aptitude to connect to the repositories. Eventually I stumbled across the explanation and the fix in a post from stream303 which I first found [here]("http://www.ubuntuforums.org/showthread.php?t=122550") and was reposted recently by handy a couple of weeks ago [here]("http://www.ubuntuforums.org/showthread.php?t=282034")  > **dbott67 said:**
>  Let's try commenting out the first 2 entries:
```
**#** nameserver 62.24.199.13
**#** nameserver 62.24.199.23
nameserver 192.168.1.1 
```  Well. I could do that. But then I would no longer be able to access the repositories for updates and upgrades. And, in any case, they would quickly be reinstated by /etc/dhcp3/dhclient.conf  Getting Nautilus to browse the Windows network would be nice. But I can still access it by typing in the IPs. So if its a choice between that and going back to not being able to use aptitude then this would be the lesser of the two evils. > **dbott67 said:**
>   The only other difference between your network & mine is that I use 'static' DHCP (basically, I reserve the same IP for each computer so that I can use port-forwarding to SSH/VNC/whatever to my home computers from work (or wherever).  On your router, the [static DHCP setting]("http://support.dlink.com/Emulators/dslg604t/home_dhcp.html") is under the DHCP button.  Yep. I know that. The use of DHCP rather than static IPs is a deliberate decision. We have people coming and going with laptops throughout the day and going back to having to configure static IPs would be a real nuisance. If it's a choice between keeping DHCP or being able to use Nautilus then, again, DHCP would be the lesser of the two evils.

It is a nuisance having to run ipconfig on a Windows box everytime I want to network with it, but I can do what I need to do in one way or another which is, after all, the point of having these pesky boxes in the first place. So I think it's probably best just to stick with things the way they are for the time being. Thanks for all your help anyway. Much appreciated. :)

---

### Post by mac_an_ultaigh on 2006-11-06
> **nickmcg said:**
>  Interestingly, Places->connect to server->[select windows network], Browse does not exhibit this problem .  Nick. I missed that first time round. Have just tried it, but it doesn't work for me. Curiouser and curiouser.   :-k

---

### Post by dbott67 on 2006-11-06
> **mac_an_ultaigh said:**
> The use of DHCP rather than static IPs is a deliberate decision. We have people coming and going with laptops throughout the day and going back to having to configure static IPs would be a real nuisance. If it's a choice between keeping DHCP or being able to use Nautilus then, again, DHCP would be the lesser of the two evils.

Actually, I'm recommending 'static DHCP' not static IPs (where you program the IP on each client).  The difference is that DHCP is still used, it just reserves the same IP for a specific computer (by looking at the MAC address).  The only change would be to login to your router & click on the DHCP tab.  Enter the IP and MAC address of each computer that you want to 'reserve' and they'll always receive the same IP from the DHCP server while on your network.

As for the /etc/resolv.conf, what happens if you try  the following:

Move the local nameserver to the top:
```
nameserver 192.168.1.1
nameserver 62.24.199.13
nameserver 62.24.199.23
```

I would also be curious to know what happens if you comment out the 2 ISP nameservers and run smbtree (just to eliminate it as the problem... you can  always re-enable it later).

BTW, my comment *"The iptables -L indicates that no firewall is running on your Ubuntu box"* was more to say that "at least it's not a firewall blocking access"

-Dave

---

### Post by dbott67 on 2006-11-06
I found a great article that may be the key:

[http://www.faqs.org/docs/samba/ch07.html](http://www.faqs.org/docs/samba/ch07.html)

The key parts are the 'lmhosts' file (this is a trick that I always used on Windows networks when there was no WINS server).  Basically, you need to create a file called 'lmhosts' in the **/etc/samba** directory (**man lmhosts** for usage) with the following lines:
```

192.168.1.2  WIN2
192.168.1.3  WIN1
192.168.1.4  UBUNTU1
192.168.1.5  WIN3
```

This requires that you use 'STATIC DHCP' or 'STATIC IPs' as discussed earlier.

There is also a line in the /etc/samba/smb.conf file that would need to be uncommented (in the Global Settings section in red):
```

dbott@dapper:/etc/samba$ cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
[COLOR="Red"]name resolve order = lmhosts host wins bcast[/COLOR]


```

---

### Post by glave on 2006-11-07
Ok, this problem has cropped up for me, but in a different way.  A few days ago I installed edgy, I could see my other windows machines on the network just fine, but if I actually tried to go further than the default IPC share, I would get an error telling me the location is not a folder.

I installed samba, and it went away.

Days later, I just tried to access the network via bookmarks I'd made, it tells me it can't connect (Unknown Error 46). I poke around, try browsing the network. I can see the workgroup, but can't even go inside it to see machines (Location is not a folder again).  I checked, samba is running, I stopped it, restarted, tried again, same dice. As I'm typing this message though, I flipped over to get my exact error message, and when I tried to browse again, I got the same error, BUT a second later, I can see all the windows machines. (ACTUALLY, 2 of the machine are ubuntu ones too.)

Strange inconsistent behavior...

---

### Post by glave on 2006-11-07
Frustrating enough, I can now click on SOME of my servers and see their shares, but I get the error "Couldn't display "smb://grumpus/ROBOTRON". The location is not a folder" 

If I click into one of the 'working' servers and come back out, one of the non working ones may or may not work. Its very easy to distinguish which ones will work, as they have a little server icon beside their name, and non working ones have a generic file icon beside of them. Going into 'working' or non working ones seems to completely change which ones will or won't work the next try.

This behavior is making me think something is broken in the edgy install or something. ALL of my servers can see each other and their shares just fine (4 Windows boxes, 2 breezy boxes, and 2 xboxen).

---

### Post by nickmcg on 2006-11-08
I get the same symptoms as this - hitting the 'reload'button a few times will populate nautilus with server icons (well, it does for me).

Nick

---

### Post by glave on 2006-11-08
Same thing, simply hitting refresh is like rolling the dice on which servers become available.

Some apps (amarok) simply can't access any of the files across the network at all.

---

### Post by bayvista on 2006-11-13
I had the wsame problem and eventually tracked it down to the DNS address. This is normally left blank in a router and filled in by the ISP at connect. I was trying to use OpenDNS, but it only confused things. I have now removed the DNS addresses from Windows, Ubuntu and the D-Link router. Now I can browse both ways.

Will now try a reboot.

David

---

### Post by mac_an_ultaigh on 2006-11-26
> **bayvista said:**
> I have now removed the DNS addresses from Windows, Ubuntu and the D-Link router. Now I can browse both ways. Well. I didn't realise the D-Link didn't need "User Configuration" DNS addresses, but I tried removing them and it seems to run faster! Cheered on by this, I tried removing the prepends from /etc/dhcp3/dhclient.conf and that worked too! So I was pretty confident that this would solve the browsing Windows Workgroup from Nautilus problem. Unfortunately that bit stilll doesn't work for me.

---

### Post by gurgle on 2006-12-19
has anyone figured out how to browse yet?

---

### Post by mac_an_ultaigh on 2006-12-20
> **gurgle said:**
> has anyone figured out how to browse yet?
None I know of :(

Suspect this is a problem a Ubuntu or better still Nautilus or Samba developer would probably eat for breakfast. Unfortunately, you don't see many of them around these parts. Ideally there would be some kind of upward referral process for the stickier issues, but I haven't come across one of them yet either!

---

### Post by dannyboy79 on 2006-12-20
> **mac_an_ultaigh said:**
> Well. I didn't realise the D-Link didn't need "User Configuration" DNS addresses, but I tried removing them and it seems to run faster! Cheered on by this, I tried removing the prepends from /etc/dhcp3/dhclient.conf and that worked too! So I was pretty confident that this would solve the browsing Windows Workgroup from Nautilus problem. Unfortunately that bit stilll doesn't work for me.

i am a little confussed by this?? you say you remove your dns entries from your router and your computers and what is faster??? without dns servers to relate ip's to domain names, you shouldn't be able to surf the internet by typing [www.gogle.com](www.gogle.com), it would time out because you removed all your dns servers. you would have to know gogles ip address to surf it. so what exactly do you mean when you guys say you remove your dns servers? i have a mixed network with 2 ubuntu box (1 x and 1 normal) and 1 win xp box, and one xbox running xmbc. for some reason samba works great when all the machines are on but if windows is off, samba doesn't work, it complains that the domain master cannot be found. so a i am trying to read all the samba threads in here to get it just right!!!

---

### Post by scrooge_74 on 2006-12-20
> **dannyboy79 said:**
> i am a little confussed by this?? you say you remove your dns entries from your router and your computers and what is faster??? without dns servers to relate ip's to domain names, you shouldn't be able to surf the internet by typing [www.gogle.com](www.gogle.com), it would time out because you removed all your dns servers. you would have to know gogles ip address to surf it. so what exactly do you mean when you guys say you remove your dns servers? i have a mixed network with 2 ubuntu box (1 x and 1 normal) and 1 win xp box, and one xbox running xmbc. for some reason samba works great when all the machines are on but if windows is off, samba doesn't work, it complains that the domain master cannot be found. so a i am trying to read all the samba threads in here to get it just right!!!

Maybe he knows the IP # by hearth and don't need any stinking DNS servers :D

---

### Post by mac_an_ultaigh on 2006-12-21
> **dannyboy79 said:**
> i am a little confussed by this?? you say you remove your dns entries from your router and your computers and what is faster???I didn't say anything about removing DNS servers. All I did was simply remove the IP of my ISP from the router config page. All DNS servers otherwise left untouched. > **dannyboy79 said:**
>   without dns servers to relate ip's to domain names, you shouldn't be able to surf the internet by typing [www.gogle.com]("http://www.gogle.com/"), it would time out because you removed all your dns servers. you would have to know gogles ip address to surf it.  I'm no expert but I thought a lot of this was done by the various nameservers dotted around the planet (13 at the last count) and by your isp. Maybe somebody can put us both right on this. > **dannyboy79 said:**
>  so what exactly do you mean when you guys say you remove your dns servers?  If I said that then I certainly didn't mean it. > **dannyboy79 said:**
> .... samba doesn't work, it complains that the domain master cannot be found. so a i am trying to read all the samba threads in here to get it just right!!!  Aren't we all :)
> **scrooge_74 said:**
> Maybe he knows the IP # by hearth and don't need any stinking DNS servers :D The chance would be a fine thing. :)

---

### Post by scrooge_74 on 2006-12-21
> **mac_an_ultaigh said:**
> I didn't say anything about removing DNS servers. All I did was simply remove the IP of my ISP from the router config page. All DNS servers otherwise left untouched.  I'm no expert but I thought a lot of this was done by the various nameservers dotted around the planet (13 at the last count) and by your isp. Maybe somebody can put us both right on this.  If I said that then I certainly didn't mean it.  Aren't we all :)
 The chance would be a fine thing. :)

I usually will put the ip of my router (which was config by my ISP to act as a DNS server) last and then add the real IPs of the DNS use by my ISP plus a couple of extra ones. It helps when my router can't find for some reason my ISP DNS address.

I got a called the other day from my father, he couldn't surf, I told him to reboot the router, later I remember I did not add other DNS addresses to his PC

---

### Post by dannyboy79 on 2006-12-21
> **scrooge_74 said:**
> Maybe he knows the IP # by hearth and don't need any stinking DNS servers :D

i highly doubt that anyone in the entire world has every ip memorized for every website out there. if you know someone like this please introduce them to me as they have to be smarter than rainman.

---

### Post by dannyboy79 on 2006-12-21
OK, try to clarify the question. 
bayvista stated this: "I have now removed the DNS addresses from Windows, Ubuntu and the D-Link router. Now I can browse both ways."

then mac_an_ultaigh stated this: "Well. I didn't realise the D-Link didn't need "User Configuration" DNS addresses, but I tried removing them and it seems to run faster! Cheered on by this, I tried removing the prepends from /etc/dhcp3/dhclient.conf and that worked too! So I was pretty confident that this would solve the browsing Windows Workgroup from Nautilus problem. Unfortunately that bit stilll doesn't work for me."

So I simply wanting clarification on what you meant when you stated that you removed the DNS addresses as you clearly did. Understand now??? 

Also, when you say that there are 13 DNS servers around the world to help you resolve names to ip's that only is applicable if you can get to the internet to begin with, so my point is that if you're computer is hooked to a router and the router doesn't intelligently use the isp's dns servers to make itself like a dns server and the person says, well I added my router to my resolv.conf but still can't surf than you would have to add some dns servers to your resolv.conf to be able to surf the internet. this problem is brought up a million times in this forum. just do a search with "can't connect to internet" and you'll see most of the time it's due to not having the dns server's either configured within your router or within your computer. so i guess we are all clear now. do any of you guys use a wins server within your lan? do you guys use static or dhcp?

---

### Post by ChrisG_UK on 2007-02-18
Not being able to reach a dhcp Windows host by name "out of the box" is a total and absolute killer for Ubuntu. I have spent hours on this. I'm using 6.10 Edgy Eft.

I have installed winbind and configured it in nsswitch.conf

I have checked resolv.conf - just my router in there.

I can ping Google.com, no problem. If I ping my Windows box, I get a good reply from 62.210.183.12, which is the wrong address. But then, guess what? Exactly the same result from a ping of any non-existent name! ping xyz123456 - good reply! ping zzzzzz - good reply...

I can ping my XP box by address but as it's dhcp from my router that doesn't really help me. 

nmblookup finds the address of my Windows box correctly.

smbtree correctly shows the Netbios names of all my Windows machines, followed by "Error connecting to 62.210.183.12 (Connection refused)" - always that same 62 address.

Grr!

---

### Post by ChrisG_UK on 2007-02-18
I just discovered that the winbind demon (winbindd) is not running. If I start it manually, it doesn't stay running. Anyone know why that could be or how to investigate?

---

### Post by ChrisG_UK on 2007-02-23
Hi everyone,

I got a bit further with this, but now I'm stuck. To re-cap, what I'm trying to do is connect from Ubuntu to a share on a Windows XP Home machine. My Ubuntu machine and my XP machine are both connected to a common or garden domestic home router, which provides DHCP. I know I could setup the Windows box with a static ip address but I'm stubborn and I want this to work as it should, by name. The simplest solution to this appears to be this one:

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)

This seems to work for some people but for others, winbind refuses to run - and I'm one of the unlucky ones.

When I first tried to start winbindd, it was giving the error "idmap uid range missing or invalid". So in smb.conf I uncommented the idmap uid and idmap gid lines. Now when I try to run winbindd it fails with "unable to initalize domain list". This has foxed me for several days now. I have hunted high and low and read all the docs, but nothing works. I have downloaded the source code and I'm about to get stuck in, but please, if anyone has any ideas, I would really, really appreciate the help!

---

### Post by ChrisG_UK on 2007-02-25
Well, I tried but it looks like the source code for winbind 3.0.22 doesn't match the install package. I'm completely stuck now and can't continue with Ubuntu.

---

### Post by truxntrax on 2007-03-12
Anyone got any other suggestions.  I have been reading on this issue for weeks!  Done all the suggested steps - here is the output of SMBTREE:

john@john-linux:/etc$ smbtree
Password: 
WORKGROUP
        \\JOHN-VISTA     
        \\JOHN-LINUX                    john-linux server (Samba, Ubuntu)
                \\JOHN-LINUX\ADMIN$             IPC Service (john-linux server (Samba, Ubuntu))
                \\JOHN-LINUX\IPC$               IPC Service (john-linux server (Samba, Ubuntu))
                \\JOHN-LINUX\home               share
                \\JOHN-LINUX\bin            
                \\JOHN-LINUX\root           
                \\JOHN-LINUX\john           
                \\JOHN-LINUX\print$             Printer Drivers

Why can't I connect to my machine \\john-vista?  I can ping it.  I have created a windows user to log on (on the vista machine) but every time nautilus just asks for the username, domain and password again...

Anyone any ideas?

---

### Post by rootboyralph on 2007-04-29
Hey all,

Sorry to chime in so late on all this, but after working on this EXACT same problem all day long, I decided I'd post my success story:

I've had all the same "IP works, names don't" and nautilus acting funky, and all that stuff.  I looked, I've got samba working fine, I guess winbind is working fine, I don't know.  But everytime I tried to even PING one of my windows boxes, it resolved to some crazy, means nothing IP...

So what to do?  Well I got the clue from someone else to add wins to the "/etc/nsswitch.conf" file on the "hosts" line.  This didn't do crap for me.  Well I got to thinking about where that IP is coming from and realized it couldn't be from inside my network, so it must be looking somewhere else to get those crazy IPs, so I changed the order of this line in nsswitch.conf, and put wins right behind files, and voila it worked.  All pings started routing correctly.  Everything was working fine except for Nautilus, and a simple restart cured that.

I hope this helps someone save as much time as it has cost me.

---

### Post by ChrisG_UK on 2007-04-30
Hey, thanks for that rootboyralph, sounds like you are onto something there. I gave up with Ubuntu because of this and a few other issues, but will be trying again with 7.04 soon, and will give this a go. Many thanks!

---

### Post by willough on 2007-07-01
Just wanted to add something to this post after making a discovery on our server.  I too was unable to browse Windows shares, yet able to ping each network client from the Ubuntu server.  I found that a CUPS printer was not configured properly and so I deleted it.  Once it was deleted all the Windows shares became visible as they should have been.  I've concluded that if any shareable resource is not properly configured, be it a drive or printer, the Network browse will not work as expected.  At least that is what I feel to be true after spending a couple of weeks trying all the posted solutions.  Our network worked properly but I was just unable to browse it from Ubuntu until removing the improperly configured device.

Our server is Feisty.

---

### Post by ChrisG_UK on 2007-07-02
I eventually took a different direction - it doesn't really belong on this thread so I won't go into detail. I tried to install Feisty Ubuntu but that failed due to lack of memory, so I moved to Xubuntu, and wow! am I a happy bunny now. Not only is the machine now about twice as fast as it ever was with Edgy Ubuntu (or Windows ME before that), but I was easily able to solve my Windows connectivity issues, and I find the Xubuntu GUI much more to my liking. For anyone interested in going down this route, this will help: [http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu](http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu)

---

### Post by couzin2000 on 2007-11-04
Don't know if you're interested in this, but I think the problem is located specifically in the way Nautilus handles name requests. I had this problem since my fresh install of Gutsy, and my network is made up of one Ubuntu laptop and one Ubuntu desktop - and I still had the same reaction when trying to browse with Nautilus.

But then something hit me - I ran **smbtree** and got this result:```
MSHOME
        \\SEBASTIEN-LAPTOP              sebastien-laptop server (Samba, Ubuntu)
                \\SEBASTIEN-LAPTOP\IPC$                 IPC Service (sebastien-laptop server (Samba, Ubuntu))
                \\SEBASTIEN-LAPTOP\print$               Printer Drivers
        \\SEBASTIEN-DESKT               Samba 3.0.26a
                \\SEBASTIEN-DESKT\IPC$                  IPC Service (Samba 3.0.26a)
                \\SEBASTIEN-DESKT\Desktop-Home   
                \\SEBASTIEN-DESKT\MyFiles        
                \\SEBASTIEN-DESKT\print$       
``` and I realized that the reason why I was getting names here is because Samba wasn't the culprit -- it was configured properly.

So I went into Nautilus again, only this time typed into the adress bar:```
smb://SEBASTIEN-DESKT
``` and I immediately accessed, **through Nautilus**, my shares.

I've seen a similar thing happen on Windows, when you go into Network Neighbourhood, yet can't browse? Somehow I think this is related to how Explorer behaves inherently. Typically, one would have create a permanent connection to a remote drive, or "mount it" (but Windows users rarely use the term). Here in Ubuntu, I think the whole thing is similar: I went ahead into "Places" and selected "Connect to server", then selected the "Custom Location" Service type, and just typed in the address: smb://SEBASTIEN-DESKT, just as I'd gotten from smbtree.
Double click the icon on your desktop, and voilà -- all your shares.

At least that's how I solved the problem. It's a workaround, but it works.

---

### Post by pd71sat on 2007-11-22
> **rootboyralph said:**
> Hey all,

Sorry to chime in so late on all this, but after working on this EXACT same problem all day long, I decided I'd post my success story:

I've had all the same "IP works, names don't" and nautilus acting funky, and all that stuff.  I looked, I've got samba working fine, I guess winbind is working fine, I don't know.  But everytime I tried to even PING one of my windows boxes, it resolved to some crazy, means nothing IP...

So what to do?  Well I got the clue from someone else to add wins to the "/etc/nsswitch.conf" file on the "hosts" line.  This didn't do crap for me.  Well I got to thinking about where that IP is coming from and realized it couldn't be from inside my network, so it must be looking somewhere else to get those crazy IPs, so I changed the order of this line in nsswitch.conf, and put wins right behind files, and voila it worked.  All pings started routing correctly.  Everything was working fine except for Nautilus, and a simple restart cured that.

I hope this helps someone save as much time as it has cost me.

rootboyralph your post helped me to solve this issue. I followed your advice and moved wins to the second position in the "hosts:" parameter of the "/etc/ nsswitch.conf" file and voila I could browse my Windows XP shares.and access my files. Thank you so much. Each problem that I have had I have been able to get my solution from this forum, even if it is to know that a full correction is not yet available.

The one problem I still have with my Windows shares (the ones that I have explicitly set to be shared are ok) is that I also see the default Windows original share names ex. C$ for the C: drive, etc. If I click this share name then it will ask for a Windows Userid and password to access, That is at least a security check before allowing access. However I would prefer that Samba not present shares other that those explicitly set by me. 

Would appreciate help, whether it is by tweaking a parameter or so, to clear up the Windows Network browse experience and only present the explicit shares.

---

### Post by Tsume on 2007-11-25
> **pd71sat said:**
> rootboyralph your post helped me to solve this issue. I followed your advice and moved wins to the second position in the "hosts:" parameter of the "/etc/ nsswitch.conf" file and voila I could browse my Windows XP shares.and access my files. Thank you so much. Each problem that I have had I have been able to get my solution from this forum, even if it is to know that a full correction is not yet available.

The one problem I still have with my Windows shares (the ones that I have explicitly set to be shared are ok) is that I also see the default Windows original share names ex. C$ for the C: drive, etc. If I click this share name then it will ask for a Windows Userid and password to access, That is at least a security check before allowing access. However I would prefer that Samba not present shares other that those explicitly set by me. 

Would appreciate help, whether it is by tweaking a parameter or so, to clear up the Windows Network browse experience and only present the explicit shares.

I tried rootboyralph's suggestion and it didn't seem to help.  I will edit this post if a reboot proves otherwise.  I won't know what winbind is for, so I don't have it, if that's of any importance.

My computer is set to get everything from the router automatically.  The DNS server on my computer is 192.168.1.1; on the router I have OpenDNS configured... and that is why the wrong IPs I am getting for my local computers are all on the OpenDNS network... something is asking the router's DNS server what my computers' IPs are, and it's giving the wrong answer:

"tsumeone@ArtemisNIX:~$ ping \\jasons-pc
PING jasons-pc.sd.cox.net (208.67.219.130) 56(84) bytes of data.
64 bytes from nxdomain.guide.opendns.com (208.67.219.130): icmp_seq=1 ttl=246 time=38.3 ms
64 bytes from nxdomain.guide.opendns.com (208.67.219.130): icmp_seq=2 ttl=246 time=34.8 ms
64 bytes from nxdomain.guide.opendns.com (208.67.219.130): icmp_seq=3 ttl=246 time=33.3 ms
64 bytes from nxdomain.guide.opendns.com (208.67.219.130): icmp_seq=4 ttl=246 time=40.9 ms
64 bytes from nxdomain.guide.opendns.com (208.67.219.130): icmp_seq=5 ttl=246 time=39.0 ms
64 bytes from nxdomain.guide.opendns.com (208.67.219.130): icmp_seq=6 ttl=246 time=31.5 ms
"

Obviously my machine is either looking in the wrong place for local computer name resolutions, or it's at least doing something much differently than windows to cause this.

---

### Post by fizeq on 2008-03-24
Tsume,

You need to install winbind.

---

### Post by Eiríkr on 2008-03-25
As another point on the graph --

I don't have windbind installed.  Never have.  I *do*, however, make sure that the [font=courier]wins support[/font] global option in my smb.conf file is set to "yes".  And I always restart Samba after making any changes to the conf file by running [font=courier]sudo /etc/init.d/samba restart[/font].  **Reloading alone is not enough** to ensure that all settings are properly loaded and implemented by the Samba daemon.  

Without windbind, but with wins support, I can still browse shares in Nautilus.  I've done this for some time.  I have not tried pinging by NetBIOS name, but recently I've got my own home LAN DNS server up and running anyway so that point is moot.  

@Tsume -- 

How hostname resolution happens depends on the contents of the [font=courier]/etc/resolv.conf[/font] file.  Mine looks like this:
```
search homelan.org
nameserver 127.0.0.1
domain homelan.org
```
The file contents can be changed directly via a text editor, or using a GUI tool like Ubuntu's Network Settings app.  Search settings in the app are under the DNS tab, in the Search Domains box on the bottom of the dialog.  

Anyway, hostnames on their own are resolved by appending the first specified search domain (and then I think the others after that in order).  So if I ran [font=courier]ping -c 4 cucumber[/font], ping would append my search domain to this standalone hostname, and therefore attempt to contact cucumber.homelan.org.  In your case, it sounds like you need to change your search domain, as it's apparently currently set to [font=courier]sd.cox.net[/font].

Cheers,

Eiríkr

---

