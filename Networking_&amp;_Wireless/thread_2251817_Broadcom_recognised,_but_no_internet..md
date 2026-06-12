---
title: "Broadcom recognised, but no internet."
date: 2014-11-06
forum: Networking &amp; Wireless
---

### Post by sean69 on 2014-11-06
Either I just don't get "it" or I'm having issues I know lubuntu recognizes my broadcom built-in PCI wireless card but I can't get internet. 
Please assist (also I have a wealth of info in "Xterminal" but don' eve know how to copy paste

---

### Post by sean69 on 2014-11-06
I have wired no issues (like plug and play easy) however wireless hasn't worked out so well.
poking around I found proprietary drivers installed them. It recognizes the driver but beyond that I don't know
 please assist

---

### Post by Bucky Ball on 2014-11-06
*Post moved to own thread.*

Please post the output of:

```
sudo lshw -C network
```

PS: Please do not duplicate post. Confusing, dilutes community effort and decrease your chances of getting support rather than increasing it. Your threads have been merged.

---

### Post by sean69 on 2014-11-06
How do I post reply?

---

### Post by Bucky Ball on 2014-11-06
Highlight the output in a terminal>Edit>copy>Quick Reply on the forums (or Adv Reply)>paste the output here between code tags (see the last link in my signature).

---

### Post by sean69 on 2014-11-06
no copying from terminal from there I got Pasting but I can't copy i read that you highlight (got that) then hit ctrl + shift + C.
When I do that I see ^C in terminal (I know that means I'm doing it wrong)

---

### Post by lisati on 2014-11-06
I'm not sure how well this will work with lubuntu, but you might be able to highlight the text you wish to copy from the terminal using your mouse, then right click and choose the copy option.

---

### Post by sean69 on 2014-11-06
```
*-network:0
       description: Network controller
       product: Broadcom Corporation
       physical id:9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=wl latency=64
       resources: irq:10 memory:d0002000-d0003fff

```
I typed that so copying issue remains and I edited out my ethernet connection because that works (and unneccesary typing)

---

### Post by sean69 on 2014-11-06
that's what  thought as well but when I do it makes the highlighting go away
also thought I got it to work yesterday to add to my frustration)

---

### Post by sean69 on 2014-11-06
```

  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=wl latency=64
       resources: irq:10 memory:d0002000-d0003fff
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:8b:58:0a
       size: 100Mbit/s
       capacity: 100Mbit/s
 capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.10.114 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:10 ioport:2400(size=256) memory:d0006000-d0006fff memory:54000000-5400ffff


``` middle clicking auto copy/pastes it (after highlighting)

---

### Post by Bucky Ball on 2014-11-06
Can you get online with a cable? If so you need to install:

b43-fwcutter
firmware-b43-installer

You have the BCM4306 and possibly the wrong driver. Do the above, reboot if the wireless doesn't come up (with the cable unplugged as it will default to that otherwise) and let's see how far we get.

See [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_driver_.28Open-source.29") for more detail. That page also tells you how to install it with no internet access.

---

### Post by sean69 on 2014-11-06
well before I restart I should let you know My computer doesn't shutdown properly it hangs on the lubuntu loading screen

---

### Post by sean69 on 2014-11-06
Iseem to lost the "taskbar" I know windos so that thing on the bottom so you access stuff is gone

---

### Post by sean69 on 2014-11-07
> **Bucky Ball said:**
> Can you get online with a cable? If so you need to install:

b43-fwcutter
firmware-b43-installer

You have the BCM4306 and possibly the wrong driver. Do the above, reboot if the wireless doesn't come up (with the cable unplugged as it will default to that otherwise) and let's see how far we get.

See [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_driver_.28Open-source.29") for more detail. That page also tells you how to install it with no internet access.

other than the fact that I have a bmc4306 v 2 not a v3 I seem to be worse of with the lack of the default panel
and no internet

---

### Post by Bucky Ball on 2014-11-07
> **sean69 said:**
> other than the fact that I have a bmc4306 v 2 not a v3 I seem to be worse of with the lack of the default panel
and no internet

I say we hold our fire on this thread and you post a new one with a descriptive title about these new issues. You'll improve your chances of help. Get back to this one when the other issues are fixed, because don't think they're related.

Post a link to the new thread here. Thanks.

PS: Not sure I said anything about a V3. Your output says this:

```
product: BCM4306 802.11b/g Wireless LAN Controller
```

Anyhoo, post a link to the new thread. ;)

---

### Post by sean69 on 2014-11-07
[http://ubuntuforums.org/showthread.php?t=2251841&p=13161848#post13161848](http://ubuntuforums.org/showthread.php?t=2251841&p=13161848#post13161848) (panel issue)
not what i wanted but that's the link
[http://ubuntuforums.org/showthread.php?t=2251843&p=13161856#post13161856](http://ubuntuforums.org/showthread.php?t=2251843&p=13161856#post13161856) (shutdown issue)

---

### Post by sean69 on 2014-11-10
now that my other issues have been taken care of, I know first I need to uninstall the propietary driver I put on there. then we can get back to fixing y wifi issue

recap: 
goal uninstall old drivers install new drivers
please assist

---

### Post by sean69 on 2014-11-11
> **Bucky Ball said:**
> Can you get online with a cable? If so you need to install:

b43-fwcutter
firmware-b43-installer

You have the BCM4306 and possibly the wrong driver. Do the above, reboot if the wireless doesn't come up (with the cable unplugged as it will default to that otherwise) and let's see how far we get.

See [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_driver_.28Open-source.29") for more detail. That page also tells you how to install it with no internet access.

I have internet (wireless) yay! thank you!

---

### Post by Bucky Ball on 2014-11-12
Excellent news and thanks for sharing the fix and marking the thread solved (it helps future travelers). I presume it was what I outllined in my previous post. Enjoy. ;)

---

