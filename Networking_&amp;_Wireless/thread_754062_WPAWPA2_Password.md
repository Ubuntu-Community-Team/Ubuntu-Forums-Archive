---
title: "WPA/WPA2 Password"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by Rmg12 on 2008-04-13
I am getting quite annoyed at the network managing system in ubuntu (hardy Heron). Every Time I turn on my laptop I have to go into the settings and apply set my password. My router is set to WPA2 and WPA encryption. There is no option in the network settings so I try WPA2. It doesn't work. I try WPA with my password and it works :confused: .
The password for my router in the network settings keeps automatically changing to alot of unknown letters/digits, (see attache pictures. One is before and one is just after I save the setting then close, then re open properties. I have to completely reboot my computer to be able to access the internet for awhile. I am completely new to Ubuntu (Iv'e used it once before in a virtual PC) and now I have used Wubi to install Ubuntu onto a virtual disc. I am very surprised and happy to find that ubuntu automatically recognizes all of my hardware including my Chicony toshiba webcam :D It's just this internet problem that is annoying me. 
I have posted this to the hardy development thread too.

---

### Post by Red-Shield on 2008-04-13
turn off the encryption and turn of macfiltering i know that is not the answer just a suggestion

---

### Post by Red-Shield on 2008-04-13
/etc/network and then nano interfaces and edit that file to your needs that will help i think then it will just be on the net when it is on unless otherwise told

---

### Post by tact on 2008-04-13
> **Rmg12 said:**
> I am getting quite annoyed at the network managing system in ubuntu (hardy Heron). Every Time I turn on my laptop I have to go into the settings and apply set my password. My router is set to WPA2 and WPA encryption. There is no option in the network settings so I try WPA2. It doesn't work. I try WPA with my password and it works :confused: .
The password for my router in the network settings keeps automatically changing to alot of unknown letters/digits, (see attache pictures. One is before and one is just after I save the setting then close, then re open properties. I have to completely reboot my computer to be able to access the internet for awhile. I am completely new to Ubuntu (Iv'e used it once before in a virtual PC) and now I have used Wubi to install Ubuntu onto a virtual disc. I am very surprised and happy to find that ubuntu automatically recognizes all of my hardware including my Chicony toshiba webcam :D It's just this internet problem that is annoying me. 
I have posted this to the hardy development thread too.

Hi there, being newb is good.  Fresh insights.  :)

Ok first thing I note from the screenshots you provided is that "roaming mode" is not enabled.  What that means is that networkmanager is NOT controlling your network connections at all. 

Network manager can only control connections for network adapters that have "roaming mode" enabled.

So if you want to give networkmanager a chance to make you very happy - let it control your interfaces.  Set all of them to "roaming mode" for a start.   Then sit back and watch it work its magic.

Cheers.

---

### Post by Rmg12 on 2008-04-15
I installed WICD and it works perfectly! thanks for your advice anyway but I recommend Wicd :D

---

### Post by tact on 2008-04-16
> **Rmg12 said:**
> I installed WICD and it works perfectly! thanks for your advice anyway but I recommend Wicd :D

Networkmanager also works great.  As noted above you were not using it when you were having problems.  NM is disabled when you do not have roaming mode enabled.  :)

Perhaps you can only truly recommend an alternative like wicd when you have properly tried both. 

I have used both wicd and NM and definitely prefer NM.  

Cheers.

---

### Post by Rmg12 on 2008-04-16
> **tact said:**
> Networkmanager also works great.  As noted above you were not using it when you were having problems.  NM is disabled when you do not have roaming mode enabled.  :)

Perhaps you can only truly recommend an alternative like wicd when you have properly tried both. 

I have used both wicd and NM and definitely prefer NM.  

Cheers.

Well I enabled roaming mode and it didn't connect at all

---

