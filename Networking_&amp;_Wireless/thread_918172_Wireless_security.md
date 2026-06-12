---
title: "Wireless security"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by GeordieJedi on 2008-09-12
Hi all. I have a couple of quick questions that I thought someone might be able to help with.

Ok, firstly I dual boot with XP (Sorry) & I originally set up my wireless router and internet via XP.

I can surf the web fine (thats not my issue).

When I use Ubuntu to get online,

I select "network manager"? choose my wi-fi network.
I'm then presented with a dialogue box called
"Wireless network key req"

The 1st option box = Wireless security
which is currently set up as WEP 128bit.

The 2nd box = Passphrase
Which I pop in my passphrase/key

The 3rd box = Authentication
Wich I normally have as "open system" (but I managed to get the "shared key" to work for the
1st time tonight...woohoo!

So my main question is =  Am I actually using an encrypted signal whilst I'm surfing online.
If so, is there any chance I can get something a little bit more robust eg: WPA 1 or 2?

Thanks in advance for any help.

Take it easy.

---

### Post by stone@bruti on 2008-09-12
> **GeordieJedi said:**
> Hi all. I have a couple of quick questions that I thought someone might be able to help with.

Ok, firstly I dual boot with XP (Sorry) & I originally set up my wireless router and internet via XP.

I can surf the web fine (thats not my issue).

When I use Ubuntu to get online,

I select "network manager"? choose my wi-fi network.
I'm then presented with a dialogue box called
"Wireless network key req"

The 1st option box = Wireless security
which is currently set up as WEP 128bit.

The 2nd box = Passphrase
Which I pop in my passphrase/key

The 3rd box = Authentication
Wich I normally have as "open system" (but I managed to get the "shared key" to work for the
1st time tonight...woohoo!

So my main question is =  Am I actually using an encrypted signal whilst I'm surfing online.
If so, is there any chance I can get something a little bit more robust eg: WPA 1 or 2?

Thanks in advance for any help.

Take it easy.


Hi,
take a look at the first few posts of this forum

[http://www.wifi-forum.com/wf/showthread.php?t=3187]("http://www.wifi-forum.com/wf/showthread.php?t=3187")

the difference between an open auth and a shared key is the way you connect to your wireless router, WEP is not a secure connection no matter what auth you use.

just because you use a shared key doesn't meen your communication is encripted (Not 100% sure, only 90%, please correct me if i'm wrong !! :s  )

once a hacker has gotten in to your wifi, nothing will stop him doing a man in the middle attack and sniff all of your data. the only way your data is encrypted on the internet is if you visit https sites.

to get wpa working you will need wpasupplicant (sudo apt-get install wpasupplicant) but you could have a few problems depending on the driver / wifi chipset you are using. the best way to find out is to try now that you know that wep works fine.

hope that helps

good luck

Stone

---

### Post by GeordieJedi on 2008-09-13
Cheers, stone@bruti. I appreciate the help.

---

