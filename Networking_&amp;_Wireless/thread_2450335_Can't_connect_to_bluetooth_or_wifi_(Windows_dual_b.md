---
title: "Can't connect to bluetooth or wifi (Windows dual boot neither)"
date: 2020-09-11
forum: Networking &amp; Wireless
---

### Post by lucas.detre1 on 2020-09-11
Hello everyone,
I woke up someday to my wifi and bluetooth not working both on ubuntu and windows dual boot... Cable connections are good but wireless seems to be deactivated or badly configured / missing drivers I don't really know at that point. I'm pretty sure that my laptop has no hard lock/unlock button to switch off wireless connections for I have checked it for a while. I upgraded from 18.04 to 20.04 without seeing any change and I'm now feeling as I can't do it on my own or just on checking forums other threads.


My laptop is rather new (like 6 month old) and it worked fine until one day I just disconnected it from its RJ45 and saw that the wifi/bluetooth was not working anymore


I suspected that the problem could be on BIOS level but I can't access the good old legacy blue BIOS because when I bought this laptop there already was an UEFI overlay (InsydeH20) which doesn't allow me to change...

Anyway thanks in advance for your help and your time ! :) 


I'm not so sure on how to post my wificheck log so I'll just put it in as an attachment


[ATTACH]286936[/ATTACH]

---

### Post by CelticWarrior on 2020-09-11
Welcome.

BIOS was replaced by UEFI (which isn't an "overlay", it's the actual motherboard's firmware that replaced the 1981 BIOS) about a decade ago.

So, yes, the problem you're reporting could be related to the device being disable in UEFI. Please check that first because if not that then the hardware itself it's faulty (including but not limited to loose connections). It's really that simple. Because it happened in both OSes at the same time we know it has nothing to do with either or drivers.

---

### Post by lucas.detre1 on 2020-09-11
Hello ! Thanks for your help so far ! What I actually meant by overlay was that there is an interface which I think is called Insydeh20 which prevent me from accessing to parameters such as enabling/disabling wireless connections

This interface simply doesn't permit me to access to old bios settings and if wireless connections are disabled on this level then what am I supposed to do ?

If the hardware is faulty as you suggest it might then why did would it just "broke" all of a sudden ?

I'm just trying to understand there...

Thanks again sir

---

### Post by CelticWarrior on 2020-09-11
Starting from the last question, "[COLOR=#000000]why did would it just "broke" all of a sudden", that's what pretty much all hardware does when it breaks. Exceptions are the old mechanical HDDs that can present symptoms suggesting a failure before they actually fail. Everything else tends to fail suddenly.

Regarding the other part about accessing the firmware (UEFI) settings, [InsydeH2O]("https://www.insyde.com/products") is just one of the many firmware vendors. It IS your UEFI, not an overlay, and all the features you expect from the old BIOS and much more are there as well. **Please post the brand/model of your laptop so we can check**. Knowing the firmware is provided by Insyde is not that relevant because manufacturers then implement their own sets of features additionally, instead of, or even removing features present in the original generica firmware implementation. Yours may or may not have WiFi/BT enable/disable settings. Many don't but unlike what you think - "[/COLOR][COLOR=#000000]I'm pretty sure that my laptop has no hard lock/unlock button to switch off wireless connections" [/COLOR][COLOR=#000000]- ALL have some key or key combo, typically with the function keys to toggle "airplane mode". This is also a possibility in your case.[/COLOR]

---

### Post by lucas.detre1 on 2020-09-11
Ok alright I see your point there !

My laptop is that one from LDLC : [https://www.ldlc.com/fiche/PB00323818.html?offerId=AR202003090027](https://www.ldlc.com/fiche/PB00323818.html?offerId=AR202003090027)

The "airplane mode" function keys do nothing on both OSes though

---

### Post by CelticWarrior on 2020-09-11
So, it's built upon a CLEVO barebone, they're usually good and reliable, but any part can fail anytime.
So, if you have no options for enabling/disabling WiFi in UEFI ("BIOS") and the key combo does nothing, I would start by re-sitting the WiFi/BT card if it's user accessible. Sometimes just removing and re-inserting it does wonders. Failing that please contact your tech support because the computer is still under warranty.

---

### Post by lucas.detre1 on 2020-09-11
Are you confident that it's not software/firmware related ?

I've already explored all the options offered in UEFI

I think I won't open it because I don't want to break the warranty, I'll just try to get in touch with post-sale customer service

Anyway thanks for sharing your knowledge on UEFI/BIOS matter with me !

---

