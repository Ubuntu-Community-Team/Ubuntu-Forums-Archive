---
title: "USB WIFI adapter problems"
date: 2021-10-02
forum: Networking &amp; Wireless
---

### Post by tsmspace on 2021-10-02
I am having wifi problems in lubuntu 20.04 also. Mine are different. 

I got wificrack or whatever, it works. My wifi is functional,,,,,, sometimes. 
very often my wifi will either not connect, or will be unresponsive. I am currently wired to a windows computer on wifi, which works very well,,,,, except I can't rely on that connection, I need to get the wifi to work on the lubuntu computer. 

I don't know what it could be, but others have described it as sounding like a power issue. In the full version of ubuntu, users in this forum have apparently been able to fix a very similar sounding issue (the same basically), by changing their settings for usb power management. They switch off usb power management, then their wifi works. THe problem was that the dongle wasn't able to draw enough power all the time. However, in lubuntu,,, there IS no usb power manager of the sort described. 

I have considered switching to a full version of ubuntu, which may work on this machine, but my other computer does not leave me with this option. It's just old and underequipped for the performance that would justify using it. 

edit::::: I've installed ubuntu 20.04.3 ,, I am using wifi right now after installing the same driver I tried in lubuntu, aircrack from the various links (I'm using the rtl8812 one , I can't say where the post is but it comes up in several threads) ,, I was worried about that the problem was persisting, but I moved the dongle and that fixed it, since it was behind a bunch of metal and reaching through some walls. At the moment, it appears to be a problem only in lubuntu , I had the most recent update from the system updater. (I allow it to upgrade every time,, I've considered never upgrading, but I always let it get updates) . if I feel that the situation continues in ubuntu, I will come back and say so, in lubuntu I would still be able to use the wifi for long whiles before having issues, but I feel that it will actually not persist here, and it will work normally. 

as for the wifi range on my other computer,, it IS in a different place, but the dongle is only a few feet from the warehouse wifi hub. It should work pretty smoothly as far as connection strength, my phone and laptop work superb, I am thinking it's just lubuntu. 

actually I'm downloading ubuntu now, and probably will install it here on this computer to see what happens. 

the computers vary, but the wifi dongles are both tplink rtl88 series. this one is a t2u , the other one is a wn275 or something like that. both computers are builds, not prebuilts. I used to think the motherboard must be weak for power to usb, based on discussions I had on facebook,, however I am certain this motherboard runs wifi just fine, as in windows 7 it worked like a rocket. The consistent factor is lubuntu. I don't recall having this issue in 18.04, and it appeared in 20.04 but not immediately,, so it appears to be fairly recent of an issue. I looked on lubuntus page,, it does appear to show 19 but not 20.04 as an option,, the upgrade is via the software updater, I wonder if I should roll to 19.01 or whatever??

---

### Post by QIII on 2021-10-02
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2467621").

Please do not hijack the threads of other users.  They, and you, deserve individual attention.

You even said yourself that your issues are different.  There is no benefit to the OP for you to drag the assistance off in another direction.

---

### Post by tsmspace on 2021-10-02
sorry , newbie and wasn't thinking about it

---

### Post by morrownr on 2021-10-04
I don't fully understand your situation but I'll point you to the following site:

[https://github.com/morrownr?tab=repositories](https://github.com/morrownr?tab=repositories)


Each repo, including the one for the 8812au chipset, includes a lot of information to include installation instructions. There is also the USB-WiFi repo that contains a LOT of information regarding USB WiFi adapters on Linux.

Each of the drivers at the above site are maintained and heavily used. Let us know how it goes.

---

### Post by tsmspace on 2021-10-04
It appears to be lubuntu specific, and fairly recent. Technically the wifi works, but cuts out all the time. It appears to not be happening at all on another machine that is modern enough to run full ubuntu. 

This site you've linked is VERY interesting and will probably help me a lot. Thank you!!

---

### Post by morrownr on 2021-10-05
I used to use Lubuntu but a few years ago it started getting away from being what I needed so I moved on. Here is what I run on my old systems these days:

[https://www.raspberrypi.org/software/raspberry-pi-desktop/](https://www.raspberrypi.org/software/raspberry-pi-desktop/)

Yes, that is the x86 version of the Raspberry Pi OS. I know the drivers at the link I posted work on this OS because it is one of the test platforms that I use.

---

