---
title: "Network Connect - /opt/wicd/tray.py shows no network"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-09-15
Ive been screwing around with my kernel and wireless tools so likely this is the reason.  WICDs tray.py does not show any networks, allthough I currently am connected (as I am writing the letter).  

Im getting the following errors when starting /opt/wicd/tray.py:
kevin@Homer:~$ attempting to connect daemon...
success
attempting to connect daemon...
success
starting gui.py...
refreshing...
0
Traceback (most recent call last):
  File "./gui.py", line 1146, in update_statusbar
    strength = wireless.GetCurrentSignalStrength()
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Python.TypeError: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 451, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/opt/wicd/daemon.py", line 585, in GetCurrentSignalStrength
    strength = int(self.wifi.GetSignalStrength())
TypeError: int() argument must be a string or a number, not 'NoneType'

My iwlist executable is now located in /usr/local/sbin rather than /sbin.  Im not sure if this is the reason for the failure.  Using /usr/local/sbin/iwlist wlan0 scan clearly brings up my one wireless network.

Any ideas, nothing is in the wicd.log file that suggests a problem.

---

### Post by imdano on 2007-09-15
I'd guess it's because iwlist got moved, so wicd isn't retrieving any wireless information.  Did you add /usr/local/sbin to your path?

---

### Post by kevdog on 2007-09-15
Its in my path

```
kevin@Homer:~/bin$ echo $PATH
/home/kevin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```

However does wicd use the same path variable??

Anyway, I just copied the executables to the /sbin directory.  I hate doing sloppy work-arounds such as this, but sometimes its necessary.


Just my opinion, but the tray.py program is kind of buggy.  Ive had problems with this a few times, and now when the program is minimized the icon still states connecting rather than giving a bar graph.  The daemon program on the other hand has been rock solid!!

---

### Post by imdano on 2007-09-15
Wicd just uses your system's path variable, so I'm not really sure what was going on there.  

As for the tray problem, what version are you running?  When exactly does the icon no correctly display the connectoin status?  Is it reproducable or somewhat random?

---

### Post by kevdog on 2007-09-15
Where is my system's path variable -- or how do I know what this is??

The bugs are kind of not reproducible -- I know that is exactly what you didnt want to hear.  But this is what is happening right now

I manually tray.py at the command line.  The detected networks are shown (at most for me there are two).  I dont select any of the networks b/c Im already connected, and this is confirmed at the bottom of the gui.

I hit the close button to minimize the application to the tray.  Within the tray I get the two computer icons which then state "initializing the connection".  I have conky running on the side monitoring my network status.  I then see my local connection dropped and it stays dropped until I manuallly Cntl-c to kill the tray application.  Within about 10 seconds, I can see in conky my local area connection is once again restablished.  

Here is what I get at the command line:
kevin@Homer:/etc/ndiswrapper$ /opt/wicd/tray.py --version
attempting to connect daemon...
success
attempting to connect daemon...
success
starting gui.py...
refreshing...
2
using global dns: 0
ESSID : GoHilton.com
making a new network entry...
disabling ip
disabling dns
dns checkbox toggled False
0
using global dns: 0
ESSID : default
making a new network entry...
disabling ip
disabling dns
dns checkbox toggled False
0
Traceback (most recent call last):
  File "/opt/wicd/edgy.py", line 161, in update_tray_icon
    self.check_for_wireless_connection(wireless_ip)
  File "/opt/wicd/edgy.py", line 142, in check_for_wireless_connection
    self.set_signal_image(wireless_signal, lock)
  File "/opt/wicd/edgy.py", line 185, in set_signal_image
    self.auto_reconnect()
  File "/opt/wicd/edgy.py", line 209, in auto_reconnect
    daemon.AutoConnect(True)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
KeyboardInterrupt

I hope some of this helps.

---

### Post by imdano on 2007-09-15
Wicd isn't realizing that you're connected for some reason, since it's running daemon.AutoReconnect(), which only happens if your connection is lost.  Did this problem only start after you starting messing with wireless-tools?  Whats the output of iwconfig and iwlist scan?

---

### Post by kevdog on 2007-09-15
It either happened after I went to the latest generic kernel or the wireless tools -- I can be sure of that -- Im sure its something I broke, but Im not exactly sure what I would have done to cause it.

Here are the following:
kevin@Homer:/etc$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"GoHilton.com"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:10:8E:94:E9   
          Bit Rate=110 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan
kevin@Homer:/etc$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:8E:94:E9
                    ESSID:"GoHilton.com"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=1000
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

After I updated the kernel I didnt reinstall wicd.  Should I do that?  Im running an experimental version of WICD from your repository.  I installed it proabably about 2 weeks ago.  Is there anyway to know the exact version??? I see the current revision is 110.

---

