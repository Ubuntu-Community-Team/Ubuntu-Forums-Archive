---
title: "Wireless =|"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by ownedbyhleb on 2007-10-09
I have a (un branded) wireless USB stick. It works fine in Windows XP, but whenever I use Ubuntu, and click on the Network Icon in the tray at the top, I see my wireless network. Even if i press connect and enter the corecct 128-bit Hex WEP Key it still deosn't connect. Even with my own manual settings, its not having it. Is there anyway to fix this problem? Preferrable with the use of internet.

ty.

---

### Post by jnorthr on 2007-10-09
does your server also use the same WEP key ? You might try to confirm that the same key is being used by both your machines.

---

### Post by ownedbyhleb on 2007-10-09
Yes, Its the same WEP Key. I use it to connect in Windows, and in Windows onmy laptop. Linux just wont connect for some reason.

---

### Post by kevdog on 2007-10-09
Can you post

lshw -C usb
iwlist scan

Thanks

---

### Post by cloudy-b on 2007-10-09
When I was setting up my wireless card on my laptop, I had to use the 2nd option, the one below 128-bit WEP. I think it said 128/64-bit WEP or something. It allowed me to put in my key and connected. Give that a try and see if it works?

Barron

---

