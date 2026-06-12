---
title: "Strange wireless problem"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by SteinbergerNate on 2007-01-06
Just upgraded (clean install) to Edgy. I'm trying to connect to a wireless network. when I do iwlist, it shows the network I'm trying to get to but the configuration program doesn't show anything. I didn't have this problem in Dapper and I can't quite get iwconfig to connect to this access point. Here's the output of iwlist:
```
eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:C2:81:DA
                    ESSID:"REYNOLDS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-40 dBm  
                    Extra: Last beacon: 100ms ago

```

---

### Post by SteinbergerNate on 2007-01-13
Bump. To further explain the fact that I couldn't get iwconfig to completely connect in dapper (and now not at all in edgy) I would run iwconfig first and then the network tool on ubuntu. I had this all in a script. I think the reason I can't get iwconfig to work completely is because I don't think I really know how to use iwconfig. 

BTW, I couldn't get wireless to connect on just the network tool either.

---

### Post by phossal on 2007-01-13
Most people would recommend disabling wep/wpa on your router until you have made a connection. I personally recommend avoiding the GUI configuration tools until you're connected.

If your hardware is properly recognized - using the correct driver - connection should be this simple (with wep/wpa disabled):

```

sudo iwconfig wlan0 essid <essid> channel <channel>
sudo dhclient wlan0
```

You will replace wlan0 with the correct interface, replace <essid> with your router essid (no brackets), and <channel> with your router channel (no brackets).

Definitely check out the commands: iwconfig, and dhclient.

---

### Post by SteinbergerNate on 2007-01-13
Well, I would disable wep on the router but it's not mine. My father is graciously letting me connect with his wep key. I'm gonna try what you just posted real quick.

---

### Post by SteinbergerNate on 2007-01-13
Ok, I tried it. After running iwconfig to get it connected, I run iwconfig just to see what it's done and I get this:
```
eth1      unassociated  ESSID:"REYNOLDS"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

What's is going on here?

---

### Post by phossal on 2007-01-13
If you can't disable wep/wpa, you need to add the *key* parameter to the command:

```
sudo iwconfig wlan0 essid <e> channel <c> key <k 26-digit or 10-digit or whatever>
sudo dhclient
```

---

### Post by SteinbergerNate on 2007-01-13
Let me just post the command I'm using to try to connect. 
```
sudo iwconfig eth1 essid reynolds key restricted XXXXXX
```

---

### Post by phossal on 2007-01-13
Here are the commands I use verbatim:

```
sudo iwconfig wlan0 essid MYNET channel 7 key 7234265487
sudo dhclient wlan0
```

Is there any output when you issue the iwconfig command? Any error message?
Is there any output when you issue the dhclient command? Sleeping?

---

### Post by SteinbergerNate on 2007-01-13
No output or errors when I run iwconfig. I get sleeping after many attempts on dhclient. I also tried formatting my iwconfig syntax like yours with the channel and all but still no go. In dapper, I had to run the following script:
```
sudo iwconfig eth1 essid reynolds key restricted xxxxxxxxxxxxx
gksu network-admin
```

Once network-admin was up, I would then select the correct network and all would be good.

---

### Post by phossal on 2007-01-13
Ugh, sorry. I can't go any further because I don't know enough about your hardware. I've already been down a road like this with my own and, after all, it's Saturday night. ;) 

Sorry. Good luck.

[edit] I'm in over my head here. I can't even make another guess.

---

### Post by SteinbergerNate on 2007-01-13
Ok. Thanks for your help.

---

### Post by SteinbergerNate on 2007-01-13
Ok, I got it working. It appears that the solution was simpler that I originally thought.  I went into Synaptic and installed the netapplet package. I ran that and told it to disconnect. Then I went in and manually told it to connect to my ap with key. Works perfectly fine now.

---

