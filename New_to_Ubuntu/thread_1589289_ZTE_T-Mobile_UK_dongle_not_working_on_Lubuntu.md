---
title: "ZTE T-Mobile UK dongle not working on Lubuntu"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by al.adab on 2010-10-06
I'm trying to get an internet dongle work on Lubuntu. It's a T-Mobile UK dongle. Here's the *lsusb*: 

[I]~$ lsusb
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 002: ID 1668:2441 Actiontec Electronics, Inc. [hex] BMDC-2 IBM Bluetooth III w.56k
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 005: ID 19d2:2000 ONDA Communication S.p.A. ZTE MF627/MF628/MF628+ HSDPA**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

I installed usb_modeswitch (through synaptics) + tried to enable the dongle through the network manager wizard. When I click on my network connections, though, the dongle doesn't appear (I previously tried to do this on Ubuntu 10.04: though the dongle didn't connect, it did appear as GPRS connection on the top of the list of the wifi connections). 

Also if I go to Preferences>Disk Utility, I sometimes can see the dongle recognised as a USB memory stick and sometimes it’s not there....

any idea?

---

### Post by al.adab on 2010-10-06
Just uninstalled usb_modeswitch 1.1.0-2 and can now see the dongle in Disk Utility as a /dev/sdb device named ZTE MMC Storage (firmware 2.31) - capacity: no medium detected.

I don't really know what this means. I also had a look at 
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) but don't really understand what s/he's talking about...

is it possible that I don't really need usb_modeswitch and it's more a matter of editing some file to stop the system from recognizing it as a USB memory stick and see it for what it really is?

---

### Post by al.adab on 2010-10-06
in some posts on this kind of dongles it's suggested trying to eject it (like you eject a usb mem stick) and then it'll appear as a modem. 

I tried to do so from Disk Utility (the only place where it's visible) and got the following error message: 

[I]Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory[/I]

also this is the result of a *tail -f /var/log/syslog*

[I]$ tail -f /var/log/syslog
Oct  6 16:41:40 fiction NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Oct  6 16:41:40 fiction NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Oct  6 16:41:40 fiction avahi-daemon[718]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.26.
Oct  6 16:41:40 fiction avahi-daemon[718]: New relevant interface eth1.IPv4 for mDNS.
Oct  6 16:41:40 fiction avahi-daemon[718]: Registering new address record for 192.168.0.26 on eth1.IPv4.
Oct  6 16:41:40 fiction dhclient: bound to 192.168.0.26 -- renewal in 118158 seconds.
Oct  6 16:41:41 fiction NetworkManager: <info>  (eth1): device state change: 7 -> 8 (reason 0)
Oct  6 16:41:41 fiction NetworkManager: <info>  Policy set 'Auto Curz0nS0ho' (eth1) as default for routing and DNS.
Oct  6 16:41:41 fiction NetworkManager: <info>  Activation (eth1) successful, device activated.
Oct  6 16:41:41 fiction NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Oct  6 16:41:51 fiction ntpdate[2597]: adjust time server 91.189.94.4 offset -0.220806 sec[/I]

...and I can't see it there...bad news?

---

### Post by al.adab on 2010-10-06
found this: 
[http://ubuntuforums.org/showthread.php?t=1005910](http://ubuntuforums.org/showthread.php?t=1005910)

and this is the result of entering *sudo wvdial* in terminal: 

[I]~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F &D2 &C1
AT&F &D2 &C1
OK
--> Sending: ATS7=60 S30=0 S0=0
ATS7=60 S30=0 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","general.t-mobile.uk"
AT+CGDCONT=1,"IP","general.t-mobile.uk"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Oct  6 17:05:29 2010
--> Pid of pppd: 3067
--> Using interface ppp0
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; 
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; 
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; 
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; 
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; 
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; 
--> local  IP address 10.195.10.186
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; 
--> remote IP address 10.64.64.64
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; 
--> primary   DNS address 149.254.192.126
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; 
--> secondary DNS address 149.254.201.126
--> pppd: 8[7f]&#65533; `{&#65533; (&#65533;&#65533; 8&#65533;&#65533; &#65533;|&#65533; [/I]

this is turning into a monologue...anyone out there who could help? :)

---

### Post by al.adab on 2010-10-06
To sum it up - particularly 'cause I haven't been successful: 

a) installed usb-modeswitch_1.1.4-1+i386.deb

b) installed usb-modeswitch-data_20100826-1_all.deb

c) run *lsusb* in terminal

d) identified dongle as ID 19d2:0031 *ONDA Communication S.p.A. ZTE MF636*

e) run in terminal *sudo leafpad /etc/usb_modenswitch.conf*
- set DisableSwitching=0
- set EnableLogging=1
- inserted the following lines: 

[I]##########
# ZTE MF636 19d2:0031
DefaultVendor= 0x19d2
Default Product= 0x0031
CheckSuccess=5
##########[/I]

f) run in terminal *sudo leafpad /etc/usb_modeswitch.setup*
- inserted the following lines: 

ZTE MF636
vendor=0x19d2
product=0x0031

g) run in terminal *sudo modprobe usbserial vendor=0x19d2 product=0x0031* + *ls /dev/ttyU** (obtained */dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2*)

h) run in terminal *sudo leafpad /etc/wvdial.conf*

i) inserted the following lines: 

[I][Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = ***
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","general.t-mobile.uk"
Phone = *99#
Stupid Mode = 1[/I]

j) run the NetWork Manager wizard - automatic settings

k) run in terminal *sudo rmmod usb-storage* (the dongle is recognised as a USB memory stick - or the like - in Utility Disk)

l) run in terminal *sudo wvdial*

m) got the following result (no connection established): 

[I]~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F &D2 &C1
AT&F &D2 &C1
OK
--> Sending: ATS7=60 S30=0 S0=0
ATS7=60 S30=0 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","general.t-mobile.uk"
AT+CGDCONT=1,"IP","general.t-mobile.uk"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Oct  6 23:09:02 2010
--> Pid of pppd: 1370
--> Using interface ppp0
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> local  IP address 10.195.5.197
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> remote IP address 10.64.64.64
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> primary   DNS address 149.254.192.126
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> secondary DNS address 149.254.201.126
--> pppd: 8[08]`&#65533;&#65533;[08](&#65533;&#65533;[08]8&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08][/I]

Does anyone know what's going on here? Am I doing something wrong? The connection seems to be initially successful, but then nothing comes out of it. 

Also one thing I can't understand is why the dongle is not "seen" as GPRS modem by NetworkManager and doesn't appear in my list of connections (above the wifi connections) like in Ubuntu 10.04. But this is probably not relevant...

I really hope there's a solution to this!

---

### Post by al.adab on 2010-10-06
a thought - before I hit the sack: 

why does it say (as I run *sudo wvdial*)

*--> Cannot get information for serial port.*

??? is this relevant? If it is, where can it get such info?

---

### Post by t0p on 2010-10-06
When you run wvdial, you get that output, then it appears to "freeze", right?

This is normal with wvdial.  So run wvdial, then when it "freezes", you should be connected to the internet.  Don't close the terminal, just minimize it, then try to browse via firefox: it should work.

If firefox doesn't work, then open a new terminal window (ie still don't close the first terminal window) and try this command:

```
ping -c 5 google.com
```What output do you get from the ping command?

**EDIT:** It may be worthwhile for you to check out the link in my sig, **How to use cellphone as modem**.  There is a lot in common between HSDPA modems and cellphones in this regard.  Also, you will find further info there specifically about HSDPA/3G modems.

---

### Post by al.adab on 2010-10-07
it looks like I forgot to verify whether the experiment fullfilled its aim or not :) 

you're right t0p: although it looks like it's "freezing", it's connected to the internet :) 

I'm copying & pasting the result of launching *ping -c 5 google.com* in terminal for the record: 

[I]~$ ping -c 5 google.com
PING google.com (173.194.37.104) 56(84) bytes of data.
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=1 ttl=54 time=1295 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=2 ttl=54 time=448 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=3 ttl=54 time=59.2 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=4 ttl=54 time=73.9 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=5 ttl=54 time=64.9 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 59.283/388.367/1295.615/477.155 ms, pipe 2
 [/I]

Supposedly, if I travelled abroad and used a local internet dongle, all I'd have to do is to update both the *usb_modeswitch.conf* and the *usb_modeswitch.setup* files as well as *wvdialconf wvdial.conf*?

---

### Post by GeorgeVita on 2010-10-10
Hi **al.adab**, it seems you are connected at [post#5]("http://ubuntuforums.org/showpost.php?p=9933017&postcount=5").
Network manager is not cooperating well with wvdial and cannot 'see' the  connection. Some times you have to 'stop' network manager and 'kill' modem manager for a stable connection ([with a ZTE MF636]("http://ubuntuforums.org/showpost.php?p=9232362&postcount=117")).

After connection (as described on post#5) check Firefox to be 'online' (ALT-F W).

Just send us the output of the terminal command: **uname -a**
to check kernel version of Lubuntu.

> **al.adab said:**
> Supposedly, if I travelled abroad and used a local internet dongle, all I'd have to do is to update both the *usb_modeswitch.conf* and the *usb_modeswitch.setup* files as well as *wvdialconf wvdial.conf*?
Just choose a Huawei modem! Most of them are 'plug in' compatible and follow instructions at 'mobile broadband connection' wizard.

Regards,
George

---

### Post by alexfish on 2010-10-10
Hi [B]al.adab and george

[/B]over the last two weeks** , **
[B]the servers based at ( 149.254.* 149.254.192.*) have been dropping out connections mainly 06am to approx 12 noon 

[/B]users [B]will have to disconnect and reconnect on regular basis
[/B]even if the primary and secondary servers are connecting they will at some stage time out[B](even at first attempts to use the browser)

local  IP address  does not look correct(depends on location)
[/B]one thing that can be  done to improve the initial connection is to edit the options file

Code:
[COLOR=Blue]sudo gedit /etc/ppp/options[/COLOR]

change the value of the  ipcp-max failure

to look like

[COLOR=Blue]ipcp-max-failure 30[/COLOR]

also add this to the file

[COLOR=Blue]ktune[/COLOR] 

this will allow ip forwarding 



alexfish

---

### Post by al.adab on 2010-10-12
thanks both - sorry for the belated reply, I'm travelling right now. 

here's the 

[I]~$ uname -a
Linux fiction 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linu[/I]x

btw I'm now having problems with a Nokia CS-10 dongle on Wind Italy...modem recognized but doesn't connect:

[I]...
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
ERROR
--> Invalid dial command.
--> Disconnecting at Tue Oct 12 21:34:44 2010
xxxxx@xxxxx:~$[/I] 

shall I open a new thread or can we consider this as related to the issue with the ZTE?

---

### Post by al.adab on 2010-10-12
issue with Nokia dongle on Wind Italy described at 
[http://ubuntuforums.org/showthread.php?t=1594869](http://ubuntuforums.org/showthread.php?t=1594869)
apologies for cross-posting

---

