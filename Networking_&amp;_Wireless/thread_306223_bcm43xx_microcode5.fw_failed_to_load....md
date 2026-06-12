---
title: "bcm43xx_microcode5.fw failed to load..."
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by fisherking on 2006-11-24
Hello all,
I have recently bought myself a laptop (hp6185) with a Broadcom Wireless device (I think it is a bcm4311). 

the last days I have browsed the forum after a solution for my problem: I can't get the wireless connection to work. I have tried every single solution I have found (which is not a good thing...) but no luck!

For now I can see the network interface (eth1) but I can't do anything with it. When trying to connect to the interface I get the following message with dmesg:
```

[17179600.708000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```


[edit]
Maybe I should add that the wireless interface does show up in every possible network manager there is... including the cli commands, e.g. "dhclient" or "iwconfig"
[/edit]

---

### Post by fisherking on 2006-11-25
hups, this was an easy one... The firmware was missing... Fixed that... Now my wireless connection is working but incredible slow! Browsing the forums for a solution on that...

---

### Post by cro-marmot on 2007-11-23
Hi !!
I have the same error message as you did when trynig to install wubi.
But i don't understand what you did to correct it.
What was the problem? What did you do exactlty ? 
Thank you in advance

---

### Post by zophiel on 2007-11-24
Have you tried this solution?

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by Flare183 on 2007-11-24
Follow this [how to. ]("http://ubuntuforums.org/showthread.php?t=197102")
If that doesn't work then try installing both or one of these files below.

[Bcm Fireware]("http://www.mediafire.com/?4nvn2j9i4ym")

[BCM FwCutter]("http://www.mediafire.com/?dwwjnmo2w2t")

---

