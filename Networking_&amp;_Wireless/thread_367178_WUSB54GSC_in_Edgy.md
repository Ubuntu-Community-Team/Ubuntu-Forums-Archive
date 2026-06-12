---
title: "WUSB54GSC in Edgy"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by prongs on 2007-02-21
Hey.  So I recently switched to Ubuntu and I'm rather new to Linux in general.  I've been trying for the past few days to configure my drivers for a wireless Linksys USB card, WUSB54GSC.  I have been able to get the drivers installed and everything and my computer recognizes the card, but I can't actually connect.  I used the article on the Ubuntu forums about installing WUSB54GS v1 and v2 with ndiswrapper, and I modified drivers and driver names (ie WUSB54GSC rather than WUSB54GS), but I'm still having problems.

I can't really link exact output from terminal commands, as I'm on an XP computer downstairs, but my iwconfig shows the device is connected.  There is no ESSID (even when I try a sudo iwconfig wlan0 essid W44O8 ) and a dhclient gives a timeout with no responses.  

Any help would be greatly appreciated. :)

---

### Post by angryfirelord on 2007-02-21
When you do an essid, you need quotes. Therefore, the command would be sudo iwconfig wlan0 essid "W44O8"

I haven't used ndiswrapper, so I'm just taking a guess.

---

### Post by gradedcheese on 2007-02-21
no, you don't need quotes.  Quotes would only be needed if your ssid contained spaces.  Can you scan?  If you're not even scanning, then there's definitely something wrong, probably at the driver level:

```

iwlist wlan0 scan

```

---

### Post by prongs on 2007-02-21
this is the manual that i followed.  [http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206)

It is very feasible that I messed something up in the driver setup.  I was a little confused about which directories to put files and whatnot.  Anyone familiar with the manual, would it be possible that I have faulty drivers even though a ```
ndiswrapper -l 
``` call shows that the WUSB54GSC driver is installed?

---

### Post by prongs on 2007-02-23
Okay I reinstalled ndiswrapper and checked my dmesg to make sure the driver was installed.  This is what the iwconfig looked like: [http://img135.imageshack.us/img135/2856/screenshot1nq3.jpg](http://img135.imageshack.us/img135/2856/screenshot1nq3.jpg) .  A scan showed no results for wlan0.  Here is a screenshot of the dmesg output: [http://img338.imageshack.us/img338/9455/screenshotib8.jpg](http://img338.imageshack.us/img338/9455/screenshotib8.jpg) .

Thanks in advance for the help.

---

### Post by gradedcheese on 2007-02-23
when you want to share terminal output with us, just paste it into the post, no need for screenshots :)

Ok, so now that wlan0 exists, lets try bringing it up (via the shell because it's easier to talk about).  I am assuming:
1) you have an access point, with no WEP or other encryption enabled
2) your access point provides DHCP

first, try a scan:

```

iwlist wlan0 scan

```

do you see any access points?  is one of them the one you want to connect to.  if so, associate:

```

sudo iwconfig wlan0 essid put_ssid_here

```

now if you run "iwconfig wlan0", it should be associated.  now lets manually get an IP address:

```

sudo ifconfig wlan0 up
sudo dhclient wlan0

```

if that succeeds, then you should be online (try the browser or just ping google.com or something).

EDIT: ah, I think I misunderstood your post: you already scanned and it failed.  can you check that ndiswrapper is loaded?

```

lsmod | grep ndis

```

should return 'ndiswrapper'

---

### Post by prongs on 2007-02-23
okay the output is:

ndiswrapper    /  199316  /   0
rndis_host      /     7860   /   0
cdc_ether      /      7040   /  1   /  rndis_host
usbnet         /       18568 /  2  /  rndis_host, cdc_ether
usbcore      /      134912  /  7 /  ndiswrapper, rndis_host, cdc_ether, usbnet, ehci_hcd, uhci_hcd

---

### Post by gradedcheese on 2007-02-23
hmm... that all looks good.  someone more familiar with ndiswrapper will now hopefully step in and help you resolve this :)

---

### Post by prongs on 2007-02-23
I dont know if if this is related, but when I did ```
ndiswrapper -m
``` it returned that the alias module could not be added.  I tried the command again and it said that the alias was already present in the file, so I assumed that the program it called was just throwing an error for no reason.  Could this have anything to do with it?  Anyone familiar with ndiswrapper that could help?

---

