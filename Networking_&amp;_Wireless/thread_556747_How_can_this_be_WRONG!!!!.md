---
title: "How can this be WRONG!!!!"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by Anaphylaxis on 2007-09-21
I am following this tutorial on a FRESH (2h ago) install of Xubuntu. I am typing the EXACT same commands, and my wifi card uses the rt61 drivers in windows. Then how come others can get it working and I can't? Am I haunted or anything?

This is the tutorial.
[HOWTO RT61 on Feisty Fawn]("http://ubuntuforums.org/showthread.php?t=419709&highlight=rt61+wpa")

These are the commands I am typing:
> me@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

me@ubuntu:~$ sudo ifconfig ra0 down
Password:
me@ubuntu:~$ sudo iwconfig ra0 essid transporter
me@ubuntu:~$ sudo iwpriv ra0 set AuthMode=WPAPSK
me@ubuntu:~$ sudo iwpriv ra0 set EncrypType=TKIP
me@ubuntu:~$ sudo iwpriv ra0 set WPAPSK=I insert my code here
me@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:"transporter"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

me@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning : Network is down

me@ubuntu:~$ 


And the net works, as I am able to connect to the wpa net with my Palm tx. Just f*** great. As I mostly use my comp for surfing, how can ubuntu be n00b-friendly when I can't get my focking net up??? Grrrrrr

---

### Post by tgalati4 on 2007-09-21
Open key versus restriced key perhaps?

>sudo iwconfig ra0 key open

---

### Post by kevdog on 2007-09-21
Where is your sudo ifconfig ra0 up statement??  Gotta bring interface up sometime or its never going to workl.

---

