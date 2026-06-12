---
title: "please need help getting sprint evdo modem to work"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by jupiter600 on 2008-09-03
i have oqo model o2 with builtin sprint broadband rev a modem

it works with windows fine

in ubuntu i cant get it to work

i went to sprint site and followed the ubunto pdf file but the modprobe commands using diff product and version numbers dont work

any other commands or drivers for a sprint u720 novatel modem to work?

ubunto is useless to me if i cant access the net

---

### Post by pytheas22 on 2008-09-03
Did you take a look [here]("http://ubuntuforums.org/showthread.php?t=366229")?

If that doesn't help, please post the output of this command:
```

lsusb
```

while the modem is plugged in (it is a USB device, right?).

---

### Post by jupiter600 on 2008-09-03
> **pytheas22 said:**
> Did you take a look [here]("http://ubuntuforums.org/showthread.php?t=366229")?

If that doesn't help, please post the output of this command:
```

lsusb
```

while the modem is plugged in (it is a USB device, right?).

Yeah i went there didnt work, read a bunch of other places till didnt work:

lsusb:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 1410:2120
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 1557:0004
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by jupiter600 on 2008-09-03
> **jupiter600 said:**
> Yeah i went there didnt work, read a bunch of other places till didnt work:

lsusb:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 1410:2120
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 1557:0004
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

lol ok i see my problem now
my modem device number was incorrect,2120 was not in the list on sprint's pdf for linuix
let me try with these codes thanks for that lsusb! ima a linuix newbie sorry

---

### Post by jupiter600 on 2008-09-03
Thanks a lot problem solved

The instructions on sprint site had the product ID's just not the correct one for my modem. My model Id is apparantly 2120. Anybody know what type of modem that is? lol

(i have an oqo and modem is internal so ive never seen it,i just know it has to be a novatel)

---

### Post by pytheas22 on 2008-09-03
If you google "1410:2120" not much comes up, so probably the modem is pretty new and not well documented.  Sprint or whoever made it may have modified an existing model, but not bothered to change the name it's sold under, or the documentation that comes with it.  Unfortunately this a problem with a lot of hardware manufacturers, who sell different devices under the same name without making clear which is which.  Usually the *lsusb*, *lspci* and *lshw* commands do a good job of identifying hardware, though, regardless of the name on the box.

But I'm glad it's solved now.

---

### Post by jupiter600 on 2008-09-03
> **pytheas22 said:**
> If you google "1410:2120" not much comes up, so probably the modem is pretty new and not well documented.  Sprint or whoever made it may have modified an existing model, but not bothered to change the name it's sold under, or the documentation that comes with it.  Unfortunately this a problem with a lot of hardware manufacturers, who sell different devices under the same name without making clear which is which.  Usually the *lsusb*, *lspci* and *lshw* commands do a good job of identifying hardware, though, regardless of the name on the box.

But I'm glad it's solved now.

thanks again, one last thing
get it started i unload the usbserial driver and then type
sudo modprobe usbserial vendor=0x1410 product=0x2120
and the modem works

now how do i get that to load at boot?
i type those 2 lines in etc/modules but that still didnt work
i had to open a terminal window and manually type it

---

### Post by pytheas22 on 2008-09-03
Yes, /etc/modules is only for listing modules that need to be loaded at boot, not entire commands.  However you can easily write an init script to do what you need.  First type:
```

sudo gedit /etc/init.d/modem-up.sh
```

A blank file will open.  Add to it these lines:
```

#!/bin/bash

rmmod usbserial
modprobe usbserial vendor=0x1410 product=0x2120
```

Then save and close the file.  Then run these commands so that the system knows to execute the script at boot:
```

cd /etc/init.d
sudo -s
chmod +x modem-up.sh
update-rc.d modem-up.sh defaults
```

That should do it.  If not, let me know.

---

### Post by jupiter600 on 2008-09-03
> **pytheas22 said:**
> Yes, /etc/modules is only for listing modules that need to be loaded at boot, not entire commands.  However you can easily write an init script to do what you need.  First type:
```

sudo gedit /etc/init.d/modem-up.sh
```

A blank file will open.  Add to it these lines:
```

#!/bin/bash

rmmod usbserial
modprobe usbserial vendor=0x1410 product=0x2120
```

Then save and close the file.  Then run these commands so that the system knows to execute the script at boot:
```

cd /etc/init.d
sudo -s
chmod +x modem-up.sh
update-rc.d modem-up.sh defaults
```

That should do it.  If not, let me know.

Well pytheas22, i have to admit, you are THE MAN !!!! (unless ur a female lol) BUt thanks again that worked perfect.


And one more thing, everything is fine but i have no sound
once again i have a OQO model 02 computer (real small laptop)
any place on here i can go to search for audio drivers or something for it?

---

### Post by pytheas22 on 2008-09-04
I'm glad the modem is all set :)

To be honest I really don't know much about how sound works in Linux, although I think that many people with newer computers have sound cards that aren't supported by the version of alsa ("advanced Linux sound something") that ships with Ubuntu, so they need to compile the latest cutting-edge version of alsa from source.  This likely describes your situation.

I do know of this [guide]("https://help.ubuntu.com/community/SoundTroubleshooting") that has helped many people.  It's a good place to start.  If it doesn't help you, post the output of "lspci -nn" here and I'll see if I can find anything useful on Google pertaining to your audio device.

---

### Post by jupiter600 on 2008-09-04
> **pytheas22 said:**
> I'm glad the modem is all set :)

To be honest I really don't know much about how sound works in Linux, although I think that many people with newer computers have sound cards that aren't supported by the version of alsa ("advanced Linux sound something") that ships with Ubuntu, so they need to compile the latest cutting-edge version of alsa from source.  This likely describes your situation.

I do know of this [guide]("https://help.ubuntu.com/community/SoundTroubleshooting") that has helped many people.  It's a good place to start.  If it doesn't help you, post the output of "lspci -nn" here and I'll see if I can find anything useful on Google pertaining to your audio device.

OK great! ima go check that page out

herees the dump:

00:00.0 Host bridge [0600]: VIA Technologies, Inc. CX700 Host Bridge [1106:0324] (rev 03)
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CX700 Host Bridge [1106:1324]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CX700 Host Bridge [1106:2324]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. CX700 Host Bridge [1106:3324]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CX700 Host Bridge [1106:4324]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CX700 Host Bridge [1106:7324]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI Bridge [1106:b198]
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. Unknown device [1106:0581]
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 90)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 90)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 90)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 90)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. CX700 PCI to ISA Bridge [1106:8324]
00:11.7 Host bridge [0600]: VIA Technologies, Inc. CX700 Internal Module Bus [1106:324e]
00:13.0 PCI bridge [0604]: VIA Technologies, Inc. CX700 Host Bridge [1106:324b]
00:13.1 PCI bridge [0604]: VIA Technologies, Inc. CX700 PCI to PCI Bridge [1106:324a]
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CX700M2 UniChrome PRO II Graphics [1106:3157] (rev 03)
02:01.0 Audio device [0403]: VIA Technologies, Inc. VIA High Definition Audio Controller [1106:3288] (rev 10)
03:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR5413 802.11abg NIC [168c:001b] (rev 01)
03:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

---

### Post by pytheas22 on 2008-09-04
I googled a little bit for your sound card (VIA High Definition Audio Controller rev 10) + Ubuntu.  There seem to be many others who have trouble with the same card, although unfortunately most of the threads that I found were unsolved.  One guy did say that following the instructions [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto") helped.  Beyond that, I'd just work my way through that sound-troubleshooting guide, which should lead you to an answer.

Let us know if after checking out both those guides you still have no sound.

---

