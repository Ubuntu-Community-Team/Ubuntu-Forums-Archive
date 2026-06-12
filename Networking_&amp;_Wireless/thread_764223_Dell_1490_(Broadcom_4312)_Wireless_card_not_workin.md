---
title: "Dell 1490 (Broadcom 4312) Wireless card not working"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by mailforbiz on 2008-04-23
Hi

I just bought a Dell XPS 1530 notebook and was dismayed to find that the wireless doesnt work out of the box with 7.10. I tried to follow instructions in one of the posts about how to get Broadcom 4306 to work with Ndiswrapper. That didn't work either - in fact, the "Enable wireless" entry disappeared altogether from Networking menu . I don't see an entry under the list of supported cards for Broadcom 4312. Does this mean that there is no way to get wireless working on this notebook? If I have to return this notebook, that would suck because I got a great  deal on it.

Would appreciate any help - I desperately want Ubuntu to work on my laptop so I can finally be free of Micro$lavery.

Thanks.

---

### Post by dstew on 2008-04-23
Did you look in the Restricted Drivers Manager (System --> Administration) to see if you can install the firmware for the Broadcom card? See this [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy") before you give up on the Linux driver.

---

### Post by dmizer on 2008-04-23
try following this thread here.  it's four pages, but i think it'll be worth your while: [http://ubuntuforums.org/showthread.php?t=740632](http://ubuntuforums.org/showthread.php?t=740632)

---

### Post by mailforbiz on 2008-04-24
Hi Guys

Whoohoo! I was able to make wireless work with the fwcutter restriced driver/firmware!! 

I understand this is somewhat slower but atleast I am able to connect. Any idea what are the highest speeds possible with this in practice? 

Dmizer, I did try the post you linked to BEFORE I tried the restricted driver and I couldn't get wlan0 to work so don't know if my card is incapable of working with ndiswrapper or its something else.

Anyways, thanks guys for the helpful hints. Now that I have wireless working, I can begin the process of slowly weaning away from Windoze. I have to get a few more things working before I pitch to my wife the idea of a Windows-less lappy. ;-)

Regards,
HT

---

### Post by GrandpaLeaman on 2008-04-24
> **mailforbiz said:**
> Hi Guys

Whoohoo! I was able to make wireless work with the fwcutter restriced driver/firmware!! 

I understand this is somewhat slower but atleast I am able to connect. Any idea what are the highest speeds possible with this in practice? 

Dmizer, I did try the post you linked to BEFORE I tried the restricted driver and I couldn't get wlan0 to work so don't know if my card is incapable of working with ndiswrapper or its something else.

Anyways, thanks guys for the helpful hints. Now that I have wireless working, I can begin the process of slowly weaning away from Windoze. I have to get a few more things working before I pitch to my wife the idea of a Windows-less lappy. ;-)

Regards,
HT
I am using a 4311 Broadcom card. when I enter "lshw -C network" in terminal it says that the logical name is 'eth1'. Does 'wlan0' need to be changed to 'eth1'? And how do you do that? Is there someone out there who can give us some direction? I'm old and, sadly, may expire before this is resolved.

---

### Post by mailforbiz on 2008-04-25
I thought it was just the logical name the kernel assigned and the fact that it was eth1 vs wlan0 was somehow an artifact of the restricted driver use by the kernel. But since I don't have a need for a second wired interface anyways, i'm not too bothered if its eth1/wlan0 unless it makes a functional difference for my wireless. If I find out more, I'll post here but for now I'm gonna let it slide in lieu of other things that don't work (eg hibernate).

Grandpa, the way you're keeping your humor, don't worry, you'll outlive my children. ;-) My Best Regards.

---

### Post by dstew on 2008-04-25
The interface name depends on the driver. For a wireless card it can be eth0, eth1, or wlan0, or ath0, or ra0 or whatever0, depending on how the driver writer wants it.

---

