---
title: "connecting to Ethernet with GNOME"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Rowan Berkeley on 2009-02-19
Hi, I have just joined this Forum and this is my first message. I have acquired a LinuxCertified LC2430S with Ubuntu (GNOME) pre-installed, and I am trying to connect it via Ethernet to a British Telecom HomeHub, which is a router having two Ethernet connections (thus I can talk to you on a Windows machine via the other Ethernet connection on the Hub, while experimenting with the Linux connection).

When I plug both machines into the Hub Ethernet ports and switch them on, the Hub does not 'see' the Linux machine, and the Linux machine does not 'see' the Hub.

I have consulted the manuals online, and it seems all routes lead me back to the Network Connections panel, in which the only connection I can see, when the Ethernet cable to the BT HomeHub is plugged in, is 'Point to Point', and nothing happens when I click it. When I tried to connect via a USB port, I saw a button for 'Wired Connection' too, but nothing happened when I clicked that, either. There are also 'unlock' buttons on that panel, but clicking them makes no difference.

'Enable Networking' is ticked. This is certainly a vital check to make.

I tried typing 'sudo ipconfig' in the terminal and got this:

Link encap: Local Loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
inet6 addr:: 1/128 Scope: Host
UP LOOPBACK RUNNING
(and then some MTU, Metric, RX packets, TX packets, errors, bytes, etc.)

In other words, no interfaces at all.

---

### Post by egalvan on 2009-02-19
> **Rowan Berkeley said:**
> Hi, I have just joined this Forum and this is my first message. I have acquired a LinuxCertified LC2430S with Ubuntu (GNOME) pre-installed,

typing 'sudo ipconfig' in the terminal and got this:

Link encap: Local Loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
inet6 addr:: 1/128 Scope: Host
UP LOOPBACK RUNNING
(etc.)

no interfaces at all.

Sounds like you either have no hardware network interfaces, or they are turned off...

Does "lspci" show any network hardware?

And I am assuming you meant "ifconfig" and not "ipconfig" in your original post.

---

### Post by sadaruwan12 on 2009-02-19
> **Rowan Berkeley said:**
> Hi, I have just joined this Forum and this is my first message. I have acquired a LinuxCertified LC2430S with Ubuntu (GNOME) pre-installed, and I am trying to connect it via Ethernet to a British Telecom HomeHub, which is a router having two Ethernet connections (thus I can talk to you on a Windows machine via the other Ethernet connection on the Hub, while experimenting with the Linux connection).

When I plug both machines into the Hub Ethernet ports and switch them on, the Hub does not 'see' the Linux machine, and the Linux machine does not 'see' the Hub.

I have consulted the manuals online, and it seems all routes lead me back to the Network Connections panel, in which the only connection I can see, when the Ethernet cable to the BT HomeHub is plugged in, is 'Point to Point', and nothing happens when I click it. When I tried to connect via a USB port, I saw a button for 'Wired Connection' too, but nothing happened when I clicked that, either. There are also 'unlock' buttons on that panel, but clicking them makes no difference.

'Enable Networking' is ticked. This is certainly a vital check to make.

I tried typing 'sudo ipconfig' in the terminal and got this:

Link encap: Local Loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
inet6 addr:: 1/128 Scope: Host
UP LOOPBACK RUNNING
(and then some MTU, Metric, RX packets, TX packets, errors, bytes, etc.)

In other words, no interfaces at all.

I had the same problem with my new Ubuntu 8.10 installation and I've posted a similar kind of a post and here it is [http://ubuntuforums.org/showthread.php?t=1023564]("http://ubuntuforums.org/showthread.php?t=1023564")

---

### Post by Rowan Berkeley on 2009-02-19
when I typed 'sudo lspci' I got this list of interface controllers:

00.1a.0 USB Controller
00.1a.1 USB Controller
00.1a.2 USB Controller
00.1a.7 USB Controller
...
00.1d.0 USB Controller
00.1d.1 USB Controller
00.1d.2 USB Controller
00.1d.7 USB Controller
...
14.00.0 Ethernet Controller 

I have omitted the other items, but if relevant I can get them

---

### Post by egalvan on 2009-02-19
> **Rowan Berkeley said:**
> typed 'sudo lspci' got this list of interface controllers:

...
...
**14.00.0 Ethernet Controller **

I have omitted the other items, but if relevant I can get them

Is that ALL of the information it gave on the internet controller?

Here is an example of mine...

```
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
```
There is information missing from yours.
WHY it's missing may help us solve this.

---

### Post by Rowan Berkeley on 2009-02-19
no, it gave the make and model number, but I should have thought that was irrelevant.

---

### Post by tarps87 on 2009-02-19
Can you post the contents of the file
/etc/network/interfaces
```

gedit /etc/network/interfaces

```

could you also check it the card is listed when you run the command
```
lshw -C network
```

---

### Post by Simian Man on 2009-02-19
I have found that NetworkManager often crews up wired connections.  See that it isn't controlling your ethernet.

The simplest way would be to  try this in a terminal:
```

sudo /etc/init.d/NetworkManager stop
sudo /etc/init.d/network restart

```

This should at least give you a descriptive error if it doesn't work.

---

### Post by egalvan on 2009-02-19
> **Rowan Berkeley said:**
> no, it gave the make and model number, but **I should have thought that was irrelevant**.

Sadly, under Linux, it is often relevant.

Some hardware manufacturers are not Linux-friendly.

Hardwired networks cards are fairly well supported, but there are some that are not...

---

### Post by stalkingwolf on 2009-02-19
You said that you have 2 ports, one is plugged into your Win box and is working, the other does not appear to be.   Plug the cable from the Win box into your Ubuntu box.  If it works you either have a bad cable or bad port.

In this case plug the cable that you used for the Ubuntu box into the
Win port.  If it works you have a bad port on the hub.  If not plug the
win cable into the Ubuntu port.  If it works its a bad cable.

Plug everything back in as you had it. If it still does not work and you have eliminated the router and cable as possibilities.  You ethernet card may be bad.

Being that this computer came pre-installed with Ubuntu I find it hard to
believe that it has an incompatible card ( although it could happen), But a
card that has flaked out is entirely possible.

---

### Post by tarps87 on 2009-02-19
> **Rowan Berkeley said:**
> 
I tried typing 'sudo ipconfig' in the terminal and got this:

Link encap: Local Loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
inet6 addr:: 1/128 Scope: Host
UP LOOPBACK RUNNING
(and then some MTU, Metric, RX packets, TX packets, errors, bytes, etc.)


On the basis that the command use was
```
sudo ifconfig
```
It is possible that the interface is missing from the interface file. Even with no cable connect the wired interface should show up

---

### Post by rgb96 on 2009-02-19
> **tarps87 said:**
> It is possible that the interface is missing from the interface file. Even with no cable connect the wired interface should show up

Yeah, we need to see the contents of that file.

You can get it with:
```
sudo gedit /etc/network/interfaces
```

---

### Post by Rowan Berkeley on 2009-02-19
Here is a complete recap. I have also sent this information to the suppliers' engineers for their comments, since the problem is clearly in the computer's internal configuration. It appears that some or all of the interfaces on this machine are disabled. I have consulted the manuals online, and it seems all routes lead me back to the Network Connections panel, in which the only connection I can see, when the Ethernet cable to the BT HomeHub is plugged in, is 'Point to Point', and nothing happens when I click it. When I tried to connect via a USB port, I saw a button for 'Wired Connection' too, but nothing happened when I clicked that, either. There are also 'unlock' buttons on that panel, but clicking them makes no difference. 'Enable Networking' is ticked. There follow detailed diagnostics separated by double dashes.

=====

"sudo ifconfig" gives this:

Link encap: Local Loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
inet6 addr:: 1/128 Scope: Host
UP LOOPBACK RUNNING
and then some MTU, Metric, RX packets, TX packets, error rate of zero, bytes, etc.

In other words, no interfaces at all. 

=====

"sudo lspci" gives these interface items, among various other items that seem irrelevant

00.1a.0 USB Controller
00.1a.1 USB Controller
00.1a.2 USB Controller
00.1a.7 USB Controller
...
00.1d.0 USB Controller
00.1d.1 USB Controller
00.1d.2 USB Controller
00.1d.7 USB Controller
...
14.00.0 Ethernet Controller

(I have omitted the make and model details) 

=====


"sudo lshw -C network" gives:

* -network UNCLAIMED
description: Ethernet Controller
product: RTL8111/8168B PCI Express
vendor: Realtek
physical ID: 0
bus info: pci@0000.14.00.0
version: 02
width: 64 bits
clock: 33 MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list
configuration: latency=0 

=====

"sudo dmesg grep eth0" gives:

usage: dmesg [-c][-n level][-s bufsize] 

"sudo dmesg | grep eth0" gives no response.

Regarding the fact that "sudo dmesg grep eth0" gives "usage: dmesg [-c][-n level][-s bufsize]", whereas "sudo dmesg | grep eth0" gives no response - the command is in fact working correctly with the | key, which I have now located, it appears as the shifted upper case version of the / key and is shown on the key itself as two short vertical lines above one another. When I get the "dmesg [-c][-n level][-s bufsize]" message, this means that I entered an invalid option for dmesg (grep and eth0 in this case). Because I get no output when using |, this means that there are no lines outputted by dmesg that contain eth0.


=====

The network manager is nm-applet 0.6.6, and the lsb_release -r is 8.04.

/etc/network/interfaces says:

# The Loopback network interface
  auto lo
  iface lo inet loopback

# The primary network interface

and then nothing. However, etc/network/interfaces.bak-0 says

# The Loopback network interface
  auto lo
  iface lo inet loopback

# The primary network interface
  auto eth0
  iface eth0 inet dhcp

I wonder whether the interface has been disabled, after initially being enabled normally -- when I first tried to connect it to the web via Ethernet, it SEEMED to connect itself successfully and start downloading updates. After a couple of minutes of this, it stopped itself, or got stopped by the router, and since then the update manager has been complaining that certain files supposedly in the download cannot be found and installed. I have switched off the notification of this fact for the moment. If the router accidentally let it connect and do this, then cut it off, then maybe it needs a System Restore to get it back to where it was before it got hold of these updates.

---

### Post by rgb96 on 2009-02-19
try adding:

auto eth0
iface eth0 inet dhcp

back into /etc/network/interfaces and then do

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

and see if that does the trick.

---

### Post by Rowan Berkeley on 2009-02-19
Thanks; unless anyone countermands that, I shall try it tomorrow.

---

### Post by rgb96 on 2009-02-19
Yeah. I took network manager off my computer entirely. It kept changing stuff everytime I booted up, so I just learned to configure stuff manually. It isn't that hard really. You can find it all through google or these forums.

---

### Post by Rowan Berkeley on 2009-02-19
The engineer at the suppliers says:

If NetworkManager isn't establishing a connection then the following commands are to bring up the ethernet device, usually eth0, and obtain an IP address from the DHCP server, if one is present, otherwise you will manually need to setup eth0 network settings according to your network environment. You need to perform these commands as the user root:

Bring up eth0 interface:
ifconfig eth0 up

Obtain IP from DHCP:
dhclient eth0

---

### Post by rgb96 on 2009-02-19
Yeah, but it looks like your machine doesn't have eth0 defined, since it isn't in /etc/network/interfaces. You have to put:

auto eth0
iface eth0 inet dhcp

into that file before those commands will do anything useful.

Out of curiosity, are you using dhcp on your Windows machine too?

---

### Post by Rowan Berkeley on 2009-02-20
You're right, attempting to set "ifconfig eth0 up" just returns "ERROR while getting interface flags: No such device"

I've written back to the enginer at the firm that supplied the machine telling him this. Sorry for the three-sided nature of this conversation, but I have to give him the final word, or my guarantee (such as it is) will become completely worthless. He always seems to reply within 24 hours or so.

I assume that this Sony uses DHCP. It uses the default Ethernet connection to the Hub, without needing any tweaking, "installation disks", etc at all. It is pure plug and run.

---

### Post by tarps87 on 2009-02-20
> **rgb96 said:**
> try adding:

auto eth0
iface eth0 inet dhcp

back into /etc/network/interfaces and then do

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

and see if that does the trick.

Have you tried this? Without the eth0 line it will not use the interface.

You can also try copping the old configuration over the new one.
```
sudo cp etc/network/interfaces.bak-0 etc/network/interfaces
```

---

### Post by Rowan Berkeley on 2009-02-20
As I said, I want the opinion of the vendor's engineer. I note that in his own reply he said that I must reactivate the interface as user root.

But tell me exactly how to do what you suggested, in advance. Can I just type
auto eth0
iface eth0 inet dhcp
into /etc/network/interfaces using sudo? could you spell out the entire command, as you did for
sudo cp etc/network/interfaces.bak-0 etc/network/interfaces

By the way, in answer to another previous question, BT HomeHub does indeed run perfectly normal DHCP.

---

### Post by tarps87 on 2009-02-20
> **Rowan Berkeley said:**
> As I said, I want the opinion of the vendor's engineer. I note that in his own reply he said that I must reactivate the interface as user root.

But tell me exactly how to do what you suggested, in advance. Can I just type
auto eth0
iface eth0 inet dhcp
into /etc/network/interfaces using sudo? could you spell out the entire command, as you did for
sudo cp etc/network/interfaces.bak-0 etc/network/interfaces

By the way, in answer to another previous question, BT HomeHub does indeed run perfectly normal DHCP.

I think the vendor's engineer is assuming that the interface is 'enabled'

This should fix it
```
sudo cp etc/network/interfaces.bak-0 etc/network/interfaces
```

If you want to add the line manualy
```
sudo gedit /etc/network/interfaces
```
(gedit is the name of the text editor on Ubuntu)
now add the lines:
auto eth0
iface eth0 inet dhcp

reboot and try ifconfig again.

In Ubuntu the root user is disabled so for any command that needs root privileges run it using sudo.

---

### Post by Rowan Berkeley on 2009-02-20
well, I can access root by logging in as root. That's the way the machine came: my first task was to create a user ID as administrator. But I can log in as either.

I just realised, the space after "gedit" is because it is a command, not part of a string.

---

### Post by stormtrooprdave on 2009-02-20
> **Rowan Berkeley said:**
> 
"sudo lshw -C network" gives:

* -network UNCLAIMED
description: Ethernet Controller
product: RTL8111/8168B PCI Express
vendor: Realtek
physical ID: 0
bus info: pci@0000.14.00.0
version: 02
width: 64 bits
clock: 33 MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list
configuration: latency=0 



I have had experience with it saying network unclaimed.  This means there is no driver for your ethernet card/adaptor. I think the linux driver for your realtek device is called r8169 so if you do ```
sudo modprobe r8169
``` that will load the driver and auto eth0 should show up in network manager

---

### Post by tarps87 on 2009-02-20
It sounds like they have modified it after the initial install then, this could explain how the interface got removed from the interfaces file, I just don't the reason.

---

### Post by Rowan Berkeley on 2009-02-20
well, I've forwarded that suggestion to the engineer also, for his comments. My own impression, as I said back in comment #13 on this thread, is that I wonder whether the interface has been disabled, after initially being enabled normally -- when I first tried to connect it to the web via Ethernet, it SEEMED to connect itself successfully and start downloading updates. After a couple of minutes of this, it stopped itself, or got stopped by the router, and since then the update manager has been complaining that certain files supposedly in the download cannot be found and installed. I have switched off the notification of this fact for the moment. If the router accidentally let it connect and do this, then cut it off, then maybe it needs a System Restore to get it back to where it was before it got hold of these updates.

---

### Post by rgb96 on 2009-02-20
> **Rowan Berkeley said:**
>  maybe it needs a System Restore to get it back to where it was before it got hold of these updates.


It shouldn't. Also, what is this company guarantee you speak of? Ubuntu is a free operating system. It's not like they can refund you (hopefully) if it isn't working correctly. One of the main draws for me to Linux in general is all of the free community support. I really think your problem is in /etc/network/interfaces, but if it isn't, you can simply re-open that file and delete what you put in it in the first place.

---

### Post by Rowan Berkeley on 2009-02-20
Whatever the rollback for the updates would involve - assuming what I described actually happened - I don't imagine "System Restore" is the best term for it; that's a Windows term.

The guarantee of which I speak is that which attaches to the machine, as shipped to me with UBUNTU PRE-INSTALLED, specifically, at a fee.

---

### Post by rgb96 on 2009-02-20
So if you change one of the config files that people change all the time, you void your warantee?

---

### Post by Rowan Berkeley on 2009-02-20
I think that if I want the continued cooperation of the supplier, I should double-check my REMEDIAL actions with him, to see whether they accord with his account of how the thing should work. Up to a point, he is responsible. I see no point in arguing about this, though.

---

### Post by Rowan Berkeley on 2009-02-21
The engineer at LinuxCertified incautiously said this:

"If you performed updates esp a kernel update, you will need to recompile the r8168 driver module"

Now that I have grasped and faced up to what really happened (and it has taken a few days to put it together), I have sent them the following email:

"I have received the LC2430S which I ordered. Unfortunately, it has become clear that the machine was sent out with its automatic online updater switched on, so that as soon as I connected it via Ethernet to the web, it downloaded a number of updates, and attempted to install them, thereby disabling the interface, which has been dead since. I consider this to be a faulty condition in the goods supplied, and I am completely dissatisfied with the response of your engineers. Unless you are prepared to arrange, at the expense of LinuxCertified, for a qualified professional here in London to promptly restore the machine to working order, I shall have to ask you to collect the machine at your own expense and provide me with a full refund, including the cost of carriage and import tax. If you are not willing to do this, I shall begin Consumer Complaint procedures against your company."

I think that at the same time I myself can afford to hire the services of anyone here in London who is qualified to do it, to restore this machine to its previous working order (if necessary by using the system recovery disks, which I have). This would be assuming my request for a refund or replacement is refused, as I assume it will be. I shall then change the angle of my complaint so as to try to force them to re-imburse me for the cost of repairs. If any readers of this are in London and know of such a person, please post here.

---

### Post by RHCEinUK on 2009-02-22
Well, in general following sequence works on any linux box.

As root user:

# ifconfig eth0 up 

(this will make sure eth0 interface is up, regardless of any other configuration)

# dhclient eth0

(this will grab an ip address from your router)

What is the result of above commands?

---

### Post by Rowan Berkeley on 2009-02-22
A kernel update caused the driver to become inoperable because it is not the default driver expected by the update. I am trying to find someone in London who for a fee of say £100 will undertake to recompile the driver, and also to install the utility called DKMS, which is apparently able to monitor and control these conflicts. Anyone in London who wants to earn a relatively quick £100 is invited to contact me via this thread or by email:
[email]rowan.berkeley@gmail.com[/email]

---

### Post by tarps87 on 2009-02-23
I do not live near London, if you want I can guide you through compiling the driver. All the steps are in the read me but if you get stuck you can post back
[(Link to the downlod)"][http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168/RTL8111C](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168/RTL8111C)]("[Link to the downlod)
You want the version called LINUX driver for kernel 2.6.x and 2.4.x 

This will install the dkms framework
```
sudo apt-get install dkms
```

I will not be offended if you choose to wait for someone who can do it in person

---

### Post by Rowan Berkeley on 2009-02-23
well, I think I shall wait. Unless everybody in this line of business is remarkably wealthy, I should get an offer fairly soon. I have explained to the suppliers of the machine that this is my intention, and that if eventually I send them an invoice for this, and they agree to pay for it, that would be much appreciated, but I think that getting it done by someone who is actually competent is well worth a wait! 

I'm very grateful for your attention to my problem, and I do realise that, from the point of view of someone who is familiar with these things, this problem is quite minor, though not trivial.

---

### Post by Rowan Berkeley on 2009-02-23
By the way, I can't help imagining the state of mind I would be in if I didn't have this machine I am using now online (a Sony laptop with WinXP). I have spent much of the last week on this forum and two others, ubuntu-UK and something called NetworkManagerList which I now realise is utterly unsuited to the query, finding out what is actually the matter. I want to ensure that whoever I get to help me out will give the thing a general once-over, and also make sure that there aren't any other non-ubuntu-default software modules lurking in there waiting to get disabled.

---

### Post by rgb96 on 2009-02-23
Man. I'm telling you, you've way overcomplicated the whole situation. All you have to do is add a few lines to /etc/network/interfaces, and execute the commands to restart your networking interfaces. That will fix your problem. No need to complain about all this stuff, and no need to spend money to get someone to put those few lines in there fore you.

---

### Post by Rowan Berkeley on 2009-02-23
Thank you for your advice. I prefer to make my own decisions, though, and I have decided to only allow competent people to tinker with it, among whom I do not include myself.

---

### Post by Rowan Berkeley on 2009-02-24
Just to close this thread: several people on the ubuntu-uk list have assured me that some time in the near future they will be prepared to re-compile the non-default driver for me and install DKMS, so that problems of this sort will not recur. As a complete beginner, I am extremely grateful to them for this offer, and I shall wait until I can arrange a convenient occasion for it. I don't think I need to pursue the matter here or elsewhere any further in the meantime. Thanks to all who read this thread (with its rather odd title, which I suppose shows just how confused I am).

---

