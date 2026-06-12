---
title: "Ubuntu Ethernet/Network Problem"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by __dave on 2006-08-01
Hi, 
I recently installed Ubuntu 6.06 on my thinkpad T21 laptop and for some reason can't access the internet. I would really appreciate if someone could help me out with this as I just can't seem to figure out what the problem is. 
My laptop is connected via a pcmcia ethernet card to a adsl modem/router which also has a winxp pc connected to it. However, I'm pretty sure that my problem isn't down to hardware because I've tried running the damn small linux 2.0 live cd in my thinkpad and the internet works fine in that without any tweaking.
My ethernet card is deteced in ubuntu but I'm not 100% sure what network settings I should be using plus, under 'network connections' 'eth0' and 'lo' are constantly 'idle' under the status bit.
hope someone can help as this is driving me mad

---

### Post by apjone on 2006-08-01
do a cat /etc/networking/interfaces and post it here so we can help you more

---

### Post by __dave on 2006-08-01
ok..

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0 
iface wlan0 inet dhcp

---

### Post by apjone on 2006-08-01
whats the address of your adsl modem??

---

### Post by __dave on 2006-08-01
the IP address of the modem is 192.168.1.1 with the subnet mask as 255.255.255.0

---

### Post by __dave on 2006-08-01
Btw, just thought I'd better mention that I have, in the past got a working internet connection on Ubuntu 6.06 on a desktop PC using the same ethernet and modem/router connection as well.

---

### Post by apjone on 2006-08-02
change the file to the following. (make a back up first though)

auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        network 192.168.1.0
        broadcast 192.168.1.255
        address 192.168.1.3
        netmask 255.255.255.0
        gateway 192.168.1.1
auto eth0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


also check your /etc/resolve.conf and add your dns in there.

---

### Post by __dave on 2006-08-02
Hi,
Ok I've done that and now the Status under connection properties for eth0 is just flicking through idle, sending, receiving, sending/receiving and I still can't access any internet pages.

---

### Post by __dave on 2006-08-02
Upon restart the network connection is listed as being 'disconnected' :(

---

### Post by __dave on 2006-08-02
Ok, after a bit of fiddling it is no longer 'disconnected'  but permanently 'idle' again.
Could someone possibly point me in the right direction as I could really use an internet connection.

---

### Post by mips on 2006-08-03
What PCMCIA card are you using ? What chipset does it use ?
What adsl router do you have ?

Please be specific.

Try disabling power management.

---

### Post by __dave on 2006-08-04
Hi, 
I have 2 ethernet cards. One is a '3Com Etherlink III 3C589D-TP' and the other's a 'Xircom CE3B-100BTX'.
The Modem/Router I'm using is a BT Voyager 2500v.
I'll try disabling power management now. I hope this is enough information, if not then I'll have another look and see what I can come up with.

---

### Post by __dave on 2006-08-04
Hi,
After disabling power management, disabling the xircom card and setting the 3Com card to 'DHCP' and as the default gateway I am now online but the status of eth1 under network connections still constantly flicks through 'Sending/Receiving, Sending,etc' (but is thankfully never 'idle'.)
Is this normal?

---

### Post by The Shadow on 2006-08-04
I am having a similar problem; so far I have had no joy in solving it. sounds like you have tried most of the same things that did, so I can't really offer any help, just sympathy. I'll let you know if I find a solution, please post the same if you do.

---

### Post by mips on 2006-08-04
I dont use gnome so dunno whether it is normal, maybe someone else can comment.

---

### Post by blackant on 2006-08-04
I have a similar problem, but after I set the DNS correctly, I am able to surf the internet. :)

Maybe you can check your DNS settings.

---

### Post by pandionknight on 2006-08-04
I seem to be in a similar boat. No wireless internet connection. I have a G5 iMac connected to a Belkin F5D7230-4 router. My kids PC is in another room running Dapper Drake connected to a Belkin F5D7330 Wireless Ethernet Adapter. I know the PC IP should be 192.168.2.3 but it seems to be 127.0.0.1. I know the subnet should be 255.255.255.0 but it's 255.0.0.0. 

I need to change the IP and subnet for the PC, yet I have looked at the etc/network/interfaces and it looks like the others here only without the address, netmask, or network. But my system says this is a read only file. What app do I need to open it in to change it?

---

### Post by mips on 2006-08-04
> **pandionknight said:**
> I seem to be in a similar boat. No wireless internet connection. I have a G5 iMac connected to a Belkin F5D7230-4 router. My kids PC is in another room running Dapper Drake connected to a Belkin F5D7330 Wireless Ethernet Adapter. I know the PC IP should be 192.168.2.3 but it seems to be 127.0.0.1. I know the subnet should be 255.255.255.0 but it's 255.0.0.0. 

I need to change the IP and subnet for the PC, yet I have looked at the etc/network/interfaces and it looks like the others here only without the address, netmask, or network. But my system says this is a read only file. What app do I need to open it in to change it?

127.0.0.1 is the loopback interface. You need to get your wired or wireless interface up. If it is mac related maybe post in the mac section.

---

### Post by pandionknight on 2006-08-04
It's not Mac related. The iMac can connect via the router fine. I was only giving details of my set up which worked fine under SuSE for ages, and was ok for a while under Mandriva. I heard a lot about Ubuntu and Synaptic being easier than YaST so here I am. What I need to be able to do is set my IP and netmask. But apparently I do not have rights to edit etc/network/interfaces.

---

### Post by mips on 2006-08-04
> **pandionknight said:**
> But apparently I do not have rights to edit etc/network/interfaces.

This might sound stupid but I have to ask if you have tried SUDO ? 
**sudo gedit /etc/network/interfaces**

---

### Post by pandionknight on 2006-08-04
Not stupid at all. I have only been using linux since new year. I'll give it a go tomorrow, and post back.

---

### Post by Eliza Do on 2006-08-04
okay... finding this thread regarding ethernet problems brings a sigh of relief... I'm greener than green when it comes to using Ubuntu and feel super lost though I'm determined to figure this thing out.  Of prime importance is the internet connection and I'm having the same issues described throughout this thread, except that I'm a wee bit behind in that I don't understand what to do with the commands you mention (for example, sudo... what is this? and where would I input this information that you outline? everytime I try to change any settings it doesn't let me save... though this is probably a good thing cause I'm not sure what I'm doing).  

If you can incorporate my arrival on the scene to the already occuring discussion that would be great.  I'm trying to run an PCMCIA Ethernet Card (IEEE 802.3) on my "newly Linux-ed" Compaq Armada E500 laptop and have a D-Link D-3001 modem that's working just fine right now with a Mac I've got connected.

Looking forward to learning the ropes and getting things up and running!

---

### Post by RedBoot on 2006-08-05
Eliza Do and pandionknight:
You both seem to be asking: What app do I need to open it in to change it?

Maybe this is a dumb question, but have you used the menus? (System, Administration, Networking) There you can change all parameters, or just let DHCP set it up for you automatically.

---

### Post by pandionknight on 2006-08-05
Eliza. Go to Applications/Accessories/Terminal and enter: sudo gedit etc/network/interfaces (you will be asked for your password. 
Enter below the 'iface eth0 inet dhcp' line the following with your details,
address 192.000.0.0
netmask 255.000.0.0
network 192.000.0.0
broadcast 192.000.0
gateway 192.000.0.1

then Save as, browse to the etc/network/interfaces file and replace it.

---

### Post by pandionknight on 2006-08-05
Redboot. I have been to System/Administration/Networking. Should I enter my IP and Gateway in the Hosts tab?  If so, how should I refer to them under Aliases?

---

### Post by pandionknight on 2006-08-05
This could be important. Under Network settings the only device i have listed is the modem. Not ethernet eth0 and there is no 'Add' button on this tab?

---

### Post by Silent Warrior on 2006-08-05
I'm also having some similar problem. I know what sudo does, don't worry about that. (But starting gedit doesn't seem to work, though. I haven't installed any videocard-drivers yet, is that the cause? It says it can't open display(null). Those drivers are a matter for another topic, though. PMs are always welcome.)
I'm sitting behind a Nokia modem and a Belkin wireless router (not sure about their model-number, but since the other machine I'm sitting at right now uses those as well, I'll consider them tried and true), and I get no internet.
The router-settings as shown through the browser (192.168.2.1, mark that '2') shows, under Internet Settings, IP-addresses in 213.66.186.* (WAN IP and Default Gateway), and DNS-addresses as 195.67.199.27-28. Subnet mask is 255.255.255.0. LAN Settings show IP Address 192.168.2.1, same Subnet mask. DHCP Client List shows my computer as 192.168.2.2 and 2.5.
How do I go about setting that up in a working condition?

Also, I see here that the router has UPnP disabled. Is it a good idea to turn it on? Generally speaking?

---

### Post by __dave on 2006-08-05
Ok, I initially thought I'd solved my problem but it seems its just as bad.
In order to connect to the internet after I boot up, I now have to physically eject both ethernet cards (deactivate/activate doesn't have the same results for me), plug one of them back in, even though I don't plan to use it, and then plug the one I am using in a few seconds later so that it is configured as 'eth1'. I'm not entirely sure why this is seeing as the settings for eth0 and eth1 should be exactly the same.

My /etc/network/interfaces looks like this on startup:

[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp[/I]

But after unplugging/plugging the network cards in, it changes itself to this:

[I]auto lo
iface lo inet loopback




auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0
[/I]

The obvious problem being that somewhere along the line it's doing something to the settings for eth0 which I presume is why I can only access the internet through a card called eth1.

For the record, here's my ifconfig:

[I]eth0      Link encap:Ethernet  HWaddr 00:80:C7:DC:A8:A5
          inet6 addr: fe80::280:c7ff:fedc:a8a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:15174 (14.8 KiB)
          Interrupt:3 Base address:0x300

eth1      Link encap:Ethernet  HWaddr 00:60:08:93:32:FA
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260:8ff:fe93:32fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1416 errors:0 dropped:0 overruns:0 carrier:4
          collisions:1 txqueuelen:1000
          RX bytes:1143535 (1.0 MiB)  TX bytes:224055 (218.8 KiB)
          Interrupt:4 Base address:0x310

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8450 (8.2 KiB)  TX bytes:8450 (8.2 KiB)
[/I]

I am currently using the eth1 connection to type this post. The eth0 card doesn't even have a network cable attached.

Any Suggestions anyone??

---

### Post by Eliza Do on 2006-08-05
Hey Pandionknight,
Thanks for the reply but where might I find this information that you mention I need to input (netmask, gateway, etc...)?? 

Though many questions are yet to be posed I must share that I am making some headway in terms of finding access to the Terminal... and realising that's where I can put in the commands... as you can tell, this is totally unchartered territory for me... so I do appreciate the help... only wish I could offer some myself!  All in good time...

---

### Post by RedBoot on 2006-08-05
Eliza Do,
I know there's been a lot of points, but I'll repeat my suggestion:

Have you used the menus? (System, Administration, Networking) There you can change all parameters, or just *let DHCP set it up for you automatically*.

---

### Post by RedBoot on 2006-08-05
PandionKnight,
> This could be important. Under Network settings the only device i have listed is the modem. Not ethernet eth0 and there is no 'Add' button on this tab?This is extremely important. It could mean that linux doesn't even *know*about the Belkin F5D7330 Wireless Ethernet Adapter. So dealing with IPs is not going to help.

I would suggest the [Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") even though yours is not a wireless adapter. The commands they employ and the methodical, step by step process they use are excellent and you should find the point where the problem occurs before you get to the wireless commands.

---

### Post by pandionknight on 2006-08-05
> **pandionknight said:**
> Redboot. I have been to System/Administration/Networking. Should I enter my IP and Gateway in the Hosts tab?  If so, how should I refer to them under Aliases?

There is no Add button on the  Connections tab of the Networking panel to let me add the ethernet connection. It does not look the same as the image in the help files. Nor do I see any option to let DHCP set things for me like you suggest. Nor in the Networking Tools panel.

---

### Post by Eliza Do on 2006-08-05
Hey Redboot,
Yes I've tried this and it seems to have detected the Ethernet connection as it says that the interface eth1 is active... not so sure what to do now... I assume this means everything's been set up automatically?
Bare with me here... serious learning curve going on...

---

### Post by Eliza Do on 2006-08-05
okay wait!!
We've got some internet action!!
I think...

---

### Post by Eliza Do on 2006-08-05
by that I mean I now need to set up my highspeed account and password and such on this computer... I do know enough to know when the internet is working... thought I'd better clarify! :rolleyes:

---

### Post by RedBoot on 2006-08-05
PandionKnight,
Regarding your post #32:
My post #31 here refers to your post #26.

---

### Post by vidyaratha on 2006-08-11
Hi
My Dell Inspiron laptop card picks up the DHCP settings and IP address from my DSL service.
I cannot browse the internet. I can do that when I am using Windows XP on the same machine
Help please!
Thanks
Vidyaratha

---

### Post by drtvasudevan on 2006-08-11
hi guys please do the following before you meddle with network settings.

there is an ipv issue in the mozilla firefox that ubuntu ships with.
disable that by:
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change value from false to true= just double click it 
shutdown firefox
restart firefox. 

after that if you cant connect try to ping the router, the net.
and then post questions in the forum with the details

---

### Post by vidyaratha on 2006-08-12
> **vidyaratha said:**
> Hi
My Dell Inspiron laptop card picks up the DHCP settings and IP address from my DSL service.
I cannot browse the internet. I can do that when I am using Windows XP on the same machine
Help please!
Thanks
Vidyaratha

To answer my own question, I edited the /etc/networking/interfaces file and added the gateway address. 
all works beautiflly now

---

