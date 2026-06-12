---
title: "Keep losing wireless connection"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by fumoffu on 2007-08-05
Howdy, I just installed Ubuntu 7.04. However, I cant seem to keep a connection to my router. The connection stays for about 3 hours or at times 5 mins, then dies. The only way I've found to get it back is to reboot. I've looked at the forums for a solution, but can't seem to find one that works. This is the card im using Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

Any help would be appreciated

---

### Post by noob12 on 2007-08-05
Here are some things that would help diagnose the issue.

Post the output of each of these commands while the network is working
```

lspci -nn
lshw -C network
cat /etc/network/interfaces
ifconfig -a
iwconfig
iwlist scan

```

At some time when the network has *stopped* working grab the output of these and save them in files.  
```

ifconfig -a
iwconfig
iwlist scan

```
When you restore connectivity, post the files.

This might lead to more questions.

---

### Post by fumoffu on 2007-08-05
from when I was connected

---

### Post by fumoffu on 2007-08-06
disconnected

---

### Post by noob12 on 2007-08-06
Your offline.txt looks pretty close to online.

A couple of things.  Your alias for wifi0 is made wrong.  Not sure where you have that setup, but I'd remove that or if you really want to use that name, replace ath0 in your /etc/iftab.

Moving on, I think you'll have better success with NetworkManager if NM considers ath0 to be in "roaming mode".   The easiest way to do this is edit /etc/network/interfaces and **remove** these lines:
> 
iface ath0 inet dhcp
wireless-essid Sasser

auto ath0


You can also do this through the NM GUI by left-clicking the NM icon.  Select Manual Configuration, find the ath0 interface and set it to "Roaming Mode".   Close.   Once you do that, right-click on NetworkManager and Enable Wireless.  Then left click and you should see your signal bars.

---

### Post by fumoffu on 2007-08-06
> **noob12 said:**
> Your offline.txt looks pretty close to online.

A couple of things.  Your alias for wifi0 is made wrong.  Not sure where you have that setup, but I'd remove that or if you really want to use that name, replace ath0 in your /etc/iftab.

Moving on, I think you'll have better success with NetworkManager if NM considers ath0 to be in "roaming mode".   The easiest way to do this is edit /etc/network/interfaces and **remove** these lines:


You can also do this through the NM GUI by left-clicking the NM icon.  Select Manual Configuration, find the ath0 interface and set it to "Roaming Mode".   Close.   Once you do that, right-click on NetworkManager and Enable Wireless.  Then left click and you should see your signal bars.
Mmm, ok did that, but when I restarted I had no connection at all.
I'm not quite sure what you mean by wifi0 is made wrong...:(

---

### Post by noob12 on 2007-08-06
After doing this, when you right click on NetworkManager, do you see the Enable Wireless option?
Make sure it is checked, then left click and select your access point.

If this works, but you have to enable wireless each time manually when you start, check your BIOS settings for a setting that will turn the wireless on by default at boot.

If it doesn't work, please describe in detail what does happen and show me the **iwconfig** and **iwlist scan** again.  Also, can you show me the output of **cat /etc/iftab** and ```
grep wifi0 /etc/modprobe.d/* 
```.

---

### Post by fumoffu on 2007-08-06
> **noob12 said:**
> After doing this, when you right click on NetworkManager, do you see the Enable Wireless option?
Make sure it is checked, then left click and select your access point.

If this works, but you have to enable wireless each time manually when you start, check your BIOS settings for a setting that will turn the wireless on by default at boot.

If it doesn't work, please describe in detail what does happen and show me the **iwconfig** and **iwlist scan** again.  Also, can you show me the output of **cat /etc/iftab** and ```
grep wifi0 /etc/modprobe.d/* 
```.

Hm, ok, theres a problem with that, I have no Network Manager icon. At least in my panels. I can add the network monitor to the panel. Though, It doesn't have an Enable wireless option. 

Lol, I'm sorry for being so difficult.
```
iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Sasser"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:39:7A:06   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/94  Signal level=-60 dBm  Noise level=-95 dBm
          Rx invalid nwid:35170  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```
```
iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:14:BF:39:7A:06
                    ESSID:"Sasser"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/94  Signal level=-61 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:13:10:F1:94:E4
                    ESSID:"millertime"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/94  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:18:39:71:FF:F3
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/94  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:14:BF:38:84:BA
                    ESSID:"linksys_SES_10060"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/94  Signal level=-76 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 05 - Address: 00:18:F8:DF:41:58
                    ESSID:"pdsomh"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00

eth0      Interface doesn't support scanning.
```

```
cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

ath0 mac 00:16:e3:28:11:b3 arp 1
eth0 mac 00:a0:d1:3d:a7:30 arp 1
```

it didn't give me anything for ```
grep wifi0 /etc/modprobe.d/*
```

---

### Post by noob12 on 2007-08-07
OK.  I suggest editing your /etc/iftab and replacing the **ath0** with **wifi0** so that first line looks like
```

wifi0 mac 00:16:e3:28:11:b3 arp 1

```

Also, please show me the output of these two commands.  You can do this before or after you reboot.
```

aptitude show network-manager network-manager-gnome knetworkmanager | grep State

ps -ef | grep NetworkManager

```

After you reboot, I'm expecting **ath0** to go away and **wifi0** to look normal.  Can you show me the result of ```
ifconfig -a
``` done **after the reboot.**

---

### Post by noob12 on 2007-08-07
I can explain the rationale once we've confirmed some of these things.

---

### Post by fumoffu on 2007-08-07
Will do   :)

---

### Post by noob12 on 2007-08-07
OK.  You are running NetworkManager, which is what I suspected.

My suggested change to /etc/iftab didn't have the intended effect, and the wifi0 alias being shown in the earlier ifconfig is apparently common. You should revert the change in /etc/iftab so that
the interface is named **ath0** again.

In /etc/network/interfaces remove or comment out the lines for ath0 if you haven't already. 
This is equivalent to enabling "Roaming Mode" on ath0.  NetworkManager will not
deal with it if it is mentioned in /etc/network/interfaces.

Add one line
```

iface wifi0 inet manual

```
This is to keep NetworkManager from trying to do anything with that alias.  The conjecture is that your connection is breaking periodically because NetworkManager thinks it is managing something about wifi0.

Reboot.

```

ps -ef | grep nm-applet

```
If this shows **nm-applet --sm-disable**, nm-applet should be running in your panel.

If you do not see it, then ALT+F2 and type **nm-applet --sm-disable** and Enter.  If you had to do this,  let me know because we will want to add it to your session startup list.

Find the little dual-computer NetworkManager icon in the upper right panel.  This is where it
would appear if you have the standard layout.   Note that NetworkManager is not the same as the Network Monitor that you mentioned in the previous note; the icons are very similar.  

**Right click** on the NetworkManager icon and you should see Enable Wireless.  If it is present, make sure it is checked.   Once it is checked, if you left-click on the same NetworkManager icon, you should get a list of nearby signals.  Check the one corresponding to your AP ("Sasser").  Since there is no encryption key set on this AP, you should connect without any prompts.

If this doesn't work for you, let me know.  We'll back down to your manual configuration.

---

### Post by fumoffu on 2007-08-07
Ok it all seems to check out, until i get to the icon part. I don't seem to have an icon for the network manager. Is there a way to enable wireless without the use of the icon? If not, I need to find a way to get the icon back. 

I appreciate you helping me out :)

---

### Post by ugm6hr on 2007-08-07
@fumoffu:
Worth reading this: [http://ubuntuforums.org/showpost.php?p=2924402&postcount=3](http://ubuntuforums.org/showpost.php?p=2924402&postcount=3)
Has links to launchpad reports on similar issues.

I have the same chipset, and use Wicd now (see my signature link).

---

### Post by fumoffu on 2007-08-07
Hmm, I tried wicd earlier, but it didn't seem to remedy anything. Though, it's a lot nicer than NM. I'll take a look at that link. thanks ugm6hr :)

---

### Post by noob12 on 2007-08-07
Not ignoring the ugm6hr's advice.  You might want to follow that.

To proceed with NetworkManager if you want to try.  After either starting nm-applet using the ALT+F2 or seeing it running already, you should see the icon in the top right panel, to the left of your power button (in the default layout).

Attached a screenshot.

---

### Post by fumoffu on 2007-08-07
Mm, no its not there. I think its because I had to uninstall and reinstall NM after trying wicd earlier. I'm clueless as to how to get it back.

---

### Post by noob12 on 2007-08-07
OK.  Haven't seen that one before.  We'd have to figure out what's broken with nm-applet and the notification area before proceeding along this route. 

Time to examine the forks in the road:  If you want to configure manually we can do that, or if you want to continue to pursue the NM route we could do that, or you might want to try wicd again following the instructions in ugm6hr's link this time.

---

### Post by fumoffu on 2007-08-07
Hm ok, well, I'm willing to pursue with NM.

 Ok I was able to get the icon back, so I went ahead and checked the enable wireless option.

---

### Post by noob12 on 2007-08-08
Did you get signal bars when you left click on the NM icon now?

---

### Post by fumoffu on 2007-08-08
No, unfortunately :(

---

### Post by noob12 on 2007-08-08
Was this how it was before you tried the wicd install?

---

### Post by noob12 on 2007-08-08
Can you show me an iwconfig and iwlist scan now?

---

### Post by fumoffu on 2007-08-08
No, it wasn't in roaming mode, and there was no enable wireless option.

---

### Post by fumoffu on 2007-08-08
Results

---

### Post by fumoffu on 2007-08-11
Still loses the connection after 30 mins. :(

---

### Post by fumoffu on 2007-08-14
bump

---

### Post by tiny4579 on 2007-08-24
My connection drops a lot as well and I get the following from iwconfig:

ath1      IEEE 802.11g  ESSID:"barties"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:9A:21:9B:75   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=19/94  Signal level=-77 dBm  Noise level=-96 dBm
          Rx invalid nwid:5139  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Not sure why ath1 though.

---

### Post by tiny4579 on 2007-08-24
I have attached some output for diagnosis.

---

