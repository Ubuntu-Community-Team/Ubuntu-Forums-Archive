---
title: "Lost connection to internet. (DHCP?)"
date: 2005-10-29
forum: Networking &amp; Wireless
---

### Post by rambash on 2005-10-29
Running Ubuntu 5.04 The Hoary Hedgehog. :KS 

I've had my server down for about one and a half month and when i started it again it could not connect to the internet. I tried looking in the configuration but i could not fix it, i changed network card but it didnt work. I even installed Ubuntu 5.04 Hoary on another computer without any success.:mad: 

Ubuntu has previously been all satisfactory and it has never been any trouble for me.

I do believe that it is some sort of DHCP error but i do not have much knowledge on the subject.

Some information:
My gateway is: 192.168.0.1
My ip is: 192.168.0.5
I do not want to use a STATIC IP

With the command "lspci" i get the output:
0000:00:04.0 Ethernet Controller: nVidia Corporation Nforce2 Ethernet Controller (rev a1)

With the "ifdown eth0" command i get:
sit0: unknown hardware adress type 776
sit0: unknown hardware adress type 776
Listening on LPF/eth0/00:10:dc:99:f0:22
LPF/eth0/00:10:dc:99:f0:22
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
NO DHCPOFFERS recieved.
No Working leases in persistent database - sleeping

With the "ipdown eth0" i get:
sit0: unknown hardware adress type 776
sit0: unknown hardware adress type 776
Listening on LPF/eth0/00:10:dc:99:f0:22
LPF/eth0/00:10:dc:99:f0:22
Sending on Socket/fallback

With ifconfig i get:
eth0    Link encap:Ethernet  HWaddr 00:10:DC:99:F0:22
          inet6 addr: fe80::210:dcff:fe99:f022/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:216198 (211.1 KiB)
          Interrupt:22 Base address:0x2000

lo        Link encap:Local Loopback  
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436  Metric:1
          RX packets:107915 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:989046 (9.4 MiB)  TX bytes:989046 (9.4 MiB)
sit0     Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP MTU:1480 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I cant ping anything, i only get this response:
connect: Network is unreachable
I could ping localhost before thought, but not my Internal IP (192.168.0.5) :???: 

Do you know what it could be? Is it the router/modem or did i just do something wrong in Ubuntu? And if its the router or modem could you help me there? Thanks in advance :p 

Ps. I've searched the forums for two days without finding any suitable threads/answers. And lets not forget, there is NOTHING wrong with my net-cable :cool:

---

### Post by audax321 on 2005-10-29
Sounds like a router issue if the fresh install couldn't get an IP either. Is there a windows computer you can try as well? That way you could be sure its not Ubuntu. Anyway, the only thing I can recommend is resetting your router (there is usually a reset button on the router itself) and then setting up your preferences again. By the way, what kind of router do you have. I had a Linksys that died just sitting there and no number of resets could bring it back to life.

---

### Post by mips on 2005-10-29
I would suggest you check out yout network card and router ethernet port. Make sure that the speed/duplex settings match ! Also try setting the ports for full auto negotiation to see what happens.

You are currently transmitting on the Ethernet port but receiving nothing at all. I had a similair problem when I installed Breezy, strange thing is hoary did not have this problem.


[QUOTE=rambash]Running Ubuntu 5.04 The Hoary Hedgehog. :KS 
With the command "lspci" i get the output:
0000:00:04.0 Ethernet Controller: nVidia Corporation Nforce2 Ethernet Controller (rev a1)

With the "ifdown eth0" command i get:
sit0: unknown hardware adress type 776
sit0: unknown hardware adress type 776
Listening on LPF/eth0/00:10:dc:99:f0:22
LPF/eth0/00:10:dc:99:f0:22
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
**NO DHCPOFFERS recieved.**
No Working leases in persistent database - sleeping

With the "ipdown eth0" i get:
sit0: unknown hardware adress type 776
sit0: unknown hardware adress type 776
Listening on LPF/eth0/00:10:dc:99:f0:22
LPF/eth0/00:10:dc:99:f0:22
Sending on Socket/fallback

With ifconfig i get:
eth0    Link encap:Ethernet  HWaddr 00:10:DC:99:F0:22
          inet6 addr: fe80::210:dcff:fe99:f022/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          **[COLOR="Red"]RX bytes:0 (0.0 b)[/COLOR]**  TX bytes:216198 (211.1 KiB)
          Interrupt:22 Base address:0x2000

[/QUOTE]

---

### Post by Cr4z33 on 2005-10-29
Hi.
I'm getting the same problem, but I'm using static IPs.
I've a home LAN with 2 computers:[LIST]
[*]A ZyXEL Prestige 650H-E1 ADSL router (192.168.1.1).[/LIST][LIST]
[*]"Schiavetto" which is the Ubuntu machine placed in the entrance hall (192.168.1.2).[/LIST][LIST]
[*]"Cr4z33" which is the XP machine placed in the library room (192.168.1.3).[/LIST]This network worked flawlessly until I changed my ISP.
For a couple of weeks I've been without connection and as soon I got my new ADSL account Ubuntu is now unable to connect both to the LAN/router and my XP machine and I can't ping anything.
Both machines are connected via LAN cables to ports 1 and 2 of my router.
The network card in the Ubuntu machine is setup like the following:[LIST]
[*]IP: 192.168.1.2
[*]Subnet: 255.255.255.0
[*]Gateway: 192.168.1.1
[*]DNS: 192.168.1.1[/LIST]What's going on? :confused:

---

### Post by rambash on 2005-10-29
> Make sure that the speed/duplex settings match ! Also try setting the ports for full auto negotiation to see what happens.
What do you mean by speed/duplex? And what do you mean with full auto negotiation? Sorry for me being stupid :)

The internet works on windows and i've tried resetting the router and the modem.
I connected the linux computer directly to the modem and it worked so im updating my dist-version from 5.04 to 5.10 as we speak and im hoping that it will fix it. Im using NetGear RP614 with the default firmware and im gonna update it to the latest as soon as my dist-update is done.

EDIT: Okay, i got it to work. This is how i fixed it.
I connected my Ubuntu-computer directly to the modem.
Then i ran theese commands:
apt-get dist-upgrade (Which gave me an error and told me to run "apt-get update")
apt-get upgrade

Then i plugged in everything into the router and upgraded the routers firmware (throught my windows computer) and then i restarted my Ubuntu-computer.
And then it worked :). Thanks alot you guys for your help, i really aprechiate it.

I hope this will help anyone else who was similiar problems.

---

### Post by Dardie on 2005-10-30
Rambash,

post your /etc/network/interfaces...

---

### Post by Epimetheus on 2006-01-15
I have the same problem, could anyone sum up the solution for me?
Am i supposed to:
upgrade my router firmware and then what?

[EDIT] Btw, i have a RP614v3 router with firmware 6.1 (got it via the customer support) [/EDIT]

---

### Post by Cr4z33 on 2006-01-15
[quote=Epimetheus]I have the same problem, could anyone sum up the solution for me?
Am i supposed to:
upgrade my router firmware and then what?[/quote]
I solved installing again Ubuntu and now for some reasons everything is working fine. :confused:

---

### Post by Epimetheus on 2006-01-15
[QUOTE=Cr4z33]I solved installing again Ubuntu and now for some reasons everything is working fine. :confused:[/QUOTE]

Well i tried that but got the same trouble again. And the biggest problem is that i didnt got the actuall problem until the day after i reinstalled and tried booting the computer again.

---

### Post by Cr4z33 on 2006-01-15
[quote=Epimetheus]Well i tried that but got the same trouble again. And the biggest problem is that i didnt got the actuall problem until the day after i reinstalled and tried booting the computer again.[/quote]
Be sure to make the installation on a clean HD.
Make a backup of your personal files first.

---

### Post by Epimetheus on 2006-01-15
yeah i did that too... i recently noticed that if i reboot the router it works alright too... (currently operating in linux)

---

### Post by stream303 on 2006-01-17
Looks like dhcp client is picking up the DNS server inside your router instead of the nameservers of your isp:

> The network card in the Ubuntu machine is setup like the following:[LIST]
[*]IP: 192.168.1.2
[*]Subnet: 255.255.255.0
[*]Gateway: 192.168.1.1
[*]DNS: 192.168.1.1[/LIST]What's going on? :confused:

If you know the real dns addresses of your isp's nameservers, you can edit **/etc/dhcp3/dhclient.conf** and place the correct dns addresses there with one line.

Just before the request line in /etc/dhcp3/dhclient.conf, add this (using the real addresses of course):

**supersede domain-name-servers 123.45.678.90;**

(for just one known nameserver)

OR, if you know the primary and backup:

**supersede domain-name-servers 123.45.678.90, 123.45.890.12;**

(just separate with a comma and place a semicolon at the end)

Now either reboot to get a new lease, or bring your ethernet interface down and up again:

sudo ifdown eth0
sudo ifup eth0

---

### Post by Killerbird on 2006-01-19
I am having pretty similar problems as Rambush in my dorm room aswell.  I have no access to the routers and I'm not sure if this is mine or ubuntu's or the school's problem...  

When booting, the startup screen tells me that it failed to connect with the dhcp interface.  When that happens I can't get onto the network.  Sometimes on startup, my computer will connect to the network, and then after a while will lose the connection.  The windows machine doesn't seem to be having any problems with it.

---

### Post by annettekusma on 2006-04-30
I have a very similar problem here; I don't have a home network, well not that I know of, just two seperate computers...

I had one box with Ubuntu and one with FC3 and they were both connected to the internet with a D-link Dl-604 router and an Zyxel 600-series ADSL modem and it all worked fine except that I had to reconfigure my ethernet connection in Ubuntu after every log on/reboot.

Then I changed ISP and modem (still same brand and series, about one week without internet connection). Since then, only my FC3-box can be connected to the internet. This works through the modem alone or through modem and router (any of the four ports on the router will do fine).

My Ubuntu box simply won't connect anymore though I repeated the same steps as everytime when I had to reconfigure my connection. These steps are:

System -> Administration -> Networking
Connections -> Ethernet connection -> Properties
check Enable this connection
chose DHCP in Configuration-menu
OK
Activate
(OK)

It says 'The interface eth0 is active' but i can't ssh or view any website or ping anything. It times out, or 'network is unreachable'.

I get these results for all of the following situations after all of which I of course restarted computers, router and modem:

Ubuntu box connected through new modem alone
Ubuntu box connected through old modem alone
Ubuntu box connected through router and new modem
Ubuntu box connected through router and old modem
Ubuntu box and FC3 box connected through router and old modem
Ubuntu box and FC3 box connected through router and new modem

I can view the router page and change settings there though I am not sure whether they apply since the last step always is like "click OK to restart router for settings to take place" and I'm not sure what it looks/sounds like when the router restarts, nothing special seems to happen, maybe the lights blink for one nanosecond or so that I can't see it but I rather believe that Ubuntu fails to make the device restart.

Since then I re-installed Ubuntu on that one box and I'm sure it is a worser installation now (a friend helped me last time, but this time I did it alone and I'm quite a newbie to computers) and the problem remains (plus got joined by some exponential blow of new problems).

I was told to check something with ifup wich didn't help or give (a linux sysadmin at work trying to help me) any hints, so, now I'm not quite sure what to do. Since I'm getting through to the router page I assume there is no physical fault with the network card and cables. Since my other box connects readily through the router and modem I assume no physical fault with these divice and cables either.

I read this thread: [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) and hence I post:

c3po@r2d2:~$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok
c3po@r2d2:~$

c3po@r2d2:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:08:A1:40:11:6A
          inet6 addr: fe80::208:a1ff:fe40:116a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x7000

c3po@r2d2:~$

Looks like i DON'T have an IP-address. Router's IP-address, negative as well:

c3po@r2d2:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
c3po@r2d2:~$

I renamed my ipv6-driver as suggested in the thread. (then I didn't get the line with 'inet6 addr:' for ifconfig eth0).


Feel free to prompt me for more details and info on my system, but when asking for info found in files, pls give me a hint where to find them! =) Thanks beforhand!

---

### Post by mips on 2006-05-01
[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

Have a look at the above thread. Also see what happens if you assign the IP information statically.

---

### Post by Slim Odds on 2006-05-01
[QUOTE=stream303]Looks like dhcp client is picking up the DNS server inside your router instead of the nameservers of your isp:[/QUOTE]

Most routers provide automatic DNS forwarding. This means that the gateway address (usually 192.168.0.1 or 192.168.1.1, etc.) is a valid DNS server address. This is the way that my Netgear WGR614 works.

---

