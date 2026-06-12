---
title: "wireless dongle issue please help"
date: 2015-07-12
forum: Networking &amp; Wireless
---

### Post by Will_Broccolo on 2015-07-12
I have elementary os and having issues having it detect my wireless adapter. I've tried to follow the instructions here [http://ubuntuforums.org/showthread.php?t=2223902](http://ubuntuforums.org/showthread.php?t=2223902) but this is for an older version and none of the commands help. Can anyone PLEASE PLEASE help? please I need to find an answer so we can convert a ton of pcs at work TOMORROW.

info:
elementary os freya 
linksys wireless n300 ae1200

---

### Post by kurt18947 on 2015-07-12
Nothing like waiting 'til the last minute:lolflag:  Sounds like me! :redface: If you could post the results of this bash script with code tags that'd be a good start. Here are directions:  [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)[URL="http://ubuntuforums.org/showthread.php?p=12350385#post12350385"]

[/URL]
Edit:  Actually it doesn't look real promising.  According to wikidevi.com, the linksys AE1200 is not supported. 

[https://wikidevi.com/wiki/Linksys_AE1200](https://wikidevi.com/wiki/Linksys_AE1200)[URL="https://wikidevi.com/wiki/Linksys_AE1200"]
[/URL]
The post you linked previously talks about NDISwrapper. NDISwrapper has a ............ spotty..... record of success. In other words, I wouldn't count on that.  If you have time tomorrow, can you get to an office supply or electronics store? If you buy the right WiFi adapter you could plug it in and be up & running in a couple minutes. An adapter stocked by many Staples is Netgear WNA1100. Plug it in & it works at least in my experience. Other good choices are TrendNet TEW-649UB and Tenda W311Mi though the Tenda has fairly weak reception IME. The Trendnet will likely be the fastest if you can find it. Good luck.
[URL="https://wikidevi.com/wiki/Linksys_AE1200"]


[/URL]
[URL="http://ubuntuforums.org/showthread.php?p=12350385#post12350385"]


 


[/URL]

---

### Post by Vladlenin5000 on 2015-07-12
Post #2
+1

But... I would procure a different, supported and newer, WiFi device ASAP.
Those which depend on (old) Windows (XP) drivers via a cumbersome compatibility layer are doomed to fail, sooner than later. Chances are - really high - you already have in place what used to work for your dongle but it no longer works.
You've been warned!

---

### Post by Will_Broccolo on 2015-07-12
thanks guys for the advice. I should of researched before I got these I'll try to look for the others.

---

### Post by Will_Broccolo on 2015-07-12
is there a full list of compatible ones?

---

### Post by Geoffrey_Arndt on 2015-07-13
Available on Amazon or similar sites - about $20 usd - - or can get Panda 150 Ultra Wireless adapter (dongle) for 1/2 the price.

Panda  300Mbps Wireless-N USB Adapter w/ WPS button - 802.11 n, 2.4GHz - w/  High Gain Antenna -Compatible with Windows  XP/Vista/7/8/8.1/10/2008r2/2012r2, Mint 14/15/16/17/17.1, Ubuntu  12.10/13.04/13.10/14.04/14.10, Fedora 18/19/20/21, openSUSE  12.2/12.3/13.1,CentOS 6.4/6.5/7, Lubuntu 12.10/13.04/13.10/14.04/14.10,  Zorin 8.1/9.1, Kali Linux and Raspbian Wheezy

---

### Post by kurt18947 on 2015-07-15
> **Will_Broccolo said:**
> is there a full list of compatible ones?

Check in the networking & wireless section here.  Be careful of those that claim linux compatibility - they may require compiling your own driver which is not a big deal if the source is clean, sometimes it's not or what's supplied is outdated. It requires some detective work but if you buy a **chipset **that works out of the box, life is simpler. Linux doesn't care about manufacturers, it cares about chipsets. The trick is to determine which chipset a given device uses. To further complicate things, different versions of a model may use different chipsets and there may be no simple way to determine the version without opening the package.

---

### Post by slickymaster on 2015-07-15
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Lloydb39 on 2015-07-15
I bought a Belkin. Plugged it into USB. Wham! Instant wireless connection on an old Dell with an earlier version of Ubuntu/Windows XP.

---

### Post by wildmanne39 on 2015-07-15
Please use normal fonts.> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.
[http://ubuntuforums.org/showthread.php?t=2158945](http://ubuntuforums.org/showthread.php?t=2158945)
Thanks

---

### Post by kurt18947 on 2015-07-15
> **Lloydb39 said:**
> I bought a Belkin. Plugged it into USB. Wham! Instant wireless connection on an old Dell with an earlier version of Ubuntu/Windows XP.

What model Belkin?  Some work, some don't.

---

