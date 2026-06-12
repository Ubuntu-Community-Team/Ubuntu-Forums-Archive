---
title: "I can not get WIFI to work..grrr"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by hifiman on 2011-03-06
I am new to this...  i have been at this today for about 4 hrs!! I have down loaded and i think installed ndiswrapper 1.56, ndisgtk0.8.5, and dwa130 XP drivers. and nothing! i can not seem to figure out who to turn it all on.. PLEASE HELP!!

---

### Post by HeadHunter00 on 2011-03-06
first of all, can you give a little more information like what wifi card you have and probably your router. also, give me the output of lspci -n (type it in command line application -> accessories -. terminal)
that way i can see if your wireless card is being detected by ubuntu.

---

### Post by HeadHunter00 on 2011-03-06
hmm. ubuntu has a built in support for your wireless card. are you sure you are doing this right? you shouldnt need ndiswrapper at all. remove ndiswrapper: sudo apt-get remove ndiswrapper (again in terminal)

---

### Post by hifiman on 2011-03-06
I am using a d-link dwa130  and i have ATT uverse.

---

### Post by hifiman on 2011-03-06
00:00.0 0600: 8086:2580 (rev 04)
00:01.0 0604: 8086:2581 (rev 04)
00:02.0 0300: 8086:2582 (rev 04)
00:1b.0 0403: 8086:2668 (rev 03)
00:1c.0 0604: 8086:2660 (rev 03)
00:1c.1 0604: 8086:2662 (rev 03)
00:1c.2 0604: 8086:2664 (rev 03)
00:1c.3 0604: 8086:2666 (rev 03)
00:1d.0 0c03: 8086:2658 (rev 03)
00:1d.1 0c03: 8086:2659 (rev 03)
00:1d.2 0c03: 8086:265a (rev 03)
00:1d.3 0c03: 8086:265b (rev 03)
00:1d.7 0c03: 8086:265c (rev 03)
00:1e.0 0604: 8086:244e (rev d3)
00:1f.0 0601: 8086:2640 (rev 03)
00:1f.1 0101: 8086:266f (rev 03)
00:1f.2 0101: 8086:2651 (rev 03)
00:1f.3 0c05: 8086:266a (rev 03)

---

### Post by hifiman on 2011-03-06
this is a desktop

---

### Post by HeadHunter00 on 2011-03-06
oh right i forgot its a usb wireless card. give the output of 'lsusb' then.

---

### Post by hifiman on 2011-03-06
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 07d1:3b11 D-Link System DWA-130 802.11n Wireless N Adapter(rev.A1) [Marvell W8360USB]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by HeadHunter00 on 2011-03-06
oh wait, did you reboot after installing ndiswrapper driver?

---

### Post by hifiman on 2011-03-06
let me try it again...

---

### Post by HeadHunter00 on 2011-03-06
try this guide: [http://ubuntuforums.org/showthread.php?t=1645274](http://ubuntuforums.org/showthread.php?t=1645274)
sorry if i am not helping much.

---

### Post by hifiman on 2011-03-06
still nothing....

---

### Post by HeadHunter00 on 2011-03-06
did you reboot? i sure didn't see your status go offline.

---

### Post by wep940 on 2011-03-06
First you need to get to a clean state:
 
- reverse any edits you made to any files, such as the blacklist.conf file, etc.
 
- start ndiswrapper itself in the command line:
 
- open a terminal window (Applications/Accessories/Terminal)
- type:
sudo ndiswrapper -l <press enter) That's a lower case "L"
 
- if any device/driver is returned in the above list, type:
 
sudo ndiswrapper -e xxxxxx <press enter> Where xxxxxx is the
device/driver from above
 
- repeat these 2 steps until ndiswrapper no longer returns any devices/drivers
 
You *MUST* do this to clear any previous attempts, and therefore devices know to ndiswrapper that don't actually work.
 
 
Next you need the Windows XP drivers for your adapter - these *MUST* be the Windows XP drivers only. They must match the architecture - 32-bit for 32-bit Ubuntu, 64-bit for 64-bit Ubuntu (NOTE: in the link provided by HeadHunter00 it says the 64-bit driver won't work at all, so be sure you are running "normal" 32-bit Ubuntu). Note that it shows your device as rev A1, so select the first version of the device on the selection screen before getting the driver - any of the rev B onward may not work for your adapter as they may use different chipsets.
 
Then try following the link provided by HeadHunter00. I am not familiar with your adapter or I'd try this myself to see how it works.
 
Once you have ndisgtk saying the device is installed, to the following:
 
- right-click on the network manager icon and be sure "Enable Wireless" is checked.
 
- left-click on the network manager icon and see if any wireless networks show. If you already know
yours is the only network in your area, keep in mind that if the router is not broadcasting the network
name you must use the "connect to hidden network" option when you left-click network manager.
 
- if your router uses any encryption, be sure to match it's type and enter the correct password or
passphrase

---

### Post by bkratz on 2011-03-07
> **hifiman said:**
> still nothing....



Just saw your posting.  I have the rev A1 version of the DWA-130 and have installed it in every version since 8.10 using ndiswrapper. Had problems with 9.10, but got it and every version since.  If you PM me I would be happy to help you ( I have the .inf and .sys files if you don't.)


And I have ATT uverse too!!!

---

### Post by wep940 on 2011-03-08
> **bkratz said:**
> Just saw your posting. I have the rev A1 version of the DWA-130 and have installed it in every version since 8.10 using ndiswrapper. Had problems with 9.10, but got it and every version since. If you PM me I would be happy to help you ( I have the .inf and .sys files if you don't.)
 
 
And I have ATT uverse too!!!
 
Just be sure to have the OP reverse anything they have done to date.  Otherwise, be it via the simpler way of the ndisgtk GUI interface or command line ndiswrapper, things will just get more hosed.  After years of using ndiswrapper you kind of learn the hard way to remove anything that you had before - even most failures still result in an entry in ndiswrapper.

---

