---
title: "Wireless Connection Dropping (Gutsy)"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by Logistics64 on 2008-01-26
Ok I finally got my Belkin F5D7050 USB (Version 3000) wireless "card to work". I then had a problem where the connection would automatically get the information, so i maually configured it. However, now, after an average of 2 hours, my connection will drop. I have to unplug the USB (sometimes reboot) and re-connect. Do any of you guys know how i could fix this? Also, do you think install Fiesty instead of Gutsy would fix these problems? There are a few other issues, which is why I am considering Down-Grading. If it would be a good idea to down-grade, which features would i lose? (programs, themes, etc). Thank you for any help i recieve. Sorry for the long post also.

---

### Post by bwtranch on 2008-01-26
I have the exact same card. Do you have roaming enabled? if so don't. Let me know. I know I can help you get this fixed.

---

### Post by Logistics64 on 2008-01-26
Well, thanks for the fast relpy. Well, actually, i dont. The only way i could even get the net was to maually configure

---

### Post by bwtranch on 2008-01-26
Yeah, no problem. I jumped on this one 'cause I know it. Mine was doing the same thing, but here's the story...your config may be slightly different but. The zd1211 driver is already installed on Ubuntu. If you go to Network you can click on properties and then you see the options. Wait, I need to go to that computer in the other room. I'm on the wired one.

---

### Post by Logistics64 on 2008-01-26
Im usi ng the rt73 driver. Installed it using NDISWRAPPER. Thats how i got it working, now i need to stop the dropping

---

### Post by bwtranch on 2008-01-26
Okay I have roaming off Network is Belkin_N_Wireless_1fxxxx Password type is WPA personal (that's what got mine to work, when I changed that) the password and I'm using DHCP.

---

### Post by bwtranch on 2008-01-26
Oh, I didn't see your last post. Things are a little nutty around here all of a sudden. Had a cat attack outside. Anyway, I didn't have to use the wrapper and the info I got was not to use the wrapper and un-install it if you have it .Must have been right because this works 24-7.

---

### Post by Logistics64 on 2008-01-26
im confued, lemme get my Linux Box back connected, it fell off my desk :/

---

### Post by bwtranch on 2008-01-26
LOL Everybody's got weird things going on !!! The moon must be full. :) My poor cat is freaked out from something. He's OK though. I think if you just un-install that wrapper and re-boot with the card in, it should recognize it and then set it up with Networks. But, I know the zd1211 is the right driver.

---

### Post by Logistics64 on 2008-01-26
are u sure that it will automatically configure? It didnt before. Also, make sure you have version 3002. belkin made it in 1000 2000 3000 4000. V 400?0 works out of the box, the rest dont. Would using Fiesty instead help?

---

### Post by bwtranch on 2008-01-26
I've got ver. 3000 and it worked. I am using Gutsy on this machine. x86. I did have to do a re-start a couple of times and that WPA Personal was the key with no roaming. If you do a re-start with the chip in there... now wait a minute, this is the USB one, right, Oh God I hope so....

---

### Post by Logistics64 on 2008-01-26
Indeed, the USB it is
Now, it didnt auto-configure when i installed Gutsy. It was also a brand new comp put together with old parts (and a new and empty HD). So, what do u think i need to do at this point? Fiesty? Or re-do the drivers

---

### Post by bwtranch on 2008-01-26
I would try re-doing the drivers. Seems like going back to 7.04 is a step in the wrong direction. I know, it's a rough call, but I always like moving forward and take what comes. That's just me though.

---

### Post by Logistics64 on 2008-01-26
ill get back to you tommorow, ill see if it drops agasin. You can add me to aim or msn if you want. Just tell me ur S/N

---

### Post by Logistics64 on 2008-01-27
Well, it hasnt dropped yet (fingers crossed!). So if it does ill let you know. Thanks for the help!

---

