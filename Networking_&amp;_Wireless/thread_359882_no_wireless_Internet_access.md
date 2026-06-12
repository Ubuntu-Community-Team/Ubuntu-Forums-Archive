---
title: "no wireless Internet access"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Resistance on 2007-02-12
Hello, 

I am a very recent Ubuntu acquisition: I installed it ("it" being Edgy) on my laptop yesterday, with the help of a friend "in the know". I used the LiveCd for installation. We included EasyUbuntu for extra features. 

As long as we used an Internet connection with a network cable (ADSL in Belgium, Europe) everything was fine, but when I returned home and wanted to connect to the Internet on my wireless connection, it did not work...(remember I'm a novice)

I use a Netopia wireless router and a Belkin F506020 PCMCIA card in the notebook. 

Could someone please tell me what programs/drivers/settings I should instal/activate (and where) to obtain Internet wireless access.

Thanks a bunch!
Rez.

---

### Post by sumgi on 2007-02-12
Hey there, I too am a buntu noob. I installed a dual boot on my laptop yesterday. Same deal wireless does not work. I have a littlebit of a head start on you so here is some info.

First check that your card is installed. 

Here is a thorough [guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").

also watch the system logs

tail -f /var/log/messages

If the correct driver is not installed then [here]("https://help.ubuntu.com/community/WifiDocs") is a resource though I don't see any info on your model.

Let us know how that works out.

-Ryan

---

