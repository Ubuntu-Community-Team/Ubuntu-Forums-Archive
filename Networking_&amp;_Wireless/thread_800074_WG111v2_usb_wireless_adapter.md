---
title: "WG111v2 usb wireless adapter"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Itoao on 2008-05-19
Hi, I am new here and like many other posters I see I am new to Linux. I decided to put Ubuntu (Feisty) on an old machine to mess around with and see if I can understand all this. I have been poking around the forums and I have the netgear WG111 v2 USB adapter.
I checked and when doing a lusb I get
Bus002 :ID 0846:4240 Netgear, Inc. WG111 Wifi (v2)
So apparently I have the 0846:4240 chipset.
I downloaded the driver from netgear after reading this tutorial.
I read another tutorial ([https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)) but I am not sure if I added the ndiswrapper packages to the machine. The links to the packages are timing out on this machine.
Can anyone help.
Thanks

I posted this in the beginner forum but since its about networking so it is probably better to post it here. 
I have done the step 3.4.2 but when I move on to check by doing a
ndsiwrapper -l 
I get /etc/ndiswrapper/net111v2.inf
:invalid driver

Not too sure what I am doing wrong at this point. I have tried using all the different drivers from netgear website. No luck.

---

### Post by Itoao on 2008-05-20
I am at a standstill. Is there anyone that can give me a bit of guidance?
Thanks

---

### Post by ciamele on 2008-05-20
I have the same adapter, but have yet to get mine to work. Still, I may have a possible solution for you:

Ubuntu says you have version 2 of the adapter. It says the same for me. But when I go to Netgear's website and check the serial number, they say I have version 1 of the adapter. I suggest checking Netgear's site to determine which adapter version they say you have. Then try using that driver. Heck, maybe try all of the drivers.

---

### Post by ciamele on 2008-05-20
My apologies, you already said you've tried all the drivers.

I still suggest looking to see which version Netgear says you're using. While I'm not too familiar with Ubuntu, your solution could be in getting Ubuntu to recognize the actual hardware version IF you're in the same boat I'm in. But I really don't know.

One clarification: When I say I haven't been able to get my WG111 to work, I did get it to work once, for about a minute. IMO, that doesn't qualify as "working." I just plugged it in and everything seemed great until I started browsing the net. Secondly, I haven't spent much time trying to figure it out yet.

---

### Post by Itoao on 2008-05-21
Thank you for the reply. I am still so new at using Ubuntu that I am not sure what I am doing right and what I am doing wrong. I will take your advice though. Thanks

---

### Post by DRoyLenz on 2008-05-30
> **ciamele said:**
> My apologies, you already said you've tried all the drivers.

I still suggest looking to see which version Netgear says you're using. While I'm not too familiar with Ubuntu, your solution could be in getting Ubuntu to recognize the actual hardware version IF you're in the same boat I'm in. But I really don't know.

One clarification: When I say I haven't been able to get my WG111 to work,** I did get it to work once, for about a minute**. IMO, that doesn't qualify as "working." I just plugged it in and everything seemed great until I started browsing the net. Secondly, I haven't spent much time trying to figure it out yet.

Ciamele - did you ever figure out why it would only connect for a minute or so?  I'm having the same issue.  If I restart, unplug and replug in my adapter, go in to Network Settings and set everything up again, I get about 30 seconds of internet.  Let me know if you figured something out.

Thanks!

---

### Post by chili555 on 2008-05-30
If you are sure, by examining the serial number, that you actually have a v2, please see post#60 here: [http://ubuntuforums.org/showthread.php?t=799857&page=6](http://ubuntuforums.org/showthread.php?t=799857&page=6)

---

### Post by DRoyLenz on 2008-05-30
Thanks chili, but I was only able to gain one thing out of that thread, and that is that he succeeded using the Win98 driver.  I was told on everything I've looked at to use the XP driver.  I will give that a shot, and make sure to let you and all of the searchers the results.

If anybody else has anything to add, please don't hesitate to suggest something to me, for my sake, or for somebody elses.

---

### Post by Unix_Slayer on 2008-05-30
Install NDIS Wrapper. Add your .inf device driver from the Windows XP driver set. My Linksys adapter installed with the XP driver. I tried the Vista driver, but it would not work. I am using my USB adapter now. It's working fine, and getting excellent signal and speed. In Adept installer type "ndis". You'll see Windows wireless drivers. Install it. Then run it, and install your Windows XP .inf from the cd. Wella.

---

### Post by chili555 on 2008-05-30
> **Unix_Slayer said:**
> Install NDIS Wrapper. Add your .inf device driver from the Windows XP driver set. My Linksys adapter installed with the XP driver. I tried the Vista driver, but it would not work. I am using my USB adapter now. It's working fine, and getting excellent signal and speed. In Adept installer type "ndis". You'll see Windows wireless drivers. Install it. Then run it, and install your Windows XP .inf from the cd. Wella.Sir-
These guys don't have Linksys adapters and have generally tried unsuccessfully to use ndiswrapper and the XP driver.

---

### Post by Unix_Slayer on 2008-05-30
> **chili555 said:**
> Sir-
These guys don't have Linksys adapters and have generally tried unsuccessfully to use ndiswrapper and the XP driver.

It won't hurt to try. The chips in Linksys adapters are common chips, I agree. It might work, might not. But we won't know until we try it.

---

### Post by Unix_Slayer on 2008-05-30
Netgear adapters are common as well. Try the WinXP .inf. If it doesn't work, try the Windows 2000 .inf. One of them should work.


```
lsusb
```

---

### Post by ciamele on 2008-05-30
> **DRoyLenz said:**
> Ciamele - did you ever figure out why it would only connect for a minute or so?  I'm having the same issue.  If I restart, unplug and replug in my adapter, go in to Network Settings and set everything up again, I get about 30 seconds of internet.  Let me know if you figured something out.

Thanks!

I'm afraid I still haven't played with it. I had hoped to last weekend, but I'm having worse problems with my laptop. I'm not sure when I'll get around to playing with it, but it may not be in the near future. If and when I start working on it, I'll post all the details. Good luck!

---

### Post by DRoyLenz on 2008-05-30
Chili speaks the truth.

I've tried unsuccessfully multiple times with ndiswrapper.  I've installed it multiple times, with varying results, unfortunately, none of the results being success.

To clarify, it is a Netgear WG111 V2.  The label on the dongle confirms that it is indeed a V2, which from my research, leads me to believe that is one of the primary issues people have.

I have yet to try the Win98 driver, but again, I will make sure to let everyone know of my results when I do.

---

### Post by Unix_Slayer on 2008-05-31
> **DRoyLenz said:**
> Chili speaks the truth.

I've tried unsuccessfully multiple times with ndiswrapper.  I've installed it multiple times, with varying results, unfortunately, none of the results being success.

To clarify, it is a Netgear WG111 V2.  The label on the dongle confirms that it is indeed a V2, which from my research, leads me to believe that is one of the primary issues people have.

I have yet to try the Win98 driver, but again, I will make sure to let everyone know of my results when I do.

Try this link ==>[http://linuxwireless.org/]("http://linuxwireless.org/")
Preferably this link ==>[http://linuxwireless.org/en/developers/Documentation/mac80211]("http://linuxwireless.org/en/developers/Documentation/mac80211")

---

### Post by robjbrooker on 2008-06-08
Not to contribute much, but I have the same circumstances as DRoyLenz. The connection can be fixed, but only temporarily.

---

