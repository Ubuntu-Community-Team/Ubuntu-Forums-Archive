---
title: "Lubuntu 15.04 EDIMAX EW-7811-UN N150 chip Requesting a Wi-Fi Network Address..."
date: 2016-03-02
forum: Networking &amp; Wireless
---

### Post by FaultedGeologist on 2016-03-02
Lubuntu 15.04
Kernel 3.19.0-15
EDIMAX EW-7811-UN N150 chip

The networks appear under Network Connections, it shows a MAC address.  Following the instructions here:

[http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)

First off, add .sh to the file name when saving, or no options will pop up when double-clicked.  The instructions do not match my Lubuntu GUI by exact names.  Follow this:

Drop the file on your desktop, right click, Properties, Permissions tab, Access Control header > Execute dropdown > Anyone, OK

Double-click the file, select Execute, type your Admin password for the two requests, then follow the above directions for adding the file to your forum thread.  For me it returned both txt and gz files.  Am I seeing the same content in both?  Just making sure.

wireless-info.txt result:
[http://pastebin.ubuntu.com/15267642/](http://pastebin.ubuntu.com/15267642/)

Thanks in advance!  My stepson is sooo excited to get this working!  (Oh, and can someone update the sticky for the new GUI options?).

---

### Post by chili555 on 2016-03-02
I'm not sure I see exactly what is wrong. You evidently connected on boot. Then, roughly 40 minutes later, it disconnected.> deauthenticated from <MAC 'ForeverFarm' [AC3]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)That actually sounds like a router issue, for what it's worth.

In any case, the wireless immediately reconnected:> [ 2489.186591] wlan0: authenticate with <MAC 'ForeverFarm' [AC3]>
[ 2489.198349] wlan0: send auth to <MAC 'ForeverFarm' [AC3]> (try 1/3)
[ 2489.201394] wlan0: authenticated
[ 2489.204094] wlan0: associate with <MAC 'ForeverFarm' [AC3]> (try 1/3)
[ 2489.240196] wlan0: RX AssocResp from <MAC 'ForeverFarm' [AC3]> (capab=0x431 status=0 aid=1)
[ 2489.241220] wlan0: associatedThere is actually a better driver suite for your device. I suggest that you do, in a terminal and with a solid connection:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/lwfinger/rtl8192cu.git
sudo dkms add ./rtl8192cu
sudo dkms install rtl8192cu/0.1
```Reboot.

---

### Post by FaultedGeologist on 2016-03-02
Thanks for coming to the rescue, Chili!

For others, DKMS was not installed yet.  I tried the recommended code below, then modified it to apt-get and it worked:

```
sudo aptitude update
sudo aptitude install dkms
```

didn't work, for some reason aptitude wasn't recognized

```
sudo apt-get update
sudo apt-get install dkms
```

worked for me.

[B]AAaannnd, WiFi works now!  Next project...

Chili is the hot stuff!  [/B]

---

### Post by chili555 on 2016-03-02
Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by FaultedGeologist on 2016-03-08
@chili555 and anyone else:
Thanks for the help, things were working great.  I used the dongle for the Raspberry Pi (still troubleshooting that part), then moved it back up to the PC for Ubuntu.  It functions for terminal updates and a retroarch install, but will not function for the Firefox browser.  I ran
```
sudo apt-get update
``` 
before the process, rebooted, then in the process.  Any idea why the terminal would have access to the interwebs, but not the browser?  Do I need to run the script again to show you some info?

---

### Post by chili555 on 2016-03-08
>  Do I need to run the script again to show you some info? Yes, please. The more hard facts we have, the faster and better we can, hopefully, find the answer.

---

### Post by FaultedGeologist on 2016-03-10
@chili555

I was getting delays and errors using the wifi card to do updates, so I plugged the 100' cat cable and ran the update and upgrade commands.  After doing so, I rebooted.  The wifi connects quickly, but nothing comes up in the browser.  I ran 4 pings successfully.  Nothing in the text file jumped out at me.  As noted in the file, link quality is 93% and signal strength is 45%.

[http://pastebin.ubuntu.com/15341583/](http://pastebin.ubuntu.com/15341583/)

I am using kernel 3.19.0-15, but the update just pulled 3.19.0-51 - would this have anything to do with the difficulty?

Thanks again!

---

### Post by chili555 on 2016-03-10
I suspect that the problem is this:> [   30.925264] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   32.000780] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[   46.957669] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   48.961799] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0
[   60.984813] rtl8192c_set_FwPwrMode_cmd(): Mode = 1, SmartPS = 2
[   66.997985] rtl8192c_set_FwPwrMode_cmd(): Mode = 0, SmartPS = 0I believe the card/driver are continuously flipping in and out of power management. Please try:```
sudo -i
modprobe -r rtl8192cu
echo "options rtl8192cu rtw_power_mgnt=0"  >  /etc/modprobe.d/rtl8192cu.conf
modprobe rtl8192cu
exit
```Any improvement?

It might take a reboot.

---

### Post by FaultedGeologist on 2016-03-11
@chili555 I ran the above code, then checked the file referenced - it created the change you coded above.  The browser didn't appear to work immediately after reboot.    I unplugged the router power again, then attached the usb thumbnail-dongle to a usb hub directly to the back of the mobo instead of the front usb case ports.  Now the browser works again.  It remains a mystery...  The connection is still kind of crappy, which is maybe to be expected for a thumbnail dongle receiving signal across the house.

---

