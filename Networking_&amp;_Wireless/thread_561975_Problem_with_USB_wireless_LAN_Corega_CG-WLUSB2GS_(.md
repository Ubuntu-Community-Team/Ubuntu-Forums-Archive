---
title: "Problem with USB wireless LAN Corega CG-WLUSB2GS (Atheros AR5523)"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by cactusman on 2007-09-28
Hi!

I'm a brand new Linux user (2 days). I've completely uninstalled windows xp from my computer and installed Ubuntu 7.04 Feisty Fawn.
Everything works well, except my USB wireless LAN :
Corega CG-WLUSB2GS
Chipset : Atheros AR5523
Files on the manufacturer installation CD : ar5523.bin, CgU2GS.inf, CGU2GS.sys, CGU2GS9x.sys
My computer : emachines J3064

I installed it with ndiswrapper.
Right after installing the driver...

If I type "ndiswrapper -l" I get :
> cgu2gs : driver installed
        device (07AA:0031) present

If I type "tail /var/log/messages" I get :
> Sep 28 19:22:58 yumiloic-desktop gconfd (root-8783): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep 28 19:22:58 yumiloic-desktop gconfd (root-8783): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Sep 28 19:22:58 yumiloic-desktop gconfd (root-8783): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep 28 19:22:58 yumiloic-desktop gconfd (root-8783): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep 28 19:22:58 yumiloic-desktop gconfd (root-8783): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep 28 19:23:08 yumiloic-desktop kernel: [ 7768.768866] usb 3-5: USB disconnect, address 6
Sep 28 19:23:10 yumiloic-desktop kernel: [ 7770.771705] usb 3-5: new high speed USB device using ehci_hcd and address 7
Sep 28 19:23:11 yumiloic-desktop kernel: [ 7770.904978] usb 3-5: configuration #1 chosen from 1 choice
Sep 28 19:23:28 yumiloic-desktop gconfd (root-8783): GConf server is not in use, shutting down.
Sep 28 19:23:28 yumiloic-desktop gconfd (root-8783): Exiting
yumiloic@yumiloic-desktop:~$ 

If I type "iwconfig" I get :
> lo        no wireless extensions.
eth0      no wireless extensions.

So whatever, I decide to unplug my USB device and then reconnect it... In a couple of seconds the screen freeze and I have to restart the computer.
If I start the computer with the USB device plugged, Ubuntu freeze and doesn't start.
I spent 2 whole nights trying fixing it but I can't find anything more to try...

It works perfectly on windows xp.
Any idea? (please help me I need some sleep lol...)

---

### Post by HokeyFry on 2007-09-28
what version of ndiswrapper are you using?

i believe that "ndiswrapper -version" will produce this, but i am on a school machine right now and cannot tell you for sure

---

### Post by cactusman on 2007-09-29
Thanks for your answer.

Before I wrote the first message, I installed the driver following this way :
[http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html]("http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html")

After your answer, I decided to remove ndiswrapper, download the last stable version -1.48- on the official website ([http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)) and try to reinstall the driver following the procedure of the official website.

The result it's exactly the same.

Now if I do "ndiswrapper -v" I got :
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48
vermagic:       2.6.20-16-generic SMP mod_unload 586 
yumiloic@yumiloic-desktop:~$ 

The strange thing is that the wireless use to work more or less at the beginning.
I don't remember how I did but basically the USB device appeared "no connected" in ndisgtk but was working anyway. I had a connection but if I restarted the computer I had to push a button on my LAN connected to the phone line, otherwise it was not detected by the USB device...

I'm lost !:confused:

---

### Post by cactusman on 2007-09-29
I got informations about the chipset here :
[http://www.corega.co.jp/product/os/pc_unix_distributions.htm]("http://www.corega.co.jp/product/os/pc_unix_distributions.htm")

They describe some ways to install the usb device on Linux.
Unfortunately it doesn't seems to have a way to install it on Debian...

It's in japanese I know sorry I don't speak japanese...

I got the file wlusb2gs_w_110.exe from the same website but couldn't extract it neither with cabextract nor unshield :
> 
yumiloic@yumiloic-desktop:~/driverwifi$ unshield x wlusb2gs_w_110.exe
Failed to open wlusb2gs_w_110.exe as an InstallShield Cabinet File
yumiloic@yumiloic-desktop:~/driverwifi$ cabextract -d drivers wlusb2gs_w_110.exe
wlusb2gs_w_110.exe: no valid cabinets found

All done, errors in processing 1 file(s)


---

### Post by cactusman on 2007-09-29
Ok I found others drivers in the aisa website here :
[http://www.corega-asia.com/support/download/driver.php]("http://www.corega-asia.com/support/download/driver.php")

Apparently the devices with AR5523 need 2 drivers to works : athfmwdl.inf and netCgGSU.inf.

So i tried and it works but when i restart the computer it doesn't detect automatically the connection...

My USB pendrive doesn't work properly neither...

I think go back to windows...

---

### Post by cactusman on 2007-09-29
Ok It's almost working!

Finally I found the good files here : 
[http://www.corega-asia.com/support/download/driver.php]("http://www.corega-asia.com/support/download/driver.php")

I installed athfmwdl.inf AND netCgGSU.inf with the proper method (ndiswrapper only with terminal)

After the install, I have a connection and...

ndiswrapper -v donne :
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48
vermagic:       2.6.20-16-generic SMP mod_unload 586 

If I type "ndiswrapper -l" I get :
athfmwdl : driver installed
netcggsu : driver installed
        device (07AA:0030) present

If I type "tail /var/log/messages" I get :
Sep 29 22:52:15 yumiloic-desktop kernel: [ 2284.253379] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Sep 29 22:52:15 yumiloic-desktop kernel: [ 2284.254075] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 29 22:53:29 yumiloic-desktop kernel: [ 2358.691516] eth0: link down
Sep 29 22:53:29 yumiloic-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Sep 29 22:53:35 yumiloic-desktop kernel: [ 2364.051539] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep 29 22:53:38 yumiloic-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Sep 29 22:53:38 yumiloic-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Sep 29 22:53:38 yumiloic-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Sep 29 22:53:38 yumiloic-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Sep 29 22:56:59 yumiloic-desktop gconfd (yumiloic-5355): Failed to send buffer

If I type "iwconfig" I get :
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"CG-Guest"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 0A:0A:79:B2:D3:00   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

BUT, when I restart the computer I have 3 possibilities :
1- the usb device do the connection
2- the usb try to do the connection and the screen freeze (I have to restart the computer)
3 (most of the cases)- Impossible to do the connection,  the command "ndiswrapper -l" don't respond and "iwconfig" give :
> 
lo        no wireless extensions.
eth0      no wireless extensions
 

Any idea?

---

