---
title: "[SOLVED] Still no wireless"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by notanerd on 2008-10-19
I have now been trying for a month to get wireless working on my laptop with 8.04. when I type in lshw - C network i get this result

WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:10:80:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:7c:4d:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

What can I do to fix this. I just can't seem to enable the wireless card?

Please help me

---

### Post by Bucky Ball on 2008-10-19
If you can connect via a cable, download through Synaptics:

**ubuntu-restricted-extras**

Open a terminal and paste in:

** sudo nano /etc/modprobe.d/blacklist**

and look for this section:

```
# replaced by b43 and ssb.
blacklist bcm43xx
```Make sure it look like that. Go to:

** System->Administration->Hardware Drivers**

... and make sure the Broadcom B43 Driver is ticked and in use. If you have been playing around with ndiswrapper, you need to either uninstall it or blacklist it also.

---

### Post by notanerd on 2008-10-19
lspci gives me this result for my wireless card

 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by Bucky Ball on 2008-10-19
Follow my last post and tell us what happens. :)

---

### Post by superprash2003 on 2008-10-19
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Bucky Ball on 2008-10-19
> **superprash2003 said:**
> try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

ndiswrapper is not longer required for this card anymore I didn't think.

---

### Post by notanerd on 2008-10-19
the text was correct and i have uninstalled ndiswrapper. I also enabled and installed b43 cutter, which then downloaded the firmware. do i need to reboot for this to take effect?

---

### Post by notanerd on 2008-10-19
i am trying to use wifi radar so i type sudo wifi-radar into terminal and it says 

dhclient3 --version 2>&1
wlan0     Interface doesn't support scanning : Network is down

the bottom line is repeated again and again and again

---

### Post by Bucky Ball on 2008-10-19
Is the wireless light on?

Enter:

**ifup**

... to bring the card up, then:

                                       **sudo dhclient -r**

    [LEFT]That releases your dhcp address. Then

[/LEFT]
    [LEFT][B]sudo dhclient

[/B][/LEFT]
    [LEFT]That renews it again.

[/LEFT]
        [LEFT][B]sudo iwlist wlan0 scan

[/B][/LEFT]
    [LEFT]Scan for networks[/LEFT]

---

### Post by notanerd on 2008-10-19
evan@durruti:~$ ifup
ifup: Use --help for help
evan@durruti:~$ sudo dhclient -r
[sudo] password for evan: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:7c:4d:e7
Sending on   LPF/wlan0/00:90:4b:7c:4d:e7
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:03:25:10:80:44
Sending on   LPF/eth0/00:03:25:10:80:44
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
evan@durruti:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:7c:4d:e7
Sending on   LPF/wlan0/00:90:4b:7c:4d:e7
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:03:25:10:80:44
Sending on   LPF/eth0/00:03:25:10:80:44
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.0.2 from 192.168.0.1
DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.2 from 192.168.0.1
bound to 192.168.0.2 -- renewal in 42513 seconds.
evan@durruti:~$ sudo iwlist wlan0 scan
wlan0     No scan results

---

### Post by Bucky Ball on 2008-10-19
System->Admin->Network

Unlock, click your wireless device then properties. In there, make sure all details are correct (ESSID, security if required), untick enable roaming and in Configuration, make sure it is set to:

**Automatic Configuration (DHCP)**

---

### Post by notanerd on 2008-10-20
OK that is all done. I have no security on my wireless. No connection as of yet, is wifi-radar a waste of time, should i go back to Network Manager?

---

### Post by Bucky Ball on 2008-10-20
> **notanerd said:**
> OK that is all done. I have no security on my wireless. No connection as of yet, is wifi-radar a waste of time, should i go back to Network Manager?

Might be an idea until you get a solid connection with your router. Never played with wi-fi radar but would imagine it will look for any network, we just want to nail the known one for now. No luck I take it? You have the ESSID the same on router and computer? In 'Network'?

Could you paste the result of:

[B]iwconfig

[/B]... and try:[B]

sudo iwlist scan

[/B]Also, can you run an ethernet cable and reboot. See if you can get a connection that way for the moment so we might be able to download some things.

---

### Post by notanerd on 2008-10-20
I am currently connected to the modem with an ethernet cable. 

iwlist comes up with this

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"alana"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist scan comes up with this

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by Bucky Ball on 2008-10-20
Looks right for the wireless. Bit stumped why it is not happening if the ESSID and security (WPA or whatever) details are correct for the router. 

```
Mode:Managed  Frequency:2.412 GHz ** Access Point: Not-Associated**   
```That is the only problem. Need to do a couple of things but will think a bit more about it later. :)

ps: is the wireless light on and switch in the right position, if it has one?

---

### Post by notanerd on 2008-10-20
thanks for all your help

---

### Post by Bucky Ball on 2008-10-22
Did you get things working?

---

### Post by notanerd on 2008-10-23
No its not working yet. I am not currently living with an internet connection, but I would still love some help :)

---

### Post by notanerd on 2008-11-13
still having no love with the wireless

---

### Post by notanerd on 2008-11-22
OK so I have moved house and now have a internet connection at home again. I would really love to solve this problem with wireless as I am currently running a 10m ethernet cable through the house and its very impractical. I also am spending a lot of time at my girlfriends and can't use my laptop with her wireless either. Please help, I'll be your best friend :)

---

### Post by Olivier2371 on 2008-11-22
Well, if you want i will explain how i connected my wireless.

1rst I installed ubuntu 8.04, then i went to the software sources to modify from uk server for me to main server, updated ubuntu (304 updates). I was connected to my router through nic interface. After i rebooted the laptop,
then i went to the router setup program to make sure of the wireless settings. After that i went back to ubuntu to System->Administration-> Hardware drivers. I found my wireless adapter driver, enabled it. I restarted the computer and then clicked on the network icon, switched to my wireless, entered the encryption mode my router uses, the password and the mode for the encryption. And I was connected.

My wireless button is not lit under ubuntu but is lit under windows.

Broadcom 43411

---

### Post by notanerd on 2008-11-22
i have tried those steps before with no success, thank you

---

### Post by Joe2Shoe on 2008-11-22
SEE MY post here: [http://ubuntuforums.org/showthread.php?t=990216](http://ubuntuforums.org/showthread.php?t=990216)
nothing else worked.
On a fresh install of Ubuntu v8.10, this is all I did, and my BCM4306 rev. 02 wifi works!

ndiswrapper and fwcutter did not work previously on a previous install of 8.10.

---

### Post by Joe2Shoe on 2008-11-22
If that doesn't work, try this.

Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper.  This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install ndisgtk (System/Administration/Synaptic Package Manager).
   3. Open ndisgtk (System/Administration/Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.


[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.

---

### Post by Olivier2371 on 2008-11-22
Joe2Shoe,

You seem to be a great guy but I followed most of the post on networking and the only answer you give to people is to use ndiswrapper because it works for you. If it was so then they wouldn't be the need for a forum on networking.

Please try to come up with other idea.

---

### Post by Joe2Shoe on 2008-11-22
Olivier,
I beg to differ.
Yes, I offered NDISwrapper, and lots of other 'fixes'.  Often times it takes more than one attempt to figure out the correct path, or a combination of paths to wifi connection.
If one attempt did not work for someone, I offered another, and another.  Then, hopefully, it will eventually be resolved.
There is no 'quick' fix.
Thank you for your observation.
Joe2Shoe.

---

### Post by Ayuthia on 2008-11-22
Just to recap what I understand--you have installed ndiswrapper, it did not work so you uninstalled it, and then installed b43-fwcutter.  You also tried using wifi-radar and have switched back to network manager.

If that is all correct, can you post the results of the following for me:
```
lsmod|grep -e b43 -e ssb -e ndiswrapper -e bcm43xx
lshw -C network
```
The first command will help us see what modules are currently loaded.  The second command was posted in the original post, but you have made some changes so I just want to see if the information still looks correct.

Then I would like to see what happens when you do the following (please also remove your wired connection to prevent any conflicts):
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
This will remove the possible conflicting wireless drivers and then load the b43 module.  The third step will then bring up your wireless card and then scan for wireless sites.  If we still get no scan results, there is another link that I will post that might help.  I don't want to give it yet because I want to make sure that we are only using the b43 driver and nothing else.

---

### Post by Olivier2371 on 2008-11-22
notanerd,

Look at the link below it will explain everything you need to know.       (I hope!!)

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

---

### Post by notanerd on 2008-11-22
Yes you are right about what I have tried to do so far. Here the outputs of the commands

lsmod|grep -e b43 -e ssb -e ndiswrapper -e bcm43xx

b43                   127400  0 
rfkill                 10528  3 rfkill_input,b43
mac80211              194324  1 b43
led_class               7304  1 b43
input_polldev           6928  1 b43
ssb                    38020  1 b43

lshw -C network

*-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:10:80:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.2 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:90:4b:7c:4d:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx

This was reapeated about 10 times
WARNING: /etc/modprobe.d/blacklist.save line 40: ignoring bad line starting with 'x'

sudo modprobe b43

WARNING: /etc/modprobe.d/blacklist.save line 40: ignoring bad line starting with 'x'

sudo ifconfig wlan0 up

worked fine

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by Bucky Ball on 2008-11-23
wlan0     No scan results

Working but not finding any access points. Make sure you have right details for your router in System->Administration->Network.

---

### Post by Ayuthia on 2008-11-23
You might try this link:
[http://ubuntuforums.org/showthread.php?t=885173](http://ubuntuforums.org/showthread.php?t=885173)

lwfinger is going to need some information from you that is listed in the first post.  However the there is a character missing in his command so you will need to provide the following information:
```
SPROM=$(find /sys/devices -name ssb_sprom)
sudo cat $SPROM > sprom.dat
```

lwfinger has /sys/device where it should be /sys/devices.

Hopefully that will fix the problem.

---

### Post by notanerd on 2008-12-01
ok so i tried all the suggestions from lwfinger and he now suggests that I have to configure the modem manually. I don't really know what this means and I still don't detect any wireless networks automatically

iwlist scan comes up with this

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

and sudo ifconfig comes up with

eth0      Link encap:Ethernet  HWaddr 00:03:25:10:80:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:161161 errors:0 dropped:0 overruns:0 frame:1
          TX packets:105875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:208752853 (199.0 MB)  TX bytes:14696296 (14.0 MB)
          Interrupt:23 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93908 (91.7 KB)  TX bytes:93908 (91.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:7c:4d:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-7C-4D-E7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

any ideas anyone?

---

### Post by Ayuthia on 2008-12-01
If you have encyrption on your router right now, you will want to turn it off just to test.  You can connect manually by doing the following:
```
sudo dhclient -r
sudo iwconfig wlan0 essid router-name
sudo dhclient wlan0
```If it assigns an ip address, then you are connected.  If it goes back to sleep, then there are still some connection problems.

---

### Post by cokeonice on 2008-12-01
This is a long shot but it worked for me!

Try disabling your onboard modem in the BIOS.

---

### Post by notanerd on 2008-12-02
did not work i am afraid here are the outputs

sudo dhclient -r 

There is already a pid file /var/run/dhclient.pid with pid 10294
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

sudo iwconfig wlan0 essid sandy

had no output

sudo dhclient wlan0

There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:7c:4d:e7
Sending on   LPF/wlan0/00:90:4b:7c:4d:e7
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

sudo iwconfig comes up with this too

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"sandy"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by notanerd on 2009-01-05
so i feel like I should just give up on this wireless card I just re installed 8.10 from scratch and still am getting nothing

---

