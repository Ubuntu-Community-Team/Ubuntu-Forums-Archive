---
title: "Ralink RT3370 / D-Link DWA-123 N150: Disconnected network you are now offline"
date: 2013-12-14
forum: Networking &amp; Wireless
---

### Post by boris_619 on 2013-12-14
Hi all, first of all say I'm a new user in linux, and therefore in lubuntu also English is not my native language, but with my limited knowledge and help of translators hope I can communicate without problem.

My problem is that I can not connect to my router and therefore can not access internet.
My wireless find all the wifi networks in my neighborhood (they appear in the taskbar), but when I type the password and try to connect to any of them, after a few seconds of loading, the following message appears: "Network Disconnected you are now offline"

I have read post with similar problems but could not solve mine, although I have learned to use certain commands that I hope will be useful.

Distribution: Lubuntu 13.10
Kernel Version: 3.11.0-13-generic

My wireless adapter:
```
Bus 001 Device 012: ID 2001:3c17 D-Link Corp. DWA-123 Wireless N 150 Adapter(rev.A1) [Ralink RT3370]
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2001 D-Link Corp.
  idProduct          0x3c17 DWA-123 Wireless N 150 Adapter(rev.A1) [Ralink RT3370]
  bcdDevice            1.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
```

Some  logs (sorry if it is not required, but as I do not know what it means  I try to copy the parts that seem important) there are times when it  says connected but internet (I tried to search on google) and internet does not work:
```
[ 8670.875280] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8670.881289] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8721.220260] ieee80211 phy8: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110
[ 8771.220215] ieee80211 phy8: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x101c with error -110
[ 8821.220286] ieee80211 phy8: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110
[ 8871.220233] ieee80211 phy8: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -110
[ 8880.968072] INFO: task wpa_supplicant:1456 blocked for more than 120 seconds.
[ 8880.968082] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8880.968088] wpa_supplicant  D c18d69a0     0  1456      1 0x00000000
[ 8880.968098]  f2159ab8 00200086 c1a3d600 c18d69a0 000007e5 c1a3d600 f7bde600 c1a3d600
[ 8880.968111]  c18d69a0 f2159a64 c1a3d600 f7bde600 f2058ce0 f2159a70 c1045168 f2159a7c
[ 8880.968123]  c162b762 f7bd9470 f2159a90 c10731fc f2159a90 00200282 00000000 f2159aac
```

```
[ 9123.312041] usb 1-3: new high-speed USB device number 12 using ehci-pci
[ 9123.458314] usb 1-3: New USB device found, idVendor=2001, idProduct=3c17
[ 9123.458326] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 9123.458332] usb 1-3: Product: 11n Adapter
[ 9123.458337] usb 1-3: Manufacturer: Ralink
[ 9123.576040] usb 1-3: reset high-speed USB device number 12 using ehci-pci
[ 9123.716025] ieee80211 phy9: rt2x00_set_rt: Info - RT chipset 3390, rev 3213 detected
[ 9123.744772] ieee80211 phy9: rt2x00_set_rf: Info - RF chipset 000b detected
[ 9123.745790] ieee80211 phy9: Selected rate control algorithm 'minstrel_ht'
[ 9123.849570] ieee80211 phy9: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 9123.849671] ieee80211 phy9: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[ 9125.791354] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9125.797062] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9152.011686] wlan0: authenticate with 00:26:24:ca:73:39
[ 9152.077572] wlan0: direct probe to 00:26:24:ca:73:39 (try 1/3)
[ 9152.280107] wlan0: direct probe to 00:26:24:ca:73:39 (try 2/3)
[ 9152.484116] wlan0: direct probe to 00:26:24:ca:73:39 (try 3/3)
[ 9152.688072] wlan0: authentication with 00:26:24:ca:73:39 timed out
[ 9154.211030] wlan0: authenticate with 00:26:24:ca:73:39
[ 9154.238471] wlan0: direct probe to 00:26:24:ca:73:39 (try 1/3)
```

```
[ 9565.902156] wlan0: authenticate with 00:26:24:ca:73:39
[ 9565.937779] wlan0: send auth to 00:26:24:ca:73:39 (try 1/3)
[ 9565.973453] wlan0: send auth to 00:26:24:ca:73:39 (try 2/3)
[ 9565.977449] wlan0: authenticated
[ 9565.977884] rt2800usb 1-3:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 9565.980072] wlan0: associate with 00:26:24:ca:73:39 (try 1/3)
```

```
[10841.291141] wlan0: send auth to 00:26:24:ca:73:39 (try 1/3)
[10841.296625] wlan0: authenticated
[10841.297312] rt2800usb 1-3:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[10841.300208] wlan0: associate with 00:26:24:ca:73:39 (try 1/3)
[10841.356887] wlan0: associate with 00:26:24:ca:73:39 (try 2/3)
[10841.360421] wlan0: RX AssocResp from 00:26:24:ca:73:39 (capab=0x411 status=0 aid=2)
[10841.371015] wlan0: associated
[10841.371096] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10848.547548] wlan0: deauthenticated from 00:26:24:ca:73:39 (Reason: 15)
[10848.561954] cfg80211: Calling CRDA to update world regulatory domain
[10848.574182] cfg80211: World regulatory domain updated:
[10848.574194] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[10848.574199] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10848.574204] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10848.574209] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[10848.574215] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10848.574220] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[10850.051498] wlan0: authenticate with 00:26:24:ca:73:39
[10850.089682] wlan0: send auth to 00:26:24:ca:73:39 (try 1/3)
```

```
[11589.597720] wlan0: send auth to 00:26:24:ca:73:39 (try 1/3)
[11589.601175] wlan0: authenticated
[11589.605602] rt2800usb 1-3:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[11589.608379] wlan0: associate with 00:26:24:ca:73:39 (try 1/3)
[11589.639572] wlan0: RX AssocResp from 00:26:24:ca:73:39 (capab=0x411 status=0 aid=2)
[11589.647637] wlan0: associated
[11589.647720] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11658.030950] wlan0: deauthenticated from 00:26:24:ca:73:39 (Reason: 7)
[11658.053768] cfg80211: Calling CRDA to update world regulatory domain
[11658.068004] cfg80211: World regulatory domain updated:
[11658.068091] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11658.068098] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11658.068103] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11658.068107] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[11658.068112] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11658.068117] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11659.550415] wlan0: authenticate with 00:26:24:ca:73:39
[11659.581903] wlan0: send auth to 00:26:24:ca:73:39 (try 1/3)
```

During one of the many connection attempts came this error message, but it only happened on one occasion:
```
Connection activation failed
(4) Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

If it is  necessary connect to internet from that computer to solve the  problem, could do, because the connection through cable works  properly.

---

### Post by varunendra on 2013-12-15
Welcome to the forums boris !

I must say your English (or your translator) is pretty impressive, and so is your attention to details ! :)

When the wireless hangs, do you experience some misbehaviours in the system too (like some programs not responding, or menus not opening etc.)? Or is it just the wireless?

As a temporary test, please try -
```
sudo modprobe -rv rt2800usb
sudo modprobe -v rt2800usb nohwcrypt=Y
```
This will be a temporary change and will be lost at next boot. If it helps, we can make it permanent.

If it doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us a detailed report that may lead us to some more clues.

---

### Post by boris_619 on 2013-12-16
Thanks for the welcome and your attention. I hope that my English is still good. :smile:
> When the wireless hangs, do you experience some misbehaviours in the  system too (like some programs not responding, or menus not opening  etc.)? Or is it just the wireless? 
Is just the wireless, all other programs work correctly and fluently.
> As a temporary test, please try -
```
sudo modprobe -rv rt2800usb
sudo modprobe -v rt2800usb nohwcrypt=Y
```
When I use "sudo modprobe -rv rt2800usb" the computer hangs and I have to force reboot, with "sudo modprobe -v rt2800usb nohwcrypt=Y" connects for a few seconds (I connect to google) but it switched off again (I could not even complete a quest).
> If it doesn't help, please follow the "Wireless Script" link in my  signature, download and run the script as per instructions there, and  post back the report it generates. It will give us a detailed report  that may lead us to some more clues.
I think I need some time to do this and I need to study for a big test on Thursday, but as soon as I finish it, I will try this solution and post the results.

---

### Post by varunendra on 2013-12-18
> **boris_619 said:**
> When I use "sudo modprobe -rv rt2800usb" the computer hangs and I have to force reboot

This is not good. The second command will have no effect once the driver is already loaded. Let's try the permanent way. Please do this in a terminal -
```
echo "options rt2800usb nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800usb.conf
```
This will create a .conf file in the /etc/modprobe.d directory that will cause the rt2800usb driver to load with the "nohwcrypt=Y" parameter automatically since next boot.

If this helps, we have already done what needed to be done. If not, please post the wireless_script report as originally requested.

And to revert the above change, if required -
```
sudo rm /etc/modprobe.d/rt2800usb.conf
```
which will simply delete the custom .conf file we created.

---

### Post by boris_619 on 2013-12-19
> This is not good. The second command will have no effect once the driver  is already loaded. Let's try the permanent way. Please do this in a  terminal -
     ```


echo "options rt2800usb nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800usb.conf

```


After entering this command and reboot, the problem persisted.

I need to delete the file .conf before running wireless_script?

I do not delete it and got this:[ http://pastebin.ubuntu.com/6601186/]("http://pastebin.ubuntu.com/6601186/")

I do not understand most of the lines, but the line 100 to the 106 my access point (R-MRPD) is not displayed.

---

### Post by varunendra on 2013-12-19
> **boris_619 said:**
> I need to delete the file .conf before running wireless_script?

Leave the .conf file for now, it won't do any harm, if can't help. We'll remove it later if required.

A few observations/recommendations based on the report -

[indent]
**1)** The signal strength of all the access points the adapter could scan looks too weak. Are you close enough to the AP you are trying to connect to?

**2)** Many of these APs are using the dreaded WPA/WPA2 mixed mode encryption. It is HIGHLY recommended to change the encryption type in the router to pure WPA2-PSK (AES/CCMP) only. No mixed mode, no TKIP. Even if this alone can't help, leave it like this.
***[COLOR="#800000"]EDIT:[/COLOR]*** Just noticed you mentioned your AP isn't even mentioned in the report. Is is set to use correct frequencies/channel as permitted by your country's "Regulatory Settings"? Is it detected by other devices there?

**3)** In your computer, please try -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
Does the "Power Management" turn off? Does this change survive a reboot? Most importantly, does it help improving signal strength (and possibly connectivity)?

**4)** If your router/AP provides an option to change the band and is currently set to use the N-channel (e.g. "b/g/n"), try disabling the N-channel in the router by setting it to "g-only" or "b/g-only" mode.
[/indent]

After making any change in the router, save the changes and reboot it to make sure the changes take effect properly. Also, you may have to delete the existing connection in Network Manager and recreate it after making any changes in the router (although mostly it is not necessary, just to make sure).

**PS:**
Have you tried the proprietary driver yet? It may be our next shot if the above suggestion don't help. But any solution will only work if the actual signal strength is good enough where you are trying to connect.

---

### Post by boris_619 on 2013-12-21
**1)** The access points with low signal are far, but the point I want to connect has good signal. After running the script several times got this result:
```
Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
```
Is it a good signal? In the GUI I have between 2 and 3 waves in the R-MRPD's icon and the rest of signals only 1 or 0.
[B]
2)[/B] Why should I change this setting? Why WPA/WPA2 is not recommended?
I guess my router has the right frequencies, it works perfectly with other devices (phones, consoles...) and even with the same wireless usb but in WinXP.
I changed the wireless settings, I now have this:
-Current channel: 6. What does this mean? What number is recommended?
[COLOR=#ff0000]_**EDIT:**_[/COLOR] -WPA[COLOR=#ff0000]_**2**_[/COLOR]-PSK: Enabled.
-WPA/WPA2 Encryption: AES.
-WPA Pre-Shared Key: *********. This password is generated automatically. How I can see the password instead of a succession of points?
Would be possible to use WPS connection? is it recommended?

**With this setup I got connect to internet with lubuntu****!**\\:D/ but looks slower, it may be the settings?
Now I have a new problem and that is that this setting does not seem compatible with winxp, but possibly because it is not updated with service pack 3...
I'll update when I have time and I'll tell you if I could solve it :)

**3)** It is recommended that I do this now that the network runs?

**4)** I don't know what is this.

I have not used proprietary drivers yet.

Although internet works I'd like your answer to my questions :), but if you think that the problem is solved we could leave here...
Thank you very much.

---

### Post by varunendra on 2013-12-22
> **boris_619 said:**
> After running the script several times got this result:
```
Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
```
Is it a good signal?
Only good enough to be somehow 'usable'. If I understand correctly, the perfect signal strength in nm-tool is represented by 100 (or 70/70 in "iwconfig" output). Anything below 36 is hardly stable, but 47 (assuming it doesn't go below 40) should be just sufficient enough to keep it connected and usable.

> **2)** Why should I change this setting? Why WPA/WPA2 is not recommended?
The mixed mode is just for backward compatibility with cards that are too old and can't support WPA2. It must use TKIP encryption (to support WPA(1) part) which is not only weak but also inefficient, causing the encryption mechanism (on both router and card/driver sides) to work much harder. This not only affects the speed, but sometime also severely affects overall performance and stability with some Linux drivers. You can't achieve speeds higher than 54 Mbps with TKIP encryption regardless of which OS you are on (windows, mac, android, linux...).

You may read this post and the links in it for a bit more detailed discussion about this : [http://ubuntuforums.org/showthread.php?p=12817495](http://ubuntuforums.org/showthread.php?p=12817495)

> I guess my router has the right frequencies, it works perfectly with other devices (phones, consoles...) and even with the same wireless usb but in WinXP.
I don't have an authentic answer for why it works well on other platforms, but my assumption is that it is so either because the chip/card manufacturers themselves design the drivers for those platforms and keep them updated (because those platforms are of commercial interest for them), or the platform uses much simpler drivers (like android or other mobile platforms, because they don't need complex functions, just simple connectivity on an 'always on' OS).

On the other hand, Linux drivers are almost always designed and maintained by volunteers, and the chip manufacturers never disclose the internals of their chips so that these drivers can be optimized to work smoothly with them and take full advantage of the capabilities of both the OS and the chip the same time.

> I changed the wireless settings, I now have this:
-Current channel: 6. What does this mean? What number is recommended?
A channel is just a **defined range of frequencies** used to establish wifi communication. Recommended channels is usually the one which is least occupied, to avoid interference from neighbourhood connections. However, it has been observed that **channels 1 or 11** (or whichever is the highest available channel in your country) usually work best with Linux drivers. I personally believe (have no authentic source to back this up) that it is because these two channels are at the lower and higher boundaries of the available band spectrum, thus getting least interference by other overlapping channel frequencies (see the images in this wikipedia page to understand this : [http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11)).

> 
-[COLOR="#FF0000"]WPA-PSK: Enabled[/COLOR].
-[COLOR="#FF0000"]WPA/WPA2[/COLOR] Encryption: AES.
-WPA Pre-Shared Key: *********. This password is generated automatically. How I can see the password instead of a succession of points?
Would be possible to use **WPS** connection? is it recommended?
The recommended encryption is pure **[COLOR="#006400"]WPA2[/COLOR]**-PSK with AES. Not WPA-PSK or WPA/WPA2 mixed mode. Choosing the mixed mode means you are choosing TKIP, even if the router settings don't make that clear.

I didn't know about the term "WPS connection" until you asked above, and hence don't know how this is implemented by the routers. Although after reading [this article]("http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup"), it seems turning it off is a better and much more sensible choice. But if you still want to keep using it, maybe your router's user manual can offer better help than I can. Obviously, I won't recommend using it though.

> **With this setup I got connect to internet with lubuntu!**\\:D/ but looks slower, it may be the settings?
Most probably. As per your description, you are still using WPA/WPA2 mixed mode, which may be a bottleneck.

> Now I have a new problem and that is that this setting does not seem compatible with winxp, but possibly because it is not updated with service pack 3...
Change the encryption to pure WPA2-PSK with AES, and I'm sure winxp will support it beautifully.

As per your description above, you have chosen WPA/WPA2 mixed mode, but only AES, no TKIP. As per my knowledge, this is a non-standard combination that doesn't comply with IEEE 802.11 standards, and shouldn't even be possible (with WPA(2), you **must** use TKIP), but I also know and frequently keep seeing routers that allow this weird combination. How they handle this internally is something only God knows, or the manufacturer himself.

It may be this weird combination of encryption type (WPA/WPA2 mixed mode) and encryption algorithm (only AES, no TKIP) that is confusing the windows driver. If this sounds complicated, maybe taking a look at the user's manual can help. Could you find an online version of your router's user manual for us?

> **3)** It is recommended that I do this now that the network runs?
Yes it is still recommended.

Keeping the "Power Management" on wifi off is a way to improve wifi performance at the cost of less power saving (this power saving is mostly ignorable anyway). The advance power management feature can make the connection unstable/weak especially if the signal is already weak and/or the driver is buggy.

However, the "sudo iwconfig wlan0 power off" command should be needed only once. If it turns on again after reboot, then we may need other ways to turn it off and keep it that way even across reboots.

> **4)** I don't know what is this.
Give me the link to your router's user manual and I may be able to show you what (or rather "where") that is in your router/access-point. Function-wise, it is a method to tell the router which frequency ranges and speed standards to use. The [**N-channel**]("http://en.wikipedia.org/wiki/IEEE_802.11n") offers speeds higher than 54 Mbps, but can cause trouble 'sometimes' with 'some' Linux drivers in 'some particular conditions'. In those cases, turning it off (if the router allows that change) and using only 'g' or 'b/g' mode solves the problem.

> I have not used proprietary drivers yet.
If you are satisfied with the performance, with or without implementing the recommendations about changing the encryption/band/channel (in the router) and using the driver parameter (in Ubuntu), we don't need to try that. But if it is unsatisfactory, even after trying all the recommendations, we may give it a shot if you wish.

Sorry if I wrote too much, but hope it answers your questions and makes a few things clearer for you as well as those who may come across this thread/post later. :)

---

### Post by boris_619 on 2013-12-23
> The mixed mode is just for backward compatibility with cards that are  too old and can't support WPA2. It must use TKIP encryption (to support  WPA(1) part) which is not only weak but also inefficient, causing the  encryption mechanism (on both router and card/driver sides) to work much  harder. This not only affects the speed, but sometime also severely  affects overall performance and stability with some Linux drivers. You  can't achieve speeds higher than 54 Mbps with TKIP encryption regardless  of which OS you are on (windows, mac, android, linux...).

You may read this post and the links in it for a bit more detailed discussion about this : [http://ubuntuforums.org/showthread.php?p=12817495](http://ubuntuforums.org/showthread.php?p=12817495)
I think that I understand what I read in those links, but I am not sure how to configure my router with those options.

> A channel is just a **defined range of frequencies** used to  establish wifi communication. Recommended channels is usually the one  which is least occupied, to avoid interference from neighbourhood  connections. However, it has been observed that **channels 1 or 11**  (or whichever is the highest available channel in your country) usually  work best with Linux drivers. I personally believe (have no authentic  source to back this up) that it is because these two channels are at the  lower and higher boundaries of the available band spectrum, thus  getting least interference by other overlapping channel frequencies (see  the images in this wikipedia page to understand this : [http://en.wikipedia.org/wiki/IEEE_802.11](http://en.wikipedia.org/wiki/IEEE_802.11)).
I will use channel 1 then.

> The recommended encryption is pure **[COLOR=#006400]WPA2[/COLOR]**-PSK  with AES. Not WPA-PSK or WPA/WPA2 mixed mode. Choosing the mixed mode  means you are choosing TKIP, even if the router settings don't make that  clear.
Please, check out my previous post, I made a mistake when typing it.
 I meant to say:
Current channel: 6.
-WPA[COLOR=#ff0000]**2**[/COLOR]-PSK: Enabled.
-WPA/WPA2 Encryption: AES.
-WPA Pre-Shared Key: *********.
Sorry for my mistake, Do you think that now is right?

> Could you find an online version of your router's user manual for us?
> Give me the link to your router's user manual and I may be able to show  you what (or rather "where") that is in your router/access-point.  Function-wise, it is a method to tell the router which frequency ranges  and speed standards to use. The [**N-channel**]("http://en.wikipedia.org/wiki/IEEE_802.11n")  offers speeds higher than 54 Mbps, but can cause trouble 'sometimes'  with 'some' Linux drivers in 'some particular conditions'. In those  cases, turning it off (if the router allows that change) and using only  'g' or 'b/g' mode solves the problem.

Here it is: [http://www.telecom.li/CFDOCS/cms3/admin/cms/download.cfm?FileID=9823&GroupID=171](http://www.telecom.li/CFDOCS/cms3/admin/cms/download.cfm?FileID=9823&GroupID=171)

> However, the "sudo iwconfig wlan0 power off" command should be needed  only once. If it turns on again after reboot, then we may need other  ways to turn it off and keep it that way even across reboots.
It turns on again after reboot :(

> If you are satisfied with the performance, with or without implementing  the recommendations about changing the encryption/band/channel (in the  router) and using the driver parameter (in Ubuntu), we don't need to try  that. But if it is unsatisfactory, even after trying all the  recommendations, we may give it a shot if you wish.
If this improves performance, I would like to give it a try.

> Sorry if I wrote too much, but hope it answers your questions and makes a  few things clearer for you as well as those who may come across this  thread/post later. :smile:
I have solved many questions! thank you very much for the help, I think I understand everything pretty well and sorry for the typing mistake in my previous post.

---

### Post by varunendra on 2013-12-24
> **boris_619 said:**
> -**[COLOR="#FF0000"]WPA/WPA2[/COLOR]** Encryption: AES.
....
Do you think that now is right?

This^ doesn't look good. This is mixed mode with WPA which means TKIP would still be in use (WPA needs TKIP, WPA works with AES). Recommended encryption is WPA2 only, with AES.

To keep the power management off, let's try disabling the default power management script. Please do -
```
sudo touch /etc/pm/power.d/wireless
```
This will create a blank file in /etc/pm/power.d directory due to which the default wireless power management script in /usr/lib/pm-utils/power.d would be disabled.

After that, run the power off command again -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
immediately to make sure Power Management turned off, then reboot and check again to see if the change persisted this time.

**PS:**
I'm unable to download the pdf correctly (doesn't open after downloading), most probably due to the super slow gprs speed I'm getting at the moment. Please confirm the pdf itself is not corrupt. Or just give me the **brand name and full model no. of your router** so that I can look it up myself.

---

### Post by boris_619 on 2013-12-24
> This^ doesn't look good. This is mixed mode with WPA which means TKIP  would still be in use (WPA needs TKIP, WPA works with AES). Recommended  encryption is WPA2 only, with AES.
I think that I can not choose an option other than WPA/WPA2 Encryption.

[IMG]http://img32.imageshack.us/img32/9841/k04b.png[/IMG]

It is possible that this option refers to WPA encryption when WPA is enabled and WPA2 encryption when WPA2 is enabled?

> immediately to make sure Power Management turned off, then reboot and check again to see if the change persisted this time.
After entering the command the power management turns off, but after reboot turns on again.

> I'm unable to download the pdf correctly (doesn't open after  downloading), most probably due to the super slow gprs speed I'm getting  at the moment. Please confirm the pdf itself is not corrupt. Or just  give me the **brand name and full model no. of your router** so that I can look it up myself.[SIZE=2]
His name is: [SIZE=2]Technicolor / Thomson TCW750-4.[/SIZE]
I think the pdf is not corrupt. You can download it and view its specifications from here: [http://www.speedguide.net/routers/technicolor-thomson-tcw750-4-4-ethernet-port-wireless-1298](http://www.speedguide.net/routers/technicolor-thomson-tcw750-4-4-ethernet-port-wireless-1298)[/SIZE]

---

### Post by varunendra on 2013-12-26
Sorry for the late reply. I have got indulged in something that doesn't allow me any time to dedicate on the forums. I'm not sure when I'll get time again to reply back.

Anyway, the settings in the screenshot seem as they should be. Only WPA2-PSK is enabled, rest are disabled, and this is what we want. The selected encryption is AES which is again exactly what we want. You are right about this -
> It is possible that this option refers to WPA encryption when WPA is enabled and WPA2 encryption when WPA2 is enabled?

Your router supports b/g modes only, not N-channel, so that is ruled out.

Now the only things that look suspicious to me are -
1) The WPS functionality. I have no experience with this so am not sure if this can cause any troubles. Maybe it's just this 'suspicion about the unknown', but I guess temporarily disabling it shouldn't hurt.
2) WMM under QoS. This has been reported a few times as the culprit. Try disabling "WMM Support" under QoS (page 58 of the pdf, which is actually page 53 of the manual).

Post back the outcome and let's see if we are lucky enough.

---

