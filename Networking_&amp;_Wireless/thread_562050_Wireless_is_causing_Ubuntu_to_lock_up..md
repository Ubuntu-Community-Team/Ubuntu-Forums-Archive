---
title: "Wireless is causing Ubuntu to lock up."
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by Vadi on 2007-09-28
I bought a F5D7010 wireless card, version 7, or 7000 (same thing), which uses the Realtek 8185 chipset. Looking at the fsf's website, that version number was close, as was the old version of the card listed. So I thought I'd be all good.

Now, eh, when I got the card, it turns out that it's not recognized at all. As in, iwconfig doesn't even list it. Following the instructions on the ubuntu wiki, I got the windows driver for realtek, installed it via ndiswrapper, hooked up the device ID to the driver, and it worked. yay. almost.

For whatever reason, wireless is causing my ubuntu to -completely- (my keyboard input doesn't work, mouse neither, and my little clock screenlet freezes, so pretty much everything is paused) for about 5 mins, every few minutes. This is extremely annoying. I looked at the system log, and it records that wlan0, my wireless, is being reset. Each reset causes the complete lockup. Why does it reset, I have no idea why.

If anyone can help me diagnose this, that'd be great. I'm really pissed off at the moment at wireless :(.

Here are some symptoms I gathered. After each reset, wicd says that I'm connected to "None", but the signal and IP is fine. 

ndiswrapper -l tells me:

net8185 : driver installed
        device (1799:701F) present

And I'll post the whole system log, since I don't know which parts are necessary and I shouldn't cut out, but the important lines are where it says wlan0 is being reset. That causes the complete lockup ([click]("http://pastebin.com/m36a7d45a")).

Oh and I know you can compile realtek drivers from source, I tried, but the instructions were unclear/wrong, because it didn't work. I just want my wireless to work, I don't want to know *how* does it work :(

---

### Post by philtbelfast on 2007-10-07
I have a feeling im experiencing the same problem, my computer completely freezes whenever theres network traffic, sometime it only takes a second of activity sometimes nearly a minute.

How did you get access to the log file saying that your wireless was being reset and ill look and check if thats whats happening to me as well.

Im quite new to linux so please make any instructions completely idiot proof!

---

### Post by Vadi on 2007-10-07
I'm no expert either. This problem only seems to occur randomly when I'm on a wireless connection.

To see the log file, you can go to System - Administration - System Log. On your left you'll see a bunch of logs, I think you want the 'user.log'.

---

