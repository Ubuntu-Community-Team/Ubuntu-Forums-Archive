---
title: "How do I connect?"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by joeri_83 on 2007-02-10
Hi,

I'm a beginner to all this, and should warn you of that.

Anyway, I'm having trouble connecting to my wireless network. I use Ubuntu 6.10 and have an ipw3945 wireless card. Ubuntu seems to know it's there, and when I use WiFi Radar I can see the network I want to connect to, but there is no way to connect. If I boot the computer with the wired cable pulled out it doesn't connect to the wireless either. The network's SSID is ANY.

How do I fix this?

---

### Post by lavinog on 2007-02-10
what do you mean there is no way to connect with wifi radar?
is there a button that says connect or disconnect above the close button?
also is the network you want to connect to called "ANY" or is that what iwconfig says?

what happens when you press connect on wifiradar?

---

### Post by joeri_83 on 2007-02-10
There is no connect button in wifi radar, only a disconnect one (and if I press it nothing seems to happen). And it is the network that is called ANY. 

iwconfig says the following:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9267   Missed beacon:0

sit0      no wireless extensions.

Thanks for the quick reply!

---

### Post by lavinog on 2007-02-10
try renaming the ssid to another name besides ANY, "any" is a keyword to tell iwconfig to connect to any essid which never seemed to work for me anyway.

the disconnect button turns into the connect button when disconnected, but I wonder if the network being called ANY is preventing it from disconnecting.

---

### Post by joeri_83 on 2007-02-10
Renamed my essid to "abc" and rebooted, didn't help. I still can't disconnect. As for the ssid of the network itself I can't do anything about it, as it is provided by my university and they have decided upon that name. Any other ideas? (Thanks for the help, btw)

---

### Post by joeri_83 on 2007-02-10
I might add that the wifi indicator light on my laptop flashes like a madman, if that matters at all.

---

### Post by lavinog on 2007-02-10
does wifi radar at least say connected to ...(ip...)
is there another area on campus that has another ssid
(for instance my campus has two different ssid's at some buildings)
are you sure that the ssid you are trying to connect to is the campus' ssid?
do you know someone that is able to connect...maybe check the info from their computer.

also maybe try deleting the ssid in wifi-radar and create a new one with the correct ssid

---

### Post by joeri_83 on 2007-02-10
Right now wifi-radar say connected to abc ip... and an ip-number, which I assume it has gotten from the wired network. Before I plug it in it has 127.0.0.1

The campus only has one ssid, unfortunately, though I know ANY is the right one as it worked just fine in Win XP (which I am trying to switch from). 

How do I do the thing you suggested last?

---

### Post by lavinog on 2007-02-10
> **joeri_83 said:**
> I might add that the wifi indicator light on my laptop flashes like a madman, if that matters at all.

this could be the problem
do you know what wireless card you have? u
are you using ndiswrapper? did you set it up or was it installed automatically?

use: 
lspci | grep -i "wireless"
to find what card you have

the ip address 127.0.0.1 is a loopback ip address it isn't assigned by the campus. which means it isn't connecting.

---

### Post by joeri_83 on 2007-02-10
This is what I get from that command:

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

It is the card I have, IPW3945. I haven't installed any drivers, but are rather using the one set up automatically (from the kernel?)

Where do I go from here?

---

### Post by lavinog on 2007-02-10
I'm searching the forums to see if anyone else had a flashing light.
in the mean time you might want to try:
sudo iwlist
sudo iwconfig
sudo iwconfig essid ANY
sudo dhclient

---

### Post by joeri_83 on 2007-02-10
Thanks a lot! I'll paste the output from those commands here:

sudo iwlist:
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event

sudo iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"abc"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3366   Missed beacon:0

sit0      no wireless extensions.

sudo iwconfig essid ANY:
Error : unrecognised wireless request "ANY"

sudo dhclient:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:47:66:12
Sending on   LPF/eth1/00:13:02:47:66:12
Listening on LPF/eth0/00:15:c5:14:c4:72
Sending on   LPF/eth0/00:15:c5:14:c4:72
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.193.64.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.193.64.1
bound to 10.193.69.43 -- renewal in 39455 seconds.

---

### Post by lavinog on 2007-02-10
actually i didn't think to ask...is it normal for your wireless indicator to blink when connected?

---

### Post by lavinog on 2007-02-10
sorry i forgot to include the interface
sudo iwlist eth1
sudo iwconfig eth1 essid ANY
sudo dhclient eth1

---

### Post by lavinog on 2007-02-10
ok i found something

[http://www.ubuntuforums.org/showthread.php?t=350145&highlight=wireless+blinking+light]("http://www.ubuntuforums.org/showthread.php?t=350145&highlight=wireless+blinking+light")

it seems that the driver for you card is only partially enable and you have to install the linux-restricted modules package.
for legal reasons it isn't installed by default

---

### Post by joeri_83 on 2007-02-10
Nope, the indicator is supposed to shine with a solid light.

New output.

sudo iwlist eth1:
iwlist: unknown command `eth1'

sudo iwconfig eth1 essid ANY:
Nothing appears, as if I had just pressed return

sudo dhclient eth1:
There is already a pid file /var/run/dhclient.pid with pid 10730
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:47:66:12
Sending on   LPF/eth1/00:13:02:47:66:12
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by joeri_83 on 2007-02-10
Okay, thanks a lot!

Since I'm a noob: how do I install the restricted module?

---

### Post by lavinog on 2007-02-10
first go into synaptic package manager
click settings > repositories
then check the proprietary drivers (restricted)
close that window
then click on reload
then search for restricted modules
you should see one that says linux restricted modules generic
click on the box next to it and select mark for installation
it should give you a box saying that it needs to install other modules too...click mark or ok
then click apply
when it is done... restart and let me know if anything changes

---

### Post by joeri_83 on 2007-02-10
It seems like I have already installed that module. At least the box is already ticked in.

---

### Post by lavinog on 2007-02-10
ok i found some more. I am getting this from:
[]("http://www.ubuntuforums.org/showthread.php?t=348123&highlight=ipw3945+driver+install")

> start the daemon thus:
/sbin/ipw3945-$(uname -r)
If there is an error message that ipw3945d is aleady running, but in fact it's not, delete /var/run/ipw3945.pid and try again (seems to be a bug that pid is left over).


There does seem to be a lot of people with your card that are having similar problems

---

### Post by joeri_83 on 2007-02-10
Ok. This is what I get:

bash: /sbin/ipw3945-2.6.17-11-generic: No such file or directory

Does that mean actually haven't got the modules (though Synaptic certainly suggests that I do)? Or should I replace something in the line?

---

### Post by lavinog on 2007-02-10
which version of ubuntu are you using edgy or dapper?

---

### Post by joeri_83 on 2007-02-10
Edgy (6.10)

---

### Post by lavinog on 2007-02-10
i guess there should have been a 'd' after the 5.
try
/sbin/ipw3945d-$(uname -r)

---

### Post by joeri_83 on 2007-02-10
First gave me this:
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-02-10 13:49:49: WARNING: Could not access '/var/run/ipw3945d.pid':
Permission denied (13)
2007-02-10 13:49:49: ERROR: Could not determine if daemon already running.

So I removed /var/run/ipw3945d.pid, since I assumed that's what the quote you posted said. Now it tells me this:

ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-02-10 13:51:26: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

However running lspci | grep -i "wireless" still gives me:
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by lavinog on 2007-02-10
try
sudo /sbin/ipw3945d-$(uname -r)

some programs especially programs that have to do with configuration require that they be ran as super user.

also we should be on the right track because i have found numerous posts saying that this is the solution.

---

### Post by joeri_83 on 2007-02-10
Alright, that seems to have started a process. What do I do next?

This is what it said:
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
Intel PRO/Wireless 3945ABG Network Connection found at:
 /sys/bus/pci/drivers/ipw3945/0000:0b:00.0
Daemon launched as pid 12989.  Exiting.


I should point out that my wifi indicator lamp has now stopped flashing and is turned off. If I start wifi-radar I can't see anything there anymore.

---

### Post by lavinog on 2007-02-10
ok now try:
sudo iwlist
sudo iwconfig eth1 ANY
sudo dhclient

if nothing try installing network-manager-gnome with synaptic
and try using network manager instead of wifi-radar. some people claim that that also helped.

if that still fails try running sudo /sbin/ipw3945d-$(uname -r) again and see if the light comes back on...or try turning your wireless off and on again...or even try rebooting and see if anything changes

---

### Post by lavinog on 2007-02-10
I also noticed you have the latest kernel...earlier today there was a message claiming that there was a issue with the latest kernel not installing correctly, but now it is fixed. i would go into synaptic and press reload and mark all updates and apply. just to be sure.

---

### Post by joeri_83 on 2007-02-10
No luck so far, though a reboot made the wifi-indicator flash again. I downloaded network-manager-gnome, where do I find it?

---

### Post by lavinog on 2007-02-10
i'm not exactly sure how to use the network manager. you might want to try in a terminal sudo network-manager-gnome
or try typing sudo network then press tab and it should give you a list of programs that start with network (a really handy feature in terminal)
you can also try looking under internet in your menu.

if you find it and it doesn't work try running the ipw3945d thing again and try again
also did you do the update thing i mentioned?

---

### Post by joeri_83 on 2007-02-10
Seems like network-manager-gnome isn't really installed, though synaptic claims it is, as I can't find it. The terminal claims there is no such command (and network+tab yields network-admin only) and it's not under internet. I did update also, but there was nothing to update. 

I ran the ipw-thing, which first had me close the old process, and then I relaunched it, which made the light stop flashing.

---

### Post by lavinog on 2007-02-10
when the light stopped flashing did it turn off or stay on?
i read that one person had his light turn off and he just had to turn on his wireless by pressing fn-f2 and it worked.

if we can get a solid light then we have made progress.
as soon as a solid light comes on... try wifi radar

---

### Post by joeri_83 on 2007-02-10
It turns off, and then when I press fn+F2 nothing happens. 

When the light was flashing I could turn it off by pressing those keys, as well as turn it on which returned it to the flashing state.

---

### Post by lavinog on 2007-02-10
post your:
/var/log/messages

you can do this by pressing alt-f2 and typing > gedit /var/log/messages

i am currently looking up ndiswrapper options for your card.
ndiswrapper lets you use the windows driver in linux

---

### Post by joeri_83 on 2007-02-10
Thanks for all the help!

Here is the log from my last reboot (as the whole thing is huge, tell me if you need it though). I've killed the old process and done the ipw-thing and the light is off.

Feb 10 15:56:06 johan-laptop kernel: [17179740.912000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 15:56:13 johan-laptop kernel: [17179748.748000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 10 15:56:13 johan-laptop kernel: [17179748.748000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 10 15:56:14 johan-laptop kernel: [17179749.248000] Kill switch must be turned off for wireless networking to work.
Feb 10 15:56:14 johan-laptop kernel: [17179749.564000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 10 15:56:14 johan-laptop kernel: [17179749.564000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 10 15:56:15 johan-laptop kernel: [17179749.952000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 15:56:19 johan-laptop kernel: [17179753.976000] Kill switch must be turned off for wireless networking to work.
Feb 10 15:56:19 johan-laptop kernel: [17179753.976000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 10 15:56:19 johan-laptop kernel: [17179753.976000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.

---

### Post by lavinog on 2007-02-10
> Kill switch must be turned off for wireless networking to work.
this looks like something to look into...after googling the phrase i came across a page that recomended turning off wireless hotkey in bios.
are you familiar with changing your bios?
there might be some sort of option to disable wireless hotkey or something similar.

also: > ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
is abg what you entered in or did you enter abc?

---

### Post by joeri_83 on 2007-02-10
I entered in abc so I assume the ABG is the three standards for wireless. I'll reboot now and see if I can find any such settings in there. I'll report back in a minute.

---

### Post by lavinog on 2007-02-10
> **joeri_83 said:**
> I entered in abc so I assume the ABG is the three standards for wireless.

yeah...your right.

---

### Post by joeri_83 on 2007-02-10
I disabled the wireless key in bios, but it seems as if there is no change. I also booted the computer up with the wired network cable pulled out. Here is the log:

Feb 10 16:13:13 johan-laptop gconfd (johan-4822): starting (version 2.16.0), pid 4822 user 'johan'
Feb 10 16:13:13 johan-laptop gconfd (johan-4822): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 10 16:13:13 johan-laptop gconfd (johan-4822): Resolved address "xml:readwrite:/home/johan/.gconf" to a writable configuration source at position 1
Feb 10 16:13:13 johan-laptop gconfd (johan-4822): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb 10 16:13:13 johan-laptop gconfd (johan-4822): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb 10 16:13:13 johan-laptop gconfd (johan-4822): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Feb 10 16:13:15 johan-laptop kernel: [17179610.628000] NET: Registered protocol family 10
Feb 10 16:13:15 johan-laptop kernel: [17179610.628000] lo: Disabled Privacy Extensions
Feb 10 16:13:15 johan-laptop kernel: [17179610.628000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 10 16:13:15 johan-laptop kernel: [17179610.628000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 10 16:13:15 johan-laptop kernel: [17179610.628000] IPv6 over IPv4 tunneling driver
Feb 10 16:13:20 johan-laptop gconfd (johan-4822): Resolved address "xml:readwrite:/home/johan/.gconf" to a writable configuration source at position 0
Feb 10 16:14:10 johan-laptop kernel: [17179665.224000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:14:36 johan-laptop kernel: [17179691.292000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 10 16:14:36 johan-laptop kernel: [17179691.292000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 10 16:14:41 johan-laptop kernel: [17179696.668000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 10 16:14:41 johan-laptop kernel: [17179696.668000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Feb 10 16:14:42 johan-laptop kernel: [17179697.384000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Feb 10 16:14:42 johan-laptop kernel: [17179697.384000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.

Is the eth1 link not ready, important? eth0 was presumably not ready since I pulled out the cable.

---

### Post by lavinog on 2007-02-10
did you run the ipw3945 thing? if not what does the log look like after you do

---

### Post by joeri_83 on 2007-02-10
I did. I now ran it again, after closing the pid from the last attempt. My log reads like this:

Feb 10 16:17:14 johan-laptop kernel: [17179850.144000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:17:22 johan-laptop kernel: [17179857.224000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:18:22 johan-laptop kernel: [17179917.636000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:18:23 johan-laptop kernel: [17179918.640000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:19:23 johan-laptop kernel: [17179979.012000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:20:24 johan-laptop kernel: [17180039.388000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:21:24 johan-laptop kernel: [17180099.764000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:22:24 johan-laptop kernel: [17180160.144000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:23:25 johan-laptop kernel: [17180220.516000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:23:26 johan-laptop kernel: [17180221.520000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:24:26 johan-laptop kernel: [17180281.892000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:25:27 johan-laptop kernel: [17180342.264000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:28:27 johan-laptop kernel: [17180522.744000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:29:28 johan-laptop kernel: [17180583.160000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:29:29 johan-laptop kernel: [17180584.152000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:32:29 johan-laptop kernel: [17180764.744000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:33:30 johan-laptop kernel: [17180825.484000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:34:30 johan-laptop kernel: [17180885.856000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:35:31 johan-laptop kernel: [17180946.228000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:35:46 johan-laptop kernel: [17180962.100000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

However the wifi indicator is off, and if I run wifi-radar it will not discover anything.

---

### Post by lavinog on 2007-02-10
try
> ipw3945d-$(uname -r) --kill --foreground --log-file=~/wireless_debug 
instead of removing the pid file
and post the ~/wireless_debug file

---

### Post by joeri_83 on 2007-02-10
Hmm ... while it seems to have killed the process, it didn't produce any such file. Because it should be in my Home directory, right, and I should be able to open it with gedit ~/wireless_debug.

Also I needed to have sudo at the beginning to run the command.

The var/log/messages reads like this:

Feb 10 16:50:52 johan-laptop kernel: [17181867.736000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:51:52 johan-laptop kernel: [17181927.736000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:52:52 johan-laptop kernel: [17181987.736000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 10 16:53:53 johan-laptop kernel: [17182048.104000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

If I start the process again nothing seems to happen, and the only thing produced in the logfile is a few more lines containing the same message as the one above.

---

### Post by lavinog on 2007-02-10
is there a switch also to turn on and off your wireless? what laptop do you have?

---

### Post by joeri_83 on 2007-02-10
No switch, as far as I know. It's a Dell Inspiron 6400.

---

### Post by lavinog on 2007-02-10
i found that intel release a new driver for linux two weeks ago
i'm starting to run out of ideas it maybe something to look into.
> [http://downloadcenter.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21#DRI](http://downloadcenter.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21#DRI)

---

### Post by joeri_83 on 2007-02-10
I'll give it a shot. I really appreciate all the effort you've made to help me out.

---

### Post by joeri_83 on 2007-02-10
I tried to install the drivers. THe result is that now Ubuntu does not even think the wireless card exists (in network-admin it doesn't show up), and if I run iwconfig it shows this:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by lavinog on 2007-02-10
I found a bug report associated with some dells with your wireless card and edgy
> [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452)

you may want to try installing dapper drake instead and see if that works.
dapper tends to be more reliable with new users.

---

### Post by joeri_83 on 2007-02-11
Maybe I will do that.

Thanks a lot for taking the time to help me out.

---

### Post by shreg on 2007-02-20
I had quite de same problem with my ipw2200 and wifi-radar (in Edgy).

I resolved it by editing my wifi-radar.conf (/etc/wifi-radar.conf).

There I modified  :

```
interface = 
```
with
```
interface = eth1
```

"eth1" is **my** wifi interface name.

I suppose also that if your add manually a profil to this file it should work also...
My profile look like this :
```

[NETWORK_ESSID]
prescript = 
use_wpa = no
postscript = 
mode = 
key = MY_WEP_KEY
use_dhcp = yes
security = 
channel = 

```

---

