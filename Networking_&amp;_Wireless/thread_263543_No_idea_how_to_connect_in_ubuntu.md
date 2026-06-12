---
title: "No idea how to connect in ubuntu"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by Grantax on 2006-09-23
I've got my new laptop today, and also a new wireless router.
I've tried connecting to it with a laptop with windows on it, and it worked fine.
I have no idea how to connect with ubuntu, but I tried installing the 'Wireless Assistant', but it shuts down as soon as I starts, after giving me this error:
"No usable wireless devices found.
Wireless Assistant will now quit."

Laptop:
FSC Amilo Li1720

Router:
Linksys WRT54GL

---

### Post by tagra123 on 2006-09-23
You may need to use ndiswrapper for your card to be usable.

Search for ndiswrapper in these forums or google.

---

### Post by Grantax on 2006-09-23
Can I use 'sudo apt-get install ndiswrapper' ?

---

### Post by Grantax on 2006-09-23
How do I install it?
I tried using the 'make' command, but it's not working..

---

### Post by tagra123 on 2006-09-23
You can use apt-get install ndiswrapper to install it.

You may have to enable the universe and multiverse repositories for it to install.

---

### Post by Grantax on 2006-09-23
I'm a new linux user as I said..
How do I do that?

Edit: I found it in the package list thing, and I installed ndisgtk and ndiswrapper-utils, and I restarted, but I am still getting the same problem...

---

### Post by tagra123 on 2006-09-23
I think this how-to may help.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Grantax on 2006-09-23
Ok, I will uninstall my installation tomorrow, and read that tutorial.

---

### Post by Grantax on 2006-09-24
Ok, I did what the tutorial told me, but It doesn't work, I got this far:

  sudo depmod -a
  sudo modprobe ndiswrapper
  tail /var/log/messages

After I typed that, I was supposed to get no error messages, but I got a couple.. And the tutorial doesn't explain what to do if I'm getting error messages, but these are the errors I got:

localhost gconfd (root-7996): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

localhost gconfd (root-7996): GConf server is not in use, shutting down.

localhost gconfd (root-7996): Exiting

localhost kernel: [17183224.548000] ndiswrapper version 1.8 loaded (preempt= yes,smp=no)

localhost kernel: [17183224.552000] ndiswrapper: driver net5211 (,09/15/2005,4.1.2.111) loaded

localhost kernel: [17183224.556000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 209

localhost kernel: [17183224.968000] ndiswrapper: using irq 209

localhost kernel: [17183224.976000] wlan0: vendor: ''

localhost kernel: [17183224.976000] wlan0: ndiswrapper ethernet device 00:c0:a8:ba:47:56 using driver net5211, 168C:001C.5.conf

localhost kernel: [17183224.976000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK



Edit: And instead of the .sys, .inf and .bin file the tutorial tells me to put in 1 folder, I only had .sys, .inf and a .cat file. (no .bin file)

---

### Post by lnxnewbie on 2006-09-24
Grantax,
Do you know what wireless chipset is in your laptop?
Ubuntu supports wireless right out of the box for a number of chipset.

---

### Post by Grantax on 2006-09-24
Notebook: Fujitsu-Siemens CELSIUS H240

    * Chipset: Atheros Communications, Inc. Unknown device 001c (rev 01)
    * pciid: 168c:001c (rev 01)

Edit: I don´t know the difference, but before I started the tutorial, I uninstalled it through the package list (Synaptic something) by selecting 'Mark for Removal', not 'Mark for Complete Removal'..
What is the difference?

---

### Post by tagra123 on 2006-09-24
> **Grantax said:**
> Ok, I did what the tutorial told me, but It doesn't work, I got this far:

  sudo depmod -a
  sudo modprobe ndiswrapper
  tail /var/log/messages

After I typed that, I was supposed to get no error messages, but I got a couple.. And the tutorial doesn't explain what to do if I'm getting error messages, but these are the errors I got:

localhost gconfd (root-7996): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

localhost gconfd (root-7996): GConf server is not in use, shutting down.

localhost gconfd (root-7996): Exiting

localhost kernel: [17183224.548000] ndiswrapper version 1.8 loaded (preempt= yes,smp=no)

localhost kernel: [17183224.552000] ndiswrapper: driver net5211 (,09/15/2005,4.1.2.111) loaded

localhost kernel: [17183224.556000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 209

localhost kernel: [17183224.968000] ndiswrapper: using irq 209

localhost kernel: [17183224.976000] wlan0: vendor: ''

localhost kernel: [17183224.976000] wlan0: ndiswrapper ethernet device 00:c0:a8:ba:47:56 using driver net5211, 168C:001C.5.conf

localhost kernel: [17183224.976000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK



Edit: And instead of the .sys, .inf and .bin file the tutorial tells me to put in 1 folder, I only had .sys, .inf and a .cat file. (no .bin file)


I have one belkin router that I had to install the windows drivers. I don't think I had the bin file either.

It looks to me like it might be recognizing your card now. As I recall I had similar messages. 

Until you get everything working turn off the WEP or other protection on your router. Once you get it working turn it back on. Most routers have a web interface to do this. See the routers instructions.

Try using the System > Administration > Networking and seeing if the wlan (wireless router is showing up now.)

If it is Activate it. The click on properties.  Select the ESSID (Name of the wireless network) Most routers broadcast this unless its been turned off. Select DHCP and then close the box. Close the Networking box.

It should work if wlan was detected.

If not try System > Administration > Networking again.

This time click on deactivate, then activate. Close it.

THe networking might work at this point.

By the way if it gets too frustrating: Most belkin cards work out of the box, without ndiswrappeer, but not all of them. A belkin f5d7010 PCMCIA card worked with no effort except setting it to the corect router essid. I entered the essid, wep and it worked.

---

### Post by Grantax on 2006-09-24
I´ve already done what you said.
I could access wlan0 in the networking thing, and I´ve set the essid to the same as ssid in the router config.
WEP has always been off, because the router is new.
I have selected DHCP.

I have installed Wireless Assistant, as I mentioned earlier, and after I installed the drivers, wireless assistant worked.
But it doesn´t find any networks.

Edit: I get negative output when trying sudo ifup wlan0 (I'm not entirely sure if that was the command.. but something like that)

---

### Post by tagra123 on 2006-09-24
Do you happen to also have a eth0? If so deactivate it. I recall this giving be a problem on the desktop.

It appears that the computer is detecting the card so you sound real close.

You may also try setting a static ip using the networking box

Should be something like:

Static

IP 192.168.1.100
   255.255.255.0
   192.168.1.1

Might help?


And make sure the connection at the bottom is wlan0 or whatever your wireless card is above

---

### Post by tagra123 on 2006-09-24
Try the following (some addresses may need change for your router/computer)

```
sudo cp /etc/network/interfaces /etc/network/interfaces.nonworking.backup
sudo gedit /etc/network/interfaces.dhcp.withoutwep
```

ADD THIS TO THE FILE

```

# This file describes the network interfaces available on your
system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#auto eth0

# The primary network interface


#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
broadcast 192.168.1.255
wireless-essid yourwifi
#EDIT THE LINE ABOVE "YOURWIFI" needs to be changed.

```

save the file and the copy it

```
sudo cp /etc/network/interfaces.dhcp.withoutwep /etc/network/interfaces
```

Reboot the computer and see if the networking will work now. You may still need to go to system-administration-networking and click on activate.

since you saved a backup you can get to where you were before by copying the original file back if you need to.

```
sudo cp /etc/network/interfaces.nonworking.backup /etc/network/interfaces
```

---

### Post by Grantax on 2006-09-24
Will do..
The eht0 is deactivated.. I did like the tutorial posted in the first page said, so the wired connection isn´t working for me anymore.

How do I reverse this?

sudo killall dhclient
sudo ifconfig eth0 down

---

### Post by Grantax on 2006-09-24
I'm trying to start my laptop but it stops at 'Configuring network interfaces'.......

Edit: nvm it just took about a minute..

Edit: Sorry, non of the above worked for me. But thanks for trying, I really want this to work..

Edit: A little update: When I set the properties thing to DHCP, and my Default gateway device to wlan0, it always goes back to nothing. (The next time I open network settings, the default gateway device is nothing..)

But when I set it to a static IP adress, then the default gateway device stays the way I set it, and last time I selected my Network connections, I could actually TRY to connect to my network. (That was before the reboot, now I can't do it anymore)

Even though I could try to connect to the network, it never succeeded.

Edit: I set it up myself now and the wireless connection thing shows up all the time, I'm trying to connect to 'linksys' (which is the ssid of the router), but it times out..

---

### Post by tagra123 on 2006-09-24
I found some links that might be helpful.

[http://www.ubuntuforums.org/showthread.php?t=258801](http://www.ubuntuforums.org/showthread.php?t=258801)

I found this in an article at [http://mymindandi.blogspot.com/2006/09/review-of-ubuntu-606-lts-dapper-drake.html](http://mymindandi.blogspot.com/2006/09/review-of-ubuntu-606-lts-dapper-drake.html)

> On the Laptop things went beautifully. The Atheros wireless adapter was automatically detected. All I had to do was enter my essid and my wep encryption key. That was it. I was even impressed to see that, when I entered my essid and encryption key while in live mode and then installed Ubuntu to my hard drive, my wireless settings where transferred to my HD install.

Mikes me wonder if booting from the live cd and then entering your essid would be helpful.

Oh, Oh. The router. I just remembered Windows XP will change the wireless settings sometimes. WEP or WPA may have been turn on by XP.

---

### Post by Grantax on 2006-09-25
First of all, in the other thread, the guy´s network card could actually find access points, mine can't.

And the CD thing doesn´t work for me either. (It doesn't decect my card)

Edit: When I entered 'iwlist wlan0 frequency, it sais that it was on channel 1, and my router is on channel 11, I changed it, but it still won´t find my network.
And in the wlan0 configuration I didn´t enter any essid.. because I see no point of entering it there when I will connect to different networks..

And when I connect, and I input the Network Name, am I supposed to enter the ssid there? (Or maybe domain name of the network?)

And as usual, I can't set the default networking device.

And what terminal command do I have to you to run Wireless Assistant?

---

### Post by wieman01 on 2006-09-26
Please run the following commands and post the output here:
> ifconfig
> iwconfig
> iwlist wlan0 scan
> route
> gedit /etc/network/interfaces
> gedit /etc/resolv.conf
> sudo /etc/init.d/networking restart
Run the commands from a terminal & post the contents. It's important to understand what's going on. 

Also are you using any kind of encryption/authentication? WEP, WPA, WPA2? Does the router have DHCP enabled? MAC filtering enabled?

You're close.

---

### Post by Grantax on 2006-09-26
No, no kind of encryption.
DHCP is enabled.
Mac filtering is disabled.

Interfaces:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
```

Resolv.conf:
```
search MSHOME
nameserver 193.75.75.75
nameserver 193.75.75.193
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:B7:E0:88
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0x8800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:BA:47:56
          inet6 addr: fe80::2c0:a8ff:feba:4756/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Memory:d0100000-d0110000
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

iwlist wlan0 scan:
```
wlan0     No scan results
```

route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

sudo /etc/init.d/networking restart:
```
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:c0:a8:ba:47:56
Sending on   LPF/wlan0/00:c0:a8:ba:47:56
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:c0:a8:ba:47:56
Sending on   LPF/wlan0/00:c0:a8:ba:47:56
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]
```

---

### Post by wieman01 on 2006-09-26
I think it's obvious... You're wireless network card is enabled but the router is turned of. Could that be?

This delivers no results which is a pretty good sign that there are no wireless networks around.
> iwlist wlan0 scan
Please check the router once again. "resolv.conf" indicates that you have been connected before one way or the other (through Ethernet?).

---

### Post by tagra123 on 2006-09-26
> **wieman01 said:**
> I think it's obvious... You're wireless network card is enabled but the router is turned of. Could that be?

This delivers no results which is a pretty good sign that there are no wireless networks around.

Please check the router once again. "resolv.conf" indicates that you have been connected before one way or the other (through Ethernet?).

I mentioned before XP can change the routers settings, it asks for approval, but it can change them including WEP.


Also I would like to add the essid appears to be transmitting, or at least  before it was.  

Maybe  pushing the factory reset button on the router may help.

---

### Post by wieman01 on 2006-09-26
> **tagra123 said:**
> I mentioned before XP can change the routers settings, it asks for approval, but it can change them including WEP.

Also I would like to add the essid appears to be transmitting, or at least  before it was.  

Maybe  pushing the factory reset button on the router may help.
Ok, I must have missed that since I came in late. Have not read the whole thread. But there is something wrong under the hood.

---

### Post by Grantax on 2006-09-26
I've also mentioned that with another laptop with windows installed I could connect to the same router.

Edit: Yeah, I used to be connected through ethernet.

Can you tell me what 'Wireless ssid broadcast' means?

---

### Post by wieman01 on 2006-09-26
> **Grantax said:**
> Can you tell me what 'Wireless ssid broadcast' means?
That the name of your wireless network that the router broadcasts. I strikes me though that your wireless network card does not "see" your network. So if you're saying that your router is up & running, then it must be your wireless card that is malfunctioning.

---

### Post by Grantax on 2006-09-26
Maybe I should just install windows and try there..
Wouldn´t surprise me if it´s malfunctioning, because I'm the unluckiest person in the world and I've never in my life had a working computer.

---

### Post by Grantax on 2006-09-26
I installed windows and the drivers, but I couldn't find the network.
It said: "Make sure the wireless switch on your computer is on". (What does that mean?)
(FYI: By mistake I created a wireless network, I'm not sure if it affects how I can connect to other networks)

---

### Post by wieman01 on 2006-09-26
Oh, I have seen this before. Mmm... You can switch your wireless card on & off using a certain keyboard combination. Can you try this? I think that's your problem then.

Sometimes your wireless card is simply deactivated (hardware switch) and you have to turn it on in order for the wireless card to function. Do you happen to have a switch somewhere? Or a "FN" key on you keyboard?

If you switch that on, Ubuntu will be fine too.

You can also try to "enable" your wireless network unter "network settings" in Windows.

Does that help? I have seen this before.

---

### Post by Grantax on 2006-09-27
Ok, I'm gonna strangle the closest person to me if that´s the solution.
What would the combination be?

---

### Post by wieman01 on 2006-09-27
On my keyboard it's "FN + F2". You may also have a wireless switch somewhere else. Really depends. 

But also try to enable the wireles network under Windows.

If you cannot find anything check your PC manual or give the vendor a buzz. :-) But I think we're close.

---

### Post by Grantax on 2006-09-27
If you had known how unlucky I am when it comes to computers, you would have known that we are faaaaaaaaar away.

When this is fixed, I'm going straight back to ubuntu again.
Only problem I've had with ubuntu is sending the .odt files to a windows pc, and finding the correct character set, but mostly that´s windows´ problem.

---

### Post by wieman01 on 2006-09-27
Never ever give up. You now know what your problem is. Even Windows complains about the same thing. I am here to help you with the rest. :-)

---

### Post by Grantax on 2006-09-27
Pfft, if you had been through the same computers problems I´ve had the last year, you would have given up. :) ('I give up' is actually the subject of the last mail I sent to the company I´m buying my stuff from) :D

I've tried enabling it, but nothing works..

---

### Post by wieman01 on 2006-09-27
> **Grantax said:**
> Pfft, if you had been through the same computers problems I´ve had the last year, you would have given up. :) ('I give up' is actually the subject of the last mail I sent to the company I´m buying my stuff from) :D

I've tried enabling it, but nothing works..
Send this useless piece of hardware back to them. With kind regards! ;-)

---

### Post by Grantax on 2006-09-27
I will, just like I've did with everything else.

---

### Post by tagra123 on 2006-09-28
Heres a pcmcia card that works out of the box:

Belkin F5D7010 PCMCIA (For Laptop)  about US$30.00   


Belkin F5D7000 version3001  PCI (For Desktop) about US$30.00

I also use a Belkin router but any wireless g router should work.


Both of these cards were pretty much plug and play. All I had to enter was the ESSID and make sure the router was set to the same password. I use WEP 128 for our set up. Never messed with WPA but its supposed to work too.

While setting up everything I made sure the WEP was off until everything was working.

I think the desktop should be faster during NFS transfers but according to everyone I talk to they thik its getting full speed. I tried it on windows the other day and I think they may be right.



Office Max Might still have these online in clearance. I think walmart sells them too. 

Nice thing about walmart with questionable hardware for linus. Buy it, try it, if it doesnt work take it back and tell them -- it doesn't work with linux.

A comment about windows - the desktop card above was harder to get working correctly in windows (wanting to drop connections) then it was in linux. It stays connected in linux.

---

### Post by Fitzcarraldo on 2006-10-07
*tagra123*,

You were lucky with the Belkin F5D7010 PCMCIA card for wireless. My brother had a terrible job getting it to work (as documented in the following thread):

[http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813)

---

### Post by bmagyarkuti on 2006-10-30
Grantax, I have both good and bad news for you.

I have a Siemens Amilo LI1720 laptop, which has the same wireless configuration as yours (an Atheros AR5006EG card, built-in).

The solution for your Windows-related wireless problem is quite simple, at least, it was so for me. When booting, enter the BIOS of your computer (by pressing F2/F12), and look for an option to enable wireless. Your card is set to disabled by default, in order to ensure the security of your notebook in the store. Be careful not to touch anything sensitive in the BIOS, as it is quite easy to disorder your laptop from there. :)

Though this will solve your Windows problem, it will be of no help under Ubuntu (norther Fedora, I have been trying to make Linux wireless work for 3 days).

With Fedora, I couldn't even make ndiswrapper create a network interface for the built-in card, and now the strangest of all: my wireless USB stick, which worked with ndiswrapper on 3 Linux PCs and 2 Linux laptops for me was of no use either!!!

At this point I have decided to switch to ubuntu, as it is the most popular linux distribution. Ubuntu itself impressed me, though my wireless card (nor the usb stick) is still not working. Now, I get your no network found (interface doesent support scanning) message...

Any help (including information on how to find packages with apt-get) is appreciated.

Greetings:
Barney

---

### Post by wieman01 on 2006-10-30
Grantax has not been online for 4 weeks so I don't think he is keeping an eye on this thread.

Let's focus on your USB device first... What model have you got & what chipset is it using?

---

### Post by bmagyarkuti on 2006-11-03
Thank you for answering, and sorry for not visiting again for so long :)

I have a USR 5422 wirless adapter, it should work with ndiswrapper. However, after installing the ndiswrapper driver and loading the ndiswrapper module (modprobe ndiswrapper), the interfaci is added, still it is not able to connect to any network (no matter if it is encrypted or not).

---

### Post by happy-and-lost on 2006-11-03
Atheros... doesn't MadWIFI support that?

---

### Post by bmagyarkuti on 2006-11-04
It should.

Unfortunately, I seem to have found the only chipset it doesent: according to [this site]("http://madwifi.org/ticket/961"), my model is not supported before some 0.9 beta version of HAL.

Anyway, I am pretty confused with the entire madwifi terminology, so if you know more about it than me, I would appreciate your help.  Still, I'd prefer to use ndiswrapper. There are some [toshiba users]("http://www.jonhuxley.com/linux-laptops/") experiencing success with the factory windows driver and ndiswrapper on ar5006eg. Unfortunately, my siemens notebook's factory driver is not good enough for ndiswrapper.

Greetings: Barney

---

### Post by wieman01 on 2006-11-04
> **bmagyarkuti said:**
> Unfortunately, my siemens notebook's factory driver is not good enough for ndiswrapper.
Are you sure? Have you given it a go yet? Perhaps it does work with the latest driver from the vendor's website.

---

