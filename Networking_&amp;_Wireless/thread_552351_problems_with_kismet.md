---
title: "problems with kismet"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by javierccs on 2007-09-16
hello,


this is my first post so please be gentle...


i have been following the ubuntu forums to make kismet work for me

[http://ubuntuforums.org/showthread.php?t=230393&page=2](http://ubuntuforums.org/showthread.php?t=230393&page=2)


but when i finally got it running i got a weird message:
```
sudo iwconfig
eth0      IEEE 802.11g  ESSID:"TUXNET"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:D3:7F:B1:69
          Bit Rate:54 Mb/s   Tx-Power:14 dBm

          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:8375-54C6-6113-B465-666A-1692-8440-E4FD   Security mode:open
          Power Management:off
          Link Quality=76/100  Signal level=-57 dBm  Noise level=-58 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:702   Missed beacon:0

```

heres my .conf file:

```
# User to setid to (should be your normal user)
suiduser=javier

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,eth0,ethernet

```

im using my ibm t60 centrino duo laptop so i though the source should be ipw3945, but when i run sudo kismet, like i said i got a creepy sound and a really weird screen on my konsole:



Didn't detect any Cisco Discovery Packets, unlinking cisco dump&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                &#9474;&#9474;      0 &#9474;
&#9474;                          &#9474; Kismet-Client 2006.04.R1 build 20050815211952                Didn't see any weak encryption packets, unlinking weak file  &#9474;                                                                    &#9474;                &#9474;&#9474;      0 &#9474;
&#9474;                        WARNING: Sometimes cards don't always come out of monitor mode         &#9474;                &#9474;&#9474;        &#9474;
&#9474;                          &#9474; Context help is available for all displays, press 'h' at a         cleanly.  If your card is not fully working, you may need to more information.                                              &#9474;                &#9474;&#9474;        &#9474;
&#9474;                          &#9474;             restart or reconfigure it for normal operation.        &#9474;                &#9474;&#9474;        &#9474;
&#9474;                          &#9474; This message can be turned off by editing the kismet_ui.conKismet exiting.          &#9474;&#9474;        &#9474;
&#9474;                          &#9474;                                                                    &#9474;                &#9474;&#9474;        &#9474;
&#9474;                          &#9474; Press <Space> to continue.




then my wlan stops working and i have to get out of the screen, my wlan starts working after a minute or 2, now should i change the source?, is it able to geti it working with the card i have?

---

### Post by javierccs on 2007-09-16
btw

i installed kismet via synaptic package manager:(

---

