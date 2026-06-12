---
title: "ndiswrapper trouble - SAVE ME!"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by Carleton91 on 2007-07-08
I have followed the HOWTO on installing ndiswrapper, and it lists the version correctly and it gives me a list of commands when i type ndiswrapper.  I downloaded the driver for my wireless card (Linksys WMP11 v2.7) but i run into trouble when i try to install the driver.

I have the .inf, .sys, and .cat files in a folder on my desktop. The name of the .inf file is WMP11V27.inf

I type [FONT="Courier New"]ndiswrapper -i WMP11V27.inf[/FONT]

and this is my output:

installing wmp11v27 ...
couldn't open WMP11V27.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.

after this when i try ndiswrapper -l
i get that wmp11v27 is an invalid driver.

I've read the entire thread between Kevdog and Erky, but that suggestion didn't work for me. Please if anyone can help me with this issue I would be incredibly grateful.  I love my experience with Linux so far (like a week) but if I can't get my wireless card working I'm going to have to switch back to Windows :( Please help me

---

### Post by justind on 2007-07-08
I was having the same issue, then I tried this:

```
sudo rm -R /etc/ndiswrapper/*
```

Then after that try this:

```
sudo ndiswrapper -i WMP11V27.inf
```

Once you get it installed right you will be in the same spot I am only for your sake I hope your card works and you don't get stuck like I am.

---

### Post by Carleton91 on 2007-07-08
K i entered that code, but when I tried installing the driver again i got the same output, any other suggestions?

---

### Post by justind on 2007-07-08
use this again:

```
sudo rm -R /etc/ndiswrapper/*
```

Then unistall ndiswrapper. Reinstall it and try to do the driver. Other than that I'm not sure. I'm still a noob.

---

### Post by kevdog on 2007-07-08
Go to the /etc/ndiswrapper directory.  Ensure there are no files or directories in this directory.  If there are, delete EVERYTHING!.

Then reinstall the driver
sudo ndiswrapper -i ****.inf

---

### Post by kevdog on 2007-07-08
Can you please post the following also:

lspci -nn
lshw -C network

Thanks.

---

### Post by Carleton91 on 2007-07-08
Phew! I got the driver installed, turns out i wasn't in the folder where the driver files were when i was trying to install them :oops:  I'll post those things you requested, i just need to copy and paste them and then reboot to windows on my comp (using my brother's atm).

---

### Post by Carleton91 on 2007-07-08
Results from lspci -nn

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**01:07.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)**
01:0b.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

Results from lshw -C network

WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@01:07.0
       logical name: eth1
       version: 02
       serial: 00:06:25:1c:40:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical

where do I go from here? i've been trying the things that you suggested to Erky, but I haven't had any luck so far

---

### Post by kevdog on 2007-07-08
You currently have no driver associated with your card.  Not a problem.

Do you have the windows XP drivers for the card -- either on a CD or from the linksys website?

It sounds like you have them on your Desktop.

Please post 
ndiswrapper -v

Then when you issue command 
ndiswrapper -l

Make sure no driver is listed.  If you have a driver listed, you will have to totally delete all the contents of the /etc/ndiswrapper folder.
Once ndiswrapper -l lists nothing -- no driver then

cd ~/Desktop
sudo ndiswrapper -i ****.inf  <---Make sure .sys and .inf files are on the Desktop
Then see if installation was successful:
ndiswrapper -l

Something should be listed without an error!

---

### Post by Carleton91 on 2007-07-09
root@paul-desktop:~# ndiswrapper -l
wmp11v27 : driver installed
        device (14E4:4301) present (alternate driver: bcm43xx)

root@paul-desktop:~# ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 586 
root@paul-desktop:~# 

so it looks like the driver is installed, but no dice on the actual connection.  Do I need to point the driver to the device or something?

---

### Post by kevdog on 2007-07-09
Great you are coming along (Its not supposed to work by now!)

Ok lets keep going

```
sudo dmesg -a  <--- If there is no error, continue
sudo modprobe -i ndiswrapper
sudo ndiswrapper -m
echo ndiswrapper | sudo tee -a /etc/modules

```

To verify the module was loaded into the kernel without any errors

```
dmesg | grep ndiswrapper
```

You should see something like:

> wlan0: ndiswrapper ethernet device "xx:xx:xx:xx:xx:xx"

Ok at this point after a reboot your wireless may or may not work.  The reason it may not work is that some modifications may be needed for your /etc/network/interfaces, and /etc/iftab file.

If after a reboot, nothing works, then post the contents of these two files, along with lswh -C network

---

### Post by Carleton91 on 2007-07-09
OK I did what you suggested and posted the results in this file

entering "dmesg -a" told me that it was an invalid command, so i tried dmesg -C since that's what it suggested.

---

### Post by kevdog on 2007-07-09
Sorry it was my fault.  It was supposed to be:

sudo depmod -a

Anyway reboot, and with the network card in place, cut and paste the following:
lshw -C network

And include the files
/etc/network/interfaces
/etc/iftab

---

### Post by Carleton91 on 2007-07-09
Ok, here are the results:

root@paul-desktop:~# lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@01:07.0
       logical name: eth1
       version: 02
       serial: 00:06:25:1c:40:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=32 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:fe9fc000-fe9fdfff irq:20


/etc/netowrk/interfaces:

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid 2WIRE154
wireless-key 3127487812

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1

/etc/iftab:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:01:6c:a9:31:ec arp 1
eth1 mac 00:06:25:1c:40:02 arp

---

### Post by kevdog on 2007-07-09
First do the following:
```

gsku gedit /etc/modprobe.d/blacklist
```

Add to the bottom of the file:
```

blacklist bcm43xx
```

Reboot.

Then can you repost the last 3 three things I asked for.

As for your router, turn off any WEP/WPA or MAC filtering for now.  We can add this later.  I just want basic connectivity first.

---

### Post by Carleton91 on 2007-07-09
Ok here it is:

root@paul-desktop:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@01:07.0
       logical name: eth1
       version: 02
       serial: 00:06:25:1c:40:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wmp11v27 driverversion=1.47+Linksys,07/30/2002, 3.08.28 latency=32 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:fe9fc000-fe9fdfff irq:20

Iftab:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:01:6c:a9:31:ec arp 1
eth1 mac 00:06:25:1c:40:02 arp 1


Interfaces:

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid 2WIRE154
wireless-key 3127487812

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1
auto eth1

---

### Post by kevdog on 2007-07-09
Alright, great news -- your driver is now associated with your card:

> configuration: broadcast=yes[COLOR="Red"] driver=ndiswrapper+wmp11v27[/COLOR] driverversion=1.47+Linksys,07/30/2002, 3.08.28 latency=32 link=yes multicast=yes wireless=IEEE

So now we just have to do some cleanup

Based on what you presented, here is the MAC address of your wireless card:
> serial: 00:06:25:1c:40:02

But when I see your /etc/iftab file I see two MAC addresses listed:
> wlan0 mac 00:01:6c:a9:31:ec arp 1
eth1 mac 00:06:25:1c:40:02 arp 1

I think the only thing that should be in your iftab file is the following:
```
wlan0 mac 00:06:25:1c:40:02 arp 1
```

So you might have to edit it to reflect the changes: (gksu gedit /etc/iftab

Second lets take a look at your /etc/network/interfaces:
You have many interfaces listed.

> auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid 2WIRE154
wireless-key 3127487812

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth1
auto eth1

Lets back up the configuration
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

Now lets make a new interfaces file for you (gksu gedit /etc/network/interfaces)
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid 2WIRE154
wireless-key 3127487812
```

Reboot and lets see what happens!

---

### Post by Carleton91 on 2007-07-09
Well, I changed the files like you told me, but I'm not connected yet.  I've just been opening Firefox when I start ubuntu to check.  Is there a way like in windows where you can see a list of wireless connections that you can connect to?

Also are there any other files i can post that would be of any help?

---

### Post by kevdog on 2007-07-09
Do me a favor, turn off WEP on your router (or WPA) and have no MAC filtering.

Edit you /etc/network/interfaces file and remove the following or put a # sign in front of the lines:
wireless-essid 2WIRE154
wireless-key 3127487812

Once done, with the editing and router changes, do:
sudo /etc/init.d/dbus restart

Then from command terminal do:
iwlist scan

Post the above along with:
ifconfig

along with

lshw -C network

---

### Post by Carleton91 on 2007-07-09
Ooo, is there any way i can keep WEP on?  My router also gives internet access to three other computers in the house, and when i turned WEP off earlier today i discovered that it stops them from having internet, and I couldn't figure out how to reconnect to the the router wirelessly (i tried turning WEP off in my settings in windows to match the router, but still couldn't connect) so i ended up having to dig out an ethernet cable and shift my brother's computer around (the router is in his room) so i could plug it directly into the router.  To summarize it was a pain in the butt, and if pissed a couple people off :p

But, if it is absolutely necessary, i can do it again, but it will have to be when everyone but me is at work, so like 3 eastern tomorrow.  

Is there anything else i can do in the mean time?

---

### Post by kevdog on 2007-07-09
Ok dont make the changes to the interface file. 

Post 
iwlist scan
ifconfig
lshw -C network

---

### Post by Carleton91 on 2007-07-09
Oh... i rebooted before I saw that, but I did the iwist and got what i think is my router :)

here's what came up:

```
root@paul-desktop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0D:72:74:C9:69
                    ESSID:"2WIRE154"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

root@paul-desktop:~# 
```

I'll reboot and post those other things now.

---

### Post by Carleton91 on 2007-07-09
Okey doke, here are the results of ifonfig and lshw -C network

```
root@paul-desktop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:A9:31:EC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1332 (1.3 KiB)  TX bytes:1332 (1.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:06:25:1C:40:02  
          inet6 addr: fe80::206:25ff:fe1c:4002/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Memory:fe9fc000-fe9fe000 

wlan0:ava Link encap:Ethernet  HWaddr 00:06:25:1C:40:02  
          inet addr:169.254.1.175  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:fe9fc000-fe9fe000 

root@paul-desktop:~# 


root@paul-desktop:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@01:07.0
       logical name: wlan0
       version: 02
       serial: 00:06:25:1c:40:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wmp11v27 driverversion=1.47+Linksys,07/30/2002, 3.08.28 latency=32 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:fe9fc000-fe9fdfff irq:20

```

---

### Post by kevdog on 2007-07-09
The good news is that your wireless card is working -- it can see your router just fine.  The bad news is that it can not obtain an IP address

Ok here is what I want you to do.
Edit your /etc/network/interfaces file and put a # sign in front of all the lines except the lines containing lo -- the loopback interface.

Once done, do
sudo /etc/initd./dbus restart

You are using Kubuntu right?? 
See if you have Knetworkmanager package installed.

I think you can do
sudo aptitude search knetworkmanager

Post what it says!

Hopefully it will look like
i knetworkmanager -User friendly KDE frontend for NetworkManager

If this doesnt work then we are going to have to issue manual commands.

---

### Post by Carleton91 on 2007-07-10
I'm using just regular ubuntu, so when i tried doing the first command nothing happened, and the second one just said that program isn't installed.

After i changed my interface files like you said though, I moused over the network icon in the top right of the screen, and my router was an option to connect to.  The only problem was that it said that it wasn't the right password, so I'm going to try to disable encryption tomorrow and see if i can get it to work.  Thank you so much for the help so far

---

### Post by kevdog on 2007-07-10
If you are using regular Ubuntu - great

Do the following:
System->Administration->Networking

Select wireless connection -> Properties

Enable roaming mode!

See if you can connect.  You might have to do a manual configuration like entering WEP key.  Again make sure there is only the loopback commands in the /etc/network/interfaces file!

---

### Post by Carleton91 on 2007-07-10
OK, so I enabled roaming mode, and when i mouse over the network icon i can see my network as an option, I click on it to connect, but whether i have encrpytion on or not, it doesn't connect.  It just says Connecting to network, then it switches to the orange "!" triangle thing and says no network connection I've tried multiple times with encrpytion on and off.

Oh and what does the 64 bit ASC II option mean when it asks me for a passcode? I'm almost positive that my router is 64 bit hex, since its 10 digits long but I don't know what ASC II means

---

### Post by kevdog on 2007-07-10
What if you try the following with the applet:

Select Manual Configuration
Choose your wireless interface -> Properties

Unclick enable roaming
Then fill in the boxes appropriatedly
ESSID
WEP key -- You can choose either Ascii (text you can read) or Hexidecimal (Letter and Numbers)

Then choose DHCP for connection type

As far as WEP goes -- use another computer to log into router and turn off the WEP key if you can.  If you cant, then at least make sure you have the correct Ascii or Hexadecimal Key
Also make sure your router is not set to do any MAC filtering.  

See what happens.

If this doesnt work then we are going to have to type everything at the command line to see if we can at least get a signal

---

### Post by Carleton91 on 2007-07-10
ok i tried doing manual configuration, but still no luck :(

---

### Post by kevdog on 2007-07-10
Is WEP turned off or on??

---

### Post by kevdog on 2007-07-10
If WEP is turned off try the following

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "My Network"

If everything you are receiving in the terminal looks good, then type
sudo dhclient  <---This should give you a dyanamic IP address

---

### Post by Carleton91 on 2007-07-10
k i turned WEP off and this is what i got when i entered the above:

root@paul-desktop:~# sudo iwconfig essid "2WIRE154"
Error : unrecognised wireless request "2WIRE154"
root@paul-desktop:~# sudo iwconfig essid "My Network"
Error : unrecognised wireless request "My Network"
root@paul-desktop:~# sudo dhclient
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:06:25:1c:40:02
Sending on   LPF/wlan0/00:06:25:1c:40:02
Listening on LPF/eth0/00:01:6c:a9:31:ec
Sending on   LPF/eth0/00:01:6c:a9:31:ec
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


the first two ifconfug commands did not return anything

---

### Post by kevdog on 2007-07-10
Again kind of experimenting with this one:

#1.  Make sure you can see your network -- If the card cant see it, no way a connection can be made.  To see if the network is visible

```
iwlist wlan0 scan
```

Please post this output

#2. Assuming you can see your router called "2WIRE154", then lets try to connect manually.  I gave the instructions in the last post, however I think you mistyped the instructions:

Your entry: sudo iwconfig essid "2WIRE154"
Correct entry: sudo iwconfig wlan0 essid "2WIRE154"

Lets do the following:

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "2WIRE154"
sudo ifconfig wlan0 up
```

Please post the output of above, thanks! -- please be careful about your typing!

---

### Post by Carleton91 on 2007-07-10
Ok, so I did that, but i got the same output from dhclient as before BUT when i disabled networking and then reenabled it, i tried connecting like i had a 1000 times before, only this time it worked! :)  I got the little bar thing with signal strength and everything.

Only issue is that i opened firefox and still got the same Try Again screen :(

So it says I'm connected, but no internet.  Any suggestions?

---

### Post by Carleton91 on 2007-07-10
](*,)  I just rebooted and could not get the connection thing i had going there back

---

### Post by kevdog on 2007-07-10
Try a few things after rebooting

Try to connect -- if doesnt work

sudo /etc/init.d/networking restart

Try again, if doesnt work

sudo /etc/init.d/dbus restart

Try again -- if doesnt work

Try manual settings as in previous post

And if this doesnt work, please post entire dmesg output.
dmesg > dmesg.txt
Include as attachment dmseg.txt

---

### Post by Carleton91 on 2007-07-10
Ok, above suggestions were unsuccessful.  Here is dmesg.txt, I had to compress it.

---

### Post by kevdog on 2007-07-10
Please post:
iwlist wlan0 scan

Are you sure WEP is off along with no MAC filtering on the router??

---

### Post by kevdog on 2007-07-10
Try the following and give me a synopsis of the output

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 mode Managed
sudo iwconfig wlan0 essid 2WIRE154
sudo ifconfig wlan0 up

```

---

### Post by Carleton91 on 2007-07-10
Haha! This was posted using Ubuntu! I turned WEP off again like you told me and then did the ifconfig down iwconfig combo and then dhclient got me an IP address.  My issue now is going to be putting encryption back on, I'll keep you posted :)

---

### Post by Carleton91 on 2007-07-10
So... I've tried tinkering with encrpytion, but the issue seems to be that my Windows PC's down the hall have issues connecting when the encryption is off, probably due to some firewall issue, but my Ubuntu computer has issues connecting when its on.

Is there a way to manually connect like we just did but add the encrpytion key on to the end next to essid?

---

### Post by kevdog on 2007-07-10
Here is what I was able to dig up:

iwconfig [interface] key 1111-1111-1111-1111 (set 128 bit WEP key)

iwconfig [interface] key 11111111 (set 64 bit WEP key)

iwconfig [interface] s:mykey (set key as an ASCII string)

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 mode Managed
sudo ifconfig wlan0 (INSERT APPROPRIATE FORMAT HERE FROM 3 CHOICES ABOVE)
sudo iwconfig wlan0 essid 2WIRE154
sudo ifconfig wlan0 up

```

---

### Post by Carleton91 on 2007-07-11
It worked!!

Thanks a million kevdog!!

---

### Post by kevdog on 2007-07-11
We can automate this if you want so you dont have to type it everytime!

---

### Post by Carleton91 on 2007-07-11
haha i just got home and 15 minutes of typing later I'm connected, I would love to automate it! :)

also can we make it so I can do it when I'm not logged in as root? I hear that being root while connected to the internet can mean bad times

---

### Post by kevdog on 2007-07-11
Why are you logged in as root???

Well try this

```
sudo ifconfig wlan0 down
sudo mv /etc/network/interfaces /etc/network/interfaces.bak
gksu gedit /etc/network/interfaces
```

Then add
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
     wireless-mode managed
     wireless-essid <your wireless SSID>
     wireless-key XXXXXXXX  <---Use previous key that worked on command line
auto wlan0

```


Save the file

```
sudo /etc/init.d/dbus restart
```

Hopefully that will work for you

---

### Post by Carleton91 on 2007-07-11
Well that automation did not end up working out, but I logged on as my regular user name since up to your comment I had thought I was supposed to be in root.

but anyway, I had some issues getting connected manually again and I figured I would post terminal text so you could see.  I'm not sure exactly what was going on, but it seemed like sometimes when i entered the commands, they didn't do anything, but other times they worked.  I think maybe the inclusion or omission of quotes may have made the difference but I'm not sure.

See for yourself.


EDIT: I've done some more tinkering around, and I've discovered that after i run sudo dhclient and it fails, if I type the series of commands for the manual connection, and then run sudo dhclient again, i get an ip address.  I'll keep testing.

---

### Post by Carleton91 on 2007-07-11
So I think as it turns out the quotes around "2WIRE154" are crucial.  I'm going to check if i can do the automation now with some different quotes

---

### Post by Carleton91 on 2007-07-11
More weirdness.... I did a /networking restart and a /dbus restart and then i tried connecting and here's what happened

it seems almost like I have tell it the essid with and without quotes.

---

### Post by kevdog on 2007-07-11
Do you have a wired connection eth0 and a wireless connection wlan0 going at the same time???  I see from what you posted both wlan0 and eth0 are listed.

---

### Post by Carleton91 on 2007-07-11
Nope, only the wireless, is there some way to disable the wired card?

---

### Post by Carleton91 on 2007-07-11
My iftab file doesn't contain anything about wired either:

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

wlan0 mac 00:06:25:1c:40:02 arp 1

---

### Post by kevdog on 2007-07-11
Make sure only the lo and wlan0 interfaces are mentioned in the /etc/network/interfaces file.
Delete lines of other interfaces!

---

### Post by Carleton91 on 2007-07-11
Yea, 

auto lo
iface lo inet loopback

is the only thing in my interfaces file right now, so I don't know where that eth0 thing is coming from

---

### Post by kevdog on 2007-07-12
Please do the following:

lshw -C network


This will show all networking devices

---

### Post by Carleton91 on 2007-07-12
Ok, so I when I booted up today i plugged in the exact same 4 commands twice, except they didn't work until the second time.  After that I did the lshw -C network.  Here's the script:

```
paul@paul-desktop:~$ sudo ifconfig wlan0 down
Password:
Sorry, try again.
Password:
paul@paul-desktop:~$ sudo iwconfig wlan0 essid "2WIRE154"
paul@paul-desktop:~$ sudo iwconfig wlan0 key 3127487812
paul@paul-desktop:~$ sudo ifconfig wlan0 up
paul@paul-desktop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:06:25:1c:40:02
Sending on   LPF/wlan0/00:06:25:1c:40:02
Listening on LPF/eth0/00:01:6c:a9:31:ec
Sending on   LPF/eth0/00:01:6c:a9:31:ec
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
paul@paul-desktop:~$ sudo ifconfig wlan0 down
paul@paul-desktop:~$ sudo iwconfig wlan0 essid "2WIRE154"
paul@paul-desktop:~$ sudo iwconfig wlan0 key 3127487812
paul@paul-desktop:~$ sudo ifconfig wlan0 up
paul@paul-desktop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 5605
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:06:25:1c:40:02
Sending on   LPF/wlan0/00:06:25:1c:40:02
Listening on LPF/eth0/00:01:6c:a9:31:ec
Sending on   LPF/eth0/00:01:6c:a9:31:ec
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 172.16.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 172.16.0.1
bound to 172.16.1.38 -- renewal in 1654 seconds.
paul@paul-desktop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@01:07.0
       logical name: wlan0
       version: 02
       serial: 00:06:25:1c:40:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Linksys,07/30/2002, 3.08.28.0 ip=172.16.1.38 latency=32 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:fe9fc000-fe9fdfff irq:20
paul@paul-desktop:~$ 

```

---

