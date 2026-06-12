---
title: "Lost - Wireless Setup"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by jar3232 on 2007-03-31
I searched through literally hundreds of posts regarding wireless setup and I am even more lost then when I started, which I am not even sure if that is possible.  I went through the "How To" thread and tried a couple of things.  Nothing good so far, and as much as I hate being the noobie and asking dumb questions, I see no other options.  This is also my first experience with LINUX.  I am going to build my first system soon and want to stay away from windows.  My idea was to run just linux and use the notebooks for backups w/windows.  So this is my test experience on my old computer to see if I am smart enough.  

On the "How To" thread, I didn't see my wireless card as supported.  Which worries me.  I am running a Belkin F6D3000, and Ubuntu 6.10.  This is were i am at:

When running iwconfig this is what I get:

lo: No wireless extensions
wifi0: No wireless extensions
atho: IEE 802.11g essid: "CLE"
        mode: Managed Frequency: 2.422 GHz Access Point: Not-Associated
        Bit Rate: 1mb/s Tx-Power: 14 dBm Sensitivity=0/3
        Retry: Off RTS: thr: of Fragment thr: off
        Power Management: off
        Link Quality= 47/94 Signal Level= 48 dbm Noise Level=-95 dBm
        Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag:0
        Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0
sit0: No wireless extensions

iwlist

lo: Interface doesn't support scanning
etho: Interface doesn't support scanning
Wifi0: Interface doesn't support scanning
atho: Scan completed:
        Cell 01 - Address: (Mine)
        ESSID: "CLE"
        Mode: Master
        Frequency: 2.412 (Channel 1)
        Link Quality= 47/94 Signal Level= 48 dbm Noise Level=-95 dBm
        Encryption key: ON
        Bit Rates: A bunch
        Extra: bcn_int=100
        IE: WPA Version 1
        Group Cipher:  CCMP
        Pairwise Ciphers (1) : CCMP
        Authentication suites (1) : PSK
sit0: Interface doesn't support scanning

I "think" I have the card installed right, but who knows at this point.  I think I am getting a signal.  I tried turning off WPA, mac filtering and all that other stuff.  And I still don't get ANYTHING.  Am I totally off base?  Am I doomed to a life of windows?  Could someone PLEASE help out this poor lost noob.  Thanks in advance.

---

### Post by Floppyjoe on 2007-03-31
According to the Madwifi site at this Url:

[http://madwifi.org/wiki/Compatibility/Belkin](http://madwifi.org/wiki/Compatibility/Belkin)

Someone has reported your card to be working with the madwifi drivers

Madwifi drivers are included in the linux-restricted-modules for your kernel version.

type uname -r at the terminal to find your kernel version.

---

### Post by jar3232 on 2007-03-31
it's telling me 2.6.17.10-generic

---

### Post by Floppyjoe on 2007-03-31
> **jar3232 said:**
> it's telling me 2.6.17.10-generic

Try 
```
sudo apt-get install linux-restricted-modules-2.6.17.10-generic
```
see if that does the trick.

---

### Post by GSF1200S on 2007-03-31
> **jar3232 said:**
> it's telling me 2.6.17.10-generic

I had problems getting my wireless card to work as well. Trying madwifi is your best bet, but dont forget about ndiswrapper. It didnt work for me, but it may for you.

I couldnt get madwifi to work at first because my HAL was not compatible with the madwifi drivers. As soon as I upgraded to the Feisty beta, my madwifi drivers worked and I havent had a problem since. So, consider upgrading to Feisty if all else fails...

---

### Post by jar3232 on 2007-03-31
OK, wireless card is now working, I am almost positive, under ath0 (I assume that is my wireless connection)...I have good signal, but I still cannot connect to my network.  Should I set a static IP?  or should I just upgrade?

---

### Post by GSF1200S on 2007-03-31
> **jar3232 said:**
> OK, wireless card is now working, I am almost positive, under ath0 (I assume that is my wireless connection)...I have good signal, but I still cannot connect to my network.  Should I set a static IP?  or should I just upgrade?

Hold on one sec while I switch to GNOME.. XFCE is currently having permission issues with wireless. No, I never had to set static, and you shouldnt either...

---

### Post by jar3232 on 2007-03-31
:) I am not going anywhere...I am determined to get this working.  Thanks for your help btw...

---

### Post by GSF1200S on 2007-03-31
> **jar3232 said:**
> OK, wireless card is now working, I am almost positive, under ath0 (I assume that is my wireless connection)...I have good signal, but I still cannot connect to my network.  Should I set a static IP?  or should I just upgrade?

Ok, for some reason on mine I have two different devices for my wireless. I have ath0 and wifi0. Im connected through the internet through ath0, but if I disable wifi0 my internet connection stops just the same. What settings do you have in the network manager? Are you trying to connect to a network with a WEP/WPA key?

Im just trying to get all this info together so I can search some threads.. I know I had a similar problem when I was close to connecting.. youve got a stupid problem right now, meaning youre close...

---

### Post by GSF1200S on 2007-03-31
> **jar3232 said:**
> :) I am not going anywhere...I am determined to get this working.  Thanks for your help btw...

Im just curious..

type

dmesg

in a terminal and post anything that seems to relate to your wireless. Im no expert here mind you, but I think we can get this eventually..

After this, type in a terminal:

iwconfig

and post those results...

Finally, type in a terminal:

ifconfig

and post the results... maybe I can figure something out comparing it to mine...

---

### Post by GSF1200S on 2007-03-31
> **GSF1200S said:**
> Im just curious..

type

dmesg

in a terminal and post anything that seems to relate to your wireless. Im no expert here mind you, but I think we can get this eventually..

After this, type in a terminal:

iwconfig

and post those results...

Finally, type in a terminal:

ifconfig

and post the results... maybe I can figure something out comparing it to mine...

Oh and another thing.. run the update manager and make sure that you have the latest updates. I had a problem selecting between my wireless and wired connections, but upon the latest updates, the problem was immediatly resolved.

---

### Post by jar3232 on 2007-03-31
> Are you trying to connect to a network with a WEP/WPA key?

Yes, I followed the "how to" on that section.  I have also tried enabling/disabling that function, no change at all...

dmesg

wifi0: 11a/b/g rates: ... standard 64, 9, 13, 18, 24, 36, 48, 54 bps
wifi0: h/w encryption support: wep aes aes_ccm tkip
wifi0: mac 10.5 phy 6.1 radio 6.3
wifi0: use hw queue 1 for wme_ac_be traffic
ath0: no IPv6 routers present

Seems like most of the wireless stuff there...but I could be wrong...

[COLOR="Red"]NOTE: I switched my connection, via the two computers and the single bar to wifi0, I get a lot of activity from sending/receiving, but no signal bar and the computer turned a different color, but when I go to configure, I get "The interface does not exist" ??
[/COLOR]

iwconfig

lo: No wireless extensions
wifi0: No wireless extensions
atho: IEE 802.11g essid: "CLE"
mode: Managed Frequency: 2.422 GHz Access Point: Not-Associated
Bit Rate: 1mb/s Tx-Power: 14 dBm Sensitivity=0/3
Retry: Off RTS: thr: of Fragment thr: off
Power Management: off
Link Quality= 47/94 Signal Level= 48 dbm Noise Level=-95 dBm
Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag:0
Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0
sit0: No wireless extensions

iwlist

lo: Interface doesn't support scanning
etho: Interface doesn't support scanning
Wifi0: Interface doesn't support scanning
atho: Scan completed:
Cell 01 - Address: (Mine)
ESSID: "CLE"
Mode: Master
Frequency: 2.412 (Channel 1)
Link Quality= 47/94 Signal Level= 48 dbm Noise Level=-95 dBm
Encryption key: ON
Bit Rates: A bunch
Extra: bcn_int=100
IE: WPA Version 1
Group Cipher: CCMP
Pairwise Ciphers (1) : CCMP
Authentication suites (1) : PSK
sit0: Interface doesn't support scanning

I don't have a wired connection.  Router is in the basement, and the computer is on the 2nd floor...I knew that was going to cause me troubles one day...

---

### Post by GSF1200S on 2007-03-31
> **jar3232 said:**
> Yes, I followed the "how to" on that section.  I have also tried enabling/disabling that function, no change at all...

dmesg

wifi0: 11a/b/g rates: ... standard 64, 9, 13, 18, 24, 36, 48, 54 bps
wifi0: h/w encryption support: wep aes aes_ccm tkip
wifi0: mac 10.5 phy 6.1 radio 6.3
wifi0: use hw queue 1 for wme_ac_be traffic
ath0: no IPv6 routers present

Seems like most of the wireless stuff there...but I could be wrong...

[COLOR="Red"]NOTE: I switched my connection, via the two computers and the single bar to wifi0, I get a lot of activity from sending/receiving, but no signal bar and the computer turned a different color, but when I go to configure, I get "The interface does not exist" ??
[/COLOR]

iwconfig

lo: No wireless extensions
wifi0: No wireless extensions
atho: IEE 802.11g essid: "CLE"
mode: Managed Frequency: 2.422 GHz Access Point: Not-Associated
Bit Rate: 1mb/s Tx-Power: 14 dBm Sensitivity=0/3
Retry: Off RTS: thr: of Fragment thr: off
Power Management: off
Link Quality= 47/94 Signal Level= 48 dbm Noise Level=-95 dBm
Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag:0
Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0
sit0: No wireless extensions

iwlist

lo: Interface doesn't support scanning
etho: Interface doesn't support scanning
Wifi0: Interface doesn't support scanning
atho: Scan completed:
Cell 01 - Address: (Mine)
ESSID: "CLE"
Mode: Master
Frequency: 2.412 (Channel 1)
Link Quality= 47/94 Signal Level= 48 dbm Noise Level=-95 dBm
Encryption key: ON
Bit Rates: A bunch
Extra: bcn_int=100
IE: WPA Version 1
Group Cipher: CCMP
Pairwise Ciphers (1) : CCMP
Authentication suites (1) : PSK
sit0: Interface doesn't support scanning

I don't have a wired connection.  Router is in the basement, and the computer is on the 2nd floor...I knew that was going to cause me troubles one day...

All that stuff is identical to mine, can you post "ifconfig"? Ill throw some simple crap out there just in case were nuking this... Right click on the network icon in the system tray and make sure "Enable Wireless" is checked.. Make sure on the network manager that roaming mode is enabled. Make sure everything is set to DHCP connection. Turn the security off on your router (if possible) just so we can establish some connection. 

Once again, I really would like to see the results of ifconfig...

I have to run an errand right now, so unfortunately I will be unable to respond promptly. I will be gone a few hours, but I will respond immediately upon my return.. Well get this eventually. The most important thing is that its recognizing your network, which means the wireless card is interfacing with Linux...

---

### Post by jar3232 on 2007-03-31
Well I here you go, hope this helps (me), I am moving on to another problem, I seem to have many of them.  I tell you, this program has been very humbling... 

jeff@jeff-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:17:3F:48:A1:5A  
          inet6 addr: fe80::217:3fff:fe48:a15a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11170 (10.9 KiB)  TX bytes:11170 (10.9 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-17-3F-48-A1-5A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5990 errors:0 dropped:0 overruns:0 frame:31936
          TX packets:59656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:553479 (540.5 KiB)  TX bytes:2601768 (2.4 MiB)
          Interrupt:201 Memory:eeb40000-eeb50000
> 
Right click on the network icon in the system tray and make sure "Enable Wireless" is checked.. Make sure on the network manager that roaming mode is enabled.

When I right click on the network icon, the only options I receive are: properties, help, about, remove from panel, move, lock panel

---

### Post by GSF1200S on 2007-04-01
> **jar3232 said:**
> Well I here you go, hope this helps (me), I am moving on to another problem, I seem to have many of them.  I tell you, this program has been very humbling... 

jeff@jeff-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:17:3F:48:A1:5A  
          inet6 addr: fe80::217:3fff:fe48:a15a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:H        UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11170 (10.9 KiB)  TX bytes:11170 (10.9 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-17-3F-48-A1-5A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5990 errors:0 dropped:0 overruns:0 frame:31936
          TX packets:59656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:553479 (540.5 KiB)  TX bytes:2601768 (2.4 MiB)
          Interrupt:201 Memory:eeb40000-eeb50000


When I right click on the network icon, the only options I receive are: properties, help, about, remove from panel, move, lock panel

Sorry for the long response time.. drunks can be so hard to keep in line...

Man, I just dont see whats going on... Its showing in ifconfig that packets are being transmitted and received. You said yourself you can see the wireless networks, but you cant connect to them- where can you see the networks? Are they in a dropdown box from the system tray, or can you only see them when you open the network box from the system menu?

I cant believe someone else hasnt posted a fix to be honest.. I think the people who have had expierience with this just havent seen the thread..

Lets try this- go to your Synaptic Package manager, and make sure all of the following are installed- check to make sure these are installed...

Gnome-netstatus-applet
Gnome-nettool
ifupdown
iptables
iputils-ping
iputils-tracepath

If they are, cool, whatever ones are missing, install.

These next three should be installed, but even if they are, reinstall them:

net-tools
network-manager
network-manager-gnome

When youre done with this, try a restart, and see if it works.. If it doesnt, then post up here and ill dig deeper... I know I did most of this trying to get my wireless working, but I dont know what exactly fixed it... Its too bad we dont have a techie in here who can spit out some terminal codes, eh?? Good luck...

**Edit** You know I just realized something... Your ath0 device isnt sending/receiving anything, but your wifi0 is. On my ifconfig readout, BOTH are sending/ receiving... Try the stuff I put above, but im gonna look into why ath0 is reading how it does..

---

### Post by jar3232 on 2007-04-01
> network-manager
network-manager-gnome

I cannot find either of those on the list...I am trying to figure out how to install them as we speak...


[COLOR="Red"]EDIT: OK, I found a reallllllly long cord and it gets on fine with the wired connection.  I am trying to run an update...

EDIT EDIT: Still does not work...[/COLOR]

---

### Post by GSF1200S on 2007-04-02
> **jar3232 said:**
> I cannot find either of those on the list...I am trying to figure out how to install them as we speak...


[COLOR="Red"]EDIT: OK, I found a reallllllly long cord and it gets on fine with the wired connection.  I am trying to run an update...

EDIT EDIT: Still does not work...[/COLOR]

Dang it... im researching this further... I dont understand how your having a problem...

---

### Post by jar3232 on 2007-04-02
Either do I...

Once again, thanks for your help...

---

### Post by GSF1200S on 2007-04-03
Anyone else? I know some of you out there can probably give us at least some direction.

Ive been trying to give advice, but relatively speaking, im a noob too.. Im beginning to run out of ideas...

---

### Post by josephus on 2007-04-05
Can you try this sequence of commands.  If possible try to do this without any encryption until we get this part sorted out.
```

sudo ifconfig ath0 down
sudo ifconfig ath0 up
sudo dhclient ath0
```

Right now it sounds to me that you are able to able to connect to the router, but you are not being assigned assigned an ip address.

Edit:  I just re-read the post and I think I mixed this post with another one that I was looking at.  It doesn't seem you are even connecting with the router.  But give those commands a try anyway, and maybe we'll get lucky.

---

### Post by jar3232 on 2007-04-05
This is what I got...I can do it with security on, off, whatever...I live in Cleveland, people stealing my internet is the least of my concerns...

> jeff@jeff-desktop:~$ sudo ifconfig ath0 down
jeff@jeff-desktop:~$ sudo ifconfig ath0 up
jeff@jeff-desktop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:17:3f:48:a1:5a
Sending on   LPF/ath0/00:17:3f:48:a1:5a
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
jeff@jeff-desktop:~$ 

[COLOR="Red"]EDIT: Should I install ndiswrapper or something?  I feel like I am missing something REALLY obvious here...How do you pick the network you want to connect to? [/COLOR]

---

### Post by GSF1200S on 2007-04-05
> **jar3232 said:**
> This is what I got...I can do it with security on, off, whatever...I live in Cleveland, people stealing my internet is the least of my concerns...

Dangit.. Im running out of ideas. I cant find any post or webpage that deals with your problem. Ironically, Im having the same problem when I try to use the XFCE interface. Wifi Radar shows the surrounding signal and networks, but I cant connect...


Lets try this, and this is my last resort.

Before we do, let me ask you a question.. Have you tried to install the NVIDIA drivers (or ATI) for Linux yet? If so, the methods we are using are going to create problems there. I can walk you through a NVIDIA driver install, but let me know...

Ok, im assuming youre trying to use madwifi for your wireless. Go to the Synaptic package manager and search for madwifi. Find a package called 'madwifi tools' and download/install it. Then, search for 'linux restricted modules'- remove them. Next, open up firefox, and google for 'madwifi.' On the madwifi homepage, download version 0.9.3 as a .tar.gz (not bz2) and put it in your home folder.

Next. right click on the madwifi package, and extract its contents to your home folder as well. Then open a terminal...

In the terminal, change directory to the extracted folder. For example, mine was in the madwifi-0.9.3 folder so I typed:

cd madwifi-0.9.3

in the terminal window. Then type:

sudo make

Then:

sudo make install

Then:

sudo make clean

Then just restart... 

Maybe that will fix it... youll have the drivers and the tools you need. Let me know what happens with this

---

### Post by josephus on 2007-04-06
Your problem is somewhat of a mystery to me.  

If you want to connect to a specific access point you can specify it by essid or by address number

```
sudo iwconfig ath0 essid "ESSID_NAME"
sudo iwconfig ath0 ap xx:xx:xx:xx:xx
```

Usually if you want it done automatically
```
sudo iwconfig ath0 essid any
```

With your encryption on the router off, make sure you disable encryption on your wireless card with
```
sudo iwconfig ath0 key off
```

and then use sudo ifdown ath0 && sudo ifup ath0 sequence.  You might also want to change from restricted to open mode by trying

```
sudo iwconfig ath0 enc open
```

All these options are documented and can be read using 
```
man iwconfig
```

Also can you double check your settings in the Network Settings Manager.  Open it up
with System->Adminstration->Networking.  Make sure ath0 is enabled.

-----

I'm sure you've read through this already, but just in case you haven't: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Did made a note of how turning off acpi helps for some people.

-----

Have you connected to the router on this hardware before using windows?

----

If none if this works.  I suggest trying ndiswrapper or the next version madwifi.  One option might to burn the Feisty Fawn beta and see if the Live CD can make your wifi work.

Hope some of this helps.

---

### Post by dwalraven on 2007-04-06
Jar3232,

I'm another noob at this, so consider this a 'blind leading the blind' bit of assistance.  

Do you have WEP or WAP turned on at your access point?  If so, do you have have the right password set up in your network settings?  64bit, 128bit, plain text or hex?  

The pieces look to be talking, but they are not speaking the same language.  If you uncheck the 'enable wireless' logout and then log back in, then try setting up the card with new settings...

Just an idea...

---

### Post by jar3232 on 2007-04-06
Right before I killed ubuntu, Below is what I saved...I  am positive it is something I did...So, I am attempting to reinstall and try again...I feel like Homer Simpson on Ubuntu...O, they have the internet on computers now?

> jeff@jeff-desktop:~$ cd madwifi-0.9.3
jeff@jeff-desktop:~/madwifi-0.9.3$ sudo make
Password:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/jeff/madwifi-0.9.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/jeff/madwifi-0.9.3/ath/if_ath.o
  CC [M]  /home/jeff/madwifi-0.9.3/ath/if_ath_pci.o
  LD [M]  /home/jeff/madwifi-0.9.3/ath/ath_pci.o
  CC [M]  /home/jeff/madwifi-0.9.3/ath_hal/ah_os.o
  HOSTCC  /home/jeff/madwifi-0.9.3/ath_hal/uudecode
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c: At top level:
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c: In function 'main':
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/jeff/madwifi-0.9.3/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/jeff/madwifi-0.9.3/ath_hal/uudecode] Error 1
make[2]: *** [/home/jeff/madwifi-0.9.3/ath_hal] Error 2
make[1]: *** [_module_/home/jeff/madwifi-0.9.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [modules] Error 2
jeff@jeff-desktop:~/madwifi-0.9.3$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.17-11-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/jeff/madwifi-0.9.3/ath'
test -d //lib/modules/2.6.17-11-generic/net || mkdir -p //lib/modules/2.6.17-11-generic/net
cp ath_pci.ko //lib/modules/2.6.17-11-generic/net
cp: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/jeff/madwifi-0.9.3/ath'
make: *** [install-modules] Error 1
jeff@jeff-desktop:~/madwifi-0.9.3$ sudo make clean
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i clean; \
        done
make[1]: Entering directory `/home/jeff/madwifi-0.9.3/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/jeff/madwifi-0.9.3/ath'
make[1]: Entering directory `/home/jeff/madwifi-0.9.3/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/jeff/madwifi-0.9.3/ath_hal'
make[1]: Entering directory `/home/jeff/madwifi-0.9.3/ath_rate'
for i in amrr/ onoe/ sample/; do \
                make -C $i clean; \
        done
make[2]: Entering directory `/home/jeff/madwifi-0.9.3/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/jeff/madwifi-0.9.3/ath_rate/amrr'
make[2]: Entering directory `/home/jeff/madwifi-0.9.3/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/jeff/madwifi-0.9.3/ath_rate/onoe'
make[2]: Entering directory `/home/jeff/madwifi-0.9.3/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/jeff/madwifi-0.9.3/ath_rate/sample'
make[1]: Leaving directory `/home/jeff/madwifi-0.9.3/ath_rate'
make[1]: Entering directory `/home/jeff/madwifi-0.9.3/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/home/jeff/madwifi-0.9.3/net80211'
make -C ./tools  clean
make[1]: Entering directory `/home/jeff/madwifi-0.9.3/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig core a.out
make[1]: Leaving directory `/home/jeff/madwifi-0.9.3/tools'
rm -rf .tmp_versions
rm -f *.symvers svnversion.h
jeff@jeff-desktop:~/madwifi-0.9.3$ 


---

