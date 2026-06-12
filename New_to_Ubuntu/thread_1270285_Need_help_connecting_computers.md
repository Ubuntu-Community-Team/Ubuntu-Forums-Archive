---
title: "Need help connecting computers"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by the.dark.lord on 2009-09-19
I need to connect two computers via an ethernet cable, both computers have ethernet ports. I understand this can be done configuring the IP addresses or something-but I can't figure out what to do, can someone help? Both computers run Ubuntu.

Thanks!

---

### Post by mikeyphi on 2009-09-19
Assuming both computers have unused network cards attached to the ethernet ports - do the following:
Open Network settings (you need to enter password)
Select 'Wired Connection'
select 'Properties'
deselect 'Roaming mode'
in Configuration - select 'static IP address'
in IP address - enter '192.168.50.10'
in subnet mask - enter '255.255.255.0
in gateway address - enter '192.168.0.1'

select OK

Same on second computer except IP address is '192.168.50.11'

---

### Post by mapes12 on 2009-09-19
> **the.dark.lord said:**
> I need to connect two computers via an ethernet cable, both computers have ethernet ports. I understand this can be done configuring the IP addresses or something-but I can't figure out what to do, can someone help? Both computers run Ubuntu.

Thanks!It goes like this for me. You may need a cross over cable:

I guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved.

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```Is a meta package and will install both applications. Or you can search for it in Synpatic and install it from there.

2.) Go to the machine you want to connect to. You need to find the machines IP address, so in Terminal:

```
ifconfig
```

This should give you an output just like this one

> eth0 Link encap:Ethernet HWaddr 00:50:da:e0:67:74
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1732 (1.7 KB) TX bytes:1732 (1.7 KB)

wlan0 Link encap:Ethernet HWaddr 00:11:50:dd:a9:16
inet addr:**192.168.1.68** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1661090 (1.6 MB) TX bytes:342426 (342.4 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).

So, in my case the address would be 192.168.1.68

3.) Access the computer
Now, when you want to access a computer from the other, go to places>connect to server.
- Choose SSH as the "service type" from the drop down list
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This is the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK

You may get a message about keys on first time connection. Just OK it

You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

Hope this helps.

---

### Post by Lemuel111 on 2010-01-17
I am looking at connecting my desktop pc which is running Ubuntu 9.10 to my laptop which is runing xp via a crossover cable (if I can get my wireless sorted I would like to ditch xp on the laptop!). The reason being I need to get connected to the internet to set up my wireless on my desktop (wired not possible either). My laptop can connect to the internet. Is this possible and if so how do I do it?
Thanks.

---

### Post by jflaker on 2010-01-17
do you have a router available, even if you borrow it?

---

### Post by Iowan on 2010-01-17
Sounds like you need to set up connection sharing on XP, then use it as a gateway for Ubuntu.

---

### Post by Lemuel111 on 2010-01-18
> **jflaker said:**
> do you have a router available, even if you borrow it?


I have a wireless router which is accessable via my laptop with xp.

---

### Post by Lemuel111 on 2010-01-18
> **Iowan said:**
> Sounds like you need to set up connection sharing on XP, then use it as a gateway for Ubuntu.


How do I set it up? Thanks

---

### Post by pirateghost on 2010-01-18
> **Lemuel111 said:**
> How do I set it up? Thanks
if you have a router, there is no need to set up internet connection sharing in xp.  use the router for what it is designed for.  sharing network resources

plug the 2 computers into the router and BAM! you are on the same network.  if your router is handing out DHCP then there should be nothing you need to configure for ip addresses.

by the way, you can connect to your router configuration page WITHOUT xp, just open firefox and type in the router's IP address and log in.

---

### Post by Lemuel111 on 2010-01-20
> **pirateghost said:**
> if you have a router, there is no need to set up internet connection sharing in xp.  use the router for what it is designed for.  sharing network resources

plug the 2 computers into the router and BAM! you are on the same network.  if your router is handing out DHCP then there should be nothing you need to configure for ip addresses.

by the way, you can connect to your router configuration page WITHOUT xp, just open firefox and type in the router's IP address and log in.


The router is in the hall downstairs and the computer upstairs. I don't have any cables long enough for both laptop & desktop to connect to the router downstairs. The laptop currently has wireless connection to the router though but not the Ubuntu desktop.

---

### Post by Swab on 2010-01-20
Here is a guide to setting up Internet Connection Sharing on Windows XP:

[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

In your case the wireless connection will be the one you need to share.

---

### Post by Lemuel111 on 2010-01-20
> **Swab said:**
> Here is a guide to setting up Internet Connection Sharing on Windows XP:

[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

In your case the wireless connection will be the one you need to share.

The first part of this guide is easy enough (the host computer) but how do you set up the client part in Ubuntu because this guide is based on someone using Windows?

Thanks

---

### Post by John Bean on 2010-01-20
> **Lemuel111 said:**
> The router is in the hall downstairs and the computer upstairs. I don't have any cables long enough for both laptop & desktop to connect to the router downstairs. The laptop currently has wireless connection to the router though but not the Ubuntu desktop.

Add an inexpensive wireless card to the desktop machine. This is by far the best way to move forward from your present situation.

---

### Post by Lemuel111 on 2010-01-20
> **John Bean said:**
> Add an inexpensive wireless card to the desktop machine. This is by far the best way to move forward from your present situation.

I have a Belkin USB G+ wireless card which I can't get working. I then bought a D-link G122 wireless card which I was told would work 'out of the box'. However I can't get this to work either. Any suggestions?

---

### Post by Swab on 2010-01-21
> **Lemuel111 said:**
> The first part of this guide is easy enough (the host computer) but how do you set up the client part in Ubuntu because this guide is based on someone using Windows?

Thanks

There shouldn't be anything to setup on the Ubuntu machine, just plug it in.

---

### Post by Lemuel111 on 2010-01-21
> **Swab said:**
> There shouldn't be anything to setup on the Ubuntu machine, just plug it in.

I'm plugged in but nothing is showing on my Ubuntu machine.

---

### Post by Swab on 2010-01-22
> **Lemuel111 said:**
> I'm plugged in but nothing is showing on my Ubuntu machine.

While the ethernet cable is plugged in can you open up a terminal window and post the output of the command ifconfig  ?

As I understand it, the windows machine should be assigning you an IP address via DHCP.

---

