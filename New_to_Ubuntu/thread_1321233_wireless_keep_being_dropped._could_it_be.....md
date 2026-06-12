---
title: "wireless: keep being dropped. could it be...."
date: 2009-11-09
forum: New to Ubuntu
---

### Post by penguinv on 2009-11-09
I have wireless. It keeps being dropped. The signal is always good but it fluctuates, as if it is blown by the wind.

[INDENT]Windows picks it up right away (but I have to ask)
Ubuntu finds it and asks me but by that time it's already gone so I'm back to using windows.
-----> obviously both are unsatisfactory and the dropping certainly is not the fault of the OS but I'd like to mine the collective mind for information. Ha it's already dropped while I typed this far.[/INDENT]

Situation: neighbor at the other end in a 1 story, 4 apts long building. She has kindly given me her wireless password. So I cannot control the router at all.

What can be causing this? Teach me some radio principles if you can, please.
What can I do about this?

Thank you for your time!

PenguinV- Dell Dimension 4600 desktop. XP-Home,SP1/wubiUbuntu-9.04     
(re the SP1, I cant keep up the connection. I am working on

---

### Post by sandyd on 2009-11-09
> **penguinv said:**
> I have wireless. It keeps being dropped. The signal is always good but it fluctuates, as if it is blown by the wind.

[INDENT]Windows picks it up right away (but I have to ask)
Ubuntu finds it and asks me but by that time it's already gone so I'm back to using windows.
-----> obviously both are unsatisfactory and the dropping certainly is not the fault of the OS but I'd like to mine the collective mind for information. Ha it's already dropped while I typed this far.[/INDENT]

Situation: neighbor at the other end in a 1 story, 4 apts long building. She has kindly given me her wireless password. So I cannot control the router at all.

What can be causing this? Teach me some radio principles if you can, please.
What can I do about this?

Thank you for your time!

PenguinV- Dell Dimension 4600 desktop. XP-Home,SP1/wubiUbuntu-9.04     
(re the SP1, I cant keep up the connection. I am working on

most likely the signal is too weak. or has too much noise in it. metal objects such as staircases disrupt wireless signals (hence, the anti-wifi paint i saw on ebay used particles of metal in it...)

---

### Post by coldReactive on 2009-11-09
> **carlee said:**
> most likely the signal is too weak. or has too much noise in it. metal objects such as staircases disrupt wireless signals (hence, the anti-wifi paint i saw on ebay used particles of metal in it...)

Or the signal might be from an imac, which windows constantly will not connect to unless you manually connect to it (manual essid, wep key, no ieee auth, etc.)

Wish Ubuntu could turn on/off ieee auth since I think that's what my problem was.

---

### Post by twisted_steel on 2009-11-09
It could be some sort of interference with another access point.  I had some problems recently at my house where I would constantly lose the connection upstairs but not downstairs.  It turned out that one of my neighbors was also running on Channel 1.  Thanks to the magic of channel overlapping, the only real choices in the US are Channels 1, 6, and 11.  I moved my router to Channel 11 and it's been perfect.

[http://en.wikipedia.org/wiki/IEEE_802.11g-2003#Channels_and_Frequencies](http://en.wikipedia.org/wiki/IEEE_802.11g-2003#Channels_and_Frequencies)

Kismet is nice for taking a look to see what other devices are out there, though you would need to have a connection long enough to download and install the application ;)

[http://www.kismetwireless.net/](http://www.kismetwireless.net/)

---

