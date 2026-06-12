---
title: "Trouble getting wireless to work"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by likemyredhair on 2006-12-25
Hey,
I've read a lot of other people's posts about wireless problems and still haven't been able to fix my problem.  I'm new to Linux and I would appreciate any help that I could get.
My HP laptop has a Broadcom 4306 wireless card.

Thanks.

---

### Post by Floppyjoe on 2006-12-25
You might try the Wiki and look for wifi info.

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
or
[https://wiki.ubuntu.com/WifiDocs/WiFiTroubleshooting?highlight=%28wifi%29](https://wiki.ubuntu.com/WifiDocs/WiFiTroubleshooting?highlight=%28wifi%29)
or
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

hope this helps.

---

### Post by likemyredhair on 2006-12-26
Well...I tried them.
The first link seemed to be the most helpful.  I got to the part that says to type "ping -n 4.2.2.2 -c 4" and when I deactivate the wired connection, I get "Destination host unreachable". 
So...any suggestions?
Thanks again.

---

### Post by c.dric on 2006-12-26
maybe your system still tries to connect to the internet through the old (wired) route.

Disable your wired connection first ... activate your wireless connection as explained in the guide and then ping to test the connection.

just an idea.

could you post the output of 

iwconfig 
ifconfig
route

if you're still having troubles ?

---

### Post by likemyredhair on 2006-12-26
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:01:7C:4F  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe01:7c4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:744437 (726.9 KiB)  TX bytes:90144 (88.0 KiB)
          Interrupt:193 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9943 (9.7 KiB)  TX bytes:9943 (9.7 KiB)


route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


Also, I just realized that in the first link, it says "First thing you'll need to do is get the wireless-tools package".  Guess I over-looked that before...ha.  But anyway I'm not sure how to install it.  It says "'make install' should do the right thing for you", but since I'm new to this (linux) I'm not sure what that means.

But maybe you guys can read the iwconfig, ifconfig, and route and maybe figure out something that's missing.

I really appreciate the help.

---

### Post by likemyredhair on 2006-12-26
sorry about those smilies there, not sure I guess something translated to a Suprised face, hope you can still use the info

---

### Post by c.dric on 2006-12-26
There is a graphical interface to install new program called Synaptic located in your System menu.

But I think wireless-tools is already installed on your system.

It looks like your card can't detect your wireless access point ... 
are you sure the ap is up and you typed the name correctly in the network manager ?

you could try this command to see if your card detect any wireless access point :

```
sudo iwlist scan
```

---

### Post by Floppyjoe on 2006-12-26
try sudo iwlist eth1 scan

---

### Post by likemyredhair on 2006-12-26
I just realized that I had Wireless connection unchecked in Network Settings.
So I guess I should send that info again, but now that it is checked, I'm trying sudo iwlist scan and I get...

sudo iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.


But now with Wireless connection checked...

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:01:7C:4F  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe01:7c4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39343638 (37.5 MiB)  TX bytes:1088588 (1.0 MiB)
          Interrupt:193 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9943 (9.7 KiB)  TX bytes:9943 (9.7 KiB)


route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by likemyredhair on 2006-12-26
> **Floppyjoe said:**
> try sudo iwlist eth1 scan

sudo iwlist eht1 scan:


eth1      Interface doesn't support scanning : No such device

---

### Post by Floppyjoe on 2006-12-26
Next you want to add some code into the /etc/network/interfaces file to make sure your computer knows what settings the router is using. Look for entries called eth1 or the name your computer calls your interface. It may be different.
Enter :
Code:

sudo gedit /etc/network/interfaces

If you see this:
Quote:
auto eth1
iface eth1 inet dhcp
Then enter the following code below it:
Code:

wireless-essid YourNetworkName 
wireless-channel 11
wireless-mode managed

Where YourNetworkName is your routers Essid and you enter the channel that your router is using instead of 11.

You should see something like this:
Quote:
auto eth1
iface eth1 inet dhcp
wireless-essid YourNetworkName
wireless-channel 11
wireless-mode managed
Then save this file and close it.

---

### Post by likemyredhair on 2006-12-27
Well I'm not sure what you mean by channel but here's what shows up when I entered...


sudo gedit /etc/network/interfaces:

auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2eth1
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp







iface eth1 inet dhcp
wireless-essid linksys











auto eth0

auto eth1



Again, thanks for the help.

---

### Post by c.dric on 2006-12-27
i just realized your card is not supported out of the box in ubuntu ... 
did you install ndiswrapper and the correct driver ? if not that's most probably the cause of your problems. 

here are two good howtos specifically for your Broadcom 4306 card : 
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
[http://ubuntuforums.org/showthread.php?t=291088](http://ubuntuforums.org/showthread.php?t=291088)

---

### Post by likemyredhair on 2006-12-27
alright i'll try right now

---

### Post by likemyredhair on 2006-12-27
Alright, I'm using the first link...and Ive gotten to the part where it says to use the code "sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf" and to "make sure the .sys file is in there also, without it, it wont work".  I do not see any .sys files this is what I see...

Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX


So, then, I thought I'd skip to the next step and typed in "ndiswrapper -l" and it says "No drivers installed"

---

### Post by c.dric on 2006-12-27
Did you download the zip with the drivers ? 

if not, [download it now]("http://home.nc.rr.com/thehinnants/stuff/drivers/bcmwl5.zip") and extract the two files on your desktop.

then type this command in a terminal : 

sudo ndiswrapper -i ~/Desktop/bcmwl5.inf

if you don't get any errors you can continue with this command : 

ndiswrapper -l

then continue with the howto.

---

### Post by likemyredhair on 2006-12-27
Ok, I did that, now it says "bcmwl5  driver present,  hardware present", but I still don't see a .sys file when I enter "sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf"... I see this:

Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX




Also when I enter:


~$ sudo modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

---

### Post by c.dric on 2006-12-27
when they said to type the command 

sudo ndiswrapper -i ~/folder where driver is/bcmwl5.inf

they meant that you should replace "folder where driver is" by the location where you extracted the driver files (bcmwl5.inf & bcmwl5.sys)

you don't have to do that anymore because i already gave you the right command in the previous post (sudo ndiswrapper -i ~/Desktop/bcmwl5.inf) and it worked fine (bcmwl5 driver present, hardware present).

> Also when I enter:
~$ sudo modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

It's a common problem apparently and they give a fix at the end of the how-to (Problem 2)
I'm copy/pasting it here under : 

> Shaton found a fix for the FATAL: Error inserting ndiswrapper problem. Thank You Shaton!
If you get an error saying

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

then try this.
Code:

```

sudo apt-get install ndiswrapper-utils-1.8 sudo 
rm /usr/sbin/ndiswrapper sudo 
ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```


u can retry the following command after that : 

sudo modprobe ndiswrapper

and hopefully finish the rest of the how-to :)

---

### Post by likemyredhair on 2006-12-27
We'll my wireless is working.  Awesome!

The light on my wireless button is acting kinda weird, though.

Should there be a wireless signal icon up by the clock, I saw that on a screen shot and I don't have it?

No big deal though, at least I got the wireless to work.  I really appreciate your help.

Thanks!

---

### Post by likemyredhair on 2006-12-27
I just restarted my computer and the wireless isn't working...dang.

---

### Post by c.dric on 2006-12-27
Make sure you didn't skip some part of the how-to .

Also take a look at the replies following the how-to, especially the first post of page 4, there are a  few posts with a problem similar to yours. 

I hope you get it working.

---

### Post by likemyredhair on 2006-12-27
Well... I went back over the How To and when I was done there was no Wireless Connection in the Network Settings.  Ha.  But I restarted my computer and the Wireless Connection is back.

As far as the first post on page 4 of that thread...
> **ubunturules said:**
> Make sure you did
```
sudo rmmod bcm43xx
```

Do you have a file called /etc/modprobe.d/bcm43xx.
If you do, delete it.

then try
```
sudo ndiswrapper -m
```
```
sudo modprobe ndiswrapper
```



I did a search for "bcm" and nothing came up so I assume that's good enough.


When I entered "sudo ndiswrapper -m" I got

"modprobe config already contains alias directive"


And when I entered "sudo modprobe ndiswrapper" nothing happened.

---

### Post by Floppyjoe on 2006-12-27
If you entered the command:
```
sudo ndiswrapper -m
```

it is the same as:
```
sudu gedit /etc/modules
```
and adding the word ndiswrapper to this file.

now your internet should be connected at startup.

no need to enter the modprobe command again in the terminal.

---

### Post by likemyredhair on 2006-12-27
I entered "sudo gedit /etc/modules" and it opened another window.
In that window I added "ndiswrapper" at the end.  Is that what you meant for me to do?
Anyway, I did that, saved it, and restarted and the wireless is still not working.
What now?


...Just a reminder, I really appreciate you guys' help.  Ha.

---

### Post by c.dric on 2006-12-28
could u deactivate your wired connection, reboot the computer and 
then copy/paste the output of the following commands ?

lsmod | grep ndiswrapper

sudo iwlist scan

iwconfig

ifconfig

route

---

### Post by likemyredhair on 2006-12-29
lsmod | grep ndiswrapper:
ndiswrapper           208656  0 
usbcore               134912  7 ndiswrapper,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd


sudo iwlist scan:
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

sit0      Interface doesn't support scanning.


iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:01:7C:4F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by c.dric on 2006-12-29
could u post the output of these 2 commands ?

sudo ndiswrapper -l

lsmod | grep bcm

---

### Post by likemyredhair on 2007-01-06
sorry for the lack of reply ive been really busy with the new year, plus i havent been able to connect to the internet via ethernet cable.  I will in a day or two.

---

### Post by likemyredhair on 2007-01-14
sudo ndiswrapper -l
Password:
Installed drivers:
bcmwl5          driver installed, hardware present 


lsmod | grep bcm
bcm43xx               127252  0 
ieee80211softmac       33792  1 bcm43xx
ieee80211              35272  2 bcm43xx,ieee80211softmac

---

### Post by teaker1s on 2007-01-17
easy to sort

when you are happy that your wireless networking is correct then

sudo gedit /etc/modules

Add the word ndiswrapper and save the file using "save as" this will then load everytime you boot

---

### Post by likemyredhair on 2007-01-17
i typed "sudo gedit /etc/modules" and "ndiswrapper" is already in that list, i guess i already did that.  so do you have any other suggestions?
thanks.

---

