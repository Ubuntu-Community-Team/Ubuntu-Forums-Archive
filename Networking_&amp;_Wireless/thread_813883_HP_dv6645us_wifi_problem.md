---
title: "HP dv6645us wifi problem"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by edwin.e.johnson on 2008-05-31
first i got a new computer dv6645us has a broadcom4311 wifi card in it just like my old computer "which i set up with ubuntu aswell".
well as shitty as it is i could not get 7.10 to boot on new computer because of video card issues but 8.04 worked.
as it turned out my wifi never showed up in restricted driver manager. 
so i figured ndiswrapper and bcmwl5    no luck at all. light on wifi has been blue since first install i blacklisted bcm43xx and all that stuff. still no go

it shows up in LSPCI
"03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)"

but iwconfig only shows L0 and eth0 but says no wifi.
i even changed to the bcmwl6 driver that came with my computer still nothing. 

any help would be great thanks.

---

### Post by paulphillips on 2008-05-31
I take it this hasn't helped?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by edwin.e.johnson on 2008-05-31
no.

---

### Post by Ayuthia on 2008-05-31
The bcmwl6 driver (Vista) does not work with NDISwrapper yet.  You need to try an XP driver (bcmwl5).  You might try this [link]("http://ubuntuforums.org/showthread.php?t=766560").

---

### Post by edwin.e.johnson on 2008-05-31
that is the first one i tried still same problem.

hate to say it but it works fine with mandriva

---

### Post by marx1984 on 2008-07-01
I got this laptop working with Gentoo, but stick with ubuntu until you get more in touch with the Gnu/Linux System. First things first -- Install the latest or next to latest version of ndiswrapper. So make sure you have Kernel headers, gcc, glibc are all installed as mentioned here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

Please read the above. It will show you how to install and configure NDISwrapper.

The NDISwrapper Website's "list" Shows us that device ID 14e4:4311 is supported by a Win32 driver located at [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en)

I tried it. It works,although, when under heavy network load it will fail but it  works about 95% of the time.

Follow the instructions located at the first link provided in this post. It will not fail you. I created a script to initiate my wireless connection at boot. It's poorly written so I won't post it here unless someone wants me to do so :-D 

Let me know how I may further help you. If you're having trouble don't hesitate to ask me in this thread.


--Cheers

---

