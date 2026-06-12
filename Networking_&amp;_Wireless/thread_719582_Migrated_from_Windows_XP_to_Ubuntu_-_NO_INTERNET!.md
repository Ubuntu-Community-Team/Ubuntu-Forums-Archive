---
title: "Migrated from Windows XP to Ubuntu - NO INTERNET!"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by F D B on 2008-03-09
Hey everybody!

Well, let me try to, briefely, explain what's going on.
I've always had Windows XP with SP2 installed, but since I saw and read some of the nice advatages of Ubuntu, I decided to install it on the same comp, with dual boot (no WUBI).
Wherever I browsed to search for Ubuntu advantages, I kept on finding that "INTERNET WAS DETECTED RIGHT AWAY!" .... "YOU COULD BROWSE WHILE INSTALLING", etc, etc, etc...

When I was installing it, I did not have any internet connection, I assumed that it could be because it was not installed yet, which made sense. But after the installation was completed, and I logged in to Ubuntu 7.10 for the first time I still had no internet connection.

I've tried almost everything!
I've tried setting it manually... and still nothing
I have a D-LINK router, and a DSL modem. I have two computers working as a wireless network at home, with no security (OPEN SYSTEM), the name of the network (or SSID) is "default". My IP is: 192.168.0.7, and the routers is: 192.168.0.3
I tried setting all that from within Ubuntu, but no results... plus there's no way to select a Open System... so I left the default security option and set no password.... still nothing.

I'm running out of ideas. At this point it would be much easier to forget about Ubuntu and stay with Windows, which never gave me problems with wireless or internet connections, but I really want to try Ubuntu fully working.
So I hope you can help me.

I'm a newbie at Linux, so please whenever you tell me to do something, PLEASE take into account I don't know what I'm doing, so don't act like it's obvious... like "go here, and run the 'x' command".

Thank you so much in advance.

F D B.

---

### Post by Druke on 2008-03-09
ok when you click on teh network manager in the system tray (by the clock, it will look like a computer screen), do you see any networks?

---

### Post by F D B on 2008-03-09
Well... I can't remember if there were any connections available when I first accessed Ubuntu, but now that I've tried a lot of stuff, including setting it up manually I see one called "default" and with a few orange squares next to it. The two little screens (monitors) icons used to have a "X" or something that gave me the heads up about something not being right, although there's no more "X" now... I have the two monitors, but no light on them like I was used on XP where everytime I'd sent or receive a pack from internet one of the two would light up.

Plus I'm pretty sure that the "default" connection I see now, is the one I set up myself... it's driving me insane.

---

### Post by F D B on 2008-03-09
I tried bootin again from the LiveCD and I could see the "default" wireless connection, I clicked on the orange bar and it tried to connect, but no success...=(

---

### Post by Kralizec on 2008-03-09
First of all, an explanation of the Ubuntu network icons:
[LIST]
[*]Two monitors with an X = no connection
[*]Two monitors with no X = wired connection (that is, Ethernet cable plugged in)
    The monitors do not light up.
[*]4 bars shaped like steps with some coloration = connected to wireless network
[/LIST]

Secondly, many wireless cards do work perfectly right after install, and to my knowledge all Ethernet cards do. However, there are some that need configuration (mine did). Pretty much any Broadcom wireless card will need some configuration.

To find out the type of wireless card you have, open a terminal (Applications -> Accessories -> Terminal) and then enter the command ```
lshw -C network
``` and post the output here.

---

### Post by perfecttao on 2008-03-09
Can you go into the applications menu, into accessories, then terminal.

At the command line, can  you type ifconfig

If you can paste the results here?

Thanks

---

### Post by F D B on 2008-03-09
Here's the outcome of **lshw -C Network**

> 
federico@CORE2DUO:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:cf:90:e1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 00
       serial: 00:17:9a:02:3d:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.7 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g


---

### Post by F D B on 2008-03-09
And here's the result of ifconfig:

> 
federico@CORE2DUO:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:DB:CF:90:E1  
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:2620 (2.5 KB)  TX bytes:2620 (2.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:9A:02:3D:11  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe02:3d11/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:1226 (1.1 KB)  TX bytes:5467 (5.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-9A-02-3D-11-00-00-00-00-00-00-00-00-00-00  
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



Hope you can help me a little now guys :(

---

### Post by F D B on 2008-03-09
Oh, and by the way... now the network icons are just two monitors (no x), and when I click on them I have no connection to select, no orange bars... nothing.....

---

### Post by Kralizec on 2008-03-09
I found some other threads specifically referring to your wireless card, so it might be worth it to look through them:

[http://ubuntuforums.org/showthread.php?t=132980]("http://ubuntuforums.org/showthread.php?t=132980")
[http://ubuntuforums.org/showthread.php?t=408987]("http://ubuntuforums.org/showthread.php?t=408987")

---

### Post by F D B on 2008-03-09
First let me thank you, but still can't make it work. Well the first link isn't even about my card, I don't have any RaLink one.

And the second one is kind of confusing.

I'm still trying though.

---

### Post by Kralizec on 2008-03-09
According to the results of your lshw, your wireless card is indeed a RaLink: ```
product: RT2561/RT61 rev B 802.11g
vendor: RaLink
```.
But at this, I've pretty much exhausted my ability to help you beyond pointing you to other resources.
You might want to check out some of the pages on the Ubuntu wireless main page: [https://help.ubuntu.com/community/WifiDocs/]("https://help.ubuntu.com/community/WifiDocs/")

---

### Post by F D B on 2008-03-09
It shouldn't be this complex... I mean, why so many commands, so many stuff like this?... I don't get the point...

I guess I might as well uninnstall Ubuntu and end my Linux adventure here, at least for the time being.

Thanks a lot for your help anyways.

---

### Post by perfecttao on 2008-03-10
The good news is that your wireless card is picking up an address:

> wlan0 Link encap:Ethernet HWaddr 00:17:9A:02:3D:11
inet addr:192.168.0.7 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::217:9aff:fe02:3d11/64 Scope:Link
UP DIFUSIÓN CORRIENDO MULTICAST MTU:1500 Metric:1

Which means that the Wireless card is probably working ok.  The problem is now most likely caused by either an incorrect gateway or by a DNS problem.

Could you try (at a command line again)

Ping 192.168.0.1

then try:

ping [www.bbc.co.uk](www.bbc.co.uk)

Let me know the ouput....

I hope this doesn't put you off using Ubuntu!

---

### Post by F D B on 2008-03-10
> **perfecttao said:**
> The good news is that your wireless card is picking up an address:



Which means that the Wireless card is probably working ok.  The problem is now most likely caused by either an incorrect gateway or by a DNS problem.

Could you try (at a command line again)

Ping 192.168.0.1

then try:

ping [www.bbc.co.uk](www.bbc.co.uk)

Let me know the ouput....

I hope this doesn't put you off using Ubuntu!
Thank you for your interest in helping me out.
Two questions:
1-Why ping 192.168.0.1 ? My router is set to be 192.168.0.3... shouldn't I ping that one?

2-never had to set any DNS, just my IP (192.168.0.7), the subnet mask, and the router's ip (192.168.0.3). Because the DNS's are already set on the router... so Internet just used them from there, from the router.

Should I set them manually on Ubuntu anyway?

---

### Post by F D B on 2008-03-10
How can I set a OPEN SYSTEM (no encryption) wireless setting on Ubuntu?
Because when I manually try to set my connection I set all this:
SSID: default (that's the name)
>Static IP (mine: 192.168.0.7, mask: 255.255.255.0, router's: 192.168.0.3)

But I have to leave the security mode as default (WPA), because my router is set to OPEN SYSTEM (NO ENCRYPTION) but there's not such option on Ubuntu.

I need help guys.

---

### Post by F D B on 2008-03-10
Nothing to do, huh?!

Sorry for keep on asking but I want to try Ubuntu at its fullest, with internet.

---

### Post by F D B on 2008-03-11
There must be some expert here that can help me!

Otherwise I really will have to format the partition and deleted Ubuntu without having even tried it at its fullest....

PLEASE!

---

### Post by F D B on 2008-03-11
By the way, one more thing that might help you help me... someone told me here that I have a RaLink card or something like that.... well my Wireless adapter is a D-Link Airplus G DWL - G510 Wireless PCI Adapter not a RaLink one.

---

### Post by handydan918 on 2008-03-11
lshw and lspci rarely lie.
You are mistaking the label on the box for the chip the manufacturer used in the wireless card. adlink will show up as whatever kind of chip is running on it. This is why we ask for the terminal output of lspci, etc. 

So. 

can you ping 192.168.0.3 or whatever your router is at? See, the thing is, this is all very likely a network issue, not a 'buntu issue, per se. Your wireless is working. The ifconfig output shows an ip assigned to wlan0 that appears to be correct for your network. 
Stick with this and work thru it. It'll pay off. 
BTW, the reason that wireless in linux is such a bitch is because most hardware vendors don't write drivers for linux, and many won't publish their specs so the community can write them. It isn't  the Ubuntu developers fault. Buy hardware that's supported, and the others may see the light!

---

### Post by F D B on 2008-03-11
I see... and it's totally understandable but oh well, isn't miy hardware supported??? It's one of the most common routers. Most common network adapters...

Thank you for your answer.
Well if you think Ubuntu is set preoperly, then I've ran out of options here, because there's nothin else to set on the router.
And as I said when I try to ping 192.168.0.3 (the router) I get no response from it. And I can't access to the router from Firefox, like I do in Windows.
I've set everything just like I'd do in windows, same IP for me, same IP for the router, same subnet mask...

One more question as I've already said How can I set a OPEN SYSTEM (no encryption) wireless setting on Ubuntu?
Because when I manually try to set my connection I set all this:
SSID: default (that's the name)
>Static IP (mine: 192.168.0.7, mask: 255.255.255.0, router's: 192.168.0.3)

But I have to leave the security mode as default (WPA), because my router is set to OPEN SYSTEM (NO ENCRYPTION) but there's not such option on Ubuntu.

---

### Post by Eiríkr on 2008-03-11
A couple thoughts and questions --
[list][*]Your router is completely a separate issue from your network adapter.  Hardware support on the Ubuntu side is only relevant to your hardware adapter (unless your router is physically part of your computer).  
[*]This line in your [font=courier]ifconfig[/font] results suggests that your computer is at least able to talk to *something*:
```
RX bytes:1226 (1.1 KB) TX bytes:5467 (5.3 KB)
```
If your wireless were completely cut off, you'd expect the bytes received (RX) and transmitted (TX) to both be zero.  This is not the case; which suggests that the issue is not that your OS can't properly use your card, but rather that there's some configuration snafu getting in the way.  
[*]I notice you've manually configured your IP address and gateway (router) settings.  Is there any chance your router has gotten reset at any point?  This happened to me a while back and it took me some time to realize that this meant the router's IP address had reverted to the manufacturer's default value of 192.168.0.1.  Anyway, try pinging that address just in case.
[*]What happens if you abandon your current manually-entered static configuration and set your adapter to use DHCP?  Sometimes letting the software handle things automagically can fix issues.
[*]I notice your machine also seems to have a hard-wired network port, eth0.  What happens if you set eth0 to use DHCP, and physically connect your computer to your router?  After doing so, can you ping your router?  Can you access the router admin interface in your web browser?  If so, make sure the router's IP address and net mask are what you expect, and that the wireless functionality is still on and running, with the WSSID and pass key(s) you expect.  
[*]Please also post us the results of this command:
```
cat /etc/network/interfaces
```
This prints out the contents of the /etc/network/interfaces file.  This file defines a number of different network interface config settings, and could well be useful in this thread.[/list]
Good luck,

Eiríkr

---

### Post by F D B on 2008-03-11
> **Eiríkr said:**
> A couple thoughts and questions --
[list][*]Your router is completely a separate issue from your network adapter.  Hardware support on the Ubuntu side is only relevant to your hardware adapter (unless your router is physically part of your computer).  
[*]This line in your [font=courier]ifconfig[/font] results suggests that your computer is at least able to talk to *something*:
```
RX bytes:1226 (1.1 KB) TX bytes:5467 (5.3 KB)
```
If your wireless were completely cut off, you'd expect the bytes received (RX) and transmitted (TX) to both be zero.  This is not the case; which suggests that the issue is not that your OS can't properly use your card, but rather that there's some configuration snafu getting in the way.
Yeah I noticed that too yesterday, but I wasn't able to realize where it was getting that info from since I couldn't do anything, not even pinging.


> **Eiríkr said:**
> 
[*]I notice you've manually configured your IP address and gateway (router) settings.  Is there any chance your router has gotten reset at any point?  This happened to me a while back and it took me some time to realize that this meant the router's IP address had reverted to the manufacturer's default value of 192.168.0.1.  Anyway, try pinging that address just in case.
Well this can't be possible, because I still can connect to internetfrom within Windows XP. I can access the router, and ping it, everything. And I'm using the same configurations as in Ubuntu (same IPs)... so if the router would have reset itself I wouldn't be able to connect from Windows either, since it uses the same gateway and same config I've set for it on Ubuntu.

> **Eiríkr said:**
> 
[*]What happens if you abandon your current manually-entered static configuration and set your adapter to use DHCP?  Sometimes letting the software handle things automagically can fix issues.
I've tried that but: 1st- It wouldn't even be logical, because I've set my router with certain specifications, that would require a manual configuration, just like in Windows. But leaving that fact aside for a moment, I've tried it, yes and still no luck. Enabled DHCP, rebooted, and it found my "default" wireless network with some oranges squares next to it, when I try to connect it it says something like "attempting to connect to 'unkonwn' network 76%"  Hmmm and I think that sometimes it even said 0%, but I can't remember when was the case... I mean I can't remember what were the settings I was using when I got that 0%.

> **Eiríkr said:**
> 
[*]I notice your machine also seems to have a hard-wired network port, eth0.  What happens if you set eth0 to use DHCP, and physically connect your computer to your router?  After doing so, can you ping your router?  Can you access the router admin interface in your web browser?  If so, make sure the router's IP address and net mask are what you expect, and that the wireless functionality is still on and running, with the WSSID and pass key(s) you expect.
Well I can't try that. See, my house has 2 floors, and the router is connected to the modem and to my father's PC in the 2nd one, upstairs. My computer is in my room and receives the wireless connection from upstairs. And he (my father) won't allow me to change the whole thing and take it to my room just to try Ubuntu.

But I could try that nevertheless from my computer without pluggin the whole thing directly to my computer... it's just that I don't know how to select and set eth0 to DHCP. But still... that wouldn't work for wireless connections anyway, would it?

> **Eiríkr said:**
>   
[*]Please also post us the results of this command:
```
cat /etc/network/interfaces
```
This prints out the contents of the /etc/network/interfaces file.  This file defines a number of different network interface config settings, and could well be useful in this thread.[/list]
Good luck,

Eiríkr

Ok, I will try that command as soon as I get home.
Let me THANK YOU a lot for your interest and for helping me out, please don't stop.

Thanks.

---

### Post by Eiríkr on 2008-03-11
No problem, I've been in similar shoes myself.  ;)

---

### Post by F D B on 2008-03-11
> **Eiríkr said:**
> No problem, I've been in similar shoes myself.  ;)
Yeah.
Hey about the answers I gave you in my previous post... can you think of anything else? 

Thx.

---

### Post by Eiríkr on 2008-03-11
It really looks like some sort of config issue, but then I suppose it could be an obscure and subtle driver bug.  Driver bugs usually prevent the device from being used at all, though, which combined with the fact that your wireless is transmitting and receiving is what makes me think it's the config.  That's why I was hoping to get a look at your /etc/network/interfaces file.

---

### Post by F D B on 2008-03-11
Ok, I'm hittin home in about 2 hours and a half. I'll do it as soon as I get there.
I don't know where you're from, or what time is it there now, but if it's not too late and you're still on the net PLEASE make sure you check in about 3 hours to see the outcome of what you're telling me to do.

Thank you, you're far too kind.

---

### Post by F D B on 2008-03-11
Oh one more thing, I've been told by some guys of the Network & Systems area of my workplace to switch off the router and turn it on again after a couple of minutes.
I might try that as well.

---

### Post by F D B on 2008-03-11
Well I'm back home...
I tried the **cat /etc/network/interfaces** command, and here's the outcome:


```

federico@CORE2DUO:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback











iface wlan0 inet static
address 192.168.0.7
netmask 255.255.255.0
gateway 192.168.0.3
wireless-essid default

auto wlan0
```

Really just little information there, but everything seems about right, I mean that's exactly what I've set manually. So...

I'll keep hoping for your kind help.

Thanks.

---

### Post by Eiríkr on 2008-03-11
Great, I think we might be getting somewhere!

The section towards the bottom defines your wireless interface.  I'm not 100% sure, but I think the [font=courier]auto wlan0[/font] bit wants to go at the top of this section.  

That aside, the [font=courier]wireless-essid[/font] line is missing something, and there's another line altogether that I don't see.  Try editing the file like so:
```
sudo gedit /etc/network/interfaces
```
... and edit / add the following lines:
```
wireless-essid NETWORK_NAME
wireless-key KEY
```
Replace the caps with the appropriate values for your network.  Without these, your wireless network interface will happily sit there and converse briefly with your wireless router, which is what produced the RX and TX counts we saw earlier.  **But**, without your computer being able to properly specify the network name and key, your router will just say "Sorry Charley" and that'll be all you get.  

HTH,

Eiríkr

---

### Post by F D B on 2008-03-11
Wow I gotta dmit you got me excited now.
But I don't understand something:
What am I supposed to replace the KEY value with?
I mean... I've specified in two or three of my posts in this topic that I have an OPEN SYSTEM, no encryption, no password.

Or is KEY supposed to be something else?

Thank you

---

### Post by F D B on 2008-03-11
See? this is what I'm talking about... 
These are 3 pics of the most important configurations on my router, so you can see it's an open system, with no security (I don't care about it)... so what I'm supposed to set in that KEY value you just told me?

[[IMG]http://img215.imageshack.us/img215/5866/dlink1pi3.th.jpg[/IMG]](http://img215.imageshack.us/my.php?image=dlink1pi3.jpg)

[[IMG]http://img135.imageshack.us/img135/7963/dlink2tt3.th.jpg[/IMG]](http://img135.imageshack.us/my.php?image=dlink2tt3.jpg)

[[IMG]http://img205.imageshack.us/img205/9766/dlink3ks3.th.jpg[/IMG]](http://img205.imageshack.us/my.php?image=dlink3ks3.jpg)

---

### Post by handydan918 on 2008-03-11
Post the output of ```
ping 192.168.0.3

```and also  ```
ping 192.168.0.1
```

Please don't just comment that they "didn't work". Not that we don't trust you. 
But we don't. :)

---

### Post by Omnios on 2008-03-11
Hi on my old tower I had a problem connecting to the internet hough its wired. Problem was no matter how I tried setting up the networking pannnel app I could not use the browser. 
 
 
 Anyways I use a dirty hack to connect wired to my router. I right click the app and dissable the netorking on the app.
 
 Then I open the Linux terminal and use the following.
 
this is the equivilent to xp config release
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

```
 
 the down and up is like releae
dhclient subscibes the connection and assignes the ip.
eth0 is the connection you are using if other than eth0 used that. 
 
 I found this wierd but is the only way I can get a connection.

---

### Post by Eiríkr on 2008-03-11
> **F D B said:**
> Wow I gotta dmit you got me excited now.
But I don't understand something:
What am I supposed to replace the KEY value with?
I mean... I've specified in two or three of my posts in this topic that I have an OPEN SYSTEM, no encryption, no password.

My bad, getting my threads mixed up.  :-|  But read below, this is actually the right track to be following :D:

I figured out that the relevant man page for this situation is [font=courier]iwconfig[/font], which informs us of the following (most relevant sections bolded):
> **key/enc[ryption]**

Used to manipulate encryption or scrambling keys and security mode.  To set the current encryption key, just enter the key in hex digits  as  _XXXX-XXXX-XXXX-XXXX_  or _XXXXXXXX_.  To set a key other than the current key, prepend or append _[index]_ to the key itself (this won’t change which is the active key). You can also enter  the  key  as an ASCII string by using the _s:_ prefix. Passphrase is currently not supported.

To change which key is the currently active key, just enter _[index]_ (without entering any key value).  

_off_ and _on_ disable and reenable encryption.

**The  security  mode  may be _open_ or _restricted_, and its meaning depends on the card used. With most cards, in _open_ mode no authentication is used** and the card may also accept  non-encrypted  sessions, whereas in _restricted_ mode only encrypted sessions are accepted and the card will use authentication if available.

If you need to set multiple keys, or set a key and change the active key, you  need to  use  multiple  key  directives. Arguments can be put in any order, the last one will take precedence.

Examples :

```
iwconfig eth0 key 0123-4567-89
iwconfig eth0 key [3] 0123-4567-89
iwconfig eth0 key s:password [2]
iwconfig eth0 key [2]
**iwconfig eth0 key open**
iwconfig eth0 key off
iwconfig eth0 key restricted [3] 0123456789
iwconfig eth0 key 01-23 key 45-67 [4] key [4]
```

So in your case, don't use the [FONT="Courier New"]iwconfig[/FONT] command, but rather edit /etc/network/interfaces directly, and replace KEY in the example I gave earlier with "open" (minus the quotes).  

HTH,

Eiríkr

---

### Post by F D B on 2008-03-11
To sum up, I should got back to Ubuntu and do this:
Open a Terminal and
```
sudo gedit /etc/network/interfaces
```

Edit the following lines:
```

wireless-essid NETWORK_NAME
wireless-key KEY
```

Replacing KEY for "open"


Right?

---

### Post by F D B on 2008-03-11
> **handydan918 said:**
> Post the output of ```
ping 192.168.0.3

```and also  ```
ping 192.168.0.1
```

Please don't just comment that they "didn't work". Not that we don't trust you. 
But we don't. :)
LOL...
I did it and the outcome is the following one:
Having set manually the router gateway to 192.168.0.3 and pinging that same address I got about 230 "host unreachable" messages but at 234 it stopped and showed this:
234 packets transmitted, 0 received, +176 errors, 100% packet loss, time 233003ms

But when I pinged 192.168.0.1 (I previously set manually the router gateway to 192.168.0.1 too, so there wouldn't be any differences)
I got about 500 host unreachable messages, and no final result... it kept on going on, till I stopped it manually.

So there you go...

---

### Post by Eiríkr on 2008-03-11
Bingo, replace KEY with "open" and NETWORK_NAME with "default" (less the quotes).

---

### Post by Eiríkr on 2008-03-11
Handydan forgot that on Linux, ping continues forever unless you specify how many times to repeat with the [font=courier]-c[/font] option.  To ping an address four times, for instance,
```
ping -c 4 192.168.0.3
```

---

### Post by F D B on 2008-03-11
> **Eiríkr said:**
> Bingo, replace KEY with "open" and NETWORK_NAME with "default" (less the quotes).
Hmmm I think that's wrong... because I tried changing KEY for open and then when I go to SISTEM>ADMIN>NETWORK in the security part it's changed "automatically" to WEP and with a "misterious" 4 digits password, which I bet is, casually,  "open"...

Oh and, surprisingly the network's name is set to "network" and not to "default" the way it should be...

So... still nothing

---

### Post by Eiríkr on 2008-03-11
Sorry, "the security part" of what?  You've lost me here.

---

### Post by F D B on 2008-03-11
> **Eiríkr said:**
> Sorry, "the security part" of what?  You've lost me here.
When you go to System>Admin>Network you have some stuff to fill...
ESSID = default
Security or something like that (WPA, WEP, etc).... which should be OPEN SYSTEM or NO ENCRYPTION or something, which actually isn't available.
But by default it comes as WPA... I used to leave the password blank because I actually set no password. When I edited what you just told me it changed to WPE and a mysterious 4 digit password which I'm sure is "open" which is the value I set on "wireless-key KEY"..

---

### Post by Eiríkr on 2008-03-11
Ah, yes, GUI interfaces can often act screwily if the inteface designers forgot about certain configuration options.  I would *completely ignore* the GUI side of things, edit the /etc/network/interfaces file again to make sure all settings are as they should be, and then, *without opening System > Admin > Network*, see if you can access the web.  

There's a chance you might need to restart your network:
```
sudo /etc/init.d/networking restart
```
Then open /etc/network/interfaces to make sure nothing's changed, and try browsing a website that's sure to be online.

---

### Post by F D B on 2008-03-11
> **Eiríkr said:**
> Ah, yes, GUI interfaces can often act screwily if the inteface designers forgot about certain configuration options.  I would *completely ignore* the GUI side of things, edit the /etc/network/interfaces file again to make sure all settings are as they should be, and then, *without opening System > Admin > Network*, see if you can access the web.  

There's a chance you might need to restart your network:
```
sudo /etc/init.d/networking restart
```
Then open /etc/network/interfaces to make sure nothing's changed, and try browsing a website that's sure to be online.
Well bro, still no luck.

I tried restarting, then going to the interfaces thing, checked everything was ok, tried to browse but no internet. That was with my manual configuration still on through the GUI interface as well.
Then I disabled that one, left it on 'automatic mode'... and re-edited the interfaces thing through the terminal... restarted the network... still nothing...

If you saw the screen captures from my router settings, it seems to be everything ok. And earlier you said my config seems to be ok as well, so.... if everything is OK, why doesn't it work? what's missing here?.....

---

### Post by F D B on 2008-03-11
By the way, check this:
```

federico@CORE2DUO:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:DB:CF:90:E1  
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 


lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:14216 (13.8 KB)  TX bytes:14216 (13.8 KB)


wlan0     Link encap:Ethernet  HWaddr 00:17:9A:02:3D:11  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          UP DIFUSIÓN MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:3204 (3.1 KB)  TX bytes:9053 (8.8 KB)


wmaster0  Link encap:UNSPEC  HWaddr 00-17-9A-02-3D-11-00-00-00-00-00-00-00-00-00-00  
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



federico@CORE2DUO:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

federico@CORE2DUO:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0      U     1000   0        0 wlan0
0.0.0.0         192.168.0.3     0.0.0.0             UG    100    0        0 wlan0

```

All this time we've been setting things up fro eth0, but is that my wireless adapter? isn't it wmaster0?
```

federico@CORE2DUO:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:cf:90:e1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 00
       serial: 00:17:9a:02:3d:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.7 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g

```

---

### Post by handydan918 on 2008-03-11
> **Eiríkr said:**
> Handydan forgot that on Linux, ping continues forever unless you specify how many times to repeat with the [font=courier]-c[/font] option.  To ping an address four times, for instance,
```
ping -c 4 192.168.0.3
```
Very close to true. Handydan forgot that not eveyone has their fingers hardwired to ctrl+c after starting a ping....
I am always surprised when Windows stops at 4 pings!

:lolflag:

---

### Post by F D B on 2008-03-11
> **handydan918 said:**
> Very close to true. Handydan forgot that not eveyone has their fingers hardwired to ctrl+c after starting a ping....
I am always surprised when Windows stops at 4 pings!

:lolflag:

Anything else to help me? I tried pinging 192.168.0.1 just like you said...
I'm really dissapointed, thought it would be much easier...

Could reinstalling linux fix anything at this point?
I can't even install Network Manager back...

---

### Post by Eiríkr on 2008-03-12
About the ifconfig results, we've been working on wlan0, not eth0, so no worries there.  One of the previous command result dumps you posted showed wmaster0 as the "logical" name of your RaLink wireless device, which would then seem to be an alias or somesuch for wlan0; not really sure why or what it's doing there.  It's clearly not doing much, what with having no IP address assigned and having zero bits RX or TX.  

And sometimes a wipe and reinstall can seemingly magically make things work, even right after wiping and installing.  I don't know why.

---

### Post by F D B on 2008-03-12
> **Eiríkr said:**
> About the ifconfig results, we've been working on wlan0, not eth0, so no worries there.  One of the previous command result dumps you posted showed wmaster0 as the "logical" name of your RaLink wireless device, which would then seem to be an alias or somesuch for wlan0; not really sure why or what it's doing there.  It's clearly not doing much, what with having no IP address assigned and having zero bits RX or TX.  

And sometimes a wipe and reinstall can seemingly magically make things work, even right after wiping and installing.  I don't know why.
So you think at this point the best thing for me to do is reinstall Ubuntu? Or format the partition and then install Ubuntu from scratch? Nothing else to try...?
If so,  should I install Gutsy Gibbon again, or maybe try with Feisty Fawn?

---

### Post by F D B on 2008-03-12
Don't want to let this die yet, lol

---

### Post by Eiríkr on 2008-03-12
Well, if it were me, I'm a bit of a stubborn sort about some things, so I'd stick with Gutsy, and do a completely fresh install, wiping and reformatting the hard drive (provided that this was a spare machine and / or I had already backed up anything on it I might need).  I'm pretty much at the end of what I can think to do without being right there in front of the machine, which leaves me thinking a fresh wipe-and-reinstall might be the next step.  Anyone else with any ideas / advice / epiphanies?

**PS --**

There *is* one other thing I might try before reinstalling -- this trouble seems like it might be related to the fact that your wireless router has no key assigned.  I've run into other problems where a password-less access situation wasn't handled properly (for Samba access to a Windows share in that case).  What about assigning a simple, impossible-to-forget key on the router?

---

### Post by F D B on 2008-03-12
> **Eiríkr said:**
> 
There *is* one other thing I might try before reinstalling -- this trouble seems like it might be related to the fact that your wireless router has no key assigned.  I've run into other problems where a password-less access situation wasn't handled properly (for Samba access to a Windows share in that case).  What about assigning a simple, impossible-to-forget key on the router?

I tried that already 3 days ago... I got into the router settings and configured a WEP -64bit hex password, then I went to ubuntu and did the same thing, set the password on my manual wirless connection, and if I recall correctly (I did so many things lately that I might be mixing them up a lil bit) Ubuntu detected the 'default' network, it showed the orange bar (on Network Manager) and when I clicked on it to connect it  tried to connect but never got success, it said "**attempting to connect to 'unknown'** - it didn't say default, don't know why - **network 76%**" I never got to understand what that 76% meant.

> **Eiríkr said:**
> Well, if it were me, I'm a bit of a stubborn sort about some things, so I'd stick with Gutsy, and do a completely fresh install, wiping and reformatting the hard drive (provided that this was a spare machine and / or I had already backed up anything on it I might need).  I'm pretty much at the end of what I can think to do without being right there in front of the machine, which leaves me thinking a fresh wipe-and-reinstall might be the next step.  Anyone else with any ideas / advice / epiphanies?
I'm a really stubborn person, not that that's good... but from what I read people got far more complaints with Ubuntu than they did with Feisty. Every Ubuntu forum I got into I see tons of people having internet (wireless) problems, with Gutsy.

But what do you mean with fresh wipe install? You mean I should reformat THE WHOLE DRIVE? getting rid of Windows XP as well? Or just format the partition where Ubuntu is installed, and then install it over freshly?.

---

### Post by F D B on 2008-03-12
...Still

---

### Post by F D B on 2008-03-12
Also, while we're at it.. before I go into the whole process let me ask you a couple of things that come to my mind, due to this recently, not good, experience.

1-How do I format a partition with Ubuntu? Just booting from the LiveCD and installing it again?

2-When I boot from the LiveCD, should I try to set the wireless connection from there? Or wait until Ubuntu is installed, remove the LiveCD from the CD Drive and only then try to configure the wireless from Ubuntu installed on my HDD?

3-Do I set it manually from within System>Admin>Network GUI or from a terminal go to the interfaces file and do it there?

4-When you set it with the GUI interface, there's a tab called "DNS" should I add my router's IP there, or something?
And finally the tab called "Hosts" at the right of that GUI... should I change/add/remove anything there?
[img]http://ubuntuforums.org/attachment.php?attachmentid=61352&d=1204448921[/img]

P.S: That image is not from my configuration, I took it off these boards (some other post), just so you could see which tabs I'm talking about.
Please I need answers too all these questions and the ones from my previous post too, so I can finally start the cleaning-formatting-installing part.

---

### Post by Eiríkr on 2008-03-12
About formatting -- just the partition you're installing Ubuntu to should be fine.

About the network config GUI window -- Can't get into it in detail at the moment.  Your post brings up one more idea though, try booting from the Live CD and see if that can get a connection.  If so, there's likely something that went funny during your installation.  

I'm out of the running for the rest of the day unfortunately, but I'll check back tomorrow.

Cheers,

Eiríkr

---

### Post by F D B on 2008-03-12
Ok thanks and blessings man.

I'll check back tomorrow and see how everything went on... or in case I need more help, ask so here.

---

### Post by Eiríkr on 2008-03-12
Stealing some time...  :)

> **F D B said:**
> Also, while we're at it.. before I go into the whole process let me ask you a couple of things that come to my mind, due to this recently, not good, experience.

1-How do I format a partition with Ubuntu? Just booting from the LiveCD and installing it again?

2-When I boot from the LiveCD, should I try to set the wireless connection from there? Or wait until Ubuntu is installed, remove the LiveCD from the CD Drive and only then try to configure the wireless from Ubuntu installed on my HDD?

3-Do I set it manually from within System>Admin>Network GUI or from a terminal go to the interfaces file and do it there?

4-When you set it with the GUI interface, there's a tab called "DNS" should I add my router's IP there, or something?
And finally the tab called "Hosts" at the right of that GUI... should I change/add/remove anything there?


[list=1][*]Booting from the Live CD and going through the installation process should do just fine.
[*]I'd say try it and see.  Refer to my previous post too -- I'd try booting from the Live CD and checking if the wireless works there, without even going into an installation process, just to see.
[*]Try in the Live CD first -- if the GUI allows for any key-less wireless setup, try that.  If whatever you try via the Live CD GUI doesn't work, try the command line approach that's described in this thread, and see if that produces any better results.  
[*]I'm not sure if your router's IP would work here, since the router is not technically a DNS server (unless you've got a pretty fancy router).  However, routers are generally set up to forward DNS requests, so it might work just  fine.  If it doesn't, try adding one or both of the following IP address to use OpenDNS's servers:
```
208.67.222.222
208.67.220.220
```
And the "Hosts" tab should be fully pre-configured, so you generally don't need to do anything here.  Just in case, though, it might be useful to post a screenshot of what yours looks like (not the Live CD one, but what you see when you boot off the hard drive into Ubuntu), just in case there's something completely bogus hiding in there.  [/list]

Gotta run again, but I'll see what's on the boards tomorrow.  

Cheers,

Eiríkr

---

### Post by F D B on 2008-03-12
Thank you Eirik.

However that had just brought up a couple more questions to my mind.

> **Eiríkr said:**
> 
Try in the Live CD first -- if the GUI allows for any key-less wireless setup, try that.  If whatever you try via the Live CD GUI doesn't work, try the command line approach that's described in this thread, and see if that produces any better results.  

-Why would the Live CD allow key-less wireless setup through the GUI, when the Ubuntu installation on the Hard Drive doesnt? I thought the Live CD was just a fully working example of what Ubuntu can do when it's fully installed. So if Ubuntu itself, installed, has no option to set an OPEN SYSTEM wireless connection, with no encryption, why would Live CD?


> **Eiríkr said:**
> 
I'm not sure if your router's IP would work here, since the router is not technically a DNS server (unless you've got a pretty fancy router).  However, routers are generally set up to forward DNS requests, so it might work just  fine.  If it doesn't, try adding one or both of the following IP address to use OpenDNS's servers:
```
208.67.222.222
208.67.220.220
``` 

-Why those DNS's?

Before I asked you if I should set my router's IP at the DNS tab because on Windows XP, on Network Connections propierties, where it says "Primary DNS Server" (or something like that) I always set my router's ip? Why? Simple, because my router has the ability to 'store' the primary and secondary DNS there... so by setting the router's IP on the DNS tab, each time the connection needs the DNS it'll go to the router and the router will forward them automatically.

But I insist... why did you write THOSE DNS? Aren't DNS' specific to each ISP?

Thanks man!

---

### Post by handydan918 on 2008-03-12
If you don't mind me jumping in, I'll take a swing at these until Eirikr` pops back in....

> **F D B said:**
> 

-Why would the Live CD allow key-less wireless setup through the GUI, when the Ubuntu installation on the Hard Drive doesnt? I thought the Live CD was just a fully working example of what Ubuntu can do when it's fully installed. So if Ubuntu itself, installed, has no option to set an OPEN SYSTEM wireless connection, with no encryption, why would Live CD?
That's just the point-to see if there is a post-install fubar somewhere that is preventing successful connection. > 

-Why those DNS's?

Before I asked you if I should set my router's IP at the DNS tab because on Windows XP, on Network Connections propierties, where it says "Primary DNS Server" (or something like that) I always set my router's ip? Why? Simple, because my router has the ability to 'store' the primary and secondary DNS there... so by setting the router's IP on the DNS tab, each time the connection needs the DNS it'll go to the router and the router will forward them automatically.

But I insist... why did you write THOSE DNS? Aren't DNS' specific to each ISP?

Thanks man!
No, DNS servers aren't specific to the ISP. The opendns servers are reliable and universal. I use them myself....
In fact, I configured my router to use them, too.

Now, let's see how I did as Eirikr`'s proxy....

---

### Post by F D B on 2008-03-12
Thank you for helping me and taking a bit of weight off of Eirikr's shoulder.

> **handydan918 said:**
> 
That's just the point-to see if there is a post-install fubar somewhere that is preventing successful connection. 

Hmm.. maybe I woke up slow or something... but Eirikr told me "Try in the Live CD first -- if the GUI allows for any key-less wireless setup, try that" and my question was Why would Live CD enable (THROUGH GUI) the possibility to configure a KEY-LESS (PASSWORD-LESS... OPEN SYSTEM... NO ENCRYPTION... or whatever you wanna call it) connection when Ubuntu fully installed won't?

---

### Post by handydan918 on 2008-03-12
> **F D B said:**
> Thank you for helping me and taking a bit of weight off of Eirikr's shoulder.


Hmm.. maybe I woke up slow or something... but Eirikr told me "Try in the Live CD first -- if the GUI allows for any key-less wireless setup, try that" and my question was Why would Live CD enable (THROUGH GUI) the possibility to configure a KEY-LESS (PASSWORD-LESS... OPEN SYSTEM... NO ENCRYPTION... or whatever you wanna call it) connection when Ubuntu fully installed won't?
Short answer-Who knows? But if it works, who cares?
Longer answer-There exist, as they say "many a slip twixt the cup and the lip." Not every plan is executed perfectly. And without seeming less than appreciative of Ubuntu and Canonical, I believe that their development model is inherently prone to these kinds of regressions.
The very act of running a full operating system off of a CD is a kind of magic that has become unfortunately taken for granted. The fact that there are occasional imperfections lessens the miracle only slightly.

---

### Post by Eiríkr on 2008-03-13
And many thanks to Handydan for pitching in!  :D

Yep, as to "why try the CD when the install is borked?", I've found in the past that the CD sometimes just does things differently than the full install.  And not just for Ubuntu -- I saw the same with Mandriva as well last time I was trying it out.  

And the longer-still answer ;): Basically, if I understand it correctly, the Live CD is a snapshot in time of the various bits of software, with as much as possible included in terms of different configurations to try to account for the many different types of hardware users might have.  However, in the process of a full install, the installation process usually includes:
[list][*]winnowing out all the unneeded config info to leave you with just the config data needed for your particular hardware (which raises the possibility that something will be thrown out by accident)
[*]updating software packages to use the most up-to-date versions available on the repositories
[/list]
Both of these steps pretty much guarantee that what's finally on your hard drive will not match the Live CD.  And both steps introduce plenty of room for error -- maybe a needed bit of config settings will be mistakenly pitched, or the wrong ones included, or maybe the newest package versions include new bugs that the older CD versions didn't have.  All of which sometimes means we users wind up disappointed -- "but the blooming Live CD worked, why doesn't the install???"  I've rather angrily found myself saying exactly this in the past, for what it might be worth...  Sometimes you might just have to try a different distro, or have the patience to wait until a bug gets worked through the system and properly fixed.  

Anyway, here's to hoping your snafu has a solution in the near future!

Cheers,

Eiríkr

---

### Post by F D B on 2008-03-13
Well thank you both for the help, but I'm done with Ubuntu.

Yesterday I booted from the CD, tried all the stuff we talked about to set up internet... setting it up manually, leaving it by default, editing the interface, and nothing.
So I tried to re-install it, by formatting.
The main hard drive where Ubuntu was installed was, of course, the same one where Windows XP was installed, but on a different partition. That hard drive is 150GB, most of it (almost 120GB) was reserved for XP, and the rest was the partition for Ubuntu.
The install program didn't show the options for partitioning, installing, etc, that it showed to me when I booted from the CD the very first time...actually this time it showed something like:
**Use the entired drive:**
 -140GB
-120GB (this is an entirely different hard drive I have... the slave one where I keep the downloads and stuff like that).

**Manual**

So I chose the first one (use the entire drive), and selected the 140GB disc... thinking Ubuntu was going to be smart enough to find for itself where Ubuntu is installed.
Of course I didn't do all this stuff in a rush... I stopped a million times to think about it, re-read the whole thing. But it was pretty late where I love, 1.30 AM, and none of you were around here to help me so I had to throw myself in.
I left it for 40min... it was stuck at 82%... I have a Core2Duo 2.66GHZ, 2GB RAM...so it was impossible that it took sooo much time... plus it had been stuck at 82% for 20 minutes. So I stopped the installation, and rebooted the system fearfull of what I was sure had happened: Windows was no longer there, Ubuntu was no longer there. So the next thing I found when I booted the system was a Grub error (Error 17 I think)...

So right now I'm writing from my girlfriend's PC... hatefull towards Ubuntu that didn't show the right options and wasn't smart enough to understand that IT was ALREADY installed there... all it had to do was re-format that small piece.... as I couldn't do it because UBUNTU INSTALLATION GUI never showed me the option to select what part I wanted to format.
I even tried from GParted but no..... I couldn't do anything there either.


So right know I'm wondering how the hell to format the entire C (140GB) drive to use the whole of it, and install the precious XP.


Thank you.

Bye Ubuntu, at least for the time being... and until it'll be a real quality thing and not just a beta of a future O.S

---

### Post by Eiríkr on 2008-03-13
Ooofda...  :shock:

Well, just in case it might come in handy for future reference, have a peek at the "Manual" option in future -- and it's not just Ubuntu that does this, Mandriva does too (or at least did as of their 2006 release).  That's where the bit about selecting partitions was hiding.  :-(

Anyway, about formatting the whole drive, Windows (or any other OS you might happen to try) should give you that option when you boot up the installation CD.  

For what it might be worth, all three Linux varieties I've tried so far have gone through rough patches -- RedHat, Mandrake-then-Mandriva, and apparently now also Ubuntu.  Sometimes the issue is that newer hardware is locked down with proprietary drivers that the manufacturer only provides for Windows, combined with legal ******** like the DMCA and copyright issues to try to keep anyone from back-engineering any other drivers (pretty much any distro at some point or other); sometimes the issue is that software packages become temporarily dysfunctional, like repositories and updaters disappearing or just acting funny (what drove me from Mandriva, apparently since fixed), or Ubuntu's current wireless and other networking problems; sometimes the issue is a full-on change in policy for the distro, with mass confusion and difficult migration (why I left RedHat when Fedora first showed up and was clearly a rocky start).  And it seems like Microsoft isn't entirely immune to these symptoms either, as Vista has shown *all* of these problems, with many people quite upset about drivers, goofy software issues, and mass confusion and difficult migration.  Apple has avoided some of these problems by deliberately restricting the hardware they develop MacOS for, but even then the Mac forums are not devoid of people finding bugs.  So who knows, it might just be that you've run smack dab into a set of problems inherent in the creation and evolution of any OS.  :-|  

Mind you, I'm totally *not* trying to tell you not to be frustrated -- be rightfully pissed off!  But also, learn what you can from this, so at least your time and effort hasn't been wasted.    And may you have better luck with whatever distro you next go with, be it Windows, Mandriva, Fedora, Mac (?!), one of the BSDs, or even Ubuntu again, just further down the road.  :)

Cheers,

Eiríkr

---

### Post by F D B on 2008-03-13
Yeah, you're right about everything.
But the main thing that's got me pissed off, isn't the fact that I lost all the data I had on my main hard drive, which is a lot.
It's because I had to give up on Ubuntu even before I got to try it with all of its option. Because I never got to install the Nvidia driver, because an error poppued up everytime, this means I couldn't enable all of the effects... I couldn't get Compiz (which is the main reason I got into Ubuntu), and I never got Internet working.
So aside from all those problems... I was willing to give it a second chance but it ****** up my computer.

I might try a third time some time.

---

### Post by Eiríkr on 2008-03-13
Fair enough.  You might want to try on different hardware though, even aside from the network problems you've run into, as NVidia's closed drivers have a reputation for intermittent flakiness, and they don't look too keen on letting the OSS community in.  ATI has been getting better about Linux drivers, so they might be worth a shot.  

Good luck,

Eiríkr

---

### Post by daisyfoofpoof on 2008-03-13
> **Druke said:**
> ok when you click on teh network manager in the system tray (by the clock, it will look like a computer screen), do you see any networks?

wow that worked for me thanks!

---

### Post by hookzilla on 2008-03-13
F D B,

I'm a "noobie" too and have had trouble getting wireless to work.  My adapter also uses a ralink chipset (that's a difference from XP.  In XP, you install the card.  In Linux, you install the chipset)  You might take a look at this thread.  It might help, even though it's for a different Ralink chipset.

[http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

---

### Post by F D B on 2008-03-14
Thank you hookzilla, I might try it the next time I give Ubuntu a try, if ever is any.

I'm browsing from XP again now... believe it or not, for the first time I'm appreciating Microsoft and Windows XP. Although I have no doubt Linux distros like Ubuntu will keep evolving and one day, maybe not to far away, it'll be THE o.s.

Thank you all for your help.

Oh, BTW Eirikr... I gotta admit I kinda laughed when you suggested me to buy new hardware just to try Linux/Ubuntu again in the future.... first because I wouldn't buy new hardware just to try out an O.S (I'm not just talking about Linux, this applies for Microsft ones too)... and also because I think I have prime hardware right now, top notch. I have the most used hardware, the most average... drivers should abound for all this. Core Duo 2.66GHz, MSI NEO P35 motherboard, 2GB RAM, NVIDIA GeForce 8600GTS 512MB (MSI), Ethernet card, D-LINK Router.... it's a pretty average, yet very good, system. I thought this would make things far more easier with Ubuntu... guess I was wrong.

Anyway you have been very kind and I really appreciate it. Thanks a million. 
I hope the next time I decide to try Ubuntu, you're still around to help me whenever problems might happen to me, oh... and they will happen to me.

Blessings.
F D B.

---

### Post by Eiríkr on 2008-03-14
FWIW, my intent wasn't so much to say "buy new hardware to try Linux", as it was to suggest you might want to wait a while until either a) you've got a new computer just in the course of things (seems to happen for me about every 3-5 years), or b) NVidia gets its act together and releases better drivers / opens up to the OSS community.  Re-reading my post though, it does sound like I was saying "sure, buy a new computer!" -- but that wasn't my intention.  :)

And hey, next time around, I'm sure even if I'm personally not here on the site, someone else here in the Ubuntu community will pitch in -- that's one thing I'm liking in Linux Land is how generally helpful folks can be.  Sure, there's the occasional snot who's busy trying to feel important, but on the whole, people on the boards are a positive lot.  Good luck in future, and whichever OS or distro you decide on, I find one simple rule of thumb can get you pretty far in life -- **use what works for you.**  :)

Cheers,

Eiríkr

---

