---
title: "Help! Help! Wusb54gc Help! Help!"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by edwin.e.johnson on 2007-07-12
[B][U][COLOR="Red"]

CAN ANYONE POST A USER FRIENDLY HOWTO FOR THE LINKSYS WUSB54GC RT73 CHIPSET WIRELESS CARD? POSIBLY ONE THAT DOESNT INVOLVE ALREADY HAVING THE INTERNET ALREADY CONNECTED. FOR FEISTY.

AT THIS POINT I HAVE A FRESH INSTALL AND NO CONFIGURATION HAS BEEN DONE TO THE WIRELESS AT ALL.


ANYTHING WILL HELP THANKYOU






[/COLOR][/U][/B]

---

### Post by kevdog on 2007-07-12
Look for the post entitled Howto: serialmonkey rt73.  Its written by deprius.  You will need however another computer to download some files and transfer them to a USB stick.   For a similar post search for a thread authored by Craig Jackson.  Ive responded on that thread.  I think the solution which was installing serial monkey drivers starts on part 4.

Sorry I dont know the exact posts off the top of my head, but this topic has been covered many times in the forum.

---

### Post by edwin.e.johnson on 2007-07-12
thankyou i will give it a shot and post my outcome ...


thanks again

---

### Post by edwin.e.johnson on 2007-07-12
ok well i got to the end and it just didnt work ....

it asked me to "sudo ifconfig wlan0 up"

i got error saying no wlan0

i do now have a wlan1 so i sudo ifconfig wlan1 up

but same prob as before i see the network but cant connect.

---

### Post by kevdog on 2007-07-12
Can you post the following so I can help you out:
lshw -C network
sudo modinfo rt73

Also post contents of file:
/etc/iftab

---

### Post by edwin.e.johnson on 2007-07-12
ok here it is...




ford@ford-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@01:05.0
       logical name: eth0
       version: 10
       serial: 00:19:21:dc:f5:95
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:ec00-ecff iomemory:fdeff000-fdeff0ff irq:20
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:18:f8:2c:89:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN
ford@ford-desktop:~$ 






ford@ford-desktop:~$ sudo modinfo rt73
filename:       /lib/modules/2.6.20-15-generic/extra/rt73.ko
license:        GPL
description:    Ralink RT73 802.11abg WLAN Driver 1.0.3.6 CVS 2007071123
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     8935B8531E165F31E97EBD1
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           firmName:Permit to load a different firmware: (default: rt73.bin)  (charp)
ford@ford-desktop:~$

---

### Post by kevdog on 2007-07-12
What about

/etc/iftab

Thanks

---

### Post by edwin.e.johnson on 2007-07-12
it says


eth0 mac 00:19:21:dc:f5:95 arp 1
wlan0 mac 00:18:f8:2c:89:7a arp 1

---

### Post by edwin.e.johnson on 2007-07-12
ndis wrapper wont even work... and info on that?

---

### Post by kevdog on 2007-07-12
Ok one last thing -- I see a problem already with the iftab file.  You should have something like a
/etc/modprobe.d/rt73 file or something like that. 

Can you post that here!

---

### Post by edwin.e.johnson on 2007-07-13
there is no rt73 file in there

---

### Post by edwin.e.johnson on 2007-07-13
fuckit im doing one more fresh install. and starting over from the beginning. man why cant someone just make a deb package for this thing.

---

### Post by bikeboy on 2007-07-13
Make sure manual configuration is set through Network Manager and roaming disabled.

If that doesn't work, try [this](http://www.vickersf.dyndns.org:8080/blog/2007/07/03/howto-ralink-ubuntu-feisty/) (shameless plug), rt73 shouldn't require extra packages as the drivers are built in (albeit the older ones). Unfortunately there are a few issues with Ralink in Feisty, related to Network Manager incompatibility afaik.

---

### Post by edwin.e.johnson on 2007-07-13
awesome ppl on here are actually trying to help..

thankyou ill try it.

---

### Post by edwin.e.johnson on 2007-07-13
ok that was a big help!

i did download gutsy T2 and noticed that it wasnt supported at all you have the howto on what he did to get it to work?   or can i just install ndiswrapper and the win drivers?


thanks alot

---

### Post by bikeboy on 2007-07-13
The drivers in Feisty are an older stable version but there's a conflict (hence the configuration needed), the ones in Gutsy are the new ones from serialmonkey. However, 
Gutsy currently (Tribe 2) has a bug where the ralink module was left out. It's a piece of cake to get going under Gutsy though provided you grab the latest rt2x00-cvs from serialmonkey.

A guide for Gutsy is in a forum thread [http://ubuntuforums.org/showthread.php?t=486010](http://ubuntuforums.org/showthread.php?t=486010)

Be warned, Gutsy is not even close to stable yet, things go wrong.

---

### Post by edwin.e.johnson on 2007-07-14
awesome dude thanks for the help ill let you know the outcome of the feisty one before i even try the 7.10

---

### Post by edwin.e.johnson on 2007-07-14
well it didnt work......



i got to the part

sudo chmod o+x ./wireless-up


it just says "./wireless-up : No such file or directory"


now my gutsy cd wont work either

---

### Post by bikeboy on 2007-07-14
Edit: My apologies, just noticed a typo in the howto. The difference between - and _ is important ;)

Not sure what would cause you Gutsy CD to not work. I did some checking last night and the wireless issue with Gutsy hasn't been fixed yet, Tribe 3 is due later this month so hopefully by then is won't require any mucking around.

---

### Post by edwin.e.johnson on 2007-07-14
so instead of using 

"wireless-up"

use "wireless_up"






---------------------------------- original  ----------------------------------------------


cd /etc/init.d/
gksudo gedit wireless-up
Copy and paste the following into Gedit&#8230;
#!/bin/dash
ifconfig ra0 down
iwconfig ra0 essid "your essid"
iwconfig ra0 key "your wep key if you have one"
ifconfig ra0 up
dhclient3 ra0

Then change the essid and WEP key (put s: before the key if it&#8217;s not in hex format). If you use WPA, check the Ubuntu wiki for what needs to be different, shouldn&#8217;t be much.

Save the file as wireless-up. Now, you make the file executable and just make a link to that file in the initialisation scripts that run during boot up.

sudo chmod o+x ./wireless-up
cd /etc/rc2.d/
sudo ln -s /etc/init.d/wireless-up ./S14wireless-up




--------------------------------- should it look like this ---------------------------------------------




cd /etc/init.d/
gksudo gedit wireless_up
Copy and paste the following into Gedit&#8230;
#!/bin/dash
ifconfig ra0 down
iwconfig ra0 essid "your essid"
iwconfig ra0 key "your wep key if you have one"
ifconfig ra0 up
dhclient3 ra0

Then change the essid and WEP key (put s: before the key if it&#8217;s not in hex format). If you use WPA, check the Ubuntu wiki for what needs to be different, shouldn&#8217;t be much.

Save the file as wireless_up. Now, you make the file executable and just make a link to that file in the initialisation scripts that run during boot up.

sudo chmod o+x ./wireless_up
cd /etc/rc2.d/
sudo ln -s /etc/init.d/wireless_up ./S14wireless_up



?????????????


thanks

---

### Post by bikeboy on 2007-07-14
I changed the howto on my site to fix the mistake, The file created in the text editor is wireless-up, so use that in the sudo chmod o+x command as well. You can use wireless_up if you want, or anything else for that matter, so long as it's consistent.

What you're doing is creating a text file with a set of commands for getting the wireless working when the computer starts, then making that file executable so that it can be run during the boot process. sudo chmod o+x ./wireless-up is saying...allow the owner (root) of the file in the current directory called "wireless-up" to execute the instructions in that file.

---

### Post by edwin.e.johnson on 2007-07-14
ill try it again ill post update in 5mikes....

5min

---

### Post by bikeboy on 2007-07-14
Going for dinner now, but will be sure to come and see how you did.

---

### Post by edwin.e.johnson on 2007-07-14
this is what i got......  it didnt work






ford@nide-desktop:/etc/rc2.d$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5309
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:19:21:dc:f5:95
Sending on   LPF/eth0/00:19:21:dc:f5:95
Sending on   Socket/fallback
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5327
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:f8:2c:89:7a
Sending on   LPF/wlan0/00:18:f8:2c:89:7a
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:19:21:dc:f5:95
Sending on   LPF/eth0/00:19:21:dc:f5:95
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:f8:2c:89:7a
Sending on   LPF/wlan0/00:18:f8:2c:89:7a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
ford@nide-desktop:/etc/rc2.d$

---

### Post by bikeboy on 2007-07-14
Ok, looks like Network Manager is interfering. In a terminal type 'sudo killall NetworkManager' without the quotes. Then, 'sudo /etc/init.d/wireless-up'. See how that goes.

---

### Post by edwin.e.johnson on 2007-07-14
im installing gutsy now but im almost sure it wont workout so ill try it later and post the deal here

---

### Post by edwin.e.johnson on 2007-07-14
that was quick back to feisty it is 

it just wont install anymore.

ill have feisty on here in like 10 min and have to howto done right after that


thanks for the help

---

### Post by edwin.e.johnson on 2007-07-14
ok well i did it fresh and killed network manager before i  did any of the howto..
same thing happened .

any ideas

---

### Post by edwin.e.johnson on 2007-07-14
anyone

---

### Post by kevdog on 2007-07-14
Edwin -- I give you credit for trying a lot of different things, but I feel youve been on the receving end of just some plain bad advice.  I know installing Gusty was not necessary. 

Just refresh my memory.  I know you are working with a USB device.
I think it is a ra chipset (could you verify this)

Can you also post when the card is plugged in
lshw -C network

I dont want to make any assumptions here, but  I think basically you are dealing with a bad or non-functioning driver issue.

---

### Post by edwin.e.johnson on 2007-07-15
well as it turns out im just going to wait until the official 7.10 is out as of right now mandriva will do. it just seems so limited compared to ubuntu.... anyhow thankyou much for the concern and help everyone has tried to give me.

---

