---
title: "BG2200 Wireless issues..."
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by coldcod on 2008-02-20
Need some help...
spent too many hours fighting with this already...

I have an Acer tracelmate 4000 series laptop with a Intel PRo BG2200.
I switched from XP to Ubuntu 7.1 a couple of weeks ago. Much like many comments here, my wireless worked great for the first week, then stopped working comletely.
Found the issue with iwconfig, the radio was off (kill swithc on?)
I installed the acer hot key driver which allows me to manually turn on the card, my button doesn't work. 
I use echo>on /proc/driver/acerhk/wirelessled in terminal.
This turns the card on, works great.
Everytime I shut down the laptop and restart, the wireless is off again,
and the hotkey is also off. Big pain to have to install hotkeys, then turn on card manually... every time we turn box on.
Bit much to ask of my wife (her computer), when all she wants to do is check her email.
Also, doesn't seem to want to shut off properly.. not sure if these may be related?

---

### Post by coldcod on 2008-03-05
help?

---

### Post by CheshireMac on 2008-04-09
I'm having similar issues with the same card (BG2200), on a HP nc8000 lappy. I've found that since I switched to wireless from direct, my connection has gone to the dogs. 
Every time I connect to the wireless (weak signal, by the way), I have possibly but precious moments before my card switches it's radio off. I have to go and reassign the ESSID in my tray and carry on . . . irritating to say the least. I was beginning to fear that it may be the age of this computer, creeping up on five years I think. Hearing about a similar problem is encouraging . . . 
As for your issue, are there still networks listed in your network manager? It may be that your problem is like mine, and you need to reconnect that way . . . I've tried a thousand different combinations to make it work in terminal, but I can't figure it out.
Hope this helps . . .if it doesn't, well, I could use some help with my issue as well. :)

---

