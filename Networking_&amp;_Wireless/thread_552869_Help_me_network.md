---
title: "Help me network"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2007-09-17
Hi
Im new to linux and know little about networking. I have to computers  im trying to network. One runs Ubuntu 7.04 fiesty fawn. The other runs Windows XP. I have two ethernet cords. I have an HP 10 Base T hub.
Im trying to get the two networked where i can share files between the two. and get internet on the one that doesn't, and possibly get synergy working. One gets the internet through a wifi card.Ive tried pinging from boath ends and no packages will go through. Is there a way i can get two networks running(my wifi network, and my LAN network) at the same time so i can share the internet via wifi. and share files and possibly use synergy all at the same time. I know this is possible with windows but i have no idea what to do with Ubuntu. Please help me.

this is the output on ubuntu:```
# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:06:33:20  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45733 (44.6 KiB)  TX bytes:45998 (44.9 KiB)
          Interrupt:18 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:E0:18:F1:E8:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 

eth1:avah Link encap:Ethernet  HWaddr 00:E0:18:F1:E8:42  
          inet addr:169.254.8.206  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20527 (20.0 KiB)  TX bytes:20527 (20.0 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:71:C6:AB  
          inet addr:192.168.x.x  Bcast:192.168.x.x  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe71:c6ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:516601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283035 errors:0 dropped:15 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:771280581 (735.5 MiB)  TX bytes:19787427 (18.8 MiB)
          Interrupt:20 Memory:ed000000-ed010000
```

```
# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.x.x     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
169.254.x.x     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.x.x     0.0.0.0         UG        0 0          0 wlan0


```

I didn't give out my edzact IPs for fear of hacking...
```
Host Name. . . . . . . . . . . . :walawala
Primary Dns Suffix . . . . . :
Node Type . . . . . . . . . . . . : Unknown
IP Routing Enabled . . . . .: No
WINS Proxy Enabled . . . : No

Ethernet adapter Local Area Connection 

Connection-specific DNS suffix . :
Description . . . . . . . . . . . . . . . . . . .:Intel<R> PRO/100+ Management Adapter 
ard
Physical Address . . . . . . . . . . . . . : 00-02-2A-B0-1A-F7
Dhcp Enabled . . . . . . . . . . . . . . . . : yes
Autoconfiguration Enabled. . . . . .:yes
IP Address . . . . . . . . . . . . . . . . . . . . :169.254.54.79
Subnet Mask . . . . . . . . . . . . . . . . . . :255.255.255.0
Default Gateway . . . . . . . . . . . . . . . :
Default Gateway . . . . . . . . . . . . . . :
``` 

I played a little with it in the GUI. i went to network under places on the XP computer doesnt  and itshow up. only ''Saucy'' Which i think is my brothers computer name who picks up internet from our wifi router too. Im not really interested in accessing my Brothers computer. i dont see my laptop under network places on my desktop ether. Everything is pluged in and all lights are on. What do you think i should do now?

---

### Post by lisati on 2007-09-17
A comment to start the ball rolling.
You will need to enable networking on both machines. XP Home comes with a "Network Setup Wizard". From memory, it can be accessed from "My Network Places". It will ask a few questions and possibly demand a reboot.

---

### Post by Dwiman89 on 2007-09-17
Is there a way to enable the ethernet network in ubuntu without disabling my wifi internet connection?

---

### Post by Dwiman89 on 2007-09-19
ive went through the steps of netwrking on the xp computer. i dont know what to do on my linux computer. can you please help. and is there a way i can have my wifi connection and my wired connection connected at the same time. please help.

---

### Post by w4ett on 2007-09-20
Not a real big networking guy here, but you will have to use samba to interface between window and Ubuntu:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Dwiman89 on 2007-09-20
will that allow me to share my internet connection? My Ubuntu computer picks up the internet via wifi.

---

### Post by w4ett on 2007-09-20
Also check this how to for Samba:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Internet Connection Sharing:

[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

---

### Post by noob12 on 2007-09-20
I probably can't help with the entire setup, but the first step is just getting your two interfaces up.

As far as i understand, the current NetworkManager implementation doesn't allow operating two interfaces at once.  So you would have to remove the network-manager package, and then configure your wired and wireless interfaces directly in the **/etc/network/interfaces** file.

---

### Post by Dwiman89 on 2007-09-20
cool. how do i go about doing that?

---

### Post by noob12 on 2007-09-20
OK.

This will **remove** the network-manager and gnome-network-manager packages.

```

sudo aptitude remove --purge network-manager

```

This will also cause removal of the **gnome-network-manager** package and that will tell you that it breaks a recommended package of the gnome-desktop.  You will need to accept at the question.  You will not lose the desktop.    You can reinstall both the **network-manager** and **gnome-network-manager** later if you want to use them again.

After that you need to configure each interface manually in **/etc/network/interfaces**.  The man page is **man interfaces**, and is pretty good if you are able to read that.  In order to get specific instructions from me on that you need to say for each interface whether it is dhcp-configured or statically assigned, and if static, what the ip address, subnet mask, and  gateway address (if any) should be.

ADDED:  For wireless, we'll need the ESSID, authentication-type, key, etc.  You'll need just to be able to substitute those in appropriate places.

---

### Post by Dwiman89 on 2007-09-20
this is what it said in that file
```
auto lo
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
iface wlan0 inet dhcp
```

---

### Post by noob12 on 2007-09-20
You can remove the stanzas (sections) for **eth2** and **ath0** which you don't have.


Do you know which interface you are using currently on this box to get to the Internet or is it the Windows box that is connected to the Internet?

Your earlier ifconfig output showed only the wlan0 interface with an address on a 192.168 net.  By the way, there is no reason to hide network numbers on a 192.168 net in these postings.  That's a private net.  Where did it get that address assigned from?  Do you have a wireless router there?  You only mentioned a hub.

Can you explain how you currently have things connected?

---

### Post by Dwiman89 on 2007-09-20
Um this is all i know how to get by scaning with terminal; 
```
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:0D:94:AB
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```
I dont know how to retrieve the other information. what do i do?

---

### Post by AJWhitewolf on 2007-09-20
I am assuming from your post that your ethernet 10baseT hub is seperate from your wireless AP, because of the word "hub".  If your hardware is, indeed, a hub and not a "switch", you will have to specify a static IP, as hubs have no DHCP, and cannot automatically assign an IP.  Hope that helps!

---

### Post by Dwiman89 on 2007-09-20
Im picking up wifi in the office across the house where i get the internet. Ive got two computers setting side by side. one is XP and the other is ubuntu. i would make both linux ubuntu but i cant because the xp system has a FUJITSU MAN3184MP SCSI hard drive wich is not supported by ubuntu as far as i can find out. I have the two connected through a 10 base T hub. My goal is to get The internet to my XP system through my ubuntu system and be able to share files beteen the two, and possibly get synergy working. let me know how to retrieve any other information you need.
the ubuntu computer picks up the internet with wifi

---

### Post by noob12 on 2007-09-20
OK.   We first want to get that connected.

You have no encryption on and you have the default essid "linksys".  You should  probably change that essid and enable encryption, but you can do that later.  For now it is easier to configure in the current (but insecure) situation.

Edit your **/etc/network/interfaces** file.

```

sudo gedit /etc/network/interfaces

```

Replace the section for wlan0 with this
```

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys
wireless-key off

```

Then try to bounce that interface and see if you connect and get an address.
```

sudo ifdown wlan0
sudo ifup wlan0

```

---

### Post by AJWhitewolf on 2007-09-20
I unfortunately do not know how to set up internet connection sharing in ubuntu, but it is pretty simple to do in XP (I know I'm a bad person for saying it, I am just new to linux and sharing what knowledge I have).  You will have to specify a static IP for the ethernet card on both machines, because you have a hub.  In Ubuntu, this can be done by clicking System-->Administration-->Network Tools, then selecting eth0 in the Network device drop down menu,  and clicking configure.  You would then select Static IP from the Configuration drop down menu, then specify an IP for yourself...  probably 192.168.1.x   Then enter a subnet mask (probably 255.255.255.0) and the Gateway address will be blank (I believe).  On the XP machine, you would do this by right-clicking on Network Places and selecting Properties, then right-click on your LAN connection (Probably Network Connection 1), and click Properties.  Then you will select the TCP/IP protocol, and click properties, where you will again specify that you want a static IP and change the other numbers accordingly (of course, remembering to end the IP address for this computer with a different number than the other).  At this point, the two computers should be able to recognize each other on the network, which you can test by pinging.  To do this, open a terminal, type ping (other computers IP) and press enter.  In windows, this can be done by clicking Start-->Run and typing cmd and pressing enter, then use the same command that you did in your ubuntu terminal in the windows command prompt.  As long as the two computers see each other, you should be able to share the internet that you are receiving on your wireless card to the other computer.  I can walk you through doing this in Windows XP, but I am unsure in ubuntu...  If I find an answer I will post the URL.

---

### Post by AJWhitewolf on 2007-09-20
[http://ubuntuforums.org/showthread.php?t=91370]("http://ubuntuforums.org/showthread.php?t=91370")

Perhaps this thread will help you share your connection using your ubuntu machine.

---

### Post by Dwiman89 on 2007-09-20
this is what i got fromthat first command.

```
k# sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 9579
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:6c:71:c6:ab
Sending on   LPF/wlan0/00:14:6c:71:c6:ab
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
root@hambone:/home/derrick# sudo ifup wlan0

```

```
# sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:6c:71:c6:ab
Sending on   LPF/wlan0/00:14:6c:71:c6:ab
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 42737 seconds.

```

---

### Post by noob12 on 2007-09-20
Looks good.  You should be able to ping your router at 192.168.1.1

```

ping -c 4 192.168.1.1

```

After that we will want to set up one of your two wired interfaces.  In your situation we will probably want to configure it to be bridged to the wlan.  Then your windows box will be able to get to wifi router and out to the net as well.

Are both of the two wired interfaces (eth0 and eth1) on the Ubuntu box working?  Is there any reason to use one or the other to connect to the hub with the Windows box, and is one connected already?

Also, note that the time is getting late here, and we're probably going to have to continue tomorrow.

---

### Post by mips on 2007-09-20
From interpretation I assume your wireless uses network 192.168.1.0, as your routers address falls within that network.
 
 Configure Eth0 with the following STATIC parameters: (I'm assuming this is the one connected to the hub, if not do it for eth1)
 IP Address 192.168.2.1
 Netmask 255.255.255.0
 Broadcast 192.168.2.255
 Gateway wlan0
 
 Configure your Windows PC with the following STATIC parameters:
 IP Address 192.168.2.10
 Netmask 255.255.255.0
 Broadcast 192.168.2.255
 Gateway 192.168.2.1
 
 If you need to configure DNS addresses anywhere point it to your routers address (192.168.1.1) for now.

I would also advice you to configure your wireless network for static IP (Say 192.168.1.10) then use that address as the Gateway adress for Eth0 instead of wlan0.

**Next install&start (its in the repos)Firestarter and everything should work.** If you don't like firestarter then we could setup IP Tables but I think you might prefer firestarter.
Docs are here if you need them, [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by noob12 on 2007-09-20
Yes, on second thought, that's probably easier than bridging.  You do have to enable the ip forwarding across the interfaces in addition to that.  


Go ahead and set that up and get to the point where you can at least ping between the Windows host and the Ubuntu host.

ADDED:  I hadn't noticed the suggestion to use iptables/firestarter to do forwarding and masquerading between them.  That seems like an overly complicated approach.

---

### Post by mips on 2007-09-20
> **noob12 said:**
> Yes, on second thought, that's probably easier than bridging.  You do have to enable the ip forwarding across the interfaces in addition to that.  


...

ADDED:  I hadn't noticed the suggestion to use iptables/firestarter to do forwarding and masquerading between them.  That seems like an overly complicated approach.

Firestarter will enable forwarding for you from what I recall. I don't recall having to do it myself.

IPTables would be a bit overkill unless you like fine tuning stuff to hearts content. Firestarter is a no brainer though.

---

### Post by noob12 on 2007-09-20
Maybe you can lead Dwiman89 through the rest?

---

### Post by mips on 2007-09-20
> **noob12 said:**
> Maybe you can lead Dwiman89 through the rest?

No problem but I'm sure he would value your input as well.

There really is very little left for him to do once he has setup static IPs on his interfaces. All thats left is to install firestarter from the repos, open it, select wlan0 as the internet facing interface, eth0 as the LAN facing interface and clicking on the 'Enable ICS' button.

Voila! Bob's your uncle ;)

---

### Post by noob12 on 2007-09-20
I'm staying on the thread, but I'm not too familiar with firestarter, especially in this scenario, so you're probably going to have to help with any problems he has.

---

### Post by Dwiman89 on 2007-09-20
Um you guys kinda lost me. Im not as computer literate as most. Im assuming the next step is to make everything static. i know how to do tis in windows but how do u do it in that configuration file metion above.I haven't uninstalled the network manager yet because of fear of loosing my internet. i need it in order to go to here and get help. what is the next step i should take?
and how do i pick my wifi connection withount network manager when i boot up?

---

### Post by mips on 2007-09-20
You can click on the network manager icon and manually configure the interfaces yourself just like you would in windows



have you installed firestarter yet ?

---

### Post by Dwiman89 on 2007-09-20
> **noob12 said:**
> I probably can't help with the entire setup, but the first step is just getting your two interfaces up.

As far as i understand, the current NetworkManager implementation doesn't allow operating two interfaces at once.  So you would have to remove the network-manager package, and then configure your wired and wireless interfaces directly in the **/etc/network/interfaces** file.

I need to get both my wired ethernet and wifi linksys working at the same time. Noob12 said to deeate the networkmanager so how do i configerthem both in the above way with my wired connection static.

---

### Post by noob12 on 2007-09-20
mips tells you how to configure the addresses in a posting #21 on this thread.  You can enter those things using the **System | Administration | Network**  GUI on Ubuntu and in the TCP/IP properties for the connection on Windows.

---

### Post by Dwiman89 on 2007-09-20
where do you enter the broadcast number at in windows. I can enter DNS and  WINS numbers in windows but i dont see a field for broadcast.

---

### Post by Dwiman89 on 2007-09-20
I also tried to enter the fields in ubuntu. under eth0 i filled out the fields. yet agin i couldn't find a field for a braodcast number. i also tried to enter wlan0 as the gateway, but it wouldn't let me type it.
   When i entered what i could and closed it my wireless connection was lost and i couldn't reenable it unre network manager. So i put eth0 back to dhcp then i could reconnect to wireless and open ubuntuforums... any ideas?

---

### Post by noob12 on 2007-09-20
You need not enter any broadcast address as that will be calculated automatically from your address and netmask.

You don't enter wlan0 for the gateway.   For now just use 192.168.2.1.  You can change this to the static that you assign for wlan0 later.

Get to the point where you can ping 192.168.2.10  (the windows box) from your Ubuntu host and also ping the Ubuntu host (192.168.2.1) from your windows box.   The Ubuntu host should be using wireless to get to the wifi point.  You shouldn't need eth0 for that anymore.

---

### Post by Dwiman89 on 2007-09-20
> **noob12 said:**
> You need not enter any broadcast address as that will be calculated automatically from your address and netmask.

You don't enter wlan0 for the gateway.   For now just use 192.168.2.1.  You can change this to the static that you assign for wlan0 later.

Get to the point where you can ping 192.168.2.10  (the windows box) from your Ubuntu host and also ping the Ubuntu host (192.168.2.1) from your windows box.   The Ubuntu host should be using wireless to get to the wifi point.  You shouldn't need eth0 for that anymore.

Im sorry but im lost here. im guessing i got three connections i dont know what to do with edzackly Im trying my best to fix it without loosing my wifi because then i cant get help. and i can only enable one at a time so that also makes it hard. im having a hard time following you. what is the next step in lamens terms please. im sorry for making this difficult. i dont understand what you mean by i dont need me ethernet any more. isnt that how a communicate with my windows box if it where possible at this point.

---

### Post by noob12 on 2007-09-20
OK.  

First step.  Make sure your wlan connectivity is working.  Yesterday we had you remove your NetworkManager and configure the wlan0 settings manually in /etc/network/interfaces.  It seemed to be working yesterday.  Make sure it is working still.  You should be able to boot, then unplug the wired connection, and still connect to the internet.

Second step.  On the Ubuntu host.  Decide which of your two wired interfaces eth0 or eht1 you are going to connect (or already have connected) to the hub shared with the Windows box.  You may not know which ethernet jack on the back corresponds to which interface.  Figure it out by plugging an active cable into only one of these two ports, and seeing which one says "Link Detected: yes" when you type
```

sudo ethtool eth0 | grep 'Link detected:'

sudo ethtool eth1 | grep 'Link detected:'

```

For simplicity, let us say that you have chosen eth0.

Plug a cable running from the jack corresponding to eth0 into the hub that you are going to share with the windows box.

Edit **/etc/network/interfaces** (using **sudo gedit /etc/network/interfaces**) and add or replace the section for eth0 with one that looks like this:

```

auto eth0
iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1

```

Save and close the file.

Now go to your Windows host.  Go to **Control Panel | Network Connections**  and find your local area network connection (usually called something like **Local Area Connection**).  Select it.  Then right-click on it and select **Properties** in the menu.  Go to the **General** tab.  Find the **Internet Protocol (TCP/IP)** line.  Select it.  Hit the **Properties** button.

Select the **Use the Following Address** radio button and enter the following in the boxes.  For IP Address use 192.168.2.10.  For netmask use 255.255.255.0, for default gateway enter 192.168.2.1.    For the DNS servers, use the following: 208.67.222.222 and 208.67.220.220 (from OpenDNS).  Note: They won't work until the routing is setup.  Hit OK.  Close.  ...

Now from the Windows host, open a command window and try to **ping 192.168.2.1**.  From the Ubuntu host try to **ping 192.168.2.10**.  You may need to lower the firewall on your Windows box for the ping be echoed.

---

### Post by Dwiman89 on 2007-09-21
OK, I Have  a  problem. i deleated  my network manager, and now my internet doesn't work. for some reason there are two interface files: one is hidden. im making this poast with a playstation  portable. i dont know how to reconect without a network manager. and i cant reinstall without a conection.

---

### Post by noob12 on 2007-09-21
> 
for some reason there are two interface files: one is hidden.

I really don't know what this means.

You should have a file called **/etc/network/interfaces**.  If you have removed it, you can create it.  The information we entered yesterday for wlan0 is still in this thread.  You can configure one of the wired interfaces as well.

---

### Post by Dwiman89 on 2007-09-21
no is still there. everything was working then all of the sudden webpages wouldn't load. and Gaim lost connection. i know it has to be the computer becaus i can get on the internet with my computer booted into windows.somethings wrong withthat file. I cant tell whats going on because i dont have my network manager. once this is all solved. how do i make connections and whatnot without a manager?

---

### Post by noob12 on 2007-09-21
You can also reinstall the network manager from the installation CD-ROM

Put in the CD-ROM and type
```

sudo apt-cdrom add
sudo apt-get install network-manager network-manager-gnome

```

---

### Post by Dwiman89 on 2007-09-21
Sorry, but for some reason it is still trying to retrieve the network manager from the internet.will it work to boot up from live cd?

---

### Post by noob12 on 2007-09-21
I think I was wrong and those packages aren't distributed in the normal form on the CD-ROM.

If you can boot the live CD and have network access that way, then you can download the packages as .deb files using the web browser.  You will need to store the files on the real hard drive, which will show up in the Nautilus explorer on the left but won't necessarily be mounted by default.

You can also store the fles when booted with Windows and copy them from the NTFS partition when booted in Ubuntu.

These assume your box is an Intel x86 machine:

web-pages:
[http://packages.ubuntu.com/feisty/net/network-manager](http://packages.ubuntu.com/feisty/net/network-manager)
[http://packages.ubuntu.com/feisty/net/network-manager-gnome](http://packages.ubuntu.com/feisty/net/network-manager-gnome)

packages:

network-manager:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager_0.6.4-6ubuntu7_i386.deb&md5sum=c6bd08b4ef893db4fb0b645e2b41b6c6&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager_0.6.4-6ubuntu7_i386.deb&md5sum=c6bd08b4ef893db4fb0b645e2b41b6c6&arch=i386&type=main)

network-manager-gnome:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager-gnome_0.6.4-6ubuntu7_i386.deb&md5sum=ecf2571f6f9cb3b0fcf7722d59b0c023&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fnetwork-manager%2Fnetwork-manager-gnome_0.6.4-6ubuntu7_i386.deb&md5sum=ecf2571f6f9cb3b0fcf7722d59b0c023&arch=i386&type=main)

---

### Post by Dwiman89 on 2007-09-21
um what is the the Nautilus explorer?

---

### Post by noob12 on 2007-09-21
It is the GNOME file explorer.  **Places | Computer** for example will bring up a Nautilus file explorer window.

---

### Post by noob12 on 2007-09-21
If you really get stuck, you might just want to copy your own files off, reinstall Ubuntu, buy a wireless adapter for the Windows box and you are done.

---

### Post by Dwiman89 on 2007-09-21
Is there a GUI app out there that can do what im tring to do that you know of?

---

### Post by Dwiman89 on 2007-09-21
Do you think it would be a good idea and how hard would it be if i where to put my wireless pci card in the windows box and get the enternet to the ubuntu box from there.
    Ii would just be so cool tohave internet on both and not have to  keep barrowing a flash drive every time i want to transfer something and use only one keybord and mouse(it gets confusing with two keybords and mice)
If you think this is a good cheep way of fixing things can you help me please?

---

### Post by noob12 on 2007-09-21
In your situation I think a better way is to spend a little on a separate card for the windows box and have both connecting directly wirelessly to your wifi access point.   I think that this solution is going to be the most painless and flexible for you.

---

### Post by Dwiman89 on 2007-09-21
yeah but right now i am limited on funds. and making my linux box get the internet through my xp box via wireless i would have internet on both and be able to share files and get synergy working. any help would be greatly appreciated. :)

---

### Post by Dwiman89 on 2007-09-22
ive set every thing to static and ive got pings to go threw from both boxes. i got it to where i got my wireless internet on the xp box. can you please help me get the internet working on linux?

---

### Post by noob12 on 2007-09-22
I'm not sure what you mean by this  > i got it to where i got my wireless internet on the xp box.

I don't think I'll be able to help you through this setup.  It's not one I'm familiar with.   If you followed the instructions so far on this thread, you should have the wireless configured on the wifi net and you should also have eth0 able to ping the xp box.  The next steps were suggested by mips, and it's not a method I'm familiar with.  Maybe you can ping him for help?

---

### Post by Dwiman89 on 2007-09-22
Well good news. I switched my wireless card over to the xp box and now both computers can access the internet. i don't really know how i got to this point but its great. 
   Now that the two computers are communicating, my next goal is to get file sharing. I got a chance to play around with it last night. On the linux box, my other computer shows up but when i try to access it it wants me to put in some sort of password. I never specified a password for this.
    My linux box doesn't show up on the xp box though, im guessing this is due to me not  adding any shared folders to the share on the linux box. I tried to add my home folder but a box kept popping up asking me to install SMB and NFS in order to share. i clicked install but the same box just kept popping up over and over again. 
Can you guys help please? thank you.

---

### Post by deadgobby on 2007-09-28
Look like you solv  ed most of your problems. I did not notice till now that you sent me a email
Did you resolved every thing in your email?
Gobby

---

### Post by Dwiman89 on 2007-09-29
its cool. i gave up. ill just have tto stick to one computer...

---

### Post by FredDie3785 on 2007-12-13
Hey I've got a question to all of you.

I have the ASMAX Wireless USB 411G (ZyDas chipset), and I've got a question. Can I share my DSL Internet Connection to other machines with that adapter??

---

