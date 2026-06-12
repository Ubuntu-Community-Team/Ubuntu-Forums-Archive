---
title: "Linksys wmp54g"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by spacecowboy706 on 2006-09-30
I cannot figure out how to make my wireless pci card connect to the internet. I am using a wmp54g from linksys. I have already installed the ndisgtk, ndiswrapper-utils and just in case the ndiswrapper-source as I wasn't sure what all I needed and i have even found the correct driver that I need "I THINK"... BUT... when i go to SYSTEM - ADMINISTRATION - WINDOWS WIRELESS DRIVERS - and then Click on the "INSTALL NEW DRIVER" button i go to where i downloaded it to and i am given the following file:

rt2500-1.1.0-b4.tar.gz

so i then extracted it to the same directory and i am given this new file:

rt2500-1.1.0-b4

So i then go back to the Wireless Network Drivers window and click the "INSTALL NEW DRIVER" button again and locate the newly extracted file "rt2500-1.1.0-b4", but here is where my problem begins...

I cannot find any ".inf" file anywhere in the file...

Please tell me what i am doing wrong or if i even have the right driver downloaded, or if i am even going about this the right way? or if there is an easier way. I have posted about this befoire and the guy who helped me just told me to use airsnort then never replied to any more of my posts... someone please help i hate having to string a cat 5 line from one end of my house to the other and Im tired of listening to my wife give me a hard time about it ! ! ! !

I may not even need a new driver as i dont even know how to check and see if i can see the broadcast? Please help ](*,)

---

### Post by spacecowboy706 on 2006-10-01
This is my second thread on this that has went unnoticed, without any help.

---

### Post by harts12 on 2006-10-02
I am having the same problem and I found this: [http://www.computing.net/linux/wwwboard/forum/28880.html](http://www.computing.net/linux/wwwboard/forum/28880.html)

It sounds like you need to put in the windows instal cd and get wmp54gsa.inf from it.

I just barely switched and could us help with getting the ndiswrapper-utils. I can't find the place I was yesterday where I could have gotten it if I was looking. If you could help me that would be swell too...

---

### Post by spacecowboy706 on 2006-10-02
I got all the ndiswrapper stuff from the Synaptic Package manager located in the menu under SYSTEM - ADMINISTRATION - SYNAPTIC PACKAGE MANAGER and then clicked on the Search button at the top and typed the name of it and it found it. when i clicked on it to mark it for install it auto-found all the required dependencies. check the apply button at the top afterwards to auto download and install the stuff. hope that helps you out...

---

### Post by basementgeek on 2006-10-02
Make sure to check that you have the correct drivers for the chip that your card uses.  I have the same card, but it has an RT61 chip, which needed a different driver.

Use "lspci" in terminal to verify which one you have.  Look for the what it says after "Network controller".  I believe that card used 3 different chips throughout its production.

Here's the tutorial I used if you do have an RT61:

[http://www.ubuntuforums.org/showthread.php?t=132980&highlight=wmp54g]("http://www.ubuntuforums.org/showthread.php?t=132980&highlight=wmp54g")

---

### Post by harts12 on 2006-10-02
Thanks, but I bypassed all of that, it wasn't necessary. Did the message I sent you help?

---

### Post by spacecowboy706 on 2006-10-02
basementgeek

lspci gives me this.....

0000:00:0a.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

I knew it was rt2500 as that is what it is in windows as well.

As for the correct drivers.. i dont know how to tell if they are the correct ones or not? can u give me some help on that?

If i go to MAIN MENU - SYSTEM - ADMINISTRATION - NETWORKING - and then enter my password - click on DEACTIVATE interface eth0 (Ethernet Connection) and then click - ACTIVATE  interface ra0 (Wireless Connection) and then - click the properties button the ESSID is automatically filled in with whatever  ssid i make up in my router (as i have tried changing that as well) so doesn't this mean that the card is working since it auto detects whatever ssid i make up? Where it states the essid it will also show a little key symbol on it if i have WEP or WPA turned on and then the little key icon will disappear if i turn the WEP or WPA off.????

harts12 - that didn't work either... still no connectivity.

---

### Post by wieman01 on 2006-10-03
Hi, 

First of all just to tell you that I have a got Linksys wusb54g v4 working with "ndiswrapper". So I am sure we'll find a solution for you as well.

Secondly, it's likely that Ubuntu has recognized your card in the first place and has installed a native Ubuntu driver (RT2xxx) which entails that you don't need "ndiswrapper" at all ("ndiswrapper" is a tool/container that simply deploys the native Windows driver for your card). Please run these command from a terminal & post the ouput:
> ifconfig
> iwconfig
> lspci
If this confirms that your card has not been recognized, we'll use "ndiswrapper" which is pretty reliable (though a bit of a hassle). "ndiswrapper" deploys & makes use of the native Windows wireless driver, so make sure that you get the right ***.exe** (for Windows) that comes with the installation CD or can be downloaded from Linksys web-site.

This file (*.exe) contains the driver files that you need: *.inf, *.cat, *.others. But let's see first if your card has been installed yet. "rt2500-1.1.0-b4.tar.gz" is the native Linux driver and is useless in conjunction with "ndiswrapper".

This is the howto we are going to use if "ndiswrapper" really applies: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

_EDIT:_
The Windows *.exe file is a ZIP archive. Open it with an archiver and you'll see all the files it contains.

---

### Post by basementgeek on 2006-10-03
> **spacecowboy706 said:**
> basementgeek

lspci gives me this.....

0000:00:0a.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

I knew it was rt2500 as that is what it is in windows as well.

As for the correct drivers.. i dont know how to tell if they are the correct ones or not? can u give me some help on that?

If i go to MAIN MENU - SYSTEM - ADMINISTRATION - NETWORKING - and then enter my password - click on DEACTIVATE interface eth0 (Ethernet Connection) and then click - ACTIVATE  interface ra0 (Wireless Connection) and then - click the properties button the ESSID is automatically filled in with whatever  ssid i make up in my router (as i have tried changing that as well) so doesn't this mean that the card is working since it auto detects whatever ssid i make up? Where it states the essid it will also show a little key symbol on it if i have WEP or WPA turned on and then the little key icon will disappear if i turn the WEP or WPA off.????

harts12 - that didn't work either... still no connectivity.


Looks like wieman01 is on the right track.  I forgot that you were trying to use ndiswrapper.

---

### Post by spacecowboy706 on 2006-10-03
As you directed wieman01, this is with the wired ethernet disabled and the  wireless enabled:

**myname@myname-desktop:~$ ifconfig**
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1516 (1.4 KiB)  TX bytes:1516 (1.4 KiB)

ra0       Link encap:Ethernet  HWaddr 00:12:17:9A:3F:C8
          inet addr:192.168.1.98  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe9a:3fc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13461 errors:2 dropped:2 overruns:0 carrier:0
          collisions:23 txqueuelen:1000
          RX bytes:7622 (7.4 KiB)  TX bytes:608167 (593.9 KiB)
          Interrupt:9

**myname@myname-desktop:~$ iwconfig**
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"KeepOut"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:0F:66:E4:B5:A9
          Bit Rate:54 Mb/s   Tx-Power:-3 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level=-52 dBm  Noise level:-195 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

**myname@myname-desktop:~$ lspci**
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:04.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:0a.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:00:11.0 Mass storage controller: Promise Technology, Inc. PDC20265 (FastTrak100 Lite/Ultra100) (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)


Does ndiswrapper apply here, or is the linux drivere good to go?

---

### Post by wieman01 on 2006-10-03
Hello Spacecowboy, 

The good news is that your card has been recognized ("ra0") so there is no need to install "ndiswrapper". Is **"KeepOut"** your wireless network by chance?

Next please do this & again post the output:
> iwlist ra0 scan
Then also show us the contents of your "network interfaces" file:
> sudo gedit /etc/network/interfaces
Then what kind of network do you want to set up:
1. DHCP or Static IP
2. Name of network ("ESSID")
3. Type of encryption/authentication (open, WEP, WPA, WPA2).

To keep it simple I would say that we choose an open network with DHCP for now. We can enable encryption/authentication later on.

Last question: Do you use any kind of firewall (e.g. Firestarter) or wireless tool (e.g."wireless assistant", "wifi radar")? If yes, then please disable all of them for the time being.

---

### Post by spacecowboy706 on 2006-10-03
Yes "KeepOut" is my wireless network.... and here is the info you requested:

myname@myname-desktop:~$ iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:XX:XX:XX:XX:A9
                    Mode:Managed
                    ESSID:"KeepOut"
                    Encryption key:off
                    Channel:6
                    Quality:64/100  Signal level:-49 dBm  Noise level:-192 dBm

myname@myname-desktop:~$ sudo gedit /etc/network/interfaces
Password: XXXXXXXXXXXXXXXX

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra0 inet dhcp
wireless-essid KeepOut

As for the kind of network i would like to setup is entirley up to you. Under Windows i "HAD" a static ip with only 4 IP leases as follows, setup in the router and the TCP/IP stack:

xxx.xxx.xx.98 - is my wired Cat5 to this pc
xxx.xxx.xx.97 - is my wireless to this pc
xxx.xxx.xx.96 - is my Wireless USB to this pc <-removed for Ubuntu
xxx.xxx.xx.95 - is my wired Cat5 to my XBOX360

I have had to do away with all that since i have encoutered these problems with the wireless in linux and now i have just plain old jane DHCP. I have turned off the WPA, Disabled the Mac Filter, Disabled Port Forwarding, Disabled DMZ Hosting, Disabled my router firewall along with rolling back my routers firmware from HyperWRT back to the original Linksys firmware.

If you can get me connecting wirelessly i can get all the rest to work, but rigfht now we are Auto DHCP with no encryption.

As for firewalls or wireless assistants i have only added the firestarter firewall when i installed ubuntu and i havent yet figured out how to disable it or even start it...but if i go to session manager it is not listed in the list of items currently running and it is not listed in the startup list. I have not installed any other wireless assistants other than Airsnort that i downloaded and installed at another persons direction on here, but that guy stopped helping me, so it never got added to the startup list.

All the "X" in the post are numbers or letters that have been removed for security.

---

### Post by wieman01 on 2006-10-03
Ok, if you have DHCP enabled and done away with MAC filtering, this will be fairly simple (that's my hope at least). All from terminal windows please:

1. Let's shut down Firestarter first of all (we'll see to the configuration for Firestarter at a later stage):
> sudo killall firestarter
2. Open "interfaces file" so that it:
> sudo gedit /etc/network/interfaces
3. Now please paste this:
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto ra0
iface ra0 inet dhcp
wireless-essid KeepOut
I deliberately commented out your ethernet connection so that the system won't get confused. 

4. Save the file.

5. Kill "wpa_supplicant" just in case it is running (which I doubt):
> sudo killall wpa_supplicant
6. Restart the network:
> sudo /etc/init.d/networking restart
That done, please post the output of the last command which will tell us if the connection has been established.

Last but not least try to "ping" your router ("ping xxx.xxx.xxx.xxx") and do another:
> iwconfig
> iwlist ra0 scan
> route
Now ideally you should be able to browse the internet using Firefox or any other browser. Could you try that?

If this has been successful, we'll configure Firestarter (best would be if you uninstalled it for the time being using Synaptic) so that it won't block your internet/DHCP connection. Later on we cater to wireless security (WPA, WEP) and Static IP.

N.B.: Airsnort is not a wireless assistant but a WEP cracking tool. Won't be a problem, no need to remove it.

---

### Post by spacecowboy706 on 2006-10-04
As you directed, here are the outputs:

**myname@myname-desktop:~$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces... postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:XX:XX:XX:3f:c8
Sending on   LPF/ra0/00:XX:XX:XX:3f:c8
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ra0/00:XX:XX:XX:3f:c8
Sending on   LPF/ra0/00:XX:XX:XX:3f:c8
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.99 -- renewal in 41224 seconds.

When i try to enter: ping 192.168.1.1 
it just sits there and does nothing until i press Ctrl+C

and now the other ouputs:

**myname@myname-desktop:~$ iwconf**ig
lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"KeepOut"
          Mode:Managed  Frequency=2.437 GHz  Access Point: [COLOR="Red"]00:XX:XX:XX:B5:A9[/COLOR]
          Bit Rate:54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=66/100  Signal level=-53 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

**myname@myname-desktop:~$ iwlist ra0 scan**
ra0       Scan completed :
          Cell 01 - Address: [COLOR="Red"]00:XX:XX:XX:B5:A9[/COLOR]
                    Mode:Managed
                    ESSID:"KeepOut"
                    Encryption key:off
                    Channel:6
                    Quality:66/100  Signal level:-59 dBm  Noise level:-192 dBm
[B]
myname@myname-desktop:~$ route[/B]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 ra0
default         192.168.1.1     0.0.0.0         UG    0      0        0 ra0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

as i got done with all this i currently have no connectivity still :( 

so I had to go back to SYSTEM - ADMINISTRATION - NETWORKING - and then disable the wireless - and then re-enable the wired... just so i could post this reply...

Just out of curiosity i booted back into windoze (just to make sure the card or router wasn't bad) and applied the changes to the ssid, DHCP, and removed the encryption and the wireless card had signal strength of 100% quality of 100% and pinged my ISP's default gateway 500 times with 0% packet loss and i was able to surf the net just fine as my speeds were at 12.5Mb Downstream and 2.5Mb Upstream.

---

### Post by wieman01 on 2006-10-04
Had you disabled Firestarter while you tried to connect?
> sudo killall firestarter

---

### Post by wieman01 on 2006-10-04
The thing is that you're definitely connected. Just need to figure out why you cannot ping the router nor have access to the Internet. This does not seem to make sense... No "wireless assistant", no "wifi-radar" you said, right?

---

### Post by wieman01 on 2006-10-04
One more thing... Please disable your wired connection by commenting the corresponding lines in "interfaces":
> auto lo
iface lo inet loopback

[COLOR="Red"]#auto eth0
#iface eth0 inet dhcp[/COLOR]

auto ra0
iface ra0 inet dhcp
wireless-essid KeepOut
It's possibly that the system gets confused if both are active.

---

### Post by spacecowboy706 on 2006-10-04
Yes i did the sudo killall firestarter and got this ouput:

myname@myname-desktop:~$ sudo killall firestarter
Password: XXXXXXXXXXXXXXXXXXX
firestarter: no process killed

I know that firestarter is on here but i dont know if itis supposed to start up by itself or if im supposed to manually start it everytime i startup the computer?

And for wireless assistant or WiFi radar I have no idea... From the session manager I get this as currently running:

gnome session properties
metacity
gnome panel
gnome volumne manager
nautilis 
update notifier
gnome power manager
gnome cups icon
kxdocker

from the session manager startup i get this:
kxdocker
update notifier
gnome power manager
gnome volumne manager

is there another way to tell other than the session manager (like a terminal command to list all running processes)

PS.. i will be online all day today as it my day off, so i can go back and forth like this as long as you can :)

---

### Post by wieman01 on 2006-10-04
Back again... Sorry for that. Different time zone (Asia) I reckon.

Ok, perhaps it's best if you **uninstalled Firestarter** using Synaptic. We will disable it for the time being only until we get this working, would that be ok? Just open Synaptic and **remove it**.

Your card works fine, but something else is blocking the connection.

---

### Post by spacecowboy706 on 2006-10-04
uninstalling firestarter now.... stand by... will edit this post when im done


WOOOOOOOHOOOOOOOO YOUR THE GREATEST DAMN UBUNTU HELPER ON THE PLANET... How come your not this forums moderator?

Are you this good with all linux distro's or just Ubuntu? 

Going to try Static leases, WPA, Mac Filters, DMZ, and all my Port Priorities now. I Should be able to figure that out own my own as it is very similiar to windoze believe it or not. :-D 

One last thing, if i reinstall firestarter with both the wireed and wireless running will it auto setup, to allow both?

---

### Post by wieman01 on 2006-10-04
Great... And again:
> sudo /etc/init.d/networking restart
> ping 192.168.1.1
> iwconfig
:-)

---

### Post by wieman01 on 2006-10-04
:-) Glad we got it working, buddy. My pleasure, really. I am a humble Ubuntu user, have not really bothered to look at other distros recently (despite the fact that I used to have SUSE installed).

Firestarter can only handle 1 adapter at a time, so you need to switch (Firestarter preferences) them every time you change your network setup. But this is generally not a problem, just one additional step after you have logged on to your system. 

So no, you cannot allow both but it's fairly simply to change the settings.

If you need a hand with Static Leases, WPA1/WPA2, etc. let me know. My network is running on WPA2 (AES rather than TKIP) so perhaps we can get together there.

Good luck for now! Let us know if you need help, ok? :-)

---

### Post by bklebel on 2006-10-24
ok i have been following your guys instructions but still have not made it work](*,) 

when i sudo /etc/init.d/networking restart its sending packets but it isn't recieving any. Also, when i change my DNS server and close, it doesn't save. When i go back into network settings there are 2 different dns servers which aren't the ones i need.

im lost ill be back

---

### Post by wieman01 on 2006-10-24
The post the results of:
> iwlist ra0 scan
> sudo gedit /etc/network/interfaces
> lspci
> iwconfig
> route
> sudo /etc/init.d/networking restart

---

### Post by bionnaki on 2006-10-25
ok. I have written a how-to on how to set up the wmp54g. 

[http://ubuntuforums.org/showthread.php?p=1409752#post1409752](http://ubuntuforums.org/showthread.php?p=1409752#post1409752)

it works perfectly. no need for ndiswrapper or wpa supplicant.

---

### Post by wieman01 on 2006-10-25
Great. I was about to post the same thing. Whether you use "ndiswrapper" or the native Linux driver does not matter at all. I prefer the Linux driver though... :-)

---

### Post by bionnaki on 2006-10-25
cool. I also prefer/recommend the linux rt2500 driver. I have not had much luck with ndiswrapper - was not stable at all.

---

