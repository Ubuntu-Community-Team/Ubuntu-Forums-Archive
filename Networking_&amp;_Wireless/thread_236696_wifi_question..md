---
title: "wifi question."
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by dannyb37 on 2006-08-15
Hi,
I don't have a problem yet, just I am abit conserned about the wifi when I install linux (later today if the hard drive comes).

There has been alot of questions about accsessing wireless networks but no internet connection.

I tried the live ubuntu 6.06 cd ealyer this week and i had this problem.

But I used to have ubuntu installed and not have this problem.

Its still the same hardware, the only thing that had changed was the router, but that shoulden't cause a problem, right?

The wifi works well in windows but not in the live cd.

Will it probably work when i install linux or probably not?
And if not, how do I fix it?

Thanks

---

### Post by hollowhead on 2006-08-15
In my limited experience probably not.  I tried running off the CD and dapper detected my wifi device in my laptop quite correctly but the light didn't come on.  Also on boot an error came up about a missing file.  I installed and the same thing happened.  Luckily someone had wriiten a script for NDISwrapper and great guide (sorry hero cannot remember who) and I downloaded onto a stick copied it onto my ubuntu box and it worked on reboot!  I'm sure all is not lost and there will be a way to get your hardware going.

---

### Post by bensexson on 2006-08-15
> **dannyb37 said:**
> Hi,
I don't have a problem yet, just I am abit conserned about the wifi when I install linux (later today if the hard drive comes).

There has been alot of questions about accsessing wireless networks but no internet connection.

I tried the live ubuntu 6.06 cd ealyer this week and i had this problem.

But I used to have ubuntu installed and not have this problem.

Its still the same hardware, the only thing that had changed was the router, but that shoulden't cause a problem, right?

The wifi works well in windows but not in the live cd.

Will it probably work when i install linux or probably not?
And if not, how do I fix it?

Thanks

What wireless adapter are you using?

---

### Post by dannyb37 on 2006-08-15
Its enbuilt into my laptop!
All I know is "Gemtek 802.11b/g Wireless LAN" if that means anything.

Thanks,

---

### Post by bensexson on 2006-08-15
According to my Google search your wireless adapter uses a Broadcomm BCM4306 chipset.  I am using the same chipset.  The reason it is not working now is because of the new bcm43xx driver.  Refer to this wiki article: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper) I personally use ndiswrapper because I couldn't get bcm43xx to go 54 mbps.

---

### Post by dannyb37 on 2006-08-15
Thanks, but how do I install ndiswrapper?

Is it

```
sudo apt-get install ndiswrapper
```?

And will that let me use the internet via wifi? :)

---

### Post by hollowhead on 2006-08-16
Yes but you'll have to install the windows driver.  This script worked for me [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wifi+manager](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wifi+manager), however, not sure the script is driver specific?

---

