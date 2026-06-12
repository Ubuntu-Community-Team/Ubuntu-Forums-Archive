---
title: "Aircrack with Hawking HWUG1"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by wushuFreak on 2007-06-02
I am an information assurance student and I am attempting to experiment with aircrack. I purchased the Hawking HWUG1 USB adapter because the Aircrack site stated the chipset was supported (and it was inexpensive)

I tried mounting it in my laptop (Dell Inspiron 1501) which already has a working card (but does not support signal level reporting) and when the Hawking is plugged in, the laptop completely freezes.

I tried mounting on a desktop as well. The Hawking was initially recognized, but only detecting 2 networks and does not support monitoring with native drivers. there are drivers recommended, but I think there may be a conflict with a native driver in Ubuntu. 

I live in an apartment complex and am surrounded by at least 15 APs at close range. 

I am running a fully updated Feisty on the laptop and desktop. 

If anyone has any advice or experience with this adapter or Aircrack-ng, I would appreciate your input.

BTW what I am doing is purely academic!

Thanks!

---

### Post by wushuFreak on 2007-06-03
bump

---

### Post by tturrisi on 2007-06-03
> I tried mounting it in my laptop (Dell Inspiron 1501) which already has a working card (but does not support signal level reporting)
what adapter? chipset?

---

### Post by wushuFreak on 2007-06-03
The Hawking HWUG1 adapter has the Ralink chipset. This adapter is listed on the Aircrack-ng site as supported by Linux and the chipset supports packet injection. I am having trouble finding any further documentation. 

There are other drivers listed on the website listed [here]("http://www.aircrack-ng.org/doku.php?id=install_drivers"). I downloaded and installed the rt2570 which is the correct one (I am almost certain). However, I am not sure if there is a native driver I should be blacklisting.

I assume there is a conflict using the Hawking on my laptop with another wireless card. I would be happy to get it to function in my desktop. As I stated, this is for academic purposes, not utility.

Thanks again!

---

### Post by tturrisi on 2007-06-03
no no no!
What adapter is onboard the laptop that you say does not support signal level reporting?

---

### Post by wushuFreak on 2007-06-03
Sorry, I didn't follow. 

It's a 1390 mini with Broadcom's 43xx chipset. I am using the newest stand-alone bcm43xx driver and followed this [howto]("http://ubuntuforums.org/showthread.php?t=434946&highlight=inspiron+1501+wireless") to install. I am nervous about screwing with the 1390s driver as my wireless is working flawlessly on my laptop for the first time in a long time without ndiswrapper.

When I run airodump, the 1390 picks up networks like crazy, but the PWR colums (signal level) on all networks reports a -1 which according to the documentation:

>  If all clients have PWR as -1 then the driver doesn&#8217;t support signal level reporting.

[http://www.aircrack-ng.org/doku.php?id=airodump-ng]("http://www.aircrack-ng.org/doku.php?id=airodump-ng")


I'm certainly close enough to the APs as the signal strength in Network Manager is very high for most networks...mine included. 

Thanks again!

---

### Post by tturrisi on 2007-06-03
Your bcm should work, but it will never work unless you patch the driver!
[http://www.aircrack-ng.org/doku.php?id=broadcom](http://www.aircrack-ng.org/doku.php?id=broadcom)

Then, instead of capturing iv's, install & use [aircrack-ptw]("http://www.wirelessdefence.org/Contents/Aircrack-ptw.htm")

I use ptw now and cracked my own home office wep in 90 seconds!

---

### Post by wushuFreak on 2007-06-03
Thanks for the speedy reply.

I was currently reading an old thread about the bcm working with the patch but most of the material I had found so far was outdated and posted by linux gurus (above my head at the moment). 

This info is looks great and very do-able! I will try this when my son takes a nap and post my results.

Thanks again for the help! The forum support here is what sets Ubuntu apart from ANY other OS.

---

### Post by tturrisi on 2007-06-03
re the ralink:
I believe ubuntu blacklists the ralink somewhere.  (this is one of the reasons I use Debian instead of ubuntu).  Follow the install instrctions for the HWUG1 here:
[http://www.aircrack-ng.org/doku.php?id=rt2570](http://www.aircrack-ng.org/doku.php?id=rt2570)
It won't hurt to install all the rtX drivers either.  That usb adapter is "supposed" to have a rt2571 chipest, but it may have a different rt chjipset.

---

### Post by wushuFreak on 2007-06-03
Excellent.

If I can get the bcm working on my laptop, I will try to use the HWUG1 on my desktop with the info you just gave.

The bcm definitely seems to have superior range over the HWUG1 (at least without a hi-gain antenna).

Thanks again! I will post my results.

---

### Post by wushuFreak on 2007-06-03
OK, I got the driver patched. I ended up downloading the most recent bcm43xx driver package, patching the main.c directly and re-installing. 

When I try the injection test I end up with the help file...
```

deacon@hal:~$ sudo airmon-ng start eth1 6

usage: airmon-ng <start|stop> <interface> [channel]

Interface       Chipset         Driver

eth1            Broadcom                bcm43xx (monitor mode enabled)

deacon@hal:~$ aireplay-ng -9 eth1
aireplay-ng: invalid option -- 9

  Aireplay-ng 0.6.2 - (C) 2006 Thomas d'Otreppe
  Original work: Christophe Devine
  http://www.aircrack-ng.org

  usage: aireplay-ng <options> <replay interface>

  filter options:

      -b bssid  : MAC address, Access Point
      -d dmac   : MAC address, Destination
      -s smac   : MAC address, Source
      -m len    : minimum packet length
      -n len    : maximum packet length
      -u type   : frame control, type    field
      -v subt   : frame control, subtype field
      -t tods   : frame control, To      DS bit
      -f fromds : frame control, From    DS bit
      -w iswep  : frame control, WEP     bit

  replay options:

      -x nbpps  : number of packets per second
      -p fctrl  : set frame control word (hex)
      -a bssid  : set Access Point MAC address
      -c dmac   : set Destination  MAC address
      -h smac   : set Source       MAC address
      -e essid  : fakeauth  attack : set target AP SSID
      -j        : arpreplay attack : inject FromDS pkts
      -g value  : change ring buffer size (default: 8)

  source options:

      -i iface  : capture packets from this interface
      -r file   : extract packets from this pcap file

  attack modes (Numbers can still be used):

      --deauth      count : deauthenticate 1 or all stations (-0)
      --fakeauth    delay : fake authentication with AP (-1)


```

I am getting the same results when I try airodump as before...
```


deacon@hal:~$ sudo airodump-ng --channel 6 eth1
                                                                 
 CH  6 ][ Elapsed: 12 s ][ 2007-06-03 16:32                                    
                                                                               
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ES
                                                                               
 00:13:10:10:73:B4   -1   0        0        0    0   6  -1                   < 
 00:13:10:4C:FD:C3   -1  51       68        0    0   6  48  WEP  WEP         d 
 00:1A:70:69:79:A0   -1   0       11        0    0   6  48  WEP  WEP         F 
 00:18:39:48:B7:FE   -1  15       24        0    0   6  48  WPA2 CCMP   PSK  2 
 00:0F:B5:DE:97:BB   -1  12       18        1    0  10  54. WPA2 CCMP   PSK  T 
 00:18:F8:4F:5A:16   -1  20       19        0    0   6  48  WEP  WEP         g 
 00:0C:41:83:E9:52   -1  73      113        1    0   6  11  WEP  WEP         B 
 00:18:39:7A:90:75   -1 100      125        5    0   6  48  WPA  TKIP   PSK  < 
 00:18:F8:EA:59:B8   -1  83      103        0    0   6  48. WPA2 CCMP   PSK  < 
 00:18:39:EF:96:95   -1  92      116        0    0   6  48  WEP  WEP         m 
 00:14:BF:07:25:D9   -1  78       95        0    0   6  48. WPA  TKIP   PSK  j 
 00:16:B6:AF:4F:36   -1  34       59        6    0   6  48  WEP  WEP         b 
 FF:FF:00:19:7D:5F   -1   0        0        0    0  -1  -1                   < 
                                                                               
 BSSID              STATION            PWR  Lost  Packets  Probes              
                                                                               
 (not associated)   00:14:A4:43:50:A4   -1     0        1  linksys             
 (not associated)   00:11:F5:D6:BD:09   -1   145        9  linksys,crowne,Groun


```


Also I tend to lose some Internet connectivity after activating airmon. Even after it is stopped. I show network connection, but I can't ping any hosts within my own network or access the Net without a reboot.

Any ideas?
Thanks in advance.
Thanks

---

### Post by tturrisi on 2007-06-03
aireplay-ng -9 eth1 is an invalid command.
aireplay-ng: invalid option -- 9

What version of aircrack-ng do you have: do:
aitcrack-ng -v

Injection test
Important note: This option is only available on aircrack-ng 0.9 and up.
[http://www.aircrack-ng.org/doku.php?id=injection_test](http://www.aircrack-ng.org/doku.php?id=injection_test)

If you installed aircrack-ng using apt-get or synaptic, then use sybaptic to completely remove it and then  download & build the later version:

 wget [http://download.aircrack-ng.org/aircrack-ng-0.9.tar.gz](http://download.aircrack-ng.org/aircrack-ng-0.9.tar.gz)
 tar -zxvf aircrack-ng-0.9.tar.gz
 cd aircrack-ng-0.9
 make
 make install

---

### Post by wushuFreak on 2007-06-03
Wow, I feel like a dunce. I failed to notice that little note. 

I have version 0.6.2 - ha no wonder!

That's what I get for doing homework, chasing my 2yo and attempting to get aircrack working...

I will install the newest version and give that a try.

Thanks very much!

---

### Post by wushuFreak on 2007-06-03
I got .9 installed and ran the basic injection test. I'm not quite sure what to make of the results...

```

deacon@hal:~$ sudo airmon-ng start eth1


Interface       Chipset         Driver

eth1            Broadcom        bcm43xx (monitor mode enabled)

deacon@hal:~$ aireplay-ng -9 eth1
This program requires root privileges.
deacon@hal:~$ sudo aireplay-ng -9 eth1
Couldn't find the location of inject_nofcs. Is your bcm34xx driver patched?
19:49:18  Trying broadcast probe requests...
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;#&#65533;Zu&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                      2
                       $0H`l@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Jw&#65533;&#65533;J&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                                     2
                                                      $0H`l@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1509;,&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
   2
    $0H`l19:49:19  No Answer...
19:49:19  Found 1 AP 

19:49:19  Trying directed probe requests...
19:49:19  00:0F:B5:DE:97:BB - channel: 10 - 'TheFlat'
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@^&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat
                           2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;:(+                  $0H`l
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat
                   2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1916;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat
                             2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat  $0H`l
                            2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;36&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat$0H`l
                             2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Oð&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                             2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4NZ&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat$0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1876;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat    $0H`l
                           2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1800;{&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat$0H`l
                             2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;W&#65533;&#65533;n&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat$0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;[H&#65533;`&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;}&#65533;&#65533;.&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; .&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;+&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat  $0H`l
                             2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;`&#65533;&#1823;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat  $0H`l
                            2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;'3!&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat$0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;3&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat    $0H`l
                           2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat$0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;d&#65533;&#1924;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat   $0H`l
                            2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#769;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat$0H`l
                             2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                             2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;:&#65533;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat$0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;\N&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;/&#65533;3&#65533;.&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;s&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?&#65533;L&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6Q50&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;2&#65533;kF&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat $0H`l
                              2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat   $0H`l
                            2
@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;dH*&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0TheFlat$0H`l
                              2
19:49:28  0/30: 0%             $0H`l


```

It is certainly not what was expected in any shape or form.

Looks like I may have screwed up the patch.

I will do some more reading. If you have any suggestions I am all ears.

Thanks again for all your help.

---

### Post by wushuFreak on 2007-06-03
Well, I've dowloaded a fresh bcm43xx driver package, patched and installed it and I keep getting the same results.

I am still not running the new module. I ran 'modinfo bcm43xx' and checked the file info and it shows the install as 5/22 which is obviously NOT today.

---

### Post by wushuFreak on 2007-06-04
I downloaded the current linux-source and unpacked it.

I followed the directions for installing the patching the bcm43xx driver and that was successful, but when I tried 'make modules', I was informed my kernel was not configured to do this and that I would have to re-configure my kernel.

When I try to use menuconfig I get this:
I couldn't get it all on here but I used the command 'sudo make menuconfig' from /usr/src/linux-source-2.6.20

```

deacon@edgy:/usr/src$ cd linux-source-2.6.20
deacon@edgy:/usr/src/linux-source-2.6.20$ sudo make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before &#8216;chtype&#8217;
scripts/kconfig/lxdialog/dialog.h:187: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:193: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:195: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:196: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:197: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:198: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:200: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:31: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:59: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:95: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c: In function &#8216;dialog_checklist&#8217;:
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;WINDOW&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;dialog&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;list&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function &#8216;getmaxy&#8217;
scripts/kconfig/lxdialog/checklist.c:129: error: &#8216;stdscr&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: &#8216;KEY_MAX&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function &#8216;getmaxx&#8217;
scripts/kconfig/lxdialog/checklist.c:137: error: &#8216;COLS&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: &#8216;LINES&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function &#8216;draw_shadow&#8217;
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function &#8216;newwin&#8217;
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function &#8216;keypad&#8217;
scripts/kconfig/lxdialog/checklist.c:143: error: &#8216;TRUE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function &#8216;draw_box&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function &#8216;wattrset&#8217;
scripts/kconfig/lxdialog/checklist.c:147: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function &#8216;mvwaddch&#8217;
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function &#8216;waddch&#8217;
scripts/kconfig/lxdialog/checklist.c:151: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function &#8216;print_title&#8217;
scripts/kconfig/lxdialog/checklist.c:156: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function &#8216;print_autowrap&#8217;
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function &#8216;subwin&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function &#8216;print_item&#8217;
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function &#8216;print_arrows&#8217;
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function &#8216;print_buttons&#8217;
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function &#8216;wnoutrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function &#8216;doupdate&#8217;
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function &#8216;wgetch&#8217;
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_UP&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_DOWN&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: &#8216;FALSE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function &#8216;scrollok&#8217;
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function &#8216;wscrl&#8217;
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function &#8216;wrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function &#8216;delwin&#8217;
scripts/kconfig/lxdialog/checklist.c:297: error: &#8216;KEY_LEFT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: &#8216;KEY_RIGHT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function &#8216;on_key_esc&#8217;
scripts/kconfig/lxdialog/checklist.c:312: error: &#8216;KEY_RESIZE&#8217; undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2

```

Am I missing a package to use this?

---

### Post by wieman01 on 2007-06-04
Just to confirm that RT2570 works with the latest version of Aircrack-ng. I tested it over the weekend. Packet injection works great, it takes about 20 - 30 to collect a sufficient number of packets, and less than a minute to crack the key.

One important note: Before you actually send out ARP requests to increase traffic and collect data packets, you need to deauthenticate an existing client from an AP, then start "aireplay-ng -3". The Aircrack-ng documentation explains that in great detail. Let me know if you need a hand with RT2570.

---

### Post by tturrisi on 2007-06-04
the kernel source dir is /usr/src/something or other
this dir will contain the dir for linux-headers too, among other things.
when patching, cd to /usr/src and run the commands from there else wget will download to /home/username dir.

---

### Post by paxmark1 on 2007-06-04
Hi.  I bought the Hawking HWUG1 and it really pulls in signals, at least in Windows.  

Where do I get the RT2571 drivier?  I have looked for it all over.  NDiswrapper a no go with the supplied driver, just a .exe with no .inf for Ndis to wrap onto.  And then there is a Prism page, I am confused.  

I have to pull packages via Windows, and have not gotten the substantial updates for Xubuntu since late April.  So advice that would work utilizing apt-get or Synaptic won't work for me yet.  Also, I don't thing I have lots of libraries to ./configure tars.  I can get .deb s from debian.

TIA  Mark

---

### Post by jpidrovo on 2007-07-06
Hi nice post....
I need some help please... 
I have a Laptop Dell latitude D610 , I run UBUNTU 7.0.4 excellent my laptop comes with a iwp220bg wireless card that is not that friendly with aircrack-ng
I also buy a Hawking HWUG1 a nice USB card I tried an windows and works fine
I have been trying to make it work with my UBUNTU but when I plug it in to my laptop  nothing happens 
I have no idea what to do ... 
I would really appreciate your help

---

