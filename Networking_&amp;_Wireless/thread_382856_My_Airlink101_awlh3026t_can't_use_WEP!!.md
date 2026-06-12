---
title: "My Airlink101 awlh3026t can't use WEP!!"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by avihappy on 2007-03-12
Hi, I am using the card listed here ( [http://www.airlink101.com/products/awlh3026t.htm](http://www.airlink101.com/products/awlh3026t.htm) ) on Ubuntu Feisty. The card is working (I can use my neighbor's unprotected network), but it won't connect to my WEP protected network (geeksquad). My router is a D-Link 624+. The key is a 10 digit number. Ubuntu asks for the key, so I give it, but it never connects. Help? :(

---

### Post by nagato on 2007-03-13
I have the same problem with my iwp2200 on Dapper. :(  If you get any ideas, please let me know, and I'll do the same.

---

### Post by tgalati4 on 2007-03-13
I have used the Airlink 101 for several weeks on an old Dell Inspiron 7500.  I had to use the ndiswrapper/windows driver and blacklist the Marvel/Libertas driver that the hardware detection seems to prefer.  This is on a Dapper 6.06.1 LTS.

There have been some wireless architecture changes between Edgy and Feisty that could trip you up.

The Airlink card works well with a standard Netgear G wireless router.  I am using WEP.  I get great signal and range in my house and backyard using a windsurfer coffee can antenna.

The card also sleeps and resumes properly, without resorting to wakeup scripts.

Good luck.

---

### Post by avihappy on 2007-03-20
This card stopped working in edgy+. It worked PERFECTLY in Dapper.

---

### Post by charles nicholls on 2007-03-20
I have just had the same prob although on my sons Vista, (must have dropped him on his head as a baby) the system could see the router but not connect. In the end I connected through an  ethernet cable and removed the wep key, so that it was an open network , his system could then connect and by logging  on through his browser, http:// 192.168.1.1 ,( this can vary)  he reapplied a new wep key.the other alternative was to use the reset button on the router to clear the wep.

---

### Post by avihappy on 2007-03-20
> **charles nicholls said:**
> I have just had the same prob although on my sons Vista, (must have dropped him on his head as a baby) the system could see the router but not connect. In the end I connected through an  ethernet cable and removed the wep key, so that it was an open network , his system could then connect and by logging  on through his browser, http:// 192.168.1.1 ,( this can vary)  he reapplied a new wep key.the other alternative was to use the reset button on the router to clear the wep.

I will look into that :)

---

### Post by dawv on 2007-03-26
i have edgy.. is there any way to get  it to work in edgy?
and if so how.. and what driver did you blacklist to get your card to get detected (i have the  EXACT same card)

---

### Post by avihappy on 2007-03-29
No, it failed. I don't get it, why did this card work in Dapper? Then, out of nowhere, it stops working on a fresh install of edgy. Feisty (what I am running now) won't work either. Please help, I am relegated to using my neighbor's slow connection. :(

BTW: My driver is ath_pci (as told by network-manager).

---

### Post by avihappy on 2007-03-29
PROBLEM SOLVED!

I was accidentally blocking myself from my router! All is good now.

If this card is failing for you, try and get on the internet (by Wired LAN) and then in the terminal type:
sudo apt-get install linux-restricted-modules-$(uname -r)

---

### Post by mohnkern on 2007-04-21
I was seeing the same problem, and tried your suggestion, and it still isn't connecting.

In windows both WEP and WPA work regardless of which way I connect to the router.


In Feisty the card works fine with security disabled, but when I try WEP (ascii) and put in the key
 word, I can't get anywhere.

I haven't tried the WEP (hex) yet, because I dread writing down the long key, and perhaps making a mistake. 


Also WPA and WPA2 aren't appearing at all, which is where I'd rather be.

Any suggestions?

---

### Post by mohnkern on 2007-04-21
Well, nm on the WEP, I managed to copy the key over to both Xp and Feisty, and WEP is working fine.

But I've installed the wpa stuff, and I'm not getting it in the gnome network manager.

I'd really like to go to wpa or wpa2.  I know the card drivers in XP support it.

---

