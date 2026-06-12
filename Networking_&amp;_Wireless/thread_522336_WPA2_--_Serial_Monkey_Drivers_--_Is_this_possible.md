---
title: "WPA2 -- Serial Monkey Drivers -- Is this possible?"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-10
Anyone with an ra based chipset using the cvs serialmonkey drivers, have you been successful getting your card to work with WPA2 encryption??

I didnt think it was possible until in the serial monkey forum I received a response from the developer who stated:
```
rt2500, rt2570, rt61 and rt73 all support WPA2 as far as I know...
```

He pointed me to look at the iwpriv_usage.txt file to look for the specifics:

> Download the CVS legacy driver you need and look at the file iwpriv_usage.txt in the Module folder.
You should find all the information you need.

Has anyone tried this -- and has it been successful with WPA2?? I looked in the iwpriv_usage.txt file and there wasnt anything specifically addressing WPA2 beyond WPA.

---

### Post by kevdog on 2007-08-10
Hmm, I can see that no one has tried this or gotten this to work.

---

### Post by wieman01 on 2007-08-13
Actually they do support WPA and even WPA2. Some stuff concerning it is posted here:

[http://ubuntuforums.org/showthread.php?t=78250]("http://ubuntuforums.org/showthread.php?t=78250")

If you need help, let us know.

---

### Post by kevdog on 2007-08-13
I read the thread above, and its clear between this thread and various others, the configuration needed in the /etc/network/interfaces file how to use WPA with the rt2500 driver.  These threads however do not specifically address WPA2 in any extent.  

If someone has a working WPA2 /etc/network/interfaces file with any serial monkey driver (rt61,73,2500, etc), could you please post it!  Maybe Im missing something about how these drivers work with wpa.  I dont think they use wpa_supplicant so Im very confused specifically about the configuration for WPA2.

Thanks

---

### Post by wieman01 on 2007-08-13
It does not specifically say WPA2, however, there is mention of AES which is part of the WPA2 suite. TKIP generally refers to WPA.

That said, I would give it a try.

---

### Post by kevdog on 2007-08-13
I guess their in lies the problem.  I personally dont have an ra card to try this one.  But with 3 separate users that I have tried wpa2 with (I have compiled and installed all the drivers), using AES in conjuction with the router being set to wpa2, didnt work.  I tried TKIP also, and this didnt work -- although TKIP did work with WPA1. 

Although I have posted directly on the serial monkey sites and gotten responses that it should work, I havent found anyone to this point that ACTUALLY was successful in getting it to work.  

As far as TKIP=WPA1 and AES=WPA2 as a rule of thumb,  Im not exactly sure where that comes from.  In speaking with the WICD developer, he's finding this not always to be the case, and this assumption oftentimes lieads to problems.

Personally Im using a Linksys WRT54GS router with wpa2 encryption, but my linksys wmp54gs card with ndiswrapper install works only with TKIP  pairwise and group settings -- no success with AES settings.

---

### Post by imdano on 2007-08-13
Yeah, they're at least supposed to.  From the iwpriv_usage.txt file:
> AuthMode                {OPEN,SHARED,WEPAUTO,WPAPSK,WPA2PSK,WPANONE}WPA2 is in there.  Now, does it actually work, who knows.  All I really know for sure is that ralink cards are a nightmare.  Even the enhanced drivers don't all work uniformly.  Trying to get them all to work in wicd has been extremely difficult, especially when having to rely on others to test every little change for me.  It seems like we're getting close, for what its worth.

---

### Post by kevdog on 2007-08-13
Youve given me an idea -- (for the next sucker wanting to try)

From what you just listed, should the following line in the /etc/network/interfaces file read:
```

pre-up iwpriv wlan0 set AuthMode=WPA2PSK
```

rather than
```

pre-up iwpriv wlan0 set AuthMode=WPAPSK
```

Wonder if any one could try this with the following reading either TKIP or AES:
```

pre-up iwpriv wlan0 set EncrypType=<TKIP|AES>
```

Snippet borrowed from this thread:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
```

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra
```

---

