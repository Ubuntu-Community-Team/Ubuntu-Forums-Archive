---
title: "Wireless troubles"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by osarusan on 2006-11-28
I'm running a Dell Inspiron 8000 with a Linksys PCMCIA wireless card. I followed a few of the guides here and was able to set it up correctly so Edgy detects the card, and the card can locate networks... however, I'm not able to connect to any networks!

I'm really new to Linux, so I'm sure I'm just doing something stupid... I've tried connecting to my home (secured) network, and it can detect it and everything, but just won't go on it. I've tried connecting it to some of the unsecured networks around, but it also won't connect them, even though it can locate them for me.

I'm really confused as to what more I can do. From all appearances, the driver and the card seem to be working fine. What else can I do to connect it?

Thanks for any help you can give...

---

### Post by drphilngood on 2006-11-28
Try troubleshooting using this guide:

[WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Good luck!

---

### Post by cmichaelboyd on 2006-11-28
open up a terminal and type 

iwconfig

and copy and paste the output here.

also, are you using wep or wpa?  

cheers

---

### Post by osarusan on 2006-11-28
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"mmeyer"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:49/100  Signal level:29/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I've tried WPA and WEP with my router, and I've tried to connect to other networks that were unsecured... none of them connected at all.

---

### Post by cmichaelboyd on 2006-11-28
try 
iwconfig wlan0 ap auto

and if that doesn't work, try

iwconfig wlan0 ap [I]insert:access:point:mac:address:here
[/I]
i know that last one may be a pain, but it could at least be a temporary fix until we figure out what else is going on.

let me know what happens, if anything

---

### Post by osarusan on 2006-11-28
Still nothing.

I've got the wireless icon in the taskbar panel area, and it tells me the signal strength, but it has 0 packets sent, and shows that it's disconnected... Rebooting didn't change anything either... any other ideas?

---

### Post by cmichaelboyd on 2006-11-28
one thing I'm still not clear on:  are you using any type of encryption at this current moment?

also, are your lights flashing on you card indicating that it's trying to do anything at all?

---

### Post by osarusan on 2006-11-28
Ah ok, here's something: I can see the other computers on my network. 

I can't connect to the internet, however... The lights on the card are on, but since theres no data going, they're not blinking.

Edit: At this moment I'm using encryption, but I'll turn it off for now.

Edit 2: Turning off security doesn't change anything. It still won't connect. Is there something I need to do to try to reconnect? I've tried ifdown and then ifup, but nothing changes.

---

### Post by cmichaelboyd on 2006-11-28
no no
leave it on if you can see the other computers!

go to your /etc/network directory and give me the contents of your "interfaces" file.

---

### Post by osarusan on 2006-11-28
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
auto wlan0
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0
map wlan0
# The primary network interface
iface eth0 inet dhcp
iface wlan0 inet dhcp
wireless-essid mmeyer
wireless-key s:



auto eth0

Here is my interfaces file.

---

### Post by cmichaelboyd on 2006-11-28
on the line that says "wireless-key s:", try changing that to say

"wireless-key *whateveryourkeyis *restricted"


see if that helps

and then reboot

---

### Post by osarusan on 2006-11-28
Nope, that didn't change anything.

---

### Post by cmichaelboyd on 2006-11-28
ugh

---

### Post by cmichaelboyd on 2006-11-28
what do you get when you type

iwlist wlan0 scan

?

---

### Post by wieman01 on 2006-11-28
Turn off encryption to eliminate this complicating factor for now. The open:
> sudo gedit /etc/network/interfaces
And replace the contents with this (it's safe):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid [COLOR="Red"]meyer[/COLOR]
_**Before you restart the network, ensure the following:**_

1. DHCP is enabled (router).
2. Security (WEP) is turned off.
3. Ehternet cabled is **unplugged**!
4. NetworkManager or Wifi-Radar are not installed & running.

Then restart the network (please post the results):
> sudo /etc/init.d/networking restart
_**EDIT:**_
The results of a network scan would be nice as well:
> iwlist scan

---

### Post by cmichaelboyd on 2006-11-28
he said he could see other computers on the network, just no internet access.  I assumed that meant that he was having no problems with encryption.

---

### Post by wieman01 on 2006-11-28
> **cmichaelboyd said:**
> he said he could see other computers on the network, just no internet access.  I assumed that meant that he was having no problems with encryption.
Yeah... I missed that point. You're right. If Internet is the only problem now, try this...

Disabling **[COLOR="Red"]IPV6[/COLOR]** in **Firefox**:

> 1. URL: "about:config" then <enter>.
2. Search for "ipv6" (use the Filter).
3. Right-click on "network.dns.disableIPv6" and select "Toggle".

Then try browsing... If you want to take it a step further (makes sense for performance reasons), the disable IPV6 globally.

To disable "ipv6" globally see this thread (first post): [http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6")

---

### Post by cmichaelboyd on 2006-11-29
I don't think it's the Firefox/IPv6 issue, because firefox will usually recover from that on it's own (by falling back to IPv4).
But just to make sure.....  
 
Osarusan, try going to a terminal and typing
 
ping -c 3 [www.yahoo.com]("http://www.yahoo.com") 
 
and give us the output.  
 
Thanks

---

### Post by wieman01 on 2006-11-29
The reason why I mention Firefox & IPV6 is that this is an issue I have seen in many threads/posts. Serious, "route" & "ping" say you are connected, but Firefox would not load any websites & simply timeout. Check it out yourself, tons of related posts.

---

### Post by zgornel on 2006-11-29
Just a quick question : why should network manager and wifi radar be uninstalled besides not running ?

---

### Post by wieman01 on 2006-11-29
It will be running if you don't uninstall it. You can kill the process manually of course, but it's safest to uninstall the programs in the first place, reinstall later on once you get this running. That's all.

---

### Post by cmichaelboyd on 2006-11-29
> **wieman01 said:**
> The reason why I mention Firefox & IPV6 is that this is an issue I have seen in many threads/posts. Serious, "route" & "ping" say you are connected, but Firefox would not load any websites & simply timeout. Check it out yourself, tons of related posts.
Exactly.  That's why I wanted osarusan to ping and see if ping can reach anything.  If it can, then it would be firefox, and if ping can't reach anything, then it's actually  his network config.  My point in asking for ping was to test your theory, though I really don't think that's the issue, because, as I stated, firefox will, after a failed IPv6 attempt, fall back to IPv4.

At any rate, let's wait and see what osarusan posts so we can actually focus on helping this person resolve the problem.

---

### Post by cmichaelboyd on 2006-11-29
> **zgornel said:**
> Just a quick question : why should network manager and wifi radar be uninstalled besides not running ?
I don't know why these would be a problem either.  Have there been any reports of folks having problems setting up wireless when these packages are installed and running?

---

### Post by osarusan on 2006-11-29
Hi guys, thanks for the load of responses! Sorry I wasn't here earlier to answer, but here's what I've tried from your advice. Sadly, no luck yet:

> osarusan@osarusan-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5291
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:20:e0:66:5f:e9
Sending on   LPF/eth0/00:20:e0:66:5f:e9
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5523
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:66:c6:e7:d7
Sending on   LPF/wlan0/00:0f:66:c6:e7:d7
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:66:c6:e7:d7
Sending on   LPF/wlan0/00:0f:66:c6:e7:d7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:20:e0:66:5f:e9
Sending on   LPF/eth0/00:20:e0:66:5f:e9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.47 -- renewal in 37490 seconds.
                                                                         [ ok ]


and 

> osarusan@osarusan-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:E6:D2:04
                    ESSID:"meyer"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/100  Signal level=31/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 02 - Address: 00:12:0E:16:54:C7
                    ESSID:"ambrose"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=3/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 03 - Address: 00:06:25:9B:8A:48
                    ESSID:"amodio1"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/100  Signal level=2/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:11 Mb/s

sit0      Interface doesn't support scanning.


Pinging didn't work either, so I don't think it's just a firefox problem. Incidentally, the network icon in my panel right next to the calendar has the wireless signal strength, and the little x next to it saying that it's disconnected from the network. However, I can access all the computers' shared folders on my home network just fine.

(In case you're wondering: I did change the network name to meyer instead of mmeyer, just so you don't think that the whole problem is based on a typo...)

---

### Post by wieman01 on 2006-11-29
Turn off encryption (possibly WEP) and try post #15 once again. The scan confirms that you have turned on wireless security:
> Cell 01 - Address: 00:E0:98:E62:04
ESSID:"[COLOR="Red"]meyer[/COLOR]"
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality=50/100 Signal level=31/100 Noise level=0/100
[COLOR="Red"]Encryption key:on[/COLOR]
Bit Rates:54 Mb/s
This should be fairly straight-forward. If you can connect, then we'll turn encryption on again & change the script accordingly.

---

### Post by osarusan on 2006-11-29
Ah, I see what happened... Even though I disabled the security, the router didn't consider it to be open until I deleted the key and then re-disabled it. Stupid router... I've gotten the scan to tell me it's disabled, so I'm retrying now. I'll repost in a minute...

Edit:
> 
osarusan@osarusan-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:E6:D2:04
                    ESSID:"meyer"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/100  Signal level=33/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 02 - Address: 00:09:5B:D6:64:50
                    ESSID:"seanispoopypants"
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality=31/100  Signal level=3/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:54 Mb/s

sit0      Interface doesn't support scanning.

So it says this now... but still won't connect. Here's an interesting thing tho: I tried setting my Wireless Security to WEP with an "Open System" instead of a "shared key", and then the network icon in the corner no longer said Disconnected... however, I still couldnt reach any websites or ping yahoo. When the encryprion is set to off, then the icon continues to say disconnected.... hmm....

---

### Post by wieman01 on 2006-11-29
Have you got NetworkManager or Wifi-Radar installed? The "icon" seems to refer to "Gnome-Network-Manager... Have you installed that tool at some point?

---

### Post by wieman01 on 2006-11-29
By the way... Run this after re-establishing the connection & post the output:
> route

---

### Post by osarusan on 2006-11-29
I haven't installed any new software other than the default Edgy stuff... I think this icon is the Gnome Network Manager, but AFAIK, neither of those you mentioned are installed or running.

route:
> osarusan@osarusan-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


---

### Post by wieman01 on 2006-11-29
If this is Gnome-Network-Manager, then it's no surprise you cannot connect. If you decide to make use of it, the your "interfaces" file needs to look like this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
#wireless-essid meyer
You must comment the lines that refer to your wireless device, otherwise NetworkManager won't work. That done, can you connect to your network by right-clicking on the NM desktop icon?

If you want to try without NetworkManager, install it using this command:
> sudo apt-get **[COLOR="Red"]remove[/COLOR]** gnome-network-manager
The reboot the computer. The script must be as in post #15 (no hash-keys).

_**EDIT:**_
Plus make sure your Ethernet cable is pulled!

---

### Post by osarusan on 2006-11-29
It wasn't the NetworkManager.. disabling it disabled my wireless card. Not sure what it was, but I think just an ordinary device notifier? Changing the settings in it changes the settings in the interfaces file... so its just a GUI interface for that I think.


Anyway, it still hasn't worked. I have to quit for the night. I'll be back tomorrow evening, and I hope you will too. :-) Thanks so much for your help so far, I really appreciate your patience.

---

### Post by cmichaelboyd on 2006-11-30
osarusan,
I noticed in looking at the output that you posted that when your network was reenabling, it didn't find any dhcp offers.  Are you absolutely certain that dhcp is enabled in your router?
 
Also, check around in your router's configuration, because some routers have to several ways to enable (and disable) dhcp, including limiting dhcp access to hardwired connections and not allowing dhcp through wireless.  Double check that your router is configured to allow dhcp for wireless.  
 
Also, (I have a lot of alsos today), are you sure that there are no limitations in your router as to what IP addresses or MAC addresses can access the internet.  If you have a firewall enabled (in the router), that may be blocking access, so double check that too.
 
Finally, I have yet another question.  Is your entire network wireless, or do you have a mixed topology (wired and wireless)?  The reason I ask is because if the computer that your network folders are stored on is wireless, it may be allowing an ad hoc connection, which could give you access to your network folders, but no internet.  Another way to check this is to log into your router's configuration and, assuming you have some monitoring capabilities, check the logs* in the router* and look at whether or not you can see that the wireless card in question is actually connecting or not.  Let me know
 
Cheers

---

### Post by wieman01 on 2006-11-30
Osarusan,

Would be great if you answered every one of cmichaelboyd's questions so that we understand what your network looks like. Please try to be as precise as possible because I think we're close.

---

### Post by osarusan on 2006-11-30
> **cmichaelboyd said:**
> Are you absolutely certain that dhcp is enabled in your router?

My router's DHCP page has 2 settings: disabled and private LAN. It's on Private LAN. I don't know what else could affect DHCP, so I can only assume that it's enabled.
 
> **cmichaelboyd said:**
> Also, check around in your router's configuration, because some routers have to several ways to enable (and disable) dhcp, including limiting dhcp access to hardwired connections and not allowing dhcp through wireless.  Double check that your router is configured to allow dhcp for wireless.  

Ah! I found something interesting! A "public LAN" setting that was hidden in another part of my router's settings. I've enabled DHCP for public LAN. I still can't ping anything though... although for the first time I'm seeing 26.2 kb worth of Packets recieved in my wlan0 connection properties. So something must be happening.
 
> **cmichaelboyd said:**
> Also, (I have a lot of alsos today), are you sure that there are no limitations in your router as to what IP addresses or MAC addresses can access the internet.  If you have a firewall enabled (in the router), that may be blocking access, so double check that too.

The router firewall is disabled, and I'm faily positive that there are no limitations like you mentioned.
 
> **cmichaelboyd said:**
> Finally, I have yet another question.  Is your entire network wireless, or do you have a mixed topology (wired and wireless)?  The reason I ask is because if the computer that your network folders are stored on is wireless, it may be allowing an ad hoc connection, which could give you access to your network folders, but no internet.  Another way to check this is to log into your router's configuration and, assuming you have some monitoring capabilities, check the logs* in the router* and look at whether or not you can see that the wireless card in question is actually connecting or not.  Let me know

It's mixed, but all the other computers on the network are wired. This laptop is the only wireless connection.

I *can* see my laptop in the router settings:
 	
Station 	MAC Address 	State 	PBCC 	Active Rate
1 	00:0f:66:c6:e7:d7 	Authorized 	Inactive 	54 Mbit/sec

So it's detecting... but still wont connect to anything. Does this offer any insight? I hope it does... it feels like we're close to me too.

---

### Post by wieman01 on 2006-11-30
Can you attach screenshots of you DHCP settings? That would certainly help. 

Is any other computer connected to that router with access to the Internet? If that's the computer you are using right now & it happens to be Windows... Simply check the network properties. That will reveal the network settings.

---

### Post by cmichaelboyd on 2006-11-30
Actually, what you've given us has helped a lot.  I also feel we are close.  Just a quick thought: have you tried typing (in a terminal):

dhclient wlan0

?

Try that, and let me know what happens.

cheers

-chris

---

### Post by cmichaelboyd on 2006-11-30
Also, try pinging your router.  

ping -c 3  [I]your.router.ip.address

[/I]and let us know the results

---

### Post by Peter The Plumber on 2006-11-30
Hello Everyone,
  I hope you'll let me weigh in. I'm having the same problem as the original poster. I have come to the same point you have. For some reason I'm not getting an IP address from my gateway on this computer. This is a T22 Thinkpad, Edgy 6.10, Linksys pcmcia wireless card with the dreaded Broadcom 4306 chipset and network-manager to run it all. This has been set up with the help of the excellent how to's on this site. Ipv6 is globally disabled and the interfaces have been disabled in 'System-Administration-Networking'. I must issue 'dhclient eth1' from a terminal to connect. I'm currently trying to find out how to get this done automatically. I've found a script to bring up interfaces but isn't that what network-manager is for?
  For the sake of clarification, I connect via ethernet with this same machine to the same gateway w/o any problem. I use the same gateway; both wired and wireless; for a T30 Thinkpad w/Dapper 6.06 and a T30 Thinkpad w/SUSE 10.0 w/o any problems.
  I'm wondering if I uninstall network-manager I can manually manage my connections. I hope this helps you sort out this posters problems as well.

Regards,

Peter

---

### Post by cmichaelboyd on 2006-11-30
Peter,

Just open your favorite text editor and edit "/etc/rc.local"
and add

dhclient eth1

to the bottom of the file and then hit enter a time or two (scripts in linux must have an empty line at the end of them...not sure why).

This works fine because your rc.local script is usually executed last in the boot sequence which would be after all of your drivers and such are loaded and your system is ready to go.


Cheers

-Chris

---

### Post by cmichaelboyd on 2006-11-30
and osarusan, if 

dhclient wlan0

works for you, then you can do the same.....just add 

dhclient wlan0

to your /etc/rc.local file.

But please post here if it works, so other folks who have this problem will be able to see how to fix it.

Thanks
-Chris

---

### Post by Peter The Plumber on 2006-11-30
> **cmichaelboyd said:**
> Peter,

Just open your favorite text editor and edit "/etc/rc.local"
and add

dhclient eth1

to the bottom of the file and then hit enter a time or two (scripts in linux must have an empty line at the end of them...not sure why).

This works fine because your rc.local script is usually executed last in the boot sequence which would be after all of your drivers and such are loaded and your system is ready to go.


Cheers

-Chris

Hi Chris,
  Thanks for the input but that doesn't work for me. Been tried. In addition I switch back and forth between wired and wireless on this machine so whatever script is called must be run while the machine is on. I wonder if we've found a bug in network-manager? I'm looking into their mailing list archives as we speak.

Regards,

Peter

---

### Post by wieman01 on 2006-12-01
Chris & Peter:

It would be best if you opened a new thread for this one... It will be increasingly hard to fight at two fronts simultaneously. It's also a question of courtesy to the original poster whose problem we have yet to resolve.

---

### Post by Peter The Plumber on 2006-12-01
> **wieman01 said:**
> Chris & Peter:

It would be best if you opened a new thread for this one... It will be increasingly hard to fight at two fronts simultaneously. It's also a question of courtesy to the original poster whose problem we have yet to resolve.

  My apologies, I will butt out. From what I've seen in a few minutes on the network-manager mailing list is this is something that nm does not quite "just do", it seems to be distro independant.

Regards,

Peter

---

### Post by osarusan on 2006-12-01
> **cmichaelboyd said:**
> Actually, what you've given us has helped a lot.  I also feel we are close.  Just a quick thought: have you tried typing (in a terminal):

dhclient wlan0

?

Try that, and let me know what happens.

cheers

-chris

Chris! That did it!! Thanks so much!!

Wow, you guys are absolutely amazing. I can't tell you how grateful I am that you stayed around to help me for so long.

One more question: about security -- will I have to leave this unsecured? My router has 2 options: WPA-PSK or WEP. Can I use either of these?



Edit: incidentally, here's my output, just in case you guys catch anything:
> osarusan@(none):~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:66:c6:e7:d7
Sending on   LPF/wlan0/00:0f:66:c6:e7:d7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
hostname: the specified hostname is invalid
bound to 192.168.1.45 -- renewal in 33538 seconds.


---

### Post by osarusan on 2006-12-01
> **cmichaelboyd said:**
> and osarusan, if 

dhclient wlan0

works for you, then you can do the same.....just add 

dhclient wlan0

to your /etc/rc.local file.

But please post here if it works, so other folks who have this problem will be able to see how to fix it.

Thanks
-Chris

Ok, I've added it. I'm assuming that I just insert it before 'exit 0'? This will make it automatically bind every time I connect to a wireless network?

---

### Post by wieman01 on 2006-12-01
Try WEP first. To do so, enable WEP on the router and update "/etc/network/interfaces":
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid meyer
wireless-key [COLOR="Red"]your_hex_key[/COLOR]
The restart the computer. Or restart the network:
> sudo /etc/init.d/networking restart
Please replace [COLOR="Red"]your_hex_key[/COLOR] with your **hexadecimal WEP key**. That should do. If you get this working, we could try WPA. That's a bit more complicated.

---

### Post by cmichaelboyd on 2006-12-01
osarusan,

WEP, WPA, or WPA-PSK should all work just fine assuming that both your card and your router support your choice.  If you turn on encryption and your connection fails, just turn it back off, verify that you can connect again, and try a different encryption mode.

I'm glad that we could help!  Enjoy!

Cheers,

-Chris


P.S.  Yes, insert it just before

exit 0

and it should bind every time you boot.  Additionally, if you want to switch between eth0 and wlan0 (for whatever reason), you can at any time type

dhclient eth0

or 

dhclient wlan0

to switch.

Good luck!

---

### Post by osarusan on 2006-12-01
Hmm... the security doesn't seem to be working, whichever one I try. Restarting the network, the computer, or running dhclient wlan0 all get no result... is there something else I need to do other than enter the security key and restart? I'd rather not leave my network unsecured if possible.

---

### Post by cmichaelboyd on 2006-12-01
I'm assuming you tried WEP.  If you want WEP, you'll need to enable it at your router (of course), and then you'll need to make sure in that in your /etc/network/interfaces file, you have your essid and your key enabled as outlined earlier in this thread.  Make sure it says 

wireless-key *yourkey* restricted

somewhere in there.  

As far as WPA and WPA-PSK goes, I'm afraid I don't have much experience with that.  Wieman may be a better help to you on that.  Also, there are quite a few wikis and howtos in the forums here that cover WPA and WPA-PSK.  Check those out as well.  If what I outlined about WEP doesn't work, or if you have anymore questions about WEP, let me know and I'll be happy to help.

Good Luck,

-Chris

---

### Post by wieman01 on 2006-12-01
Hello Osarusan:

You're on the right track... Let's get WEP working first, we can try WPA later on (see link). Could you post the contents of "/etc/network/interfaces" please?
> sudo gedit /etc/network/interfaces
Need to have a look at it again. Then also be a bit more specific as far as WEP is concerned. Are you using **"open"** or **"restricted"** WEP? What's the **key length** (128 or 64 bit)?

You can also try this script... I know that the "wireless-key" section in Edgy may look different in Edgy ("wireless-key1"):
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid meyer
[COLOR="Blue"]wireless-key1[/COLOR] [COLOR="Red"]your_hex_key[/COLOR]
Then restart the network:
> sudo /etc/init.d/networking restart
If this does not work, please post your "interfaces" file as indicated & tell us what your exact wireless security settings are.

_**EDIT 1:**_
This is a Howto on WPA should you need it later on: [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

_**EDIT 2:**_
And please remember: Enter your WEP **hexadecimal** key & not the plain-text one!

---

### Post by osarusan on 2006-12-03
Here's my interfaces file:
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid meyer
wireless-key1 31415

For now, Ive set it to WEP, Open System, with 31415 as my key. But it doesn't work...

---

### Post by cmichaelboyd on 2006-12-03
you should change your wireless key now that you've posted it.

I had trouble connecting with any type of encryption unless I had the router broadcasting the essid.  

Just something to check on....

cheers,

chris

---

### Post by wieman01 on 2006-12-04
As I suspected... "31415" is plain text rather than hexadecimal. Please try this:
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid meyer
[COLOR="DarkGreen"]wireless-key1[/COLOR] **[COLOR="Red"]s:[/COLOR]**[COLOR="Blue"]31415[/COLOR]
If this does not work, please give this a go:
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid meyer
[COLOR="DarkGreen"]wireless-key[/COLOR] **[COLOR="Red"]s:[/COLOR]**[COLOR="Blue"]31415[/COLOR]
The small **"s:"** indicates that you are entering your plain-text key. Then restart the network or computer.

_**EDIT:**_
Please don't hide your ESSID... yet.

---

### Post by osarusan on 2006-12-04
I tried it as you said, and it seems to be returning to the same problem I had before -- my card says I'm connected to the network, but I can't access any websites, or ping anything. I tried to run dhclient wlan0 again (which is what worked last time), but this time it just returned the long list of trying to send and receive -- DHCPREQUEST -- but not receiving any responses.

---

### Post by wieman01 on 2006-12-04
What kind of WEP encryption are you using? Open, restricted, key size? Perhaps even attach a screenshot of your router settings. That'll help a lot.

---

### Post by osarusan on 2006-12-05
> **wieman01 said:**
> What kind of WEP encryption are you using? Open, restricted, key size? Perhaps even attach a screenshot of your router settings. That'll help a lot.

Strangely enough, today it's working! Right now I'm using WEP, "Open System" and a plain text security key. I'm not sure why it wasn't working yesterday, but I'm glad it's working finally.

One last question: what's the difference between using "Open System" and "Shared Key" WEP? Is Open System less secure?

By the way, thank you so much for all of your help. I'd be lost without your attention to this thread. It really means a lot to me!

---

### Post by wieman01 on 2006-12-05
I am quoting: 

*"The primary difference between open and shared is that the latter has a challenge-response handshake during association. In a bizzare twist, the extra protocol makes shared less secure than open. (This is likely a side effect of the fact that WEP has been cracked for years."*

If you want to try WPA (1, 2) instead drop us a note. No problem, and it's more secure than WEP. WEP can be cracked within hours, in particular if you set it to "restricted".

---

