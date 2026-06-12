---
title: "wireless ranged decreased after switching to linux"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by epb613 on 2005-05-12
I've noticed after switching from windows to ubuntu that my wireless range had decreased. There are 2 rooms in my dorm where I used to be able to pick up a signal but can't anymore, and there are several rooms where I can still pick up a signal but it's lower than in windows.

Does anyone have any clue if there are some settings I could change (probably in iwconfig) that would fix this? Thanks.

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=epb613]I've noticed after switching from windows to ubuntu that my wireless range had decreased. There are 2 rooms in my dorm where I used to be able to pick up a signal but can't anymore, and there are several rooms where I can still pick up a signal but it's lower than in windows.

Does anyone have any clue if there are some settings I could change (probably in iwconfig) that would fix this? Thanks.[/QUOTE]


What card do you have? It might need some new firmware. If you can't find a firmware update (or if you are using something like ndiswrapper) what you see maybe what you get....

---

### Post by epb613 on 2005-05-12
I'm using an Intel 2200bg card with the latest firmware/drivers. That's an interesting idea though to maybe use the windows drivers through ndiswrapper instead of the native ones. I have used ndiswrapper with two different cards in the past and it's gone well so I may try this.

I have a theory as to the problem. I think linux is limiting the power being given to the card to save battery life. With windows I was able to set it to always transmit at max power. I have power settings off in iwconfig and my txpower is set to 20mw though and iwlist doesn't give me any other power options. So I very likely may be wrong.

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=epb613]I'm using an Intel 2200bg card with the latest firmware/drivers. That's an interesting idea though to maybe use the windows drivers through ndiswrapper instead of the native ones. I have used ndiswrapper with two different cards in the past and it's gone well so I may try this.

[/QUOTE]

Good idea. Thats using the old noggin. Thats how problems in Linux get fixed in my experiance- with some fresh thinking!

Good luck.

---

