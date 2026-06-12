---
title: "Testing wireless with WPA using Live CD"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by cbourner on 2007-01-03
Before I commit to killing Windows XP and installing Edgy on my Dell Latitude D520 (with Intel 3945 wireless), I was trying to get wireless working with WPA.

I have followed instructions related to setting up WPA supplicant, but I am unsure whether I need to obtain a different 3945 driver.

I also suspect I will need to reboot at come point, which given I'm using the live CD isn't going to get me anywhere.

Am I wasting my time?  Or is there a way to check that I can get this working using the Live CD?

Any advice (including suggestions that I am paranoid and that of course I will get it working, just do it) is sought.

Thanks!

---

### Post by SugarDaddy on 2007-01-03
Hi cbourner, welcome to the wonderful world of open source OS and Ubuntu! In order to connect to WPA encrypted routers you need wpasupplicant installed. However, I don't think wpasupplicant is included on the LiveCD but must be downloaded following installation. If anyone knows that I am wrong, please feel free to correct me.

---

### Post by cbourner on 2007-01-03
Yep, installed that using apt-get.  I was able to run the wpa_supplicant command, which attempted to connect to the AP, but this was not successful.

I read somewhere the 3945 driver in Ubuntu wasn't up to the task and that I needed to download a different one from sourceforge.  I think this is where a reboot was needed, so I stopped.

---

### Post by SugarDaddy on 2007-01-03
You might want to try looking at the sticky HowTo thread at the top of the forum on how to configure wpasupplicant.

---

### Post by wieman01 on 2007-01-04
Try WPA(1) first of all. The wpa-driver is 'wext' as far as I know. Try the sticky first, then we can help. If the native driver for "Intel 3945" is a problem, then I would give "ndiswrapper" a go.

---

### Post by cbourner on 2007-01-05
My solution was to hold my breath and jump in.   I installed Ubuntu, and I got WPA working with the 3945 using advice I found elsewhere in the Ubuntu forums.

So I'm happy.  Thanks to everyone who chipped in with advice.

There are a few things like wireless not recovering after a resume from suspend-to-RAM, but I'll create a new thread for this.

---

