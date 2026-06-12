---
title: "Wi-Fi not working (What a shock!!)"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-10-21
Hi again, I have another question to ask.

Ok, I've just advised my friend to get a Linksys Wi-Fi stick so that he can surf the web
at home as his Laptop doesn't have inbuilt wi-fi.

So I went on-line and bought the same stick as myself (From Amazon).
(It's the Linksys WUSB54GC).

However when I received it, it has the same model No on the box, but It looks completely
different. (Mine is silver and larger, whereas his is much more compact and black
it states its version 3 on the new stick, I don't see any version No on my stick).

When I put the stick into the usb drive, I don't seem to get much response.
(The led doesn't flash or give me any indication that its working).

Typing lsusb into the terminal on the laptop reveals this =

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0077 Linksys
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


So where do I go from here? Do I need to mount the stick or alter any files??


Additional notes...

The Laptop is an Acer travelmate 2312LM_L running Ubuntu 8.10 and I've just downloaded
all 680+ MB of updates and kernel and so-forth. (Tried 9.04 recently and couldn't use it
as it couldn't find the reops to download any type of software at all).

I tried the stick on my Ubuntu desktop (9.04) and got no response. However when I tried
it on my Vi$ta partition, Vi$ta states that its found new hardware (bloody hell!) and
propmts me to install new drivers. I stopped there as I didn't want to bork the wi-fi on
my Vi$ta set-up.

Any help or advice would be VERY much appreciated

---

### Post by kwacka on 2009-10-21
See this thread.

[HTML]http://ubuntuforums.org/showthread.php?t=1273401[/HTML]

---

### Post by bkratz on 2009-10-21
> **kwacka said:**
> See this thread.

[HTML]http://ubuntuforums.org/showthread.php?t=1273401[/HTML]




Here another good one (it must be-- it is 33 pages long!). See the last page first since the links to the files have moved and he gives a new address.

[http://ubuntuforums.org/showthread.php?t=1155941](http://ubuntuforums.org/showthread.php?t=1155941)

Good Luck

---

### Post by Mike_IronFist on 2009-10-21
> **GeordieJedi said:**
> Hi again, I have another question to ask.

Ok, I've just advised my friend to get a Linksys Wi-Fi stick so that he can surf the web
at home as his Laptop doesn't have inbuilt wi-fi.

So I went on-line and bought the same stick as myself (From Amazon).
(It's the Linksys WUSB54GC).

However when I received it, it has the same model No on the box, but It looks completely
different. (Mine is silver and larger, whereas his is much more compact and black
it states its version 3 on the new stick, I don't see any version No on my stick).

When I put the stick into the usb drive, I don't seem to get much response.
(The led doesn't flash or give me any indication that its working).

Typing lsusb into the terminal on the laptop reveals this =

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0077 Linksys
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


So where do I go from here? Do I need to mount the stick or alter any files??


Additional notes...

The Laptop is an Acer travelmate 2312LM_L running Ubuntu 8.10 and I've just downloaded
all 680+ MB of updates and kernel and so-forth. (Tried 9.04 recently and couldn't use it
as it couldn't find the reops to download any type of software at all).

I tried the stick on my Ubuntu desktop (9.04) and got no response. However when I tried
it on my Vi$ta partition, Vi$ta states that its found new hardware (bloody hell!) and
propmts me to install new drivers. I stopped there as I didn't want to bork the wi-fi on
my Vi$ta set-up.

Any help or advice would be VERY much appreciated

Once you plug in a USB Wifi adapter, it should just work. That is, you should be able to just click your network icon, pick a wireless network, and connect to it.

When I set up my Dad's desktop machine with a WiFi stick (in this case, a Netgear one), it didn't really indicate that it had detected the thing once I plugged it in, but I was able to click the network icon in the Notification area, connect to a network, and things went smoothly from there. So let us know if you are able to see and connect to wireless networks.

---

### Post by Mike_IronFist on 2009-10-21
> **Mike_IronFist said:**
> Once you plug in a USB Wifi adapter, it should just work. That is, you should be able to just click your network icon, pick a wireless network, and connect to it.

When I set up my Dad's desktop machine with a WiFi stick (in this case, a Netgear one), it didn't really indicate that it had detected the thing once I plugged it in, but I was able to click the network icon in the Notification area, connect to a network, and things went smoothly from there. So let us know if you are able to see and connect to wireless networks.

Whoops, I think I misinterpreted your post. If so, ignore what I just said. Sorry.

---

### Post by GeordieJedi on 2009-10-21
Thank you all for the prompt replys, It's much appreciated.

I think I'll just buy a new dongle. I've seen I dont fancy trying to
get my mate to re-compile his kernel or mess about with config files.
(He's really not a computer person at all).

I think I'll just keep the dongle myself maybe try some of the fixes, and if not, hopefully it'll be fixed in a newer release.

Cheers!

---

