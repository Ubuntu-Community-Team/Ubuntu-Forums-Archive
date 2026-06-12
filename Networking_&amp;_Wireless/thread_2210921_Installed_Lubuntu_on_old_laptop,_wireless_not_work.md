---
title: "Installed Lubuntu on old laptop, wireless not working"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by BlueGene1402 on 2014-03-13
I installed Lubuntu 13.10 on my dad's old laptop (hp compaq nx6310) and wifi isn't working.

I  don't really know how any of this stuff works or what it means, but I  did 2 things to try & get the ball rolling after reading a  few other threads:

1. I tried Ethernet
Wired  connection is weird. It's recognised, says it's connected but it's not  really there. It's not exactly zero non-existent. Extremely slow &  only opens 1 page then completely  dies. So it's only really connected in name.

2. I tried this command
**sudo lshw -numeric -C network**
Output:
**configuration: autonegotiation=on broadcast=yes driver=b44  driverversion=2.0 duplex=full ip=192.168.1.2 latency=64 link=yes  multicast=yes port=twisted pair speed=100Mbit/s**

I can't copy & paste to or from the terminal (reported that problem [here]("http://ubuntuforums.org/showthread.php?t=2210754")) so I've manually typed that. Judging from other posts it looks like the important bit. I hope it's relevant & helpful.

Work your magic you lovely people.

---

### Post by chili555 on 2014-03-13
Do you want magic ethernet or magic wireless? Please run and post:```
lspci -nn | grep -e 0200 -e 0280
```If you can't copy and paste from the terminal, I guess a pencil will have to do.

---

### Post by BlueGene1402 on 2014-03-13
I'd like to be able to use wireless, please. I checked wired in case that helps shed light on the problem & maybe aid with the diagnosis.

Here's what I got from **lspci -nn | grep -e 0200 -e 0280**[B]

02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)[/B]
**08:00.0 Network controller [0280]: [B]Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] **(rev 01)
[/B]

I was worried I would have to type large amounts of text. Envious of your right-click functioning in terminal.

Awaiting further instructions, thank you.

---

### Post by chili555 on 2014-03-13
Please hook up the ethernet temporarily. Open a terminal and do:```
sudo modprobe b44
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and tell us if it's working.

---

### Post by BlueGene1402 on 2014-03-13
I think it essentially worked, because it now recognises wifi & attempts to connect. But some other problem might be in place (maybe not even Lubuntu related, maybe general network issue?) because it just keeps going round & round and doesn't connect:

[IMG]http://i839.photobucket.com/albums/zz320/brucewhore/screenshot_zps653b411e.png[/IMG]

What I did gain is that wired is now working, hurrah. At least I'm able to install some applications, like the one I used to make this screenshot.

---

### Post by chili555 on 2014-03-13
Now that the ethernet is working, I suggest you fully update your installation and give us a new report.

---

### Post by BlueGene1402 on 2014-03-15
I seem to have lost ethernet. I was running the software updater but the process was interrupted when the electricity cut off. Lubuntu rebooted (dead laptop battery) & the router rebooted & somewhere along the way I lost it. Power failures are not uncommon on a good day & with the thunderstorm it's a lot more frequent. Hence my late reply.

---

### Post by BlueGene1402 on 2014-03-15
Oh the electricity just cut off again & when I switched everything  back on it's now all working!!!! Wifi included, hurrah. Thank you so  much **chili555** I really appreciate it. I've rebooted a couple of times just to make sure it's not a fluke & wifi still going strong :)

---

### Post by chili555 on 2014-03-15
> **BlueGene1402 said:**
> Oh the electricity just cut off again & when I switched everything  back on it's now all working!!!! Wifi included, hurrah. Thank you so  much **chili555** I really appreciate it. I've rebooted a couple of times just to make sure it's not a fluke & wifi still going strong :)Great news! Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by BlueGene1402 on 2014-03-15
I did mark it SOLVED! By the way it also somehow fixed the right-click and copy/paste problem in terminal!!

---

