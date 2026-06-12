---
title: "Connecting to Wireless Networks"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by Miss Brightside on 2008-03-03
Hi, i'm new at Linux, just like a month ago i installed Ubuntu 7.10, the laptop has a intel/pro wireless 2200BG. The driver wasn't installed during the installation but a friend managed to help me to make it work.

Now the problem is that the laptop doesn't detect any wireless networks. It only detects them when you first connect it to a wire network. After connected it, then it detects wireless networks when i click on the network icon in the task bar on the top.

Does anyone know how to detect the wireless networks? Thanks!

---

### Post by lswest on 2008-03-03
are the wireless networks found if you run ```
iwlist scan
``` in the terminal?  if so, then the problem is with nm-applet, and you can always replace it with wicd or kwifimanager, or any other network manager.  Check with the command first, if it doesn't pick up on any networks i'll go back to the drawing board :P

---

### Post by Miss Brightside on 2008-03-03
i got this 
```
pam@bumblebee:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

pam@bumblebee:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


```
Just wondering, is it possible that the wireless device isn't working again?
I followed this tutorial: [http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu)
but now when i tried it again, gives me the error of `/usr/src/linux-headers-2.6.22-14-generic''

---

### Post by lswest on 2008-03-03
Well the results definately show that the device is not scanning wireless networks, meaning that there probably is something wrong with the driver, or it's not initialized correctly.  Maybe someone else can help you set it up, i've never had the joy of linux drivers for any wireless card i've had, so i could compile it, and walk you through it, but i couldn't trouble-shoot anything, and so i'm probably not the best person to help you with it.  Hope someone can help you out more.

---

### Post by Miss Brightside on 2008-03-03
thanks for trying to help :)

---

### Post by lswest on 2008-03-03
no problem, wish i could have helped more.  Good luck with getting it working.

---

### Post by Front187 on 2008-03-03
That "Radio Off" in eth1 means that your wireless card is set not to scan for wireless networks.

I'm not sure how to turn this on through linux, but I'm looking around.

---

### Post by lswest on 2008-03-03
Oh, hey, i didn't even notice that XD Ummm, this may seem simple, but is your wireless on? (there should be a dedicated switch or an fn+f[1-12] key combination to toggle it on/off) and was the card on while you installed the driver?  Both times?

---

### Post by Miss Brightside on 2008-03-03
oh, god, you are right!
Maybe it confused me that the wireless' light button doesn't turn on when i press it or not.
I pressed the button and now it started working!

Thank you!

```

pam@bumblebee:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

rtap0     no wireless extensions.


```

```

pam@bumblebee:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:88:62:9F:59
                    ESSID:"2WIRE819"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              22 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-79 dBm  
                    Extra: Last beacon: 680ms ago
          Cell 02 - Address: 00:14:A5:85:92:33
                    ESSID:"Motorola"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=37/100  Signal level=-78 dBm  
                    Extra: Last beacon: 72ms ago

rtap0     Interface doesn't support scanning.


```

---

### Post by Miss Brightside on 2008-03-03
By the way, is any way to disable the network manager by default and set the kwifimanager? kwifimanager seems more easy to use.

---

### Post by lswest on 2008-03-03
yeah, if you go to system-->preferences-->session and uncheck "network manager" it disables it, and then you can add an item for kwifimanager (new, app name: kwifimanager, command: kwifimanager) ^^ otherwise you can ```
sudo apt-get remove nm-applet
``` which i don't think is really necessary, because i'm not sure of what other packages that would uninstall, and besides, one day, you might need it :P

P.S. glad i was able to help^^

---

