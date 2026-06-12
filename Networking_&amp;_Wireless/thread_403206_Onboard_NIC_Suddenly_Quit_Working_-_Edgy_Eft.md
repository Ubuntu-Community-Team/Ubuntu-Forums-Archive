---
title: "Onboard NIC Suddenly Quit Working - Edgy Eft"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by smittym on 2007-04-06
I am running Edgy Eft and have had no issues at since installing in January.  I have an MSI Diamond K9N, an AMD X2 64 with two onboard Gigabit NICs.

As I said, everything has operated flawlessly until now.  I used the machine last night and then when I booted up today, the nics were nonfunctional.  I can see the cards in my lshw output, but when I try to use ifconfig eth0 up (which is the card I was using), I get nothing.  I have tested the cables with the laptop I am working from now and they are fine and I have this laptop plugged into the same router and am able to connect to the network without issue.  The only recent upgrades to the machine have been an xserver upgrade on April 4 and some upgrades to kdelibs on April 5.  I am at a total loss.  Any help would be greatly appreciated.

---

### Post by x64Jimbo on 2007-04-06
Try booting a LiveCD and see if they work. I've had a couple MSI boards' integrated NICs die on me, so I'm just trying to see if the device or the OS is at fault.

---

### Post by smittym on 2007-04-06
I'll try that and post the results.

---

### Post by smittym on 2007-04-06
The LiveCD did not work either.  I can see the cards when I run ifconfig though, so it seems like they are recognized, but that's it.  I guess they could be goners.  I don't have any other wired NICS lying around, but I did hook up an old USB wireless NIC that I have.  Network Manager recognized the wireless nic, but I could not connect through it either.  Any other thoughts???

---

