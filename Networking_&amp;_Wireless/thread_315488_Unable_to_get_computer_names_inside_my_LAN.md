---
title: "Unable to get computer names inside my LAN"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2006-12-09
Good day everybody!
I've got a problem that I can't solve for years literally. I've got the following situation, I've got a D-DINK router inside my LAN that is also a PPTP and DHCP Server. So all PCs get their IP adresses through DHCP. The problem is that the DNS names for the internet work perfectly so if I type say 'ping ubuntu.com' it works. But I've got a file server inside my LAN and If I try typing 'ping server' it says:> ping: unknown host serverAnd typing say 'ping 192.168.0.4' works great as I expected. My  /etc/resolv.conf is: > search 192.168.0.1
nameserver 217.150.34.129
nameserver 192.168.0.1
domain router192.168.0.1 is my D-LINK router
217.150.34.129 is the Internet nameserver
Who gives the names to the addresses inside of the LAN and what's wrong in my case.

P.S. Everything works fine in Windows

---

### Post by DaveBorealis on 2006-12-09
Hello,

Here's one possible solution.  If the server has a static IP, which it seems it does, then add that with its hostname to the '/etc/hosts' file of your LAN machines.  You can add the IP/hostnames of any other machine with a static IP that you want your machines to know about.

Best regards,
Dave

---

### Post by PryGuy on 2006-12-09
Thanks, but I knew it. And the server does not have a static IP, everything is under DHCP here. ;) I agree that server probably should but since it's a fileserver nothing more I do not want to give it a static IP. Yet I've got two Wi-Fi notebooks and that's very important for them. I don't want to get back to static IPs.:mrgreen: Is there a way to make it work? And yet, I think I remember that some other Linux (Fedora probably) could resolve IPs inside of the LAN area so it is possible not only in theory.

---

### Post by dbott67 on 2006-12-09
There are 2 methods of name resolution that people are familiar with: DNS and WINS (although they may not know it).

Names like **host.domain.com** are resolved to IP address by DNS servers (aka bind).  Normally, you would need to install an internal DNS server on your LAN (*sudo apt-get install bind*) for fully qualified domain name resolution.  Each device on the network would have it's IP address mapped to a FQDN, thereby allowing you to connect via IP or name.domain.com.

If you're trying to ping 'server' (as opposed to *server.yourdomain.com*), then it's a WINS/winbind issue.  I'm assuming that the server is running Samba and you're trying to access it like a typical Windows server.

Earlier versions of Windows used 'netbios' to announce the name of each computer to the rest of the network so that users could browse by computer name.  On larger networks, an administrator would need to install a WINS server that would register each computer on the network and bind the IP to the Windows netbios name.  Today, WINS has been superceded by DNS in the Windows world, but it still has a useful place on smaller networks (and it's still available if you want to use it).

As DaveBorealis notes, you can manually enter local names in the 'hosts' file, but if you use DHCP, this can create problems as the entries would not be updated and the names would (potentially) point to the wrong IP address.  The 'lmhosts' file provides the equivalent static file for netbios names.

The problem here is that most people don't run their own DNS server and if you have any Windows computers on the network (or Samba shares), you really should have a WINS server or 'winbind' installed to allow people to browse by computer name.

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

You also need to have smbclient and smbfs installed.

Hope this helps.

-Dave

---

### Post by FrodoB on 2006-12-09
I think that you are wanting a bit more sophisticated  DHCP server than what your consumer grade D-Link router is going to provide you. 

Do some research on the  web, I suspect that the only way to do this with the D-link is to assign a static address to the file server.

In larger corporations, the DCHP server will let you assign a particular IP address to an ethernet device's MAC identifier, but even then static address are usually assigned to server as they need to be accessed even if the DHCP server goes down for some reason.

A Linux DHCP server could be setup to do what you want and then you would disable the DHCP server in your D-Link router, but the Linux machine would have to be up all of the time to provide the service.

An embedded solution could be to install one of the Linux open source projects on a Linksys WRT54GL and configure its DHCP server to get what you want.

Maybe someone will come along with some better suggestions.

Best of luck.

---

### Post by PryGuy on 2006-12-10
Thanks for the explanations, but one question, why do we enter the computer name during the installation then?

---

### Post by dbott67 on 2006-12-10
For things like DNS.  Although *some* people may not need it, the fact of the matter is that it's an intergrated part of the way DNS (and other networking services) work.

-Dave

---

### Post by mayonaise15 on 2006-12-10
> **PryGuy said:**
> Yet I've got two Wi-Fi notebooks and that's very important for them. I don't want to get back to static IPs.:mrgreen: Is there a way to make it work?

You can have a mixed static and dynamic addressing system.  Let's assume that your router's IP is 192.168.0.1/24.  If you set the D-Link to start handing out IPs at 192.168.0.100, any device requesting a dynamic IP will get an IP at or above 192.168.0.100.  That means that you are able to do whatever you want with the IP's between 192.168.0.2 and 192.168.0.99.  You could give your file server a satitic IP of 192.168.0.50 and then put that mapping into your /etc/hosts file.

Good Luck

---

### Post by PryGuy on 2006-12-10
Thanks! But please repeat in two words again what do I need in theory to start pinging DHCP machines by their names? A DHCP server that supports it? I have a feeling that my D-LINK server supports WINS only, many companies do not care about the Linux support nowadays. :(

---

### Post by dbott67 on 2006-12-10
I doubt your D-Link has a WINS server built-in, but if you plan on using DHCP, you'll need to do the following to any computer running ubuntu:

1. Install **smbclient, smbfs** and **winbind**
```
sudo apt-get install smbfs smbclient winbind
```
2. Edit the **/etc/nsswitch.conf** file
```
sudo gedit /etc/nsswitch.conf
```
3. Look for the following line (or similar):
```
hosts:          files dns mdns
```
4. Add the word [COLOR="Red"]wins[/COLOR]:
```
hosts:          files dns mdns [COLOR="Red"]wins[/COLOR]
```
5. Restart computer
6. Ping away, my friend.

-Dave

Okay, that was a lot more than 2 words.

---

### Post by koenn on 2006-12-10
> But please repeat in two words again what do I need in theory to start pinging DHCP machines by their names?
2 words ? a name server

thats a server that translates names to ip adresses (or vice versa).
could be a DNS server or a WINS server (as explained earlier in this tread).

The part you're missing is : if a **DHCP** server is handing out the ip addresses, then how is the **name server** going to know which host got what IP address. 
Fortunately, the hosts as well as the DHCP server can be configured to give that information to the name server, and the name server most be configured to accept it.

---

### Post by PryGuy on 2006-12-11
So it can be DNS or WINS or even both? right? There is no difference between DNS and LAN DNS?

---

### Post by dbott67 on 2006-12-11
> **PryGuy said:**
> So it can be DNS or WINS or even both? right? There is no difference between DNS and LAN DNS?

I would choose WINS for a smaller network; it's easy to setup and the client PCs self-register, menaing that you don't have to do anything once you've installed it.  Each time a PC turns on, it announces it's name & IP to the WINS server and the WINS server registers the IP-to-name mapping.  Then, you are able to browse by name instead of IP.

**_Some useful commands & tips:_**

1. **Firewalls** - make sure that any software firewalls are configured to allow samba (ports 137-139, 445)

2. Set WINS server in XP (see attached screenshot):
   - Open your Network Configuration
   - select your adapter
   - highlight TCP/IP
   - click PROPERTIES
   - click ADVANCED
   - select the WINS tab
   - enter your Ubuntu IP address

3. **smbtree**
```
dbott@thedrake:~$ smbtree
Password:
WORKGROUP
        \\THEDRAKE                      thedrake server (Samba, Ubuntu)
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\dbott
                \\THEDRAKE\print$               Printer Drivers
        \\OMEGA-XP
        \\NAS-160GB
                \\NAS-160GB\IPC$
                \\NAS-160GB\Videos
                \\NAS-160GB\Music
                \\NAS-160GB\Archive
                \\NAS-160GB\Data
                \\NAS-160GB\PUBLIC

```

DNS is a bit tougher to setup and manage, and is generally reserved for larger networks.

Technically, there's no difference between the DNS service they provide, however, a mis-configured internal DNS server can cause all sorts of problems.

Output from PING:
```
dbott@thedrake:~$ ping nas-160gb -c4
PING nas-160gb (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=32 time=0.228 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=32 time=0.232 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=32 time=0.232 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=32 time=0.236 ms

--- nas-160gb ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 0.228/0.232/0.236/0.003 ms

dbott@thedrake:~$ ping omega-xp -c4
PING omega-xp (192.168.1.105) 56(84) bytes of data.
64 bytes from 192.168.1.105: icmp_seq=1 ttl=128 time=297 ms
64 bytes from 192.168.1.105: icmp_seq=2 ttl=128 time=8.81 ms
64 bytes from 192.168.1.105: icmp_seq=3 ttl=128 time=442 ms
64 bytes from 192.168.1.105: icmp_seq=4 ttl=128 time=257 ms

--- omega-xp ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3010ms
rtt min/avg/max/mdev = 8.816/251.457/442.112/156.040 ms

dbott@thedrake:~$ ping thedrake -c4
PING thedrake (127.0.1.1) 56(84) bytes of data.
64 bytes from thedrake (127.0.1.1): icmp_seq=1 ttl=64 time=0.063 ms
64 bytes from thedrake (127.0.1.1): icmp_seq=2 ttl=64 time=0.057 ms
64 bytes from thedrake (127.0.1.1): icmp_seq=3 ttl=64 time=0.058 ms
64 bytes from thedrake (127.0.1.1): icmp_seq=4 ttl=64 time=0.057 ms

--- thedrake ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.057/0.058/0.063/0.009 ms
dbott@thedrake:~$
```

---

### Post by koenn on 2006-12-11
> **dbott67 said:**
> Technically, there's no difference between the DNS service they provide, ...
***Technically*** there's all sorts of differences, but both provide the same functionality : mapping names to network addresses.

But apart from that you're right - for a small home network WINS is probably easier, and good enough.

---

### Post by dbott67 on 2006-12-11
> **koenn said:**
> ***Technically*** there's all sorts of differences, but both provide the same functionality : mapping names to network addresses.

But apart from that you're right - for a small home network WINS is probably easier, and good enough.

I guess that's what I meant! :)

One of my favourite lines from Frasier:
> Frasier:
Hello Doug, this is Dr. Frasier Crane.  I'm listening.

Doug: 
[v.o:] Look, it's about my mother.  She's getting on now and 
         she doesn't have much of a life.  And she doesn't want to do 
         anything or go anywhere and she literally hangs around the 
         house all day.  I mean, it's very frustrating...

Frasier: I'm sorry Doug, can we just go back a second?  You said your 
         mother literally hangs around the house.  Well, I suppose 
         it's a pet peeve of mine but I suppose what you mean is that 
         she figuratively &#8220;hangs around&#8221; the house.  To literally hang 
         around the house you'd have to be a bat or spider monkey. 
         Now, back to your problem?
   
Doug: Do you mind if we stop while I tell you my pet peeve?

Frasier: Not at all.
   
Doug: [angry] I hate it when intellectual pinheads with 
         superiority complexes nit-pick your grammar when they come 
         to you for help.  That's what I got a problem with! [hangs 
         up]

Frasier: [happily:] I think what he means is, that is a thing with 
         which he has a problem.  Now it's time for a station break 
         and we'll be right back after a word from our friends at 
         [reads:] "Pizza, Pizza, Pizza." 

---

### Post by PryGuy on 2006-12-12
Thanks friends! I think I see it now...

---

### Post by koenn on 2006-12-12
> ... 
One of my favourite lines from Frasier:
Quote: ...

:) 

But still ... 
(yeah, I got a thing about accurate wording. Probably comes from editing config files and writing scripts - they tend to stop working if one's choice of words is not sufficiently accurate. ;) )

---

### Post by dbott67 on 2006-12-12
> **koenn said:**
> :) 

But still ... 
(yeah, I got a thing about accurate wording. Probably comes from editing config files and writing scripts - they tend to stop working if one's choice of words is not sufficiently accurate. ;) )

I agree... I'm guilty of it myself.  :)

Whenever I correct someone, that line from Frasier is the first thing that pops into my head!

---

