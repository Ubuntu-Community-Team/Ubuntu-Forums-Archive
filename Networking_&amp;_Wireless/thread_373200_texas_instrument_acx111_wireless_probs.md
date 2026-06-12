---
title: "texas instrument acx111 wireless probs"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by rdh on 2007-03-01
I have set up ubuntu 6.06 on a 850MHz duron pc - no problems at all, dual booting with winxp. Everything is great except for my texas instruments pci acx111 wireless card. The card is recognised in the networking wndow, and I can input wep code etc. I have tried dchp and static address, manually inputting settings, but I cannot get online. I have checked that the card is recognised using lspci_-v_¦_less, and it is listed as 
Texas Instruments ACX111 54Mbps wireless interface
vendor: unknown
device: unknown
status:status
Bus type: unknown
device type: net.8021
capabillities: net,net.80211

I found a link from google, suggesting that I type the following:
options acx firmware_ver=1.2.1.34

into /etc/modprobe.d./options

I went to file browser and found the file? folder? /etc/modprobe.d./options, typed it in, but says i cannot save the changes. 
I know that the hardware is fine, as the card works fine with xp. 

I'm sure i've missed something fundamental, but I am truely stuck. Any help would be very appreciated! Thanks

PS i'm a total novice so you may have to spell things out!

---

### Post by Kobalt on 2007-03-01
Hello,

I have a wifi card that had the exact same chip, I had to use a little trick to get it to work. Here is the thread were I explain it : [http://www.ubuntuforums.org/showthread.php?t=233565](http://www.ubuntuforums.org/showthread.php?t=233565)

Cheerio :)

---

### Post by rdh on 2007-03-01
Thanks Kobalt  I tried what you suggested, but the pc hung with error messages on reboot. I couldn't get back in at all, so ended up doing a clean install, but with breezy badger - hey presto wireless worked straight away!  Would you recommend updating to later version using the update manager, or leaving well alone! What are the advantages of a later release, and am i likely to experience problems if i do so?  many thanks rdh

---

### Post by Kobalt on 2007-03-01
The trick I described is very not likely to have caused your system to crash... 
There are many advantages to upgrading to a newer version, at first getting more up-to-date softwares. You'd also get more features, more reliability... In your case I would suggest upgrading to the next version of yours, that is to say Dapper. 
Check [this]("https://help.ubuntu.com/community/UpgradeNotes") out to learn more on upgrading.

---

