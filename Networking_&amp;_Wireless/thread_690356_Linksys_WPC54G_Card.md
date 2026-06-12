---
title: "Linksys WPC54G Card"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by itzig on 2008-02-07
Hello, I am trying to get mt wireless card working on my laptop. I followed instructions from this page:
[http://antonym.org/node/89](http://antonym.org/node/89)
but it doesn't work!?..

step # 14 talks about :
 You will see some messages saying "Forcing parameter RadioState|0 to RadioState|1"
>>>I don't see that message at all!

then I did this:
sudo modprobe ndiswrapper

 and "echo ndiswrapper >> /etc/modules"
which gives me 'permission denied'...

I have this card out of the slot al this time, was ai suppose to keep it in there?

thank you!

---

### Post by itzig on 2008-02-07
btw, I am on gutsy gibbon 7.10

---

### Post by Hightide on 2008-02-07
HI itzig

This [thread]("http://ubuntuforums.org/showthread.php?t=358762") may help

regards

:)

---

### Post by rustybronco on 2008-02-07
what version card are you using? (it's on the bottom)

---

### Post by itzig on 2008-02-08
thank you, I'll check that article. It's for edgy, but I guess that doesn't matter.
Looks like I got V1, will test that other driver...

---

### Post by rustybronco on 2008-02-08
Make sure you use the correct drivers (v1 ) for your card.
v2, v5 ect. isn't going to work.

---

