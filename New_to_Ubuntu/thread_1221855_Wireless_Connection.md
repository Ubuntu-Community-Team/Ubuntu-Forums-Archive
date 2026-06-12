---
title: "Wireless Connection"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by linlearn on 2009-07-24
Hi Experts,
I want to connect by wireless . I have a Netgear Router WPN824. I have read the forums and cant see anything for Netgear. I dont see it in the network connections. I have created a new one with my SSID but the internet does not work. I am using an Asus laptop

Any drivers missing. Any ideas?

Linlearn
P.S. I cannot get into Vista ( I have tried on this forum)

---

### Post by LowSky on 2009-07-24
router shouldnt be the issue

what type of wireless card does you pc have

if not sure please open a terminal type this command and then copy the data here

```
lspci
```
 its a lowercase L not a 1 by the way

---

### Post by Ratscallion on 2009-07-24
Can you actually see any wireless access points by running this in a Terminal:

sudo iwlist wlan0 scan

Replace wlan0 with the name of your wireless card.. (see ifconfig)
If you can't, you'll need ndiswrapper. It's included in the CD, just search ndis and you should get a list of .deb files, install the ones that are ndiswrapper (there's a few, install the lot) and ndisgtk.

---

### Post by linlearn on 2009-07-24
Ratscallion,
I get this for wlan0
wlan0     No scan results
Running ifconfig gives the following. What is my wireless card??? I use a Netgear router
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:73:0c:09  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe73:c09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19191 errors:0 dropped:0 overruns:0 carrier:9
          collisions:0 txqueuelen:1000 
          RX bytes:42313714 (42.3 MB)  TX bytes:0 (0.0 B)
          Memory:feac0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1992 (1.9 KB)  TX bytes:1992 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:71:3b:fc  
          inet6 addr: fe80::215:afff:fe71:3bfc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:20625 (20.6 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:15:af:71:3b:fc  
          inet addr:169.254.8.159  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-71-3B-FC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Thanks

Linlearn

---

### Post by lsouth on 2009-07-24
Hello
 I'm lurking with the same problem and not much savvy.  Pease tell me what you mean by "open a terminal".
Lee

---

### Post by linlearn on 2009-07-24
Hello Lee,
Go to the top menu. Applications > Accessories > Terminal
type in sudo iwlist wlan0 scan
It will ask you for a password if you have set up Ubuntu with a password.
Linlearn

---

### Post by lsouth on 2009-07-24
Thanks linlearn.
Not to hijack your thread, I'll lurk before starting another.
Lee

---

### Post by linlearn on 2009-07-24
Lowsky,
What is my card???
Output of 
$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

---

### Post by Ratscallion on 2009-07-24
Your card seems to be wlan0... Try going for a 
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
Log out then back in again
sudo iwlist wlan0 scan
You should get SOME result
Then you can use network thingy in the corner to select your network. Your router should not be the problem, it's usually wireless drivers etc.

---

### Post by Ratscallion on 2009-07-24
When ever anyone says do this in a Terminal, it means go into Applications -> Accessories -> Terminal and run the command they say in there. Good luck!

---

### Post by linlearn on 2009-07-24
Ratscallion.
I logged out .  I have closed the terminal and the browser. And back in
This is the result
wlan0  no scan results

Should I restart , you mean
Linlearn

---

### Post by Ratscallion on 2009-07-24
Hmm... Did you run those commands before you logged out? If not, you'd need to... Ah, wait a second, you've got an Atheros graphics card! Go to System -> Administration -> Hardware Drivers. There may be something in there relative to your wireless card... Try enabling that, and then restart. If nothing happens still, disable the thing in hard ware drivers (or if there was nothing in there) boot into Ubuntu and load the Live CD. Search for ndis and install ndiswrapper (there's a few, install the lot) and ndisgtk (they're .deb files). Once they're installed, you should have something new in System -> Administration (near the bottom). Then, extract the attached zip and put the file it says into it. Reboot, and try again...

---

### Post by linlearn on 2009-07-24
Ratscallion,
I found madwifi and activated. When you say restart, do you mean restarted the pc?

I cant see any network

Linlearn

---

### Post by Ratscallion on 2009-07-24
I mean restart the PC. Yes.

---

### Post by linlearn on 2009-07-24
:~$ sudo iwlist wlan0 scan
 
wlan0     Interface doesn't support scanning.

And I have installed ndis * . Went to System > Admin. At the bottom Windows wireless drives. Nothing in there.

linlearn

---

### Post by Ratscallion on 2009-07-24
Yup, shouldn't be. Disable the madwifi driver. Download + Extract the attached zip and browse to the file ndiswrapper wants from within ndiswrapper. Enable it, restart, run 
```
sudo iwlist wlan0 down
sudo iwlist wlan0 up
```
Log out, log back in and all should work.

---

### Post by linlearn on 2009-07-27
Hi Ratscallion,
 I have disabled madwifi. Then I have extracted and installed the inf file. I go to Sys > Admin >Windows Wireless driver.s Everytime it says 'unable to see if hardware is present'. Once I click OK it is there. Apparently the code 'sudo iwlist wlan0 down' is an unknown command. I typed 'sudo iwlist wlan0 scan' and I get no scan result. Please see screenshots
I have restarted a couple of times and still get no hardware present and no scan results.
The wireless connections are greyed out.
What do I do?

Linlearn

---

### Post by Ratscallion on 2009-07-27
That should be fine... Got the driver installed in ndiswrapper... It's not iwlist, it's
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```
Sorry about confusion!

---

### Post by linlearn on 2009-07-27
I did just that. I wrote the code 'sudo ifconfig wlan0 down' and up. I still get 'unable to see if hardware is present' . I dont see any wireless connection. attached network connections shows none. I must be doing something wrong.
I cant open Windows .
Linlearn

---

### Post by Ratscallion on 2009-07-27
Ok... Urm, make sure the following is sorted:
Go into Windows Wireless Drivers, a driver should be present and in the list. Ignore any errors.
Go into System -> Administration -> Hardware Drivers. There should be a driver there concerning wifi, if it's enabled, disable it and reboot. If it's disabled, leave it be.
Go into a Terminal and type ```
sudo iwconfig
``` something should have a wireless extension, for example, when I do it, I get this:
> sam@ubuntu: sudo iwconfig
eth0 : No wireless extensions
wlan0 : (load of output because it's a wifi)
Something of yours will be similar output to my wlan0, that's your wireless card.
Go into a Terminal and replace wlan0 in these examples with your wireless card, if it's wlan0, you can keep it.
```
sudo iwlist wlan0 down
sudo iwlist wlan0 up
```
That just disables, and re-enables the wifi card. Reboot.
Go back into a Terminal and type ```
sudo iwlist wlan0 scan
``` (again, replacing wlan0 with your wifi card).

Any errors in any of these steps? Output that is different to a list and details of nearby access points with the final command? Paste anything you aren't sure of here.

---

### Post by LookTJ on 2009-07-27
Ratscallion,

seems that the iwlist command doesn't like to work with interfaces :(

Here's something odd I've found

```
iwlist eth1 scan
```I get no result

However, if I replace eth1 with eth0, for some strange reason I get results. but I am pretty sure this only relates to my system setup.

Hope this resolves some confusion :)

Edit: apparently iwconfig is showing eth0 as wireless card..

so doing iwocnfig should determine your card.

:)

Carry on :)

EDIT: Something was screwed up with the config file and made my ethx opposite of what it should be.

It's all fixed now. eth1 is now my wifi interface, and eth0 is wired.

---

### Post by linlearn on 2009-07-27
Here is what I have done:-

sudo iwlist eth0 scan
eth0      Interface doesn't support scanning.
~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Linlearn

---

### Post by Ratscallion on 2009-07-27
Cool. That means wlan0 is your wireless card. Go ahead and try my steps exactly, you don't need to change wlan0 to anything else :)

---

### Post by linlearn on 2009-07-27
I have disable the driver in system>Admin.
I have typed this
sudo iwlist eth0 scan
eth0      Interface doesn't support scanning.

sonroy@sonroy-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

I have rebooted . The wireless is greyed out.

---

### Post by Ratscallion on 2009-07-27
Hmm... With the drivers disabled, wlan0 being your wifi card... You need to do 
```
sudo iwlist wlan0 scan
```
NOT
```
sudo iwlist eth0 scan
```

---

### Post by LookTJ on 2009-07-27
linlearn,
do what Ratscallion says,

```
sudo iwlist wlan0 scan
```

:)

---

### Post by StevenD on 2009-07-27
Hope it is ok to jump into this thread. I'm brand new to Ubuntu (since yesterday Sunday July 27) and am trying to get stuff set up. Some one gave me a Linksys Wireless USB Network Adapter to try out and I can't figure out how to get it connected. I plug it in but nothing is showing that it is connected.

---

### Post by linlearn on 2009-07-28
Hi Ratscallion,

**T[COLOR=Navy]hank you for your patience.[/COLOR]**
[COLOR=Navy]**I have done the following steps**[/COLOR]

>  Ok... Urm, make sure the following is sorted:
Go into Windows Wireless Drivers, a driver should be present and in the list. Ignore any errors.
Go into System -> Administration -> Hardware Drivers. There should be a driver there concerning wifi, if it's enabled, disable it and reboot. If it's disabled, leave it be.
> 
[COLOR=Navy]
**I have disabled the drivers.**[/COLOR]

> Go into a Terminal and replace wlan0 in these examples with your wireless card, if it's wlan0, you can keep it.
Code:
sudo iwlist wlan0 down
sudo iwlist wlan0 up
That just disables, and re-enables the wifi card. Reboot.> 
[COLOR=Navy][B]
Please see attachment. Done the code and rebooted from grub menu.[/B][/COLOR]

>  Go back into a Terminal and type
Code:

sudo iwlist wlan0 scan  > 

[COLOR=Navy]**I have done that. I do not get the Wireless in the network.**
[/COLOR]LookTJ thanks for jumping in

Linlearn.

---

### Post by Ratscallion on 2009-07-28
> **linlearn said:**
> Hi Ratscallion,

**T[COLOR=Navy]hank you for your patience.[/COLOR]**
[COLOR=Navy]**I have done the following steps**[/COLOR]

 Ok... Urm, make sure the following is sorted:
Go into Windows Wireless Drivers, a driver should be present and in the list. Ignore any errors.
Go into System -> Administration -> Hardware Drivers. There should be a driver there concerning wifi, if it's enabled, disable it and reboot. If it's disabled, leave it be.

[COLOR=Navy]
**I have disabled the drivers.**[/COLOR]

Go into a Terminal and replace wlan0 in these examples with your wireless card, if it's wlan0, you can keep it.
Code:
sudo iwlist wlan0 down
sudo iwlist wlan0 up
That just disables, and re-enables the wifi card. Reboot.
[COLOR=Navy][B]
Please see attachment. Done the code and rebooted from grub menu.[/B][/COLOR]

 Go back into a Terminal and type
Code:

sudo iwlist wlan0 scan  

[COLOR=Navy]**I have done that. I do not get the Wireless in the network.**
[/COLOR]LookTJ thanks for jumping in

Linlearn.

Sorry! My mistake! Therre's loads of network commands... It's meant to be
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

---

### Post by linlearn on 2009-07-28
> **Ratscallion said:**
> Sorry! My mistake! Therre's loads of network commands... It's meant to be
```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

Yes i have typed sudo ifconfig wlan0 down and up.
Rebooted and..
sudo iwlist wlan0 scan

No network seen.

Linlearn:confused:

---

### Post by ayenack on 2009-07-28
I thought this card was supported out of the box but seems not. Take a look at this it should help.

[http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278](http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278)

The driver on the page has changed location but is listed in some of the replies or you'll have to search for it using google.

---

### Post by ayenack on 2009-07-28
> **linlearn said:**
> Yes i have typed sudo ifconfig wlan0 down and up.
Rebooted and..
sudo iwlist wlan0 scan

No network seen.

Linlearn:confused:
 Think you're looking for:-

[B]sudo ifdown wlan0
sudo ifup wlan0[/B]

---

### Post by ayenack on 2009-07-28
This thread may also be of use.

[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

---

### Post by linlearn on 2009-07-28
> **ayenack said:**
> I thought this card was supported out of the box but seems not. Take a look at this it should help.

[http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278](http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278)

The driver on the page has changed location but is listed in some of the replies or you'll have to search for it using google.

I will give this a try after finishing with sudo ifdown wlan0.

---

### Post by linlearn on 2009-07-28
> **ayenack said:**
> Think you're looking for:-

[B]sudo ifdown wlan0
sudo ifup wlan0[/B]

Step1 Done this as in attachment , 
Step 2 rebooted and then
Step 3 sudo wlan0 scan. 
Still no network.

---

### Post by ayenack on 2009-07-28
If you wont to try a scan you'll have to use iwlist like this.

**iwlist wlan0 scan**

but if your woreless card is not configured then it will not show any results.

What's the name of your network (SSID)?

For instance if I type iwconfig wlan0 I get this for my wirless network.

wlan0     RT73 WLAN  ESSID:"ayenack_wireless"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 02:24:2B:76:1C:71   
          Bit Rate=1 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=48/100  Signal level:-88 dBm  Noise level:-115 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

Just out of interest have you tried using Network Settings?
**System_Administration_Network**

---

### Post by linlearn on 2009-07-29
> **ayenack said:**
> If you wont to try a scan you'll have to use iwlist like this.

**iwlist wlan0 scan**

but if your woreless card is not configured then it will not show any results.

What's the name of your network (SSID)?

For instance if I type iwconfig wlan0 I get this for my wirless network.

wlan0     RT73 WLAN  ESSID:"ayenack_wireless"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 02:24:2B:76:1C:71   
          Bit Rate=1 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=48/100  Signal level:-88 dBm  Noise level:-115 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

Just out of interest have you tried using Network Settings?
**System_Administration_Network**
I have used 'sudo iwlist wlan0 scan'. No scan results is shown.

My network ID is 'royson'.  How do I configure my wireless card?
Router: Netgear WPN824 range max.
SSID: royson
Uses WPA.

---

### Post by ayenack on 2009-07-29
Right first things first.

Go to.

**System_Administration_Network**

And see if Wireless Connection is shown there. If it is then setting up your wireless shouldn't be to painful. Post back and let me know.

BTW.
You don't need sudo with iwlist.

---

### Post by linlearn on 2009-07-29
> **ayenack said:**
> I thought this card was supported out of the box but seems not. Take a look at this it should help.

[http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278](http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278)

The driver on the page has changed location but is listed in some of the replies or you'll have to search for it using google.

I have been trying to get drivers. It is tough to get it and also the links are not all correct.
I have disabled ndiswrapper. I will install it and post results

---

### Post by ayenack on 2009-07-29
Did you check

**System_Administration_Network**

To see if **Wireless connection** is shown?

---

### Post by linlearn on 2009-07-29
> **ayenack said:**
> Did you check

**System_Administration_Network**

To see if **Wireless connection** is shown?
I have System > Administration > Network Tools
and 
System > Administration > Network Connections
Both do not show any connections. Network connections shows 'royson' which I had created. Please see attachment.

---

### Post by r.v.the.evil on 2009-07-29
i am new on ubuntu jaunty jackalope
i want 2 install wvdial in ubuntu to use mobile internet
and i linux terminal . i have write d profile as follows in eddit menu
[driver details]
phone = #777
username = internet
password = internet
and so on


i dont know how to save it
can anyonee reply me know
and tell me
, i really need it,
thanx 
with regards ,
ravi

---

### Post by ayenack on 2009-07-29
> **linlearn said:**
> I have System > Administration > Network Tools
and 
System > Administration > Network Connections
Both do not show any connections. Network connections shows 'royson' which I had created. Please see attachment.

I'm not running Ubuntu Jaunty and the Network Connection screen is different....

But it looks like you're in luck. I would guess what you need to do here is double click on royson then most likely it'll offer to connect then you'll need to enter your wpa key and you should be good to go. It might take a reboot.

If this does not work it's an idea to turn off encryption on the router and try to connect unencrypted just to see if you can connect (obviously once you've established if you can or can't turn encryption back on.)

That's about as far as I can help as I have never had to configure this particular card. It seems it's possible referring to the earlier post that I suggested. Maybe they would be your best bet from here on out. Any advice I would give would be generic wireless advice and not specific to your actual card.

---

### Post by ayenack on 2009-07-29
> **r.v.the.evil said:**
> i am new on ubuntu jaunty jackalope
i want 2 install wvdial in ubuntu to use mobile internet
and i linux terminal . i have write d profile as follows in eddit menu
[driver details]
phone = #777
username = internet
password = internet
and so on


i dont know how to save it
can anyonee reply me know
and tell me
, i really need it,
thanx 
with regards ,
ravi

You need to make a new thread (post).In the new thread you'll need to explain what editor you're using e.g. nano.

I'll answer this once here but no more question in this thread please.

If you're in terminal and you're using nano to edit the file then to save you press ctrl+o then to exit ctrl+x.

---

### Post by StevenD on 2009-07-29
I am jumping into this discussion. Sorry about this but I am not following any of this what has been discussed. I'm very very new to Ubuntu and Linux. I have a Linksys Wireless USB Adapter that some one gave me to try out and I am getting nothing showing up as being connected. I have tried to type in the line of code to try and find out what is going on but to no avail. The Ubuntu machine is not connected to the web so I am writing this from my Windows Vista machine. Anyway when I type in lspci into the Terminal I get the following:

steven@steven-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

What am I looking for?

I want to be able to install Inkscape and Scribus and it looks like the best way is to have an internet connection in order to do that. I have a wireless router (NetGear) hooked up to my Windows machine.

---

### Post by bkratz on 2009-07-29
StephenD


For a USB device you would have to use lsusb rather than lspci.

---

### Post by StevenD on 2009-07-29
Of course. I should have realized that. Anyway here is what I get when I type in lsusb.

steven@steven-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2222:3080 MacAlly 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
steven@steven-laptop:~$

What does this tell me or what do I do with this info?

---

### Post by bkratz on 2009-07-29
StephenD

It tells you that it is a Linksys WUSB11v2.5. The important part is the 066b:2212.  You should post in the Networking and wireless forum for additional help, but you might look at this  ( I found it by searching for the 066b:2212.)
It seem a little outdated but a good place to start.

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

Good luck.

---

### Post by Ratscallion on 2009-07-30
> **bkratz said:**
> stephend

it tells you that it is a linksys wusb11v2.5. The important part is the 066b:2212.  You should post in the networking and wireless forum for additional help, but you might look at this  ( i found it by searching for the 066b:2212.)
it seem a little outdated but a good place to start.

[https://help.ubuntu.com/community/wifidocs/driver/prism2_usb](https://help.ubuntu.com/community/wifidocs/driver/prism2_usb)

good luck.

+1

---

### Post by linlearn on 2009-07-30
> **r.v.the.evil said:**
> i am new on ubuntu jaunty jackalope
i want 2 install wvdial in ubuntu to use mobile internet
and i linux terminal . i have write d profile as follows in eddit menu
[driver details]
phone = #777
username = internet
password = internet
and so on


i dont know how to save it
can anyonee reply me know
and tell me
, i really need it,
thanx 
with regards ,
ravi

Ravi and StevenD,
Please start a new thread as I dont know who is replying to whom.
Many thanks,
Linlearn

---

### Post by linlearn on 2009-07-30
> **ayenack said:**
> I'm not running Ubuntu Jaunty and the Network Connection screen is different....

But it looks like you're in luck. I would guess what you need to do here is double click on royson then most likely it'll offer to connect then you'll need to enter your wpa key and you should be good to go. It might take a reboot.

If this does not work it's an idea to turn off encryption on the router and try to connect unencrypted just to see if you can connect (obviously once you've established if you can or can't turn encryption back on.)

That's about as far as I can help as I have never had to configure this particular card. It seems it's possible referring to the earlier post that I suggested. Maybe they would be your best bet from here on out. Any advice I would give would be generic wireless advice and not specific to your actual card.

Ayenack,
Thanks for your help. I will check. I created that. The wireless network was not discovered by the system.
 or I will start a new thread.

Many thanks for your help
Linlearn

---

### Post by Scunnered on 2009-07-30
**Linlearn**

I have had a quick look at what has been said before and am at a loss as you seem to be unable to connect at all.  Is this correct ?

You say you have a netgear router and a Asus laptop with Atheros wireless card and this should wotk just straight out of the box with Jaunty.

Can I assume that you are on a Virgin Media connection and if so did you have Virgin set up your router.  You need to set up things with them before it will work.  Once that has been done you should see the wireless connection on top panel. Left click on that and you should see your network shown. Click on that and you will be asked for a password which is the one you gave to Virgin and everything should work a treat.

---

### Post by ayenack on 2009-07-30
No worries linlearn. Shame I couldn't help a little more.

Just one last suggestion if you have you Ethernet wired connection plugged in when trying to connect to wireless try unplugging it then reboot and see if wireless shows anything. I know that some Atheros cards do work straight out of the box especially with Jaunty I also thought that your card was one of those that did.

BTW.
Your card is most definitely recognised by he system because when you type ifconfig you get wlan0 so your system is seeing it it's just a case of knowing how to configure it. You may have to blacklist some kernel modules or something along those lines. But the fact that it shows up on ifconfig is a positive.

---

### Post by linlearn on 2009-07-30
> **Scunnered said:**
> **Linlearn**

I have had a quick look at what has been said before and am at a loss as you seem to be unable to connect at all.  Is this correct ?

You say you have a netgear router and a Asus laptop with Atheros wireless card and this should wotk just straight out of the box with Jaunty.

Can I assume that you are on a Virgin Media connection and if so did you have Virgin set up your router.  You need to set up things with them before it will work.  Once that has been done you should see the wireless connection on top panel. Left click on that and you should see your network shown. Click on that and you will be asked for a password which is the one you gave to Virgin and everything should work a treat.

Hi Scunnered,
I am at present connected through wires to the Netgear WPN824 router, so have to sit next to the router at all times.
I was connected to the router wirelessly when I was on Windows Vista, so know that wireless works. Unfortunately while setting up Ubuntu, I have lost all data in Vista and cannot get into Windows at all. I have used Windows Vista CD, all fixmbr, etc and supergrub cd. 
Yes you are right. I am on Virgin Media but no router was not supplied by them. 
So I dont think they will support that.
Linlearn

---

### Post by linlearn on 2009-07-30
> **ayenack said:**
> No worries linlearn. Shame I couldn't help a little more.

Just one last suggestion if you have you Ethernet wired connection plugged in when trying to connect to wireless try unplugging it then reboot and see if wireless shows anything. I know that some Atheros cards do work straight out of the box especially with Jaunty I also thought that your card was one of those that did.

BTW.
Your card is most definitely recognised by he system because when you type ifconfig you get wlan0 so your system is seeing it it's just a case of knowing how to configure it. You may have to blacklist some kernel modules or something along those lines. But the fact that it shows up on ifconfig is a positive.

Oh thanks . Yes I read something about 'blacklist'. Too much of Windows . At present I have a lot of reading to do for working with Ubuntu.

cheers,
Linlearn

---

### Post by ayenack on 2009-07-30
I've just done a little search for your card and found this

[http://ubuntuforums.org/showthread.php?t=1222818&highlight=atheros+ar242x](http://ubuntuforums.org/showthread.php?t=1222818&highlight=atheros+ar242x)

So I'm sure the card should work out of the box. It seems that madwifi can bugger it so you may need to get back to your original install.

It's worth trying the Ubuntu install LiveCD you used to install. Boot using that and see if your card is listed in Network connections and if it is try connecting then you'll know for sure if the card should work out of the box.

---

### Post by nothingspecial on 2009-07-30
Ok, we`ll try manually blacklisting the kernel modules. You`ll have to bear with me because I`m not using Ubuntu Jaunty at the moment and I`m sure it has some custom blacklist config files.
```

ls /etc/modprobe.d/
```

You should see something about blacklist [COLOR="Red"]madwifi[/COLOR] or [COLOR="Red"]ath_pci[/COLOR]

Now you need to edit that file.

Sudo nano /etc/modprobe.d/[COLOR="Red"]correct_name_of_the_ath_pci_config_file[/COLOR]

There should be a line at the bottom saying ```
blacklist ath_pci
```

Put a # infront of it so it now looks like

```
#blacklist ath_pci
```

Press Ctrl+O  (to save) Return (to confirm) Ctrl+X to exit.
 
ath_pci is now not blacklisted but we had better blacklist the default ath5k module so there is no conflict.
```

sudo nano /etc/modprobe.d/blacklist
```

Add ```
blacklist ath5k
``` to the end of that file and save and close as before.

Now we need to add ath_pci to the modules that load at boot

```
sudo nano /etc/modules
```

add ```
ath_pci
``` to the end then save and close as before.

Edit**** Oh yeah and if you happen to see ath5k in there put a # in it...you shouldn`t but just incase (I`m doing this from memory btw)
Then you need to reboot.

All this is doing is enabling the madwifi drivers (as you`ve already tried) manually. I have no idea if it will work but it`s worth a try.

If it doesn`t go back through this post and reverse those 3 steps.

If nothing else atleast you will have had a go at editing a config file from the terminal with nano.

Finally, you are using jaunty not hardy aren`t you. If you are using hardy then ignore all this and post back and I`ll tell you what to do.

---

### Post by linlearn on 2009-07-30
> **ayenack said:**
> I've just done a little search for your card and found this

[http://ubuntuforums.org/showthread.php?t=1222818&highlight=atheros+ar242x](http://ubuntuforums.org/showthread.php?t=1222818&highlight=atheros+ar242x)

So I'm sure the card should work out of the box. It seems that madwifi can bugger it so you may need to get back to your original install.

It's worth trying the Ubuntu install LiveCD you used to install. Boot using that and see if your card is listed in Network connections and if it is try connecting then you'll know for sure if the card should work out of the box.

I checked my card. It is Atheros AR242 802.11abg Wireless PCI Express Adapter but802.11abg Wireless PCI Express Adapter but has no scan results. The system hangs before the login screen when the bluetooth and wireless lights come on on the laptop ,so I have done a new install with Ubuntu LiveCD yesterday.
I also noticed that it says 'modprobe' fatal. it has something to do with blacklisting I suppose.

One of the files 'blacklist ath_pci' in /etc/mod/probe.d shows:---
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

Maybe this. 
Linlearn

---

### Post by ayenack on 2009-07-30
That's is about as far as I can help you having never had to config the card unfortunately. Don't want to make things worse for you.

nothingspecial seems to know what he's talking about so would be a good idea to follow his advice. He's obviously got the card going at some point.

I'll follow the thread just to see if this can be resolved and chip in if I think I can help in anyway.

Best of luck with it.

ayenack.

P.S.
Don't forget to disable eth0 when trying to set up your wireless many times this is a contributing problem stopping wireless connection.

---

### Post by nothingspecial on 2009-07-30
That`s the one you should try putting a # infront of (known as commenting) Before blacklisting ath5k and adding ath_pci to /etc/modules as detailed in my previous post.

---

### Post by linlearn on 2009-07-30
> **nothingspecial said:**
> Ok, we`ll try manually blacklisting the kernel modules. You`ll have to bear with me because I`m not using Ubuntu Jaunty at the moment and I`m sure it has some custom blacklist config files.
```

ls /etc/modprobe.d/
```You should see something about blacklist [COLOR=Red]madwifi[/COLOR] or [COLOR=Red]ath_pci[/COLOR]

Now you need to edit that file.

Sudo nano /etc/modprobe.d/[COLOR=Red]correct_name_of_the_ath_pci_config_file[/COLOR]

There should be a line at the bottom saying ```
blacklist ath_pci
```Put a # infront of it so it now looks like

```
#blacklist ath_pci
```Press Ctrl+O  (to save) Return (to confirm) Ctrl+X to exit.
 
ath_pci is now not blacklisted but we had better blacklist the default ath5k module so there is no conflict.
```

sudo nano /etc/modprobe.d/blacklist
```Add ```
blacklist ath5k
``` to the end of that file and save and close as before.

Now we need to add ath_pci to the modules that load at boot

```
sudo nano /etc/modules
```add ```
ath_pci
``` to the end then save and close as before.

Edit**** Oh yeah and if you happen to see ath5k in there put a # in it...you shouldn`t but just incase (I`m doing this from memory btw)
Then you need to reboot.

All this is doing is enabling the madwifi drivers (as you`ve already tried) manually. I have no idea if it will work but it`s worth a try.

If it doesn`t go back through this post and reverse those 3 steps.

If nothing else atleast you will have had a go at editing a config file from the terminal with nano.

Finally, you are using jaunty not hardy aren`t you. If you are using hardy then ignore all this and post back and I`ll tell you what to do.
First of all I am using Jaunty.
I have done what you said and rebooted. No connections and wlist scanning shows none.
I went to /etc/modprobe.d and see that the saved files are showing as blacklist.save and blacklist-ath_pci.conf.save. Is this right?

---

### Post by nothingspecial on 2009-07-30
The files are called blacklist.save blacklist-ath_pci.conf.save?

I dont think that`s right. There shouldn`t be a .save extension as far as I know. Trouble is I`m at work using a different distro that doesn`t have all these fancy blacklist files, just good old /etc/modprob.d/blacklist

This one`s got me. I have the same card in three diferent netbook/laptops and they have all worked flawlessly with Jaunty although I usually enable the madwifi drivers because they work better transfering big files over my home network.

I`ll keep thinking though.

If you followed my post you had better change it all back.

---

### Post by linlearn on 2009-07-30
> **nothingspecial said:**
> The files are called blacklist.save blacklist-ath_pci.conf.save?

I dont think that`s right. There shouldn`t be a .save extension

This one`s got me. I have the same card in three diferent netbook/laptops and they have all worked flawlessly with Jaunty although I usually enable the madwifi drivers because they work better transfering big files over my home network.

I`ll keep thinking though.

If you followed my post you had better change it all back.

 When I used sudo nano /etc/modprobe.d/blacklist, I get some black lines. It does not do anything with Ctrl + o and Ctrl +X. and I dont get to the command line to type the code. The file uses up the space in the terminal. I will re-do this.

---

### Post by nothingspecial on 2009-07-30
Hang on let me explain something to you first.

---

### Post by nothingspecial on 2009-07-30
I should have waited till I got home to check.

You are editting some files that ubuntu reads at boot to know which modules (drivers) to load or not at boot.

They used to be called /etc/modules and /etc/modprobe.d/blacklist

In Jaunty the blacklist file has been split into a number of config files and the trouble is I can`t remember what they are called exactly.

If they are called /etc/modprobe.d/balcklist.conf and /etc/modprobe.d/blacklist-ath_pci.conf then those are the files you should be editing.

All sudo nano /etc/modprobe.d/blacklist will do is create a new file which might cause problems and why it looks empty.

I hope I`m explaining this alright because at the moment I don`t know what you`ve done exactly and how to rectify it untill I get home in 4 hours to have a look.

If you now have 2 files in /etc/modprobe.d called

blacklist and blacklist.conf then I`m thinking that you should probably delete blacklist especially if it is empty but I don`t want you to do that untill I can check.

I hope in my willingness to help I have not made anything worse, if I have don`t worry - it`s nothing that can`t be fixed, I just need to have a look at one of my jaunty boxes with that card.

I have to go now but I`ll check back in. In the meantime see what else you can find out.

---

### Post by linlearn on 2009-07-30
> **nothingspecial said:**
> I should have waited till I got home to check.

You are editting some files that ubuntu reads at boot to know which modules (drivers) to load or not at boot.

They used to be called /etc/modules and /etc/modprobe.d/blacklist

In Jaunty the blacklist file has been split into a number of config files and the trouble is I can`t remember what they are called exactly.

If they are called /etc/modprobe.d/balcklist.conf and /etc/modprobe.d/blacklist-ath_pci.conf then those are the files you should be editing.

All sudo nano /etc/modprobe.d/blacklist will do is create a new file which might cause problems and why it looks empty.

I hope I`m explaining this alright because at the moment I don`t know what you`ve done exactly and how to rectify it untill I get home in 4 hours to have a look.

If you now have 2 files in /etc/modprobe.d called

blacklist and blacklist.conf then I`m thinking that you should probably delete blacklist especially if it is empty but I don`t want you to do that untill I can check.

I hope in my willingness to help I have not made anything worse, if I have don`t worry - it`s nothing that can`t be fixed, I just need to have a look at one of my jaunty boxes with that card.

I have to go now but I`ll check back in. In the meantime see what else you can find out.
I have done it but there is no wireless.
Should I give this a go.
[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)
System > Admin > Hardware drivers shows 'Alternate Atheros 'madwifi' drivers. Should I disable this. It does not deactivate. I will logout and see.

---

### Post by nothingspecial on 2009-07-30
That`s how you you used to get these atheros cards working in ubuntu but you already have the driver included. You don`t need to compile the madwifi drivers coz you`ve already got them.

1st of all do me a favour and check the output of ls /etc/modprobe.d is this
```

alsa-base.conf          blacklist-firewire.conf     blacklist-oss.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist.conf          blacklist-modem.conf        libpisock9.conf
```

and nothing else, no extra files in there.

```
cat /etc/modprobe.d/blacklist-ath_pci.conf 
```

should show this
```

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath5k
```

If it doesn`t make it look that way.

Remove the line ath_pci from  /etc/modules if it is still there and remove ath5k from /etc/modprobe.d/blacklist.conf if it is still there.

You will then have a setup just like mine that has wireless with exactly the same card.

Reboot and see if anything changes.

If it doesnt post the output of ```
dmesg
```

Not the whole bloody thing just about the last 20 lines or so. This will show us messages from the kernel and hopefully give some insight as to what is wrong with your wireless.

Oh and I`m not being funny here but you`ve not got some sort of wireless switch set to off have you. When I first got ubuntu the only problem I had was no sound. I spent days doing all sort of command line stuff I didn`t understand and following guides on the web and it turned out I had the speakers plugged in the microphone hole.

---

### Post by linlearn on 2009-07-30
> **nothingspecial said:**
> 
1st of all do me a favour and check the output of ls /etc/modprobe.d is this
```

alsa-base.conf          blacklist-firewire.conf     blacklist-oss.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist.conf          blacklist-modem.conf        libpisock9.conf
```and nothing else, no extra files in there.

sonroy@sonroy-laptop:~$ ls /etc/modprobe.d
alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
blacklist               blacklist-framebuffer.conf  libpisock9.conf
blacklist-ath_pci.conf  blacklist-modem.conf        ndiswrapper
blacklist.conf          blacklist-oss.conf

Blacklist was created by sudo nano ...blacklist. It has the entry 'blacklist ath5k' just created. how do I delete this file and also the file ndiswrapper. I get permission denied deleting directly.

> 
```
cat /etc/modprobe.d/blacklist-ath_pci.conf 
```should show this
```

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath5k
```If it doesn`t make it look that way.Done 

> Remove the line ath_pci from  /etc/modules if it is still there and remove ath5k from /etc/modprobe.d/blacklist.conf if it is still there.This has an entry 'lp'. I have removed 'ath_pci'.
 

> You will then have a setup just like mine that has wireless with exactly the same card.
Reboot and see if anything changes.
will reboot now. 

> 
Oh and I`m not being funny here but you`ve not got some sort of wireless switch set to off have you. .Netgear has on/off only for LED display. Otherwise I have to reset for factory settings and start again.
I will check the manual again just in case.

I have attached what is available in Sys>Admin> Hardware drivers. Cannot disable the atheros drivers there. Attachment.

Before that I have to delete the file 'ndiswrapper' and 'blacklist' from /etc/modprobe.d. How do I do that?

Linlearn

---

### Post by Scunnered on 2009-07-30
**linlearn**
You did not say whether you activated your modem with Virgin.  If you did not this could be the cause of all your problems. 

I don't know if switching from an ethernet connection to wireless is automatic on Virgin.  It was too far back for me to remember if a password was required on ethernet connections.  It was not so long a go that I updated to wireless so I know that a password is required. In my case it was a total switch over to wireless so I am unsure of just adding a wireless modem on to the cable router.

If you have not already spoken to the helpless desk at Virgin it might just be worth your while.  They will even give you a free wireless modem if they wont support what you have but it looks like you have the same kit that they hand out free.

Hope this may be of assistance

---

### Post by linlearn on 2009-07-30
I have deleted the files 'blacklist' and 'ndiswrapper'.
There is something funny.
When I log in back and go to Sys>admin> hardware drivers. The atheros drivers is enabled always. So the wireless entry on top is disabled.
 Sometimes /etc/modprobe.d/blacklist-ath_pci.conf has 'blacklist ath5k', sometimes it goes back to 'blacklist ath_pci'. That is strange.

---

### Post by linlearn on 2009-07-30
I did a install from LiveCD and I CAN SEE ALL THE NETWORKS, though I cannot connect.
It is something I have done when doing the full install. Please see attachment.
I have seen the files in /etc/modprobe.d/blacklist-ath_pci.conf and there is 'blacklist ath_pci'

I cannot do the full install because I have done it so many times and there may be no space, I think. The last time there were 3 Ubuntu loaders on sda0.6 , sda0,7 ,etc.
I will have to remove this.
I will try with fresh install and then revert back

Linlearn

---

### Post by nothingspecial on 2009-07-30
> **linlearn said:**
> I did a install from LiveCD and I CAN SEE ALL THE NETWORKS, though I cannot connect.
It is something I have done when doing the full install. Please see attachment.
I have seen the files in /etc/modprobe.d/blacklist-ath_pci.conf and there is 'blacklist ath_pci'

I cannot do the full install because I have done it so many times and there may be no space, I think. The last time there were 3 Ubuntu loaders on sda0.6 , sda0,7 ,etc.
I will have to remove this.
I will try with fresh install and then revert back

Linlearn

If you are going to reinstall, just do one over the entire disk. After you do, get a wired connection and install wicd.

```
sudo apt-get install wicd
```

See if that helps.

---

### Post by nothingspecial on 2009-07-30
Sorry, once you do, go into your menu and go Internet > wicd and put all your passwords and stuff in.

---

### Post by linlearn on 2009-07-31
> **Scunnered said:**
> **linlearn**
You did not say whether you activated your modem with Virgin.  If you did not this could be the cause of all your problems. 

I don't know if switching from an ethernet connection to wireless is automatic on Virgin.  It was too far back for me to remember if a password was required on ethernet connections.  It was not so long a go that I updated to wireless so I know that a password is required. In my case it was a total switch over to wireless so I am unsure of just adding a wireless modem on to the cable router.

If you have not already spoken to the helpless desk at Virgin it might just be worth your while.  They will even give you a free wireless modem if they wont support what you have but it looks like you have the same kit that they hand out free.

Hope this may be of assistance
You see I did not have this problem at the start of July when I was on Vista and have been working with whatever Virgin have dished out. It was a modem . There is no switch to wireless in this modem at least. The wireless connection is from the Netgear router that I bought. So dont understand.

BTW, I can see all networks of a live CD and the WLAN lights and bluetooth comes on the laptop when I start typing the password. Then in the network(top right) I see all networks. 
But once I do a full install all networks vanish. I have just installed Ubuntu and have 4 loaders on the grub menu.

Linlearn

---

### Post by nothingspecial on 2009-07-31
> **linlearn said:**
> You see I did not have this problem at the start of July when I was on Vista and have been working with whatever Virgin have dished out. It was a modem . There is no switch to wireless in this modem at least. The wireless connection is from the Netgear router that I bought. So dont understand.

BTW, I can see all networks of a live CD and the WLAN lights and bluetooth comes on the laptop when I start typing the password. Then in the network(top right) I see all networks. 
But once I do a full install all networks vanish. I have just installed Ubuntu and have 4 loaders on the grub menu.

Linlearn

If you have done all your updates then you probably have your current and previous kernel and their respective recovery modes.

Try booting into the previous kernel. Sometimes new kernels break things that were working perfectly well before hand.

---

### Post by linlearn on 2009-07-31
> **nothingspecial said:**
> If you are going to reinstall, just do one over the entire disk. After you do, get a wired connection and install wicd.

```
sudo apt-get install wicd
```See if that helps.

You mean out of the 4 options, side by side, entire disk(which will wipe out the other things), free space and manual, choose ENTIRE disk install. 
I already have installed and see too many Ubuntu partitions on the grub menu.
And cant see any wireless in each of the partitions. The new one was on hd(0,9). I have checked the other three on /dev/sda6. 
I shall I try 'sudo apt-get install wicd' now and see what happens.

I might have to re-install this weekend ,maybe entire disk
I am having too much fun.:(
Linlearn

---

### Post by linlearn on 2009-07-31
> **nothingspecial said:**
> If you have done all your updates then you probably have your current and previous kernel and their respective recovery modes.

Try booting into the previous kernel. Sometimes new kernels break things that were working perfectly well before hand.

I am doing one by one. I have booted into the old ones and will check, though all of them do not show Wlan lights on the laptop which is a sign that there are no networks visible.
From a live CD , the bluetooth and wlan lights were on and the networks were seen. BUT I could not connect to the network. (That is another issue).The files on modprobe.d looked the same, like I have mentioned in my previous post

---

### Post by nothingspecial on 2009-07-31
So I take it you have multiple installs of ubuntu on your harddrive at the moment. This is not an ideal situation.

If I were you I would reinstall and yes choose use entire disk. I would also try Ubuntu Hardy Heron LTS instead of Jaunty and maually compile the latest madwifi drivers as detailed in the link you posted yesterday.
> 
I am having too much fun.

Just think, you`ll be a linux demon by Monday.:D

---

### Post by nothingspecial on 2009-07-31
There we have it. I can confirm it is the new kernel. I`ve just updated now, rebooted and crap no wireless.

Easiest solution - reboot and hold down escape and when the boot menu comes up choose

```
Ubuntu 9.04, kernel 2.6.28-13-generic
```

Hopefully you should have wireless.

---

### Post by Stevie78 on 2009-07-31
I had the same problem. I was supplied with a router by the ISP  where it said only the package 'For Windows and Mac OS'. I already laughed at that in the store when I told the guy that surely there will be a patch for that in Linux as Windows is such a superior OS...

Well I couldnt get one, Ubuntu just wouldnt recognize the network, no matter what. 

But then I found a way round it. :D

What I did was install and setup everything on an older laptop running on XP. Then I took the ethernet cable out, plugged into the Ubuntu desktop and Hurray! there it was. Works without problem whatsoever.

---

### Post by linlearn on 2009-07-31
> **nothingspecial said:**
> There we have it. I can confirm it is the new kernel. I`ve just updated now, rebooted and crap no wireless.

Easiest solution - reboot and hold down escape and when the boot menu comes up choose

```
Ubuntu 9.04, kernel 2.6.28-13-generic
```Hopefully you should have wireless.

I have 4 on the grub menu. I cannot boot in from 2.6.28-14 generic as it hangs most of the time. I am now in 2.6.28-13 generic and this has suppressed network manager.
I want to remove all kernels keeping one. there are 11 packages seen as in the attachment. Shall i remove them.  i have not done install using 'using entire disk' option.

 I have found the network(Attachment) in the Wicd but it wont connect.

---

### Post by linlearn on 2009-07-31
> **Stevie78 said:**
> I had the same problem. I was supplied with a router by the ISP  where it said only the package 'For Windows and Mac OS'. I already laughed at that in the store when I told the guy that surely there will be a patch for that in Linux as Windows is such a superior OS...

Well I couldnt get one, Ubuntu just wouldnt recognize the network, no matter what. 

But then I found a way round it. :D

What I did was install and setup everything on an older laptop running on XP. Then I took the ethernet cable out, plugged into the Ubuntu desktop and Hurray! there it was. Works without problem whatsoever.

It dont have a laptop with XP. I used to have one. Anyway I have connected wirelessly with Vista earlier.

---

### Post by ayenack on 2009-07-31
> **linlearn said:**
> I have 4 on the grub menu. I cannot boot in from 2.6.28-14 generic as it hangs most of the time. I am now in 2.6.28-13 generic and this has suppressed network manager.
I want to remove all kernels keeping one. there are 11 packages seen as in the attachment. Shall i remove them.  i have not done install using 'using entire disk' option.

 I have found the network(Attachment) in the Wicd but it wont connect.

Hello linlearn. If you have no important data that you want to keep and you do not want to install any other OS along with Ubuntu then if I were you I'd do a full disk install.

What confuses me about your problem is that you can see the wireless networks from the LiveCD so I'm guessing that the kernel update may have broken your wifi (as nothingspecial stated.) It's possible that if you rebuilt the wireless drivers then this would fix your problem. Possibly nothingspecial will be able to help you with this as I do not know if the drivers are in the same place as they are in 8.04. If you read the howto that I referred to in my earlier post it states that when a kernel update comes down the line it breaks the wifi they also explain how to fix it but that's on 8.04 not 9.04.

If you want to remove kernels that you don't want use synaptic and select each kernel that's of no further use to you. You'll also want to remove the kernel headers (search synaptic for linux-headers) and remove the corresponding headers to the removed kernels. But if you have more than one install of Ubuntu you would most likely be better off doing a new full install.

---

### Post by linlearn on 2009-07-31
> **ayenack said:**
> Hello linlearn. If you have no important data that you want to keep and you do not want to install any other OS along with Ubuntu then if I were you I'd do a full disk install.

What confuses me about your problem is that you can see the wireless networks from the LiveCD so I'm guessing that the kernel update may have broken your wifi (as nothingspecial stated.) It's possible that if you rebuilt the wireless drivers then this would fix your problem. Possibly nothingspecial will be able to help you with this as I do not know if the drivers are in the same place as they are in 8.04. If you read the howto that I referred to in my earlier post it states that when a kernel update comes down the line it breaks the wifi they also explain how to fix it but that's on 8.04 not 9.04.

 I will be re-installing Vista at some stage. Yes I can see wireless networks off the liveCD . I have tried this many times yesterday and today. However, All the 4 kernels on the grub menu do not have wireless. it is blanked out.
I have now installed wicd on 2.6.28-13-generic and it shows networks but once the window is closed, the wireless does not show. I might have to reset the router
Thanks for your help

---

### Post by ayenack on 2009-07-31
I've just had a look at the wicd box out you posted. It's showing your wireless network but it's also stating at the bottom that you are connected to your wired connection try disconnecting from the wired and see if you can connect to wireless it may take a minute or two for your wireless to come up.

I've had this problem many times. If it turns out that this is th problem you'll have to disable your wired connection to be able to connect to your wireless or you'll have to set up internet connection sharing which is a whole different story.

---

### Post by linlearn on 2009-07-31
> **ayenack said:**
> I've just had a look at the wicd box out you posted. It's showing your wireless network but it's also stating at the bottom that you are connected to your wired connection try disconnecting from the wired and see if you can connect to wireless it may take a minute or two for your wireless to come up.

I've had this problem many times. If it turns out that this is th problem you'll have to disable your wired connection to be able to connect to your wireless or you'll have to set up internet connection sharing which is a whole different story.

I will try this again. Wicd did not discover wireless networks .

---

### Post by linlearn on 2009-08-07
Hi Guys,
Thanks for everything. 
I cannot get it to work with WICD . I dont see any network . I can only get connected with wires.
By the way, I got into Vista by using the Recovery Disc and done a fresh install. So I am out of Ubuntu. 
I will get into Ubuntu once I thoroughly understand what the Grub menu is doing when I click Vista loader. Or I might migrate to OpenSuse.

I am closing this issue.

Thanks,
Linlearn

---

