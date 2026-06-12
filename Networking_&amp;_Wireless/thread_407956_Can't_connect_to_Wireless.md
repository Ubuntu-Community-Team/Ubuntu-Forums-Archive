---
title: "Can't connect to Wireless"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by T1m0thy on 2007-04-12
I'v just installed ubuntu on my laptop and it is the first time i have ever used anything apart from windows. Everything has gone alright (it think), though i'm finding it quite difficult to get used to.

My first problem was which unbuntu to download, i tried the one for "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)" but that didn't work at all, it just froze when i choose install. So i tired the one for "64bit AMD and Intel computers" and it worked so i stuck with that. I'm not sure if it was the right one or not?

I wanted to connect to my wireless so i went to the networking page and added the details of my wireless but it hasn't connect or anything. Also is there a way of searching for wireless networks like windows? I did hear about ndiswrapper but i couldn't get it to install.

The wireless my laptop has is "Intel Pro/Wireless 3945ABG network" if that helps?

Another thing while i'm asking for help is i can't change the screen resolution, when i click the drop down bit in screen resolution preferences there are no other options apart from 1024x768. And i can't get the screensaver to work, instead of coming up with the screensaver i select i get a blank black screen instead, the preview works fine on the screensaver page.

Thanks in advance,
Tim

---

### Post by WNxCryptic on 2007-04-13
I'm just getting back into the swing of linux myself, so I won't be able to help you on all your issues.

Your screen resolution is locked and your having troubles with the screensaver probably because your lacking the correct driver for your video card.

What version of Ubuntu have you installed?

Open the terminal (Applications-> Accessories) and type in "iwconfig" and paste what you see.

---

### Post by SomethingUniqueHere on 2007-04-13
I just did a google search for yah, take a look at this website [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) and hopefully that helps you get the wifi working.

---

### Post by T1m0thy on 2007-04-13
> Open the terminal (Applications-> Accessories) and type in "iwconfig" and paste what you see.

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"wow"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:18:4D:53:E3:6A   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=-29 dBm  Noise level=-30 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

sit0      no wireless extensions.

> I just did a google search for yah, take a look at this website [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) and hopefully that helps you get the wifi working.

Thanks, i have already downloaded that but i don't really know how to install it. It talks about all these other things i need to have to use it too.

---

