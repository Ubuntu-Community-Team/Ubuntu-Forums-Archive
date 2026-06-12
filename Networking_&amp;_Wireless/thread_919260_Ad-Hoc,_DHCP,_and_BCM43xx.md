---
title: "Ad-Hoc, DHCP, and BCM43xx"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by AndrewZorn on 2008-09-13
I have Hardy 64, a Broadcom wireless g card, and the default BCM43xx driver, which I understand now supports ad-hoc.

I'm trying to connect to my phone's wireless via WMWifiRouter, a program which creates an ad-hoc access point.

I have tried so many combinations of commands to get this to work.  I had it working earlier and had a script for it, but formatted and lost this information.  I got it work once tonight, but could not replicate it.  Here are some commands I'm using, completely not understanding the order/necessity:
```

sudo ifconfig wlan0 0.0.0.0 down
sudo ifconfig wlan0 up
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/25NetworkManager start
sudo dhclient -r wlan0
sudo dhclient wlan0
sudo iwconfig wlan0 essid 'WMWifiRouter'
sudo iwconfig wlan0 mode ad-hoc
```

DHClient king of just keeps searching and not finding anything.  Do I need NetworkManager if I'm manually defining everything?  What's the 0.0.0.0 for, I KNOW I didn't need that last time, but it won't go 'down' otherwise.  Do you end the NetworkManager first, and bring it back up last?  Because it 'interrupts' me...

When it worked, DHClient did find something and connect to it.

---

### Post by lswb on 2008-09-13
I've found NetworkManager generally to be an impediment to creating an ad-hoc network though IIRC it will connect to one that is already running. I temporarily stop network manager when creating an ad-hoc network on my laptop. Also, I've seen docs that state some drivers will reset other parameters to defaults with a mode change, and may require that a channel be specified when creating an ad-hoc network. 

I wrote a couple scripts that I placed in /usr/local/sbin so they would be in my path. They are run using sudo, with the argument "start" or "stop". self-explanatory and mimics the usual /etc/init.d script arguments. My wireless interface is eth1, substitute wlan0 or whatever as required.

First, a quick way to shut down or restart network manager

 /usr/local/sbin/netman
```

#!/bin/bash

[ "0" != "$UID" ] && ( echo "Must run as root!" ) && exit

/etc/dbus-1/event.d/25NetworkManager $@
/etc/dbus-1/event.d/26NetworkManagerDispatcher $@

```

And to start or stop the adhoc network:

/etc/local/sbin/adhoc 
```


#!/bin/bash

[ "0" != "$UID" ] && ( echo "Must run as root!" ) && exit

case $1 in

start)
/usr/local/sbin/netman stop
ifconfig eth1 down
iwconfig eth1 mode ad-hoc essid "$( cat /etc/hostname )" channel 6 
ifconfig eth1 up
avahi-autoipd --daemonize eth1 
;;


stop)
avahi-autoipd --kill eth1
ifconfig eth1 down
/usr/local/sbin/netman start
;;

*)
echo "
Usage: adhoc start|stop
Start or stop a wireless ad-hoc network. Uses /etc/hostname to set ESSID.
"
;;
esac


```

I usually just let avahi do it's link-local thing to set up ip addresses in the 169.254.x.x range. If you needed to you could install dhcp3-server from the ubuntu repositories so that the laptop could give out different ip addresses.

Maybe I'm misunderstanding though. does the phone create the ad-hoc net and you only want to join it with the laptop? If that's the case run the command:

sudo iwlist wlan0 scanning

In the output of this command you should see the essid and other info about the ad-hoc network (or any other wireless networks in range)

then try this sequence of commands:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode ad-hoc essid "YourNameHere" 
sudo ifconfig wlan0 up
sudo dhclient wlan0

You can try adding "channel X" to the iwconfig line, substituting the channel number that iwlist reported for "X", but I think the channel is not necessary to join a running ad-hoc network.

If they work put them in a script. If not post back with the errors. Good luck!

---

### Post by AndrewZorn on 2008-09-13
First off, thanks for the reply.

I am trying to connect to the network created by the phone.

This
> sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode ad-hoc essid "YourNameHere"
sudo ifconfig wlan0 up
sudo dhclient wlan0
is basically what I've been trying the whole time, with little to no success.  With and without networkmanager.

I just found this:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Did it, and now the above method seems to work... sometimes.  I wrote an alias (for now) that basically sets the mode over and over again with 1 second delays in between, then the essid over and over again with delay, then the mode again, etc... it works.  But if I script just the actual steps, even repeated, it doesn't work.  It's like it takes time and repeated attempts to get it.

Here it is:
> alias wmwifirouter='sudo /etc/dbus-1/event.d/25NetworkManager stop;sleep 1;sudo ifconfig eth1 down;sleep 1;sudo iwconfig eth1 mode ad-hoc;sleep 1;sudo iwconfig eth1;sudo iwconfig eth1 mode ad-hoc;sleep 1;sudo iwconfig eth1;sudo iwconfig eth1 mode ad-hoc;sleep 1;sudo iwconfig eth1 essid "WMWifiRouter";sudo sleep 1;sudo iwconfig eth1;sudo iwconfig eth1 essid "WMWifiRouter";sleep 1;sudo iwconfig eth1;sudo iwconfig eth1 mode ad-hoc;sleep 1;sudo iwconfig eth1 mode ad-hoc;sleep 1;sudo iwconfigh eth1;sudo iwconfig eth1 essid "WMWifiRouter";sleep 1;sudo iwconfig eth1;sudo iwconfig eth1;sudo ifconfig eth1 up;sudo dhclient eth1;'

I'm about to go through it and find out what I can start reducing, but that's really what it takes to work.  Look at the start of the output:
```
andrew@lappy:~$ wmwifirouter
 * Stopping network connection manager NetworkManager                    [ OK ] 
eth1      IEEE 802.11abg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-17 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11abg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-17 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.22 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-17 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11a  ESSID:"WMWifiRouter"  Nickname:""
          Mode:Ad-Hoc  Frequency:5.22 GHz  Cell: 02:18:41:7B:09:06   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-52 dBm  Noise level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
This time it took FOUR times... I don't get it!

EDIT or maybe it's just timing... if I put in just a single command for both mode and essid and a longer sleep before the DHClient, it seems to be working more reliably.  But it could just be chance.

---

### Post by Ayuthia on 2008-09-13
> **AndrewZorn said:**
> First off, thanks for the reply.

I am trying to connect to the network created by the phone.

This

is basically what I've been trying the whole time, with little to no success.  With and without networkmanager.

I just found this:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Did it, and now the above method seems to work... sometimes.  I wrote an alias (for now) that basically sets the mode over and over again with 1 second delays in between, then the essid over and over again with delay, then the mode again, etc... it works.  But if I script just the actual steps, even repeated, it doesn't work.  It's like it takes time and repeated attempts to get it.

Here it is:


I'm about to go through it and find out what I can start reducing, but that's really what it takes to work.  Look at the start of the output:
```
andrew@lappy:~$ wmwifirouter
 * Stopping network connection manager NetworkManager                    [ OK ] 
eth1      IEEE 802.11abg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-17 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11abg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-17 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Frequency:5.22 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-17 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      IEEE 802.11a  ESSID:"WMWifiRouter"  Nickname:""
          Mode:Ad-Hoc  Frequency:5.22 GHz  Cell: 02:18:41:7B:09:06   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-52 dBm  Noise level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
This time it took FOUR times... I don't get it!

From what I can see, it took on the fourth one because that is when you assigned it an essid.  The first three times, you just switched to ad-hoc.  I would think that the following would work:
```
sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo ifconfig eth1 down
sudo iwconfig eth1 mode ad-hoc
sudo iwconfig eth1 essid "WMWifiRouter"
sudo iwconfig eth1
sudo ifconfig eth1 up
sudo dhclient eth1
```

---

### Post by AndrewZorn on 2008-09-13
I thought breaking up the commands would be better.  Maybe not...

This seems to work:

alias wmwr='sudo /etc/dbus-1/event.d/25NetworkManager stop;sudo ifconfig eth1 down;sudo iwconfig eth1 mode ad-hoc essid "WMWifiRouter";sleep 3;sudo iwconfig eth1;sudo ifconfig eth1 up;sudo dhclient eth1;'

I'm going to try reducing that delay, but I think it's necessary.  I feel like I'm setting it, but it takes time to take effect, and running the DHCP before that's done messes it all up.

When returning to Managed, I'm getting some kernel panics... EDIT typos.

The more I reduce, it still works.  **If I take out the delay before DHCP, then it fails on the first couple 'requests' and gets it on 2 or 3.**  So I guess that's just a rushing type thing.

Now it seems like I don't even have to disable NetworkManager, though I'm not sure if I should.  It gets confused going back and forth like this and I still have to manually go back and click the network if I keep it up.  If I shut it down, after starting back up it just sits there for 30seconds or so until it finally 'sees' all the wireless networks and gets back on one.  Which is strange, this is longer than it takes at startup (which is quite quick).

Here they are:
```
alias wmwr='sudo /etc/dbus-1/event.d/25NetworkManager stop;sudo ifconfig eth1 down;sudo iwconfig eth1 mode ad-hoc essid "WMWifiRouter";sleep 3;sudo iwconfig eth1;sudo ifconfig eth1 up;sudo dhclient eth1'

alias wmwr2='sudo /etc/dbus-1/event.d/25NetworkManager stop;sudo ifconfig eth1 down;sudo iwconfig eth1 mode ad-hoc essid "WMWifiRouter";sudo iwconfig eth1;sudo ifconfig eth1 up;sudo dhclient eth1'

alias wmwr3='sudo ifconfig eth1 down;sudo iwconfig eth1 mode ad-hoc essid "WMWifiRouter";sudo iwconfig eth1;sudo ifconfig eth1 up;sudo dhclient eth1'

alias mangd='sudo ifconfig eth1 down;sudo iwconfig eth1 mode managed;sleep 3;sudo ifconfig eth1 up;sleep 3;sudo /etc/dbus-1/event.d/25NetworkManager start;sudo iwconfig eth1;sudo ifconfig eth1 up'

alias mangd2='sudo ifconfig eth1 down;sudo iwconfig eth1 mode managed;sudo /etc/dbus-1/event.d/25NetworkManager start;sudo ifconfig eth1 up;sudo iwconfig eth1'

alias mangd3='sudo ifconfig eth1 down;sudo iwconfig eth1 mode managed;sudo ifconfig eth1 up;sudo iwconfig eth1'
```
wmwr switches to WMWifiRouter/ad-hoc.  3 is the quickest but looks like the least likely to work, with the original working every time I think.
mangd goes back to managed mode.  Just like before, the first one seems to work every time, despite being the slowest.  I don't want to have to end NetworkManager every single time because it takes so long to re-find the wireless networks, but it seems to be the only reliable way.

EDIT and now the #3s seem to be working all the time.  I don't know what to trust, and might end up keeping all six, as stupid as it sounds.  Just during testing all this I haven't changed anything, sometimes I can get away with the faster 3, sometimes I cannot.

**Also, do you do eth1 up before or after starting NetworkManager, if I decide to try to keep it up?** It doesn't seem to give me trouble whenever #3s work.
It reports totally wrong info and all when on WMWifiRouter, and you have to re-connect to a certain network once you're back on managed (not even sure if it's getting the new list of networks, really... **ok now I'm getting paranoid about this, and all the trouble it may cause... but when I close/reopen NetworkManager, it takes SOOO LONG to return to the same state it gets to about 5seconds after boot!  EDIT I guess this is why you give the iwlist command (scan=scanning?)**) but otherwise SEEMS fine.

The new driver seems to be getting me WAAAAY further though.  I've had 'free' wireless internet since I got the laptop, and because of my Linux ignorance, it's rarely/barely worked.

EDIT the '3' aliases have been working many times over now.  I'm keeping ALL of them at least until I verify this in actual practice, because every time I mess with this stuff, it's never as smooth the next day.

Thank you SO MUCH, both of you!

EDIT final versions, seem to be working (I know it was what was suggested/makes sense, but I promise this was not working this well earlier.  Could have been problems with WMWifi though):
```
alias wmwifi='sudo ifconfig eth1 down;sudo iwconfig eth1 mode ad-hoc essid "WMWifiRouter";sudo ifconfig eth1 up;sudo dhclient eth1'
alias managed='sudo ifconfig eth1 down;sudo iwconfig eth1 mode managed;sudo ifconfig eth1 up;sudo iwlist eth1 scanning'
```
Should I somehow make wmwifi disconnect first, so that networkmanager shows it as disconnected?
I didn't try staying on too long.  If networkmanager starts messing with the WMWifiRouter, then I'm going to just kill it when going wmwifi and resurrect with managed.

EDIT or maybe it was 'working' the whole time.  Usually it will connect to the phone in a try or two and 5secs tops.  Others, it can take ridiculously long:
```
andrew@lappy:~$ wmwifi
There is already a pid file /var/run/dhclient.pid with pid 9840
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:1e:4c:ab:f6:74
Sending on   LPF/eth1/00:1e:4c:ab:f6:74
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.153 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.153 on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.0.153 from 192.168.0.1
DHCPREQUEST of 192.168.0.153 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.153 on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.153 from 192.168.0.1
DHCPREQUEST of 192.168.0.153 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.153 on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPOFFER of 192.168.0.153 from 192.168.0.1
DHCPREQUEST of 192.168.0.153 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.153 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.0.153 from 192.168.0.1
bound to 192.168.0.153 -- renewal in 122258 seconds.
andrew@lappy:~$ 
```
WOW!

---

