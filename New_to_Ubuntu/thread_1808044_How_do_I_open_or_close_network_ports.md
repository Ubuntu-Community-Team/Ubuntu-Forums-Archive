---
title: "How do I open or close network ports"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Ditchdoc7893 on 2011-07-19
Hello all!  I'm trying to find out how to open or close certain ports.  Better yet, I'd also like to know if there is a way to see which ones are open, closed, etc.  Any help appreciated!  Thanks!

---

### Post by haqking on 2011-07-19
> **Ditchdoc7893 said:**
> Hello all!  I'm trying to find out how to open or close certain ports.  Better yet, I'd also like to know if there is a way to see which ones are open, closed, etc.  Any help appreciated!  Thanks!

rather than just tell you the parameters and such i will encourage you to use the man pages.

the command you want to lookup is netstat and fuser

however on a default install there are no services listening on any ports and so no ports are "open" per se

---

### Post by doas777 on 2011-07-19
start with this. it will show you all listening ports (ports someone can connect to) and the application that is listening on that port:
```
sudo netstat -ntlup
```ignore the ports that are bound to internal address 127.0.0.1. they cannot be contacted from the outside. only those listening on 0.0.0.0 are externally accessible.

ubuntu ships with NO open network ports, but ports are opened by applications so if you have installed or enabled network services (network file sharing, web servers, ssh, remote desktop, etc), then you may have open ports.

ubuntu ships with a firewall config tool called ufw (the gui is called gufw and can be found in software center). remember, g/ufw are just configuration tools. once you set somthing with them, the setting gets saved and you can close the window. you do not need to run gufw on login to have your firewall work correctly with all your rules.

that said most people would not really need a firewall on their system. if you have a home router, you are usually safe enough, unless you forward ports through it, or allow upnp applications.

---

### Post by Ditchdoc7893 on 2011-07-19
To be honest, the reason I asked this particular question was specifically for running ushare and getting it to work with xbox360 (which is in itself is a pain in the *** and doesn't play well with others).  I am able to use PS3 mediashare without any problems and also ushare without any problems with the PS3.  I'm trying to figure out why I can't get the xbox to play nice.

---

### Post by foxmulder881 on 2011-07-19
The easiest way is to use ufw.

For more information, check out the man pages using the following command.

```
man ufw
```

---

### Post by doas777 on 2011-07-19
> **Ditchdoc7893 said:**
> To be honest, the reason I asked this particular question was specifically for running ushare and getting it to work with xbox360 (which is in itself is a pain in the *** and doesn't play well with others).  I am able to use PS3 mediashare without any problems and also ushare without any problems with the PS3.  I'm trying to figure out why I can't get the xbox to play nice.
so are you trying to determine if the port on the xbox is open?
if so, the easiest way is to use telnet:
```
telnet remoteIPorHostName portnumber
```
substituting hostname and portnumber with appropriate values.

if the port is open, you will see:
```

user@serverbox:~$ telnet serverbox 8080
Trying 127.0.1.1...
Connected to serverbox.
Escape character is '^]'.


```
just hit enter a couple times to exit telnet.

if the port is not open however, you will see somthing like:
```
telnet: Unable to connect to remote host: Connection refused
```

---

### Post by Ditchdoc7893 on 2011-07-19
I'm not having much luck with that.

---

### Post by doas777 on 2011-07-19
another (GUI) method to get this info is Zenmap. its in software center.
use it to scan the remote host, and it will tell you what ports are open. you should select an intensive scan if the port is above 1024.
[http://nmap.org/zenmap/](http://nmap.org/zenmap/)

---

### Post by mcduck on 2011-07-20
> **Ditchdoc7893 said:**
> To be honest, the reason I asked this particular question was specifically for running ushare and getting it to work with xbox360 (which is in itself is a pain in the *** and doesn't play well with others).  I am able to use PS3 mediashare without any problems and also ushare without any problems with the PS3.  I'm trying to figure out why I can't get the xbox to play nice.

In that case, unless you have yourself set up a firewall, the problem isn't likely to be on the Ubuntu computer but in your router's settings instead.

Like others have already said, the default Ubuntu setup doesn't have any running firewall so there isn't anyhting restricting network traffic. (This is safe, as the default install also doens't have any running services that would listen for incoming network connections, so a firewall would serve no purpose at all.) Furthermore, the ports are only open if you install some server software that listens for incoming connections, in which case you'd either actually want the server to be accessible form the Internet, or should be able to limit it's connectivity from the server's configuration. So a firewall would only be required if you had a server app that lacks the options for configuring who can access it.

---

### Post by isa.dsouza on 2012-10-02
A quick check shows this

isa@isa-eMachines-E725:~$ sudo nmap -p1-65535 -sV -sS -O 192.168.1.1
[sudo] password for isa:

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-10-02 20:42 IST
Nmap scan report for 192.168.1.1
Host is up (0.0012s latency).
Not shown: 65532 closed ports
PORT      STATE SERVICE VERSION
80/tcp    open  http?
1900/tcp  open  upnp?
49152/tcp open  unknown

so I have tried this,

isa@isa-eMachines-E725:~$ sudo netstat -ntlup
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2035/apache2    
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      3117/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      591/cupsd       
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      1076/postgres   
udp        0      0 127.0.0.1:53            0.0.0.0:*                           3117/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3114/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           573/avahi-daemon: r
udp        0      0 0.0.0.0:49901           0.0.0.0:*                           573/avahi-daemon: r
udp6       0      0 :::47534                :::*                                573/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                573/avahi-daemon: r

results from my firewall

isa@isa-eMachines-E725:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere (v6)

My question is that if the firewall shows port 22 is open and nmap shows that there are 3 other ports are in use. What ports are actually being used?

can I get some info in this regards as to what ports are used for conecting to the web and what ports are used by hackers etc?

---

### Post by Bufeu on 2012-10-02
As doas777 said; Ubuntu ships with NO open network ports (the default mode is stelth). While installing applications that need Internet access, they opens the ports which is needed to communicate.
If you want to have a good firewall, take a look at **ufw**. There's also a GUI application to ufw, called **gufw**.

---

### Post by Morbius1 on 2012-10-02
@isa.dsouza

I can tell you what the data you presented in your post tells me:

ufw tells me you created a rule to allow port 22 access. 

nmap tells me that no one is listening on port 22 so you either don't have openssh-server installed or the ssh service is not running so there's nothing to allow.

[COLOR=Blue]**EDIT**[/COLOR]: Remember that ufw / gufw are not firewalls - they are rules generators.

---

### Post by isa.dsouza on 2012-10-07
Thank you to [Morbius1]("http://ubuntuforums.org/member.php?u=982144")

I ran this command today to deny access to port 22.

isa@isa-eMachines-E725:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     DENY        Anywhere
22/tcp                     DENY        Anywhere (v6)

I always appreciate answers and this was very helpful.  Just wonder whether Morbius1 can help me to understand this screenshot, taken yesterday. 

Regarding 10104/rhythmbox, listening. cannot understand how rythmbox can listen?

I am a newbie and just want to keep a low profile here in ubuntu as windows is really more vulnerable & at least hoping for 99.99% security of my data really.

---

### Post by DuckHook on 2012-10-07
As other posters have noted, Ubuntu is awfully safe right out of the box with no open ports unless a program is installed that needs to open such ports. Denying port access is viable so long as you know (and remember) why you closed them and can reopen them in the event that an app needs access.

The bigger security exposure for most people is actually browser related. I feel it is more important to disable all scripting and accept only selected cookies in my browser than to close off all ports. If you have a router, then between its firewall and the already naturally hardened state of Ubuntu, you should be covered on the port side.

---

### Post by isa.dsouza on 2012-10-07
I will be keeping track of all this. I have screenshots and other notes to fall back on. Plus I also have his forum in case I mess up.

I trust the OS, Ubuntu is very powerful and clean, I am learning every day. I use bleachbit to clean up Firefox and the rest of the system.   No Script & AdBlock is also enabled in Firefox. :)

---

### Post by Morbius1 on 2012-10-07
> **isa.dsouza said:**
> Just wonder whether Morbius1 can help me to understand this screenshot, taken yesterday. 

Regarding 10104/rhythmbox, listening. cannot understand how rythmbox can listen?
Not an expert of rhythmbox but it's supposed to be an iTunes clone isn't it? If so then it's acting as a server to supply data ( music ) to a variety of clients. It will use avahi ( aka zeroconf - bonjour ) for server discovery on port 5353 and use Apple's DAAP port 3689 for actual file transfer.

If you were to build Linux from the ground up from it's component parts not a single port would be open. You wouldn't be able to do much however so you start adding things like dhcp so you can get an ip address and access the network - port 68 opens up. You have a printer so you install CUPS server - port 631 opens up. Want to transfer files to a Windows/OSX/Linux home network so you install Samba - ports 139,445,137,138 open up. Rhythmbox bring with it it's own port requirements.

---

