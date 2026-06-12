---
title: "Ubuntu on USB Hard Drive - Different PC - Different NIC = No Internet"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by thebacotman on 2010-09-12
Hi Ubuntu masters,

Out of curiosity I installed Ubuntu 10 64 bit (full OS) on my USB Hard Drive (w enclosure).
When I installed the Ubuntu, network card was detected, sounds was there, video card is decent, it even  play the compiz animation.
Nice! And I'm really impressed!

Then I shutdown my laptop and move this USB Hard to a different laptop.
I booted from  the USB hard drive and it manage to load gnome just fine ... however no internet, no Sound, VGA is still ok.

So I click to system > administration > hardware drivers
And a new network card Broadcom was detected.

However Ubunutu keep trying to contact the live server for downloading the driver.

Q1: Is there a way so we can pre-download the network card into a directory and ask Ubuntu to look from that folder?
Q2: If there is, I feel like want to download all possible wireless network card drivers - just in case. Any suggestion where should I look?

Thanks in advance!
Ron

---

### Post by jerome1232 on 2010-09-12
Can't you just temporarily hook the laptop up via ethernet to download the driver.

---

### Post by coffeecat on 2010-09-12
> **thebacotman said:**
> So I click to system > administration > hardware drivers
And a new network card Broadcom was detected.

I presume the Broadcom card is the wireless NIC. There's a licensing issue with Broadcom. The firmware and/or the driver cannot be included in a default install. This is down to Broadcom, although they have just had a change of heart and we may see better things from next year. Anyway, for the present, have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Seems to me you've got three options:

Connect the laptop temporarily with an ethernet cable.

Go back to the first laptop and download the necessary packages, and then go back to the Broadcom machine to use the Hardware Drivers utility.

Create a live CD with your Ubuntu ISO and use that as a repository as described in the link.

---

### Post by thebacotman on 2010-09-12
[SOLVED!]
Thanks Jerome and Cofeecat!

I switch back to the first laptop and do a download for broadcom-sta-common
```
#aptitude download broadcom-sta-common -d
```

And then I moved to the second laptop (the one that needed this driver)
Then when I do an #aptitude install broadcom-sta-common
it didn't have the dependencies ... kind of dissapointed... oh well


So I tried the direct cable connection with my router and of course that solved the internet connection problem.
And I can download the drivers easily.

Thanks a lot guys.
Changing OS from windows to linux is quite challenging.
But so far I'm very impressed with Ubuntu.
Cheers!

---

### Post by coffeecat on 2010-09-12
> **thebacotman said:**
> Changing OS from windows to linux is quite challenging.
But so far I'm very impressed with Ubuntu.

Bet you couldn't install Windows to a USB drive and have it booting up on different machines without demur! :wink:

Good luck!

---

