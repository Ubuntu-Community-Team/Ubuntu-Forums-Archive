---
title: "Use a netgear adapter with Ubuntu 8.04"
date: 2015-08-28
forum: Networking &amp; Wireless
---

### Post by Daniel_Jackson on 2015-08-28
Heres a little back story, just got a decent pc but have had tons of issues with windows not recognizes the drivers for tons of things. Also, dell quit supporting the drivers I need. So I decided to get ubuntu. Unfortunately I had to downgrade from the latest, back to 8.04 because of some issues (I guess). 
Good news is, ethernet works. Which means I do have internet on the machine. But before I do a full install (Booted from a usb), I want to make sure I can have wifi working on it as well. 

I do know that there are plenty of tutorials on how to get this thing to work, but none of them really make sense to me. Plus they are mostly for 10+, as I am running 8.04, I'm not sure that they will work. 

The device I'd like to get running is : Netgear Wireless N-300 USB Adapter WNA3100 ;
As I stated above, I am booted from a usb using Ubuntu 8.04 ;

Obviously I am super new to this, and I have no idea what I am doing. Not even sure how to figure out how to see a list of devices connected to the machine..

Any help would be awesome, and if you need more info let me know.

---

### Post by TheFu on 2015-08-28
Please move to a supported release to get help.  12.04 LTS or 14.04 LTS.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by kurt18947 on 2015-08-28
You're not making this easy on your self :D. I certainly agree with TheFu, I'd really want to run the most recent LTS my machine would support. More recent releases run more recent kernels which often have hardware driver updates missing from older releases. For example, WiFi support is MUCH better in 14.04 than it is in 8.04. Having said that, the Netgear WNA 3100 appears to use Broadcom's BMC43231 chip. This is not supported by any linux kernel to my knowledge. People that have gotten this device to work have used NDISwrapper which come with its own challenges and I wouldn't mess with it.

[https://wikidevi.com/wiki/Netgear_WNA3100](https://wikidevi.com/wiki/Netgear_WNA3100)

partial cut/paste:

```
[CENTER] **WI1 chip1:** **Broadcom** BCM43231
[/CENTER]
  **Probable Linux driver**
none, [will not be supported by brcmfmac]("http://www.spinics.net/lists/linux-wireless/msg83255.html")
**[USB ID not yet observed in any mainline kernel / this list]("https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux")**
```

There are WiFi adapters that are plug 'n' play, this is not one.  There are threads that list USB adapters known to work without going to great lengths.  A commonly available on is Netgear's WNA1100, an N150 adapter sold at Staples. I'm partial toward Trendnet TEW-649UB v1.0. It uses a RealTek 8192**SU** chip that is also plug 'n' play. It's faster, 300 down 150 up. I'm sure there are better choices, those are devices I have experience with. A lesson I've learned when shopping for hardware is to do some research about what hardware is well supported by linux and what is not. Buying supported machines & devices makes my life so much simpler. Hang in there, it gets easier.

---

### Post by Bucky Ball on 2015-08-28
As per the other posters. 8.04 is an archaic, end-of-life release we can't help you with, sorry. 14.04 LTS is the current long-term support release. If it is too heavy for your hardware I suggest you try something lighter, like Xubuntu or Ubuntu Mate. Good luck.

Here's some links:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

[http://xubuntu.org/](http://xubuntu.org/)

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by brad-bogar on 2015-08-28
You would probably need to use ndiswrapper to get this to work. That information is in this thread. [http://ubuntuforums.org/showthread.php?t=771894](http://ubuntuforums.org/showthread.php?t=771894)

---

### Post by mörgæs on 2015-08-28
Ndiswrapper is a good guess but please forget the thread mentioned above which is ancient (read last page).

First task: Get Lubuntu 14.04.3 or 15.04 running using wired internet access.

---

### Post by brad-bogar on 2015-08-28
Well fair enough on the thread being too old (perhaps). Dude, you might just try LXLE (a version of Lubuntu) at [http://lxle.net/](http://lxle.net/) if low pc specs are preventing you from trying any regular release of Ubuntu.

---

### Post by QIII on 2015-08-28
Let's adjourn and start a new thread when a supported release is installed so this doesn't become confusing.

---

