---
title: "wireless USB Ralink not working....."
date: 2011-04-06
forum: New to Ubuntu
---

### Post by braddavis on 2011-04-06
:)Hey everyone; I'm a 57 year old former parts salesman(shut down our stores-nationwide), helping my brother at his car-lot.
Since I had no idea when I'd go back to work; I figured I'd need a trade to learn , so I went into comp. repair and sales.
:confused:Boy; this is hard! But after being self-taught(reading everything I could, and buying junk to take apart and repair). I can take them apart and put them together again like an old carb; that was until I met Ubuntu 10.4..I love it!
But I don't write program, and MOS-DOS is an old CIA term for burying someone!
So I hope you can help me with this. Straight in ethernet cable, downloads, and all that is as simple as Windows 95,98,2000,XP, and Vista&7.
But the Ralink USB adapter(which has drivers for Linux) has me bum-fuzzled. I go to open it, and all these boxes, and extract program, and I'm not authorized has me about ready to only use it in towers from now on.
What in Hades am I doing wrong?
This is about more than this old partsman can handle...help a newbie;please?
Be kind; I bruise easily......

---

### Post by Joe of loath on 2011-04-06
First off, what happens when you just plug it in? Does Ubuntu detect it?

---

### Post by TBABill on 2011-04-06
Can you let us know what type of device it is? Open a terminal and paste back here the output of ```
lsusb
``` so we can be sure of what you are working with.

---

### Post by Javelin Dan on 2011-04-06
&#65279;braddavis - I feel  your pain! I too bought a Ralink wireless usb adapter a couple of months ago because I first read the reviews on Amazon and several people reported that it worked with linux (specifically Ubuntu) - it didn't. I scoured the internet searching forums, wikis,  tutorials, and asking for help. I  got many suggestions of things to try...some I understood, some I didn't...I was absolutely determined to crack this nut. I spent considerable time on a link from “Linux Forums” on how to configure a wireless card. But after almost 2 months of giving up all available evenings and weekends, I still could not make it work. I finally broke down and researched which dongle was reported to have worked with the exact distro I was fooling around with at the time (Antix 8.5) which turned out to be an *SMC* model #  SMCWUSB-C (about $15 U.S.  at Amazon.com). It was completely plug and play and works great! So the lesson is, get something you *_know  works_*. Now I have been told here that devices are not distro specific but rather kernel specific. To me, it's a distinction without a difference. Either a device works with a certain version of a certain distro or it doesn't. And some things definitely do not!  From my experience and others, this can be true of wireless cards, dial-up  modems, printers, and virtually any other piece of peripheral hardware. The only other thing I can add is beware of trying only one  wireless configuration manager. In Antix, they provide you with about 4 different ones that are all supposed to do the same thing. I can't remember which one I was first trying as I've since deleted it, but it never would see my wireless net while all the others would. The one I liked best was "Ceni" Not sure what all is available in Ubuntu's synaptic manager, but it might be worth checking out. Good luck!

---

