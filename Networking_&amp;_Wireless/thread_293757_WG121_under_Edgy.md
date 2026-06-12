---
title: "WG121 under Edgy"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by yawnster on 2006-11-05
Howdy guys,

updated to edgy yesterday, had a little trouble with my power supply failing, but thats all sorted now i think. Ive now got to the next step, wireless..

Right well ive tried using the standard network admin that comes with ubuntu, comes back negative, I put in the ESSID (used my last name, LATCHFORD).. I am using DHCP to detect settings, so i think ive configured it correctly.. Its just doesnt like the card..

Fine I say.. lets try ndiswrapper, ive tried it with 1.1 version of the utils package and the 1.8 version, both times the output of **iwconfig** has been..

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth3      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=14  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I had this card setup on Dapper, however it required a new kernel.. This is something im hoping to avoid..

Thing is that, it says driver present and hardware all present.. The lights are on, but when I try and set the ESSID or scan for a network it doesnt play ball...

Do I need to blacklist the card from the standard network admin? 

Also last time i got the card working it was under the name wlan0 and not eth3, however that was the problem before.. But i cant remember for the life of me how i managed to fix it..

Anyway, ill leave this here and anyone that can help me it would be much appreciated.. Alex

---

### Post by yawnster on 2006-11-06
Bump

---

### Post by mwaddoups on 2007-01-30
Have a look at my howto here: [http://ubuntuforums.org/showthread.php?t=177958]("http://ubuntuforums.org/showthread.php?t=177958")

After following those steps it should show up as wlan0 and work fine.

Good luck!

Mark

Edit: Dam, forgot to check the date...sorry for bumping this

---

### Post by GringoMatt on 2007-03-28
Hi Yawnster,
when I was trying to get my netgear working before I came across your guide in the community docs area, worked a treat many thanks. I recently upgraded to Feisty and guess what, yep the wireless device no longer works. Just wondered if you had moved to Feisty and if you were having similar problems to me?

cheers

Matt

---

### Post by GringoMjA on 2007-04-10
The Feisty problem has sorted itself out with some updates and is actually working better than ever now.

Matt

---

