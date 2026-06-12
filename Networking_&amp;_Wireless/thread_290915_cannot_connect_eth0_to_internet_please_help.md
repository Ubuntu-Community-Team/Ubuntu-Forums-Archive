---
title: "cannot connect eth0 to internet please help"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by timvets on 2006-11-01
can anyone please help me connect to the internet with the following hardware:
-Clevo 2700c ('speed')laptop, with a SiS900 PCI Fast Ethernet built-in card
-a D-Link 10/100 fast ethernet switch named DES1005D
-a modem provided by internet provider
I tried all kinds of things for several hours now...

note: Yesterday I got it connected to the internet with exactly the same hardware, dont know what changed actually...
note2: connecting with windows was never a problem.
note3: rather new to linux, especially when it comes to network configuration...

info on connection :
Connection Properties (the window that appears when clicking on the network icon in the toolbar (?))
'General' tab:
Name: lo
Status: idle
Activity:
Received: 93 packets
Sent: 93 packets
'Support' tab:
Address: 127.0.0.1
Subnet Mask: 155.0.0.0
Network Device:
Type: Local Loopback
Address: 00:00:00:00:00:00

when I highlight the 'lo' on the 'General' tab and type 'eth0' instead, I get:
Name: eth0
Status: idle / Receiving (alternating between these two)
Activity:
Received: 103 packets
Sent: 17 packets
'Support' tab:
Type: Ethernet
Address: 00:90:F5:0A:00:EA

when I click configure I get the Network Settings window.

I click on Ethernet connection and then on Properties:
'Enable this connection' is activated
Connection settings:
Configuration DHCP
IP address (blank)
Subnet mask (blank)
Gateway address (blank)

Default gateway device is empty, when I click on it I can select 'eth0' only, I do so and click ok

open Firefox, try to load google page, still:
'Server not found'

ifconfig gives info about eth0 and lo
dont know what lines are relevant, and since ubuntu isnt online its kind of hard to copy paste the output here.
tried sudo ifconfig eth0 up
no complaints from terminal, no change to situation.


any help please ?

thanks!

---

### Post by matthewstory on 2006-11-01
the lo device is a local loopback device . . . it's a method for Ubuntu to talk to itself, it never actually goes out over a network, it just is a way for Daemons like X-Server to talk to themselves more easily.  So lo will never have a default gateway, and has nothing to do with your inability to connect to the network.  Take a look at your /etc/network/interfaces file, it should look like this:

auto eth0
iface eth0 inet dhcp

try to bring it up with 

sudo ifup eth0

This should be followed by a series of DHCP requests echoed into the terminal, if this does not happen there's a problem with your DHCP set up.

if it goes through, you're right to

sudo ifconfig eth0

An ip address should be displayed, probably something on the internet at large if you're not using a router (a.k.a not 192.168.x.x) if that's not happening than you've got a dhcp problem again.

otherwise, see you can check it with:

ping [www.zedzone.com](www.zedzone.com)

If this doesn't work, it's probably an issue with you being allowed to connect through the modem . . . e.g. an ISP password issue.

Do you have to have a username/password to connect to the internet . . . and if so, is this handled by the modem issued to you, or is does it have to be handled by your box?

---

### Post by timvets on 2006-11-02
I remember some password/username being entered by the employee of the internet provider when activating the line.
I think it was meant for when editing my personal page, email settings etc...
I could however connect all (windows and some ubuntu) computers without entering any password.
I wouldn't know where too look for the passwords and where to fill them in on ubuntu.


~$ sudo ifup eth0
ifup: interface eth0 already configured

~$ ping [www.zedzone.com](www.zedzone.com)
ping: unknown host [www.zedzone.com](www.zedzone.com)

/etc/network/interfaces now looks like:
auto eth0
iface eth0 inet dhcp

thanks
tim

---

### Post by Iowan on 2006-11-02
Try
```
sudo dhclient
```
Check **ifconfig** to see if it has an inet address (not just an inet6).

---

### Post by timvets on 2006-11-02
ifconfig shows no inet address for eth0,
only inet6 addr: ...
'lo' has :
inet addr: 127.0.0.1 Mask:255.0.0.0
sudo dhclient returns several lines like:
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
...
and then :
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

thanks
tim

---

### Post by Iowan on 2006-11-07
It wasn't my intent to drop you - I got sidetracked with some issues of my own.   I had a reason for asking if the machine got an inet address, but now don't remember exactly why - except IPV6 can get in the way.  You might try disabling IPV6.  Information is available via **search**, but I'll see if I can find a few links for you.

Here's one:
[http://ubuntuforums.org/showthread.php?t=292661]("http://ubuntuforums.org/showthread.php?t=292661")

---

### Post by MarioT on 2006-11-08
After boot, see what do you have in /etc/resolv.conf
Should be something like
nameserver ip_address
nameserver ip_address_2

If it's empty you are not getting DNS server from your ISP. I have the same problem. 
To check whether you connection is working, type in firefox 
[http://64.236.16.116/](http://64.236.16.116/) - if you get connected to [www.cnn.com](www.cnn.com) you connection is woring just fine.
Now, try to restart network
sudo /etc/init.d/networking restart  - now, you get DNS servers in resolv.conf.
After reboot the same problem appears, does it?

I don't know how to solve the problem to get DNS automaticly from  
ISP (ok, I now, you can put sudo /etc/init.d/networking restart in rc.local) but there's workaround.

Start 
sudo pppoeconf, when it ask to get DNS form ISP say no,
sudo gedit /etc/dhcp3/dhclient.conf 
uncomment line domain-name-servers and put your DNS (ask ISP for them or you can see them in resolv.conf after network restart). In line requests remove domain-name-servers. Save file and reboot. It should work.

Please let us know whether it's working or not.

Mario

---

### Post by MarioT on 2006-11-08
> **MarioT said:**
> 
Start 
sudo pppoeconf, when it ask to get DNS form ISP say no,
sudo gedit /etc/dhcp3/dhclient.conf 
uncomment line domain-name-servers and put your DNS (ask ISP for them or you can see them in resolv.conf after network restart). In line requests remove domain-name-servers. Save file and reboot. It should work.


I forgot to say, you should run sudo pppoeconf and when it ask you to get DNS automaticly from ISP say no.

Mario

---

