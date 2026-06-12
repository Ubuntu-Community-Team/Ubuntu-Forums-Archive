---
title: "Wi-Fi help needed for beginner"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by hointz on 2009-01-02
Hi.

I am new to Linux and need some help connecting my computer to my Wi-Fi net to my old computer.

I am trying to connect via PCMCIA-card based Wi-Fi from 3COM called: 3CRWE154G72. The card did work on my windows. Now it can see some of the networks around, but can not connect to my router.

XUbuntu 8.10
3COM OfficeConnect 3CRWE154G72 Wi-Fi card
Apple Airport Extreme router

What do i do? Can someone please help? :-)


Hointz

---

### Post by southerngrey on 2009-01-02
Can you open up a terminal and paste the output from:

ifconfig
&
iwconfig

---

### Post by hointz on 2009-01-02
IFCONFIG:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:184 (184.0 B)  TX bytes:184 (184.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:12:a9:c6:d0:9c  
          inet6 addr: fe80::212:a9ff:fec6:d09c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2016 (2.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-A9-C6-D0-9C-30-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




IWCONFIG:

lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"B2C Full Access 11"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by southerngrey on 2009-01-02
OK your card is there and seems to be detecting fine, and it seems to be seeing the router but not forming a connection.  How are you connecting to the router, command line or a gui application?

Also, do you need to be able to connect to different networks in different locations or is connecting to your home network enough.  I can probably get you connected to your home network with command line but you'd need to reconnect to each new network that way, a roaming solution is probably better.

I would suggest a program called "wicd" if it is in the XUbuntu repositories, it is a good wireless manager for the GUI, it seems to form a connection where others will not.

---

### Post by southerngrey on 2009-01-02
Installing Wicd in Ubuntu - copied from [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.

---

### Post by hointz on 2009-01-02
I am configuring my router via my Mac running OSX. I am trying to connect my girlfriends old pc to my wi-fi. She only needs to connect to my home network.

The Wi-Fi card can not see my router, actually. The one listed in the previous post is my neighbours. I found something on the net saying that my card can not read WPA-2 security. Maybe I have to change that as well to WEP?

I have to run now, but will check your reply later.

Thanks for the fast replys.

---

### Post by southerngrey on 2009-01-02
OK just looked it up and I couldn't find a find a hardware update to make the card WPA-2 compatable. You may need to consider swapping the network to WPA or WEP which it is listed as supporting.  But assuming the router is broadcasting the ESSID you should still be able to see it.

If installing wicd doesnt solve the problem (running XUbuntu it will likely install the GTK library packages as dependencies fyi) then try the following commands to try and get a connection:

sudo iwconfig wlan0 essid "*YOUR ESSID HERE*" key *YOURKEYHERE* mode managed
sudo dhclient wlan0

That should force a connection to the router and enable a dhcp lease.  If that works I'll walk you through setting up a script to get it to run each time the machine boots up.

---

### Post by hointz on 2009-01-02
Sorry. I have not managed to get connected yet. Neither of your tips did the trick.

---

### Post by southerngrey on 2009-01-02
Can you confirm if your router is broadcasting it's ESSID, also did you try changing the encryption protocol.. If it's still WPA2 then the card will not be able to connect.

---

### Post by hointz on 2009-01-02
My Mac can see my router name. The router name is not supposed to have a hidden. 

My Wi-Fi card could not connect to an open router either.

After upgrading XUbuntu, to the latest updates, on my cable-network my Wi-Fi card can no longer detect any networks. Not mine nor my neighbours.

---

### Post by hointz on 2009-01-02
Ok... Now I restarted and my Wi-Fi card can see my neighbours router. I do not get why it can not see mine. Nothing shall be hidden. I can also see that my neighbour is using WPA2.

---

### Post by hointz on 2009-01-02
And then I found this:

[http://www.hyperborea.org/journal/archives/2004/10/12/airport-extreme-vs-linux/](http://www.hyperborea.org/journal/archives/2004/10/12/airport-extreme-vs-linux/)

And I also found something in Synaptic called "AirPort Config," by Jon Sevy at Drexel University. Trying that a little before bedtime...

---

### Post by southerngrey on 2009-01-02
hmm, even though you may not be able to configure the router from your XUbuntu machine you should still be able to access the network.

It's strange that you cannot see your router at all. I'll do some research and see if I can turn something up.  I'll post again soon.

---

### Post by southerngrey on 2009-01-02
ahh just had a thought.  If you have used the hardwire to connect to the network using the Xubuntu machine then the DHCP lease with that may be messing with your Wlan0 connection.

Can you repost the output from iwconfig and ifconfig.  You may need to take down cable interface in order to get the Wlan0 to connect (I had a similar issue when setting up my network)

Also this might go a lot quicker if you instant message me, once we sort the issue out we can post the solution, my MSN contact is listed on the left side of the screen, I also have ICQ and Skype if you dont have MSN.  A video call in Skype from your macbook is probably the best as then you can show me the screen on the PC and we can diagnose in real time.

---

### Post by hointz on 2009-01-04
I renamed my essid to a shorter name. Now my xubuntu is detecting my network, but I can still not connect to it. One step closer...

I have been messing with etc/network/interfaces in trying to connect to my network. At the moment there is probably something wrong with it. I also posted my "interfaces"-file below. Is there something wrong there?

I can talk to you on skype later.


IWCONFIG:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Trond"  
         Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
         Tx-Power=27 dBm   
         Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
         Power Management:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



IFCONFIG:

eth0      Link encap:Ethernet  HWaddr 00:0a:cd:06:a0:ab  
         inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
         inet6 addr: fe80::20a:cdff:fe06:a0ab/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:9164 errors:0 dropped:0 overruns:0 frame:0
         TX packets:4805 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:12839227 (12.8 MB)  TX bytes:330486 (330.4 KB)
         Interrupt:11 Base address:0x2800 

wlan0     Link encap:Ethernet  HWaddr 00:12:a9:c6:d0:9c  
         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-A9-C6-D0-9C-00-00-00-00-00-00-00-00-00-00  
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


INTERFACES:

iface wlan0 inet dhcp
name Wireless LAN card
wireless_mode managed
wireless_essid Trond
wireless_key s:***

wireless_channel 13
auto wlan0

---

### Post by southerngrey on 2009-01-04
It could be something with the interfaces file but changing the settings on the command line should fix that.  Try taking the eth0 down and then connecting

sudo ifconfig eth0 down
sudo iwconfig wlan0 essid "YOUR ESSID HERE" key YOURKEYHERE mode managed
sudo dhclient wlan0

Also it's possible that IPv6 is preventing the connection, have a read about using modprobe to remove it here on the forum, it's a pretty common thread.  I'd tell you how but I'll let you decide whether you need it.  Most people don't, and it'll speed up the connection without it, but I don't want to get you to remove it unless your sure you don't need it.  IPv6 can cause all sorts of issues in my experience though.

---

### Post by hointz on 2009-01-04
I get the message after the second line:

Error for wireless request "Set Encode" (8B2A)
       invalid argument "***".

where *** is my key.

---

### Post by hointz on 2009-01-04
Do you think it would be possible to use the windows-driver emulated in xubuntu?

---

### Post by southerngrey on 2009-01-04
I think that is the error message for an incorrect key.  What is the current encryption and are you entering in hex into the command line.

As for the windows emulater (ndisWrapper)?  It does work but I don't think the problem is with the driver, the card seems to be detecting fine.  ndisWrapper does work but it was more useful in older releases when not as many wireless cards were supported, recent releases seem to support far more wireless cards.

I suspect the issue is simply with the settings.  My experience with networking on Linux is you have to get all the settings right to get it to run at all, but once it's up it's solid.  I had similar problems to you to start with but once you get it up it'll most likely be rocksolid.

---

### Post by hointz on 2009-01-04
WPA2 encryption. What would the encryption be in hex?

---

### Post by southerngrey on 2009-01-04
When I looked it didn't look like your wifi card supported wpa2.  I would try switching the router to WEP and try to connect with that.  The commands I listed above should work but the WEP key is entered in hex not a passphrase, which is why I mentioned it.

---

### Post by hointz on 2009-01-04
I translated my key to hex with:

[http://www.defproc.co.uk/toys/hex.php](http://www.defproc.co.uk/toys/hex.php)

Then entered:

sudo iwconfig wlan0 essid "YOUR ESSID HERE" key YOURKEYHERE mode managed

but got a new error:

SET failed on device wlan0 ; Invalid argument.

---

### Post by southerngrey on 2009-01-04
If the encryption on the router hasn't changed to WEP then it still won't work, and I think WPA2 uses a different bit length hence the invalid argument.  You'll need to reset the router with a new WEP encryption key.

---

### Post by hointz on 2009-01-04
I did switch to WEP 128-bits before the last try...

---

### Post by southerngrey on 2009-01-04
My mistake sorry.  Try using this convertor instead:

[http://www.corecoding.com/utilities/wep2hex.php]("http://www.corecoding.com/utilities/wep2hex.php")

The convertor you used won't produce the right type of key.  The one above is WEP 128 specific.

---

### Post by hointz on 2009-01-04
Thanks again and sorry for being a novice.

The commands ran smoothly. Wicd did detect my router for a while but it disappeared again and I can no longer see it in my list. So still no connection after the commands.

---

### Post by hointz on 2009-01-04
Just wanted to show the text that appears after I run:

sudo dhclient wlan0

This it:

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:a9:c6:d0:9c
Sending on   LPF/wlan0/00:12:a9:c6:d0:9c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by hointz on 2009-01-04
I have found out that my wireless pc card is a prism54 card and needs drivers to operate. Found something here, but I do not understand how to install it. Do you understand something here?

[http://lekernel.net/prism54/newdrivers.html](http://lekernel.net/prism54/newdrivers.html)

I have the 3com 3CRWE254G72 card in pci version.

---

### Post by southerngrey on 2009-01-04
Sorry, fell asleep.  Your card is supported with drivers on the install cd you already have that driver running [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards3com]("https://help.ubuntu.com/community.HardwareSupportComponentsWirelessNetworkCards3com")  Its seems to have been upgraded to a pci version 

I think you've almost got it but just missing something simple.

I've just looking back through the thread, is the ethernet cable still connected?  I see that eth0 is running back in the ifconfig output.

I am not that familiar with 3com cards or airport routers so there may be something I'm missing...Anyone else got any ideas?

---

### Post by hointz on 2009-01-05
I use the wire to connect and download stuff occasiononally. Then I remove it when I try to connect with wlan.

---

### Post by hointz on 2009-01-05
Eureka.

I have just connected to my network and I am now surfing on the web. I disconnected my router (apple airport extreme) and connected another router (airport express) that I am using for remote music from iTunes.

That means that ubuntu is not compatible with airport extreme. I now have to figure out how to let ubuntu pick up the signals from my airport express on another frequency than from my extreme, because I have to use the extreme for master and the express for aitunes.

Should be easy ;) Thanks for all help.

---

### Post by southerngrey on 2009-01-05
Glad it's working.  Shame you had to adjust your hardware but if it works it works.  You may want to post that bug on launchpad, they might fix it for you.

---

### Post by hointz on 2009-01-05
Where/what is launchpad? Sorry, I am new...

---

### Post by southerngrey on 2009-01-05
It's the site Ubuntu development team uses for bug tracking [https://launchpad.net/ubuntu]("https://launchpad.net/ubuntu")

It's the place to let the developers know there is a problem with something.

---

