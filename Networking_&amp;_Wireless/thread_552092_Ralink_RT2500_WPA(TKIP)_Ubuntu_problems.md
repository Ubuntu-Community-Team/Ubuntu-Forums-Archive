---
title: "Ralink RT2500 WPA(TKIP) Ubuntu problems"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by rossco on 2007-09-16
Hi all,

I am new to Linux and have converted my old desktop into my new Ubuntu project PC.  I am pretty impressed with Ubuntu so far but I am having trouble getting a few things running.  Currently I am trying to get my Ralink RT2500 based wireless card up and running.  Network manager finds my wireless network (secured with WPA 128bit PSK(TKIP)) but it doesn't recognise that it is a WPA network and instead asks for a WEP128bit pass key.

I see that lots of other people have had similar problems after searching this forum and the internet.  Problem is I am pretty overwhelmed by the solutions that are on offer so I was wondering if anyone has a relatively simple way to get a driver for my card that I can access using Network Manager.

Also does anyone know why this problem exists?

Kind Regards
Ross

---

### Post by kevdog on 2007-09-16
ra based cards, in combination with network manager dont work very well (ok they just dont work).

There are a few other options, but they are numerous at this point and I dont know how best to advise you to go, so I will just list them in no particular order
1. Dont use network manager --> switch to WICD
2. Upgrade driver to serial monkey rt2500 driver (a more updated version), and use rutilt as the "network manager" like program.
3. Dont use the native ra driver (rt2500), use ndiswrapper/winxp driver for your card, then you can use network manager

Again any of these is feasible, I just dont know where you want to go.  Im only hesitating to offer advice on any one of these actions since I know certain people have very strong opinions about each solution.

---

### Post by rossco on 2007-09-18
Hi Kevdog,

Thanks for the reply and sorry I haven't responded (I expected to get an email when the thread was updated).

With option 1 will that just 'fix' the problem?

With option 2, I think I tried doing that but didn't know where/how to install the driver or how to tell Ubuntu not to use the default one (ie "blacklist"?).

With option 3 I installed NDISWrapper using the synaptic package manager but thats as far as I got.

I also tried another method where I installed a backported kernel version.  Which ended up breaking my system when I tried to reverse it.  I think the moral to the story is I shouldn't do things that I don't understand.  So I have reinstalled everything!  Sometimes its dangerous to follow solutions given in old forum threads...

I think that option 1 is worth trying first.  Can you explain what I need to do and also what I am doing so I can learn?

Thanks heaps.

---

### Post by unisol on 2007-09-18
first you must blacklist the rt 2500 driver . sudo gedit /etc/modprobe.d/blacklist file. add rt2500 to the end of ths file, by typing blacklist rt2500. click save and close. reboot computer. when you get back to the desktop , run iwconfig to make sure your card is not active. if you have ndiswrapper installed type ndiswrapper -v to see if it is installed. if it is type modprobe ndiswrapper.Next mount the CD that came with your wireless card and look for a driver file, probably rt2500.inf or some such. If you have a choice, then pick the one for Win98. Install this driver in ndiswrapper with: # ndiswrapper -i   cd /mnt/cdrom/Installer/rt2500.inf. check that the driver was installes ndiswrapper -l, load module with modprobe ndiswrapper, then if all goes well type ndiswrapper -m to make interface. configure network settings.
if the driver is invalid type ndiswrapper -e drivername to remove driver. hopefully you wont have to do this. if your driver is installed and network manger dont work do like kevdog said and use wicd. use version 1.3.3 as it has support for your wireless card. good luck!

---

### Post by rossco on 2007-09-21
Hi Unisol,

Thanks for your reply and the specific instructions.  I am stuck though.  Its not got anything to do with your help but I don't have a windows driver for the card!  I got it a long time ago and I think the CD is long gone.  Normally Windows finds the card and automatically installs a driver.  Do either of you know where to get one?  I tried the Ralink website but I think they only have executable installers.

--- Later....

Ok I had an idea that I would boot back into Windows and get it to find the driver and then locate the file and see if I can use it.  Ok the file is called RT2500.sys and when I run the line

ndiswrapper -l

it says: RT2500.sys : Invalid driver!

Sigh.

---

### Post by rossco on 2007-09-21
OK I think I know the problem.  The ndiswrapper help specifically says for -i command that it needs an 'inffile'

Anyone out there with an inf file?

---

### Post by unisol on 2007-09-21
its called rt2500.inf.,i believe you can get that from the ralink website. if not try sourceforge.net. if you cant get ndiswrapper to work, you can always install it from source. check this forum for the howto.

---

### Post by kevdog on 2007-09-21
Look on your windows system and do a search for 2500.  There should be both the inf and sys files

---

### Post by rossco on 2007-10-02
KevDog,

Your idea of searching Windows for the inf file was the right thing.  I found the file and did as you said (you need to have the sys file in the same directory too).

When I try the command 'ndiswrapper -m' I get 'module configuration already contains alias directive'

Network Manager shows my local wireless network SSID but won't connect to it.  I wonder if the problem above is the culprit.  Here is what I get when I type 'iwconfig':

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       IEEE 802.11g  ESSID:"MyWirelessNetwork"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1B:11:15:6C:F0   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-110 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:4/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any ideas?

---

### Post by wieman01 on 2007-10-02
> **rossco said:**
> KevDog,

Your idea of searching Windows for the inf file was the right thing.  I found the file and did as you said (you need to have the sys file in the same directory too).

When I try the command 'ndiswrapper -m' I get 'module configuration already contains alias directive'

Network Manager shows my local wireless network SSID but won't connect to it.  I wonder if the problem above is the culprit.  Here is what I get when I type 'iwconfig':

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       IEEE 802.11g  ESSID:"MyWirelessNetwork"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1B:11:15:6C:F0   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-110 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:4/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any ideas?
Have you blacklisted the old Linux driver? Please should us the contents of:
> sudo gedit /etc/network/interfaces
And do a scan:
> sudo iwlist scan
There is a tutorial in my signature for reference.

---

### Post by rossco on 2007-10-02
Contents of the interfaces file:
> 
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



iface ra0 inet dhcp
wireless-essid MyWirelessNetwork
auto ra0


And yes I have blacklisted the old linux driver.  Before I got the ndiswrapper files sorted out it didn't show a wireless adapter in network manager.

sudo iwlist scan:
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:1B:11:15:6C:F0
                    ESSID:"MyWirelessNetwork"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:100/100  Signal level:-8 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0


---

### Post by wieman01 on 2007-10-02
What about:
> ndiswrapper -l

---

### Post by rossco on 2007-10-02
ndiswrapper -l:
> 
rt2500 : driver installed
        device (1814:0201) present (alternate driver: rt2500)


---

### Post by wieman01 on 2007-10-02
So you have blacklisted "rt2500" for sure... not "rt2500usb", is that correct?

What about the contents of this one:
> sudo cat /etc/modprobe.d/ndiswrapper

---

### Post by rossco on 2007-10-02
sudo cat /etc/modprobe.d/ndiswrapper:
> 
Password:
alias wlan0 ndiswrapper


Yeah I blacklisted the rt2500 driver.  From the blacklist file:
> 
......
blacklist r8187
# added by Ross 20/9/07 to fix WPA wireless ethernet connection
blacklist rt2500


I added a note to remind myself in the future.:oops:

---

### Post by wieman01 on 2007-10-02
Please update the interfaces file as highlighted above. 

Also blacklist "rt2500usb" and restart the computer. Then try to connect once again.

---

### Post by rossco on 2007-10-02
one question:
> 
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ra0 inet dhcp
wireless-essid MyWirelessNetwork
auto ra0


Ok this is my interfaces file.  How did you want me to edit it?  I have one wireless adapter, one ethernet adapter, one adsl adapter and one dialup modem adapter.  So should I have the following:
lo
eth0
ath0
ra0

How about:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

auto ra0
iface ra0 inet dhcp


---

### Post by wieman01 on 2007-10-02
No, only:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0inet dhcp
"ra0" refers to the blacklisted driver.

---

### Post by rossco on 2007-10-02
Ok cool, that's good to know (ra0 = old linux driver, wlan0 = new ndiswrapper driver).

Now if I go to Network tools it shows all three adapters (lo, wlan0, eth0).  Also in Network Manager it shows wireless connections including my local wireless network.  But it still won't connect.  If Ubuntu couldn't load a driver for the wireless card would it still show the interface?  Ie is there a chance that even though I have said there is wlan0 that it isn't loading the ndiswrapper driver?  

I noticed that there is a setting 'ndiswrapper -a devid driver' which the help says: "use installed 'driver' for 'devid'".  I tried using "sudo ndiswrapper -a wlan0 rt2500" but get the error "'WLAN0' is not a valid device id"

Also is there a way to restart the networking without having to restart the system or should I do it anyway to be safe?

---

### Post by wieman01 on 2007-10-02
You could restart the network this way:
> sudo /etc/init.d/networking restart
Could you do also this please & post the output:
> sudo ifdown -v wlan0
> sudo ifup -v wlan0

---

### Post by rossco on 2007-10-02
sudo ifdown -v wlan0:
> 
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4244
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0e:2e:38:fe:38
Sending on   LPF/wlan0/00:0e:2e:38:fe:38
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 10.1.1.1 port 67
ifconfig wlan0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant


sudo ifup -v wlan0:
> 
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0e:2e:38:fe:38
Sending on   LPF/wlan0/00:0e:2e:38:fe:38
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.1.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
bound to 10.1.1.6 -- renewal in 1676 seconds.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant


---

### Post by wieman01 on 2007-10-02
Excellent! It says that you have received an IP address via "wlan0".

Can you do the same via Network Manager?

---

### Post by rossco on 2007-10-02
Hmmm...

Something really strange is happening.  I got it to connect a couple of times but several strange things happened.  First something ate my interfaces file and all that was in it was the loopback adapter.  I fixed that then some other stuff happened and I am thoroughly confused.  Now if I type:sudo ifdown -v wlan0
i get:

> 
ifdown: interface wlan0 not configured
ross@ross-desktop:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


I'm going to leave now until tomorrow since somehow it can't find wlan0 anymore.  Thanks wieman01 you've been a great help.  I am starting to wonder whether using WICD might be an option!

---

### Post by rossco on 2007-10-05
Hi wieman01,

I ended up unblacklisting the serialmonkey driver, removing the ndiswrapper driver, removing network manager and installing WICD.  It seems to be quite a good utility and it works well.  Only problem is that I don't know how to get it to run at start up (network is unavailable right after reboot, have to start WICD manually) and even though I checked the box 'Automatically connect to this network' I still have to click connect.  I will check the web to see if I can find any solutions to my problems as well.  Thanks for all your help.  At this early stage WICD seems to be a better alternative to the other options, may be its not included as version 1.3.3 is not a verified stable release.

---

### Post by wieman01 on 2007-10-05
> **rossco said:**
> Hi wieman01,

I ended up unblacklisting the serialmonkey driver, removing the ndiswrapper driver, removing network manager and installing WICD.  It seems to be quite a good utility and it works well.  Only problem is that I don't know how to get it to run at start up (network is unavailable right after reboot, have to start WICD manually) and even though I checked the box 'Automatically connect to this network' I still have to click connect.  I will check the web to see if I can find any solutions to my problems as well.  Thanks for all your help.  At this early stage WICD seems to be a better alternative to the other options, may be its not included as version 1.3.3 is not a verified stable release.
Good to know. I did not know WICD now supports Ralink cards. Thanks for letting me know.

---

### Post by rossco on 2007-10-05
I think that you have to get v1.3.3 or later so you have to go to the WICD website and grab the .deb file to install as synaptic has only got older versions.  Someone else earlier on in the forum said about the versioning.

Also I got it to work at start up using the info from the WICD website.

Now I am trying to set up SAMBA on it so I can share files and one thing that WICD may not have that Network Manager did is the domain, workgroup and computer name options.  Hopefully I can set them somewhere else.

---

### Post by wieman01 on 2007-10-05
> **rossco said:**
> I think that you have to get v1.3.3 or later so you have to go to the WICD website and grab the .deb file to install as synaptic has only got older versions.  Someone else earlier on in the forum said about the versioning.

Also I got it to work at start up using the info from the WICD website.

Now I am trying to set up SAMBA on it so I can share files and one thing that WICD may not have that Network Manager did is the domain, workgroup and computer name options.  Hopefully I can set them somewhere else.
No, you set them directly using SAMBA. Don't worry. There is an excellent tutorial in the tutorial section.

---

### Post by rossco on 2007-10-09
Well I don't know whether to cry or get angry and throw my PC out the window!  I can't get this thing to work all of the time.:mad:

It turns out that when I got everything to work last time that I had turned off my network encryption for a guest who couldn't connect otherwise due to old hardware.  Now with it back on it won't work.

I have blacklisted the rt2500 driver (including the usb one).  Linux won't mistake this entry for the ndiswrapper driver will it, as they have the same name?

I have removed network manager and installed wicd.

The problem I have now is that even though the rt2500 driver is blacklisted linux is still loading the card as 'ra0'.  When I go to Device Manager:
> 
net.interface = ra0
linux.sysfs_path = /sys/class/net/ra0
info.linux.driver = ndiswrapper   (strange that it comes up with the correct driver)


running the command iwconfig yields:> 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       IEEE 802.11g  ESSID:"LASTDAYS"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1B:11:15:6C:F0   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-110 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-5 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


My interfaces file is this:
> 
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid LASTDAYS

auto eth0
iface eth0 inet dhcp


Restarting the networking comes up with an error saying that wlan0 - no such device etc.

How come it still keeps coming up as ra0 even though the linux driver is blacklisted and it says it is loading the ndiswrapper driver?

---

### Post by wieman01 on 2007-10-09
> **rossco said:**
> Well I don't know whether to cry or get angry and throw my PC out the window!  I can't get this thing to work all of the time.:mad:

It turns out that when I got everything to work last time that I had turned off my network encryption for a guest who couldn't connect otherwise due to old hardware.  Now with it back on it won't work.

I have blacklisted the rt2500 driver (including the usb one).  Linux won't mistake this entry for the ndiswrapper driver will it, as they have the same name?

I have removed network manager and installed wicd.

The problem I have now is that even though the rt2500 driver is blacklisted linux is still loading the card as 'ra0'.  When I go to Device Manager:


running the command iwconfig yields:

My interfaces file is this:


Restarting the networking comes up with an error saying that wlan0 - no such device etc.

How come it still keeps coming up as ra0 even though the linux driver is blacklisted and it says it is loading the ndiswrapper driver?
What kind of device is it again? PCI or USB? Sorry if I have asked this before.

---

### Post by rossco on 2007-10-09
Sorry it is a PCI one but you suggested that I blacklist both drivers.  I feel like blacklisting every ralink driver!

---

### Post by wieman01 on 2007-10-09
> **rossco said:**
> Sorry it is a PCI one but you suggested that I blacklist both drivers.  I feel like blacklisting every ralink driver!
Ha... my fault. Could you also blacklist this one please and restart the computer:
> rt2500pci
I only realized a few days ago that there is another driver for PCI devices. Well, that's the learning curve. Sorry you are part of it. ;-)

---

### Post by rossco on 2007-10-09
Ok cool, I added rt2500pci to the blacklist file.  However I am still having problems.  Half the time the PC will boot up and the wireless card will be wlan0 and the other half it will be ra0!  I happened to notice in the boot messages that when it initialises the network that there is an entry where something is trying to change wlan0 to ra0.  I opened the log viewer to find out what was going on and I think ndiswrapper tries to change wlan0 to ra0 and sometimes it is successful and sometimes it fails.  Is this something that ndiswrapper should be doing?  Let me know if I can post anything to help you understand.

Also I'm starting to get cold feet about this approach, is there a serialmonkey development driver that is likely to work with WPA yet?  Or is compiling the driver myself likely to fix the situation?  Are you involved in the serialmonkey development?  If I could help in some way, I'm not a C programmer (an I don't think I want to become one) but I could some other way.

Wicd and network manager (I tried reverting back to NM) can see the wireless network with the ndiswrapper driver.  NM even asks for a WPA PSK.  But they both try to connect, wicd hangs saying it is requesting an IP address.

---

### Post by wieman01 on 2007-10-10
> **rossco said:**
> Ok cool, I added rt2500pci to the blacklist file.  However I am still having problems.  Half the time the PC will boot up and the wireless card will be wlan0 and the other half it will be ra0!  I happened to notice in the boot messages that when it initialises the network that there is an entry where something is trying to change wlan0 to ra0.  I opened the log viewer to find out what was going on and I think ndiswrapper tries to change wlan0 to ra0 and sometimes it is successful and sometimes it fails.  Is this something that ndiswrapper should be doing?  Let me know if I can post anything to help you understand.

Also I'm starting to get cold feet about this approach, is there a serialmonkey development driver that is likely to work with WPA yet?  Or is compiling the driver myself likely to fix the situation?  Are you involved in the serialmonkey development?  If I could help in some way, I'm not a C programmer (an I don't think I want to become one) but I could some other way.

Wicd and network manager (I tried reverting back to NM) can see the wireless network with the ndiswrapper driver.  NM even asks for a WPA PSK.  But they both try to connect, wicd hangs saying it is requesting an IP address.
I have little experience with Serialmonkey's drivers as I gave up on them a while ago. You might try them but I doubt NM will recognize them. WICD might as of late.

Could you also post the contents of:
> /etc/modprobe.d/ndiswrapper
That file should contain the "ndiswrapper" alias and hopefully it is "wlan0". I cannot tell you right now whatelse we can do. "ra0" should disappear once you have blacklisted the device.

---

### Post by rossco on 2007-10-10
To show ou what I mean, below is something I cut and pasted from the log viewer after booting up today:

> 
Oct 10 20:58:57 ross-desktop kernel: [   63.390423] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Oct 10 20:58:57 ross-desktop kernel: [   63.502310] ndiswrapper: driver rt2500 (Ralink Technology, Inc.,06/01/2006, 3.02.00.0000) loaded
Oct 10 20:58:57 ross-desktop kernel: [   63.502688] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 20
Oct 10 20:58:57 ross-desktop kernel: [   63.506665] ndiswrapper: using IRQ 20
Oct 10 20:58:57 ross-desktop kernel: [   64.010188] wlan0: ethernet device 00:0e:2e:38:fe:38 using serialized NDIS driver: rt2500, version: 0x20001, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 1814:0201.5.conf
Oct 10 20:58:57 ross-desktop kernel: [   64.010218] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Oct 10 20:58:57 ross-desktop kernel: [   64.011403] usbcore: registered new interface driver ndiswrapper
Oct 10 20:58:57 ross-desktop kernel: [   64.015583] ndiswrapper: changing interface name from 'wlan0' to 'ra0'


See the last entry changes the interface name!

Also the contents of ndiswrapper:

> 
alias wlan0 ndiswrapper


Also the drivers that come with Ubuntu (that I've blacklisted) are they the rt2x00 drivers or the legacy ones?  I might try using the legacy ones.  Or I can try the ralink linux drivers from their website.  Only I'm not sure how to install them so that Ubuntu will use them.

---

### Post by rossco on 2007-10-10
Ok I am trying to install the driver fro source and I am getting an error but I don't know what it means:

> 
ross@ross-desktop:~/rt2500-1.1.0-b4/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/ross/rt2500-1.1.0-b4/Module/rtmp_main.o
In file included from /home/ross/rt2500-1.1.0-b4/Module/rtmp_main.c:50:
/home/ross/rt2500-1.1.0-b4/Module/rt_config.h:58:40: error: linux/config.h: No such file or directory
/home/ross/rt2500-1.1.0-b4/Module/rtmp_main.c: In function ‘RT2500_open’:
/home/ross/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/ross/rt2500-1.1.0-b4/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/ross/rt2500-1.1.0-b4/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
rt2500.ko failed to build!
make: *** [module] Error 1


---

### Post by unisol on 2007-10-10
make sure build-essential is installed.

---

### Post by rossco on 2007-10-10
build-essential reckons that everything is up to date...

I used:

> 
sudo apt-get install build-essential linux-headers-$(uname -r)


I didn't try using (which was also a requirement for breezy but I'm not sure if its required for feisty as well):
> 
sudo apt-get install gcc-3.4


Do you think that I need it?

---

### Post by unisol on 2007-10-11
see the note on installing rt2500 drivers on this forum.

---

### Post by unisol on 2007-10-11
see the note on installing rt2500 drivers on this forum. Sticky: HOWTO: RT2500, etc. wireless cards

---

### Post by wieman01 on 2007-10-11
> **unisol said:**
> see the note on installing rt2500 drivers on this forum. Sticky: HOWTO: RT2500, etc. wireless cards
We have been through it but his computer is still making trouble. Hence the effort to compile the latest drivers from source...

---

### Post by wieman01 on 2007-10-12
Hey, 

Good news. Kernel 2.6.24 will come with a new set of Ralink drivers. It is likely that your device will be work out of the box soon.

---

### Post by JakeSpeare on 2007-10-14
Just upgraded to the new kernel and now wireless no longer works ...  darn.

---

### Post by kevdog on 2007-10-14
Did you upgrade the kernel only, or upgrade to Gutsy??  Vanilla kernels by default dont have any third party drivers available.

Can you post some information specifically what is not working??

lshw -C network
iwlist scan

or is it more WPA related?? Does no encryption work?

---

### Post by JakeSpeare on 2007-10-14
jake@averatec:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:30:d3:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.8 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64


jake@averatec:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



Everything worked fine until I did the latest upgrade this morning (you are right - it may not have been a kernel upgrade) .  I am running gutsy.  The wireless card is not even showing up anymore in Network Manager.

---

### Post by kevdog on 2007-10-14
There is no driver associated with your card hence the big UNCLAIMED statement.  

Can you post the following for me:
modinfo rt2500

---

### Post by odiseo77 on 2007-10-14
If this helps, I've set up a WPA-TKIP connection from my PC (using a rt2500 wireless card) to my router this way (very easy indeed):

First, edit your /etc/network/interfaces file so your wireless device section (ra0) looks something like this:

```
auto ra0
iface ra0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
pre-up iwconfig ra0 essid your_essid_here
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set Channel=11 #your channel here
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="your_passphrase_or_hexadecimal_code_here" #(without the quotes)
pre-up iwpriv ra0 set TxRate=0
```

Then, stop your network services and start them again:

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

If your router is set up properly, that should do it.

**NOTE**: I haven't followed this thread thoroughly, so if you've blacklisted the rt2500 module, the above procedure probably won't work.

Regards.

---

