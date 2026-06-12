---
title: "Ndiswrapper working, or is it?"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by Aninhumer on 2006-07-23
I have followed the instructions on the wiki to install ndiswrapper on my computer. The drivers and hardware are present however when I actually try and actuvate the device with ifup, or with the networking options it does not connect.
I think at least some elements of the drivers are working as the networking options for wlan0 detected my access point fine.

The output of lspci was:
```
0000:05:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```

And I have tried using the mrv8000c drivers both from the internet and on my driver disk, with both XP and 2000 versions.

---

### Post by Dr. Nick on 2006-07-23
was the device present at all before messing with ndiswrapper? Run 

lsmod

and look at the line with ndiswrapper loaded, does it show any other drivers loaded for your card?

I would also disable all wep/wpa until I got it to connect atleat once, Its just one less thing to get in the way

---

### Post by Aninhumer on 2006-07-24
I am not sure what this output means so I'll attach it.
I know wlan0 wasn't present before I installed the drivers.

I tried once without WEP, but I'm not sure if I did it right.
Do you just put in a blank key in the WEP section?
Or should it not give an option to?

---

### Post by Dr. Nick on 2006-07-24
ok, ill explain the lsmod thing a bit

usbcore               138948  4 ndiswrapper,ehci_hcd,uhci_hcd

means that ndiswrapper driver  is loaded for a device attached to your usb, so thats a good sign. If you had seen anything else on that line besides the ehci_hcd,uhci_hcd drivers then that could mean their was a driver conflict.

If you have logged into your router through a wired connection and disabled security (wep,wpa) then you should just leave the wep field blank.

---

### Post by beemer on 2006-07-24
I spotted this line in your lsmod:

2564  0 mrv8k

I would try this:

sudo vi /etc/modprobe.d/blacklist

add the line:

blacklist mrv8k

save and reboot

Beemer

---

### Post by Aninhumer on 2006-07-24
I tried that but it doesn't appear to make any difference.

And the mrv8k is definately gone from the lsmod output.

---

### Post by Dr. Nick on 2006-07-24
I suppose you have a wired conenction aswell? I found it easier if I went into the network control panel and disabled my ehternet, then enabled the wireless. You can set the wpe to ASCII (plain) and try that aswell

---

### Post by Aninhumer on 2006-07-25
Thank you, for your help. I don't know what I did different this time, but I managed to get a wireless connection with WEP diabled (and pulled out my ethernet cable to make sure). However I still can't get a connection with WEP enabled, is there anything I can do to help this.

---

### Post by Dr. Nick on 2006-07-25
when you set the wep key are you typing in the passphrase or the full hex key? You need the full hex key and may need to change the option in the wireless config form "plain" to "hex" What I did was use a wired conenction to go into tthe router then just copy and paste the hex key into the wireless config.

---

### Post by Aninhumer on 2006-07-25
I definately used the hexidecimal mode, and the full key.
My router doesn't appear to have an option to use anything other than a raw encryption key.
I'll try copy and pasting.

---

### Post by wislon on 2006-07-25
> **Aninhumer said:**
> I definately used the hexidecimal mode, and the full key.
My router doesn't appear to have an option to use anything other than a raw encryption key.
I'll try copy and pasting.

EDIT: It didn't work.

I saw a link using wpa_supplicant that allowed one to apparently use WEP, without having to actually set this in the network config itself, instead you set it up as a config for wpa_supplicant and let it take care of it. It's a pain to have to launch wpa_supplicant manually every time, but it may help with debugging the connection.

Google for 

```
wpa_supplicant +WEP +"{"
```

You'll find a lot of info.

Here's some other links to look at too (these helped me)

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA](http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA) (there's some stuff about WEP in there too)
[http://www.vollink.com/gary/deb_wifi.html](http://www.vollink.com/gary/deb_wifi.html)
[http://lists.freebsd.org/pipermail/freebsd-mobile/2005-October/007129.html](http://lists.freebsd.org/pipermail/freebsd-mobile/2005-October/007129.html)

A couple of other things to think of (I bumped my head on these when I was setting up WPA with my dlink USB card).

1. The WAP had MAC filtering turned on, and not a damn could I connect to it until I'd filled in my card's MAC address. Simple, but it took me almost 20 minutes to realise it. It could see the WAP, but not associate. Of course.

2. Even after I'd enabled the MAC, it still wouldn't associate because I hadn't filled in the WPA keyphrase. My advice, while testing is to turn OFF MAC address filtering and any encryption if possible.

3. Check the length of your WEP key. If you're using 64bit (i.e 40bit) WEP, the key length will be 10 characters (in ASCII mode). If it's 128bit, it'll be 26 characters.

Hope that helps! :)

---

### Post by Aninhumer on 2006-07-25
I don't have MAC filtering turned on

Are you sure it's 10 characters in ASCII mode?
Wouldn't that be 80bit?

---

### Post by Aninhumer on 2006-07-26
Is there any reason why the WEP wouldn't work with my card, without the "wpa_supplicant".

---

### Post by bensexson on 2006-07-26
Post the output from sudo iwconfig.  You may want to blank your WEP key.

---

### Post by Aninhumer on 2006-07-26
Aha, the settings aren't set in the iwconfig. But they are on the Networking tool.

I tried: "sudo iwconfig essid G604T_WIRELESS"
It returns "Error : unrecognised wireless request "G604T_WIRELESS""

Hmm...

EDIT: The same for the WEP key.

---

### Post by bensexson on 2006-07-26
The correct syntax would be sudo iwconfig wlan0 <settings>.

---

### Post by Aninhumer on 2006-07-26
So what command should I have used?

As far as I can see, that's the syntax I used.

---

### Post by bensexson on 2006-07-26
sudo iwconfig wlan0 essid G604T_WIRELESS.  You need to tell iwconfig which interface to configure.

---

### Post by Aninhumer on 2006-07-26
Whoops, I knew I'd missed something obvious.

I tried the new command but this returns:

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.

---

### Post by bensexson on 2006-07-26
What is the output of ndiswrapper -l?

---

### Post by Aninhumer on 2006-07-26
Installed ndis drivers:
mrv8000c                driver present, hardware present

---

### Post by bensexson on 2006-07-26
Well I am stumped now.  I looked at ndiswrapper's wiki and your card is supported.  It also uses a prizm54  chipset and should be supported natively by ubuntu.  Why did you decide to use ndiswrapper?

---

### Post by Aninhumer on 2006-07-26
When I first booted with the card in it didn't appear in the networking menu, so I didn't think there was an available driver.
If I could use a native driver I would prefer that.

---

### Post by bensexson on 2006-07-26
We're getting a little out of what I can help with.  Actually it looks like the ndiswrapper opage was wrong.  It is a Marvell chipset not a prizm54.  There is a native driver.  Its page is here: [http://www.saillard.org/news/2005-10-04_libertas.php](http://www.saillard.org/news/2005-10-04_libertas.php).  Also look for help with ndiswrapper here: [http://ndiswrapper.sourceforge.net/support.html](http://ndiswrapper.sourceforge.net/support.html)

---

### Post by Aninhumer on 2006-07-26
Well thanks for your help, I'll try asking on the ndiswrapper forums.

And there may be a native driver by christmas :)

---

