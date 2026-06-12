---
title: "intel pro wireless 2200bg .. medion 95400 wireless not working.. im a linux newbie"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by lochstar360 on 2007-12-13
Hi, I finally installed linux on my Medion MD95400 laptop, from Aldi, but the wireless doesn't work. There is a button on the laptop that turns the card on in windows but it doesnt work on linux. I have found out that i have an Intel Pro Wireless 2200BG card, but i need somebody to give me easy instructions (please). I have a found a few guides on the internet, but i dont understand one word of it. I have never used terminal, only ms-dos.  Could somebody please help me? I would be greatly appreicative.

Thankyou,
Lochie

---

### Post by csat on 2007-12-13
[QUOTE=lochstar360;3943688. I have never used terminal, only ms-dos. 

Thankyou,
Lochie[/QUOTE]

You are one step ahead many users.  Terminal console is like a DOS window.  Here are some links that might help you out:

[http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys](http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys)

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

[http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)

Good luck.

---

### Post by heindsight on 2007-12-14
Hi  Lochie,

How do you normally turn the card on/off in windows? Is it by some keyboard combination, or is there a dedicated switch?

It might help if you can execute the command iwconfig in a terminal and post the  the output here. To try to see if your card's on/off button does anything at all, you could perhaps run iwconfig then try to turn the card on (as you would in windows)  and run iwconfig again (if there's a difference in the then post both here).

---

### Post by heindsight on 2007-12-14
OK, never mind my previous post. I just saw  [this]("http://nickdm.homemail.com.au/md95400/linux-on-laptops.html").

apparently you need the Acer hotkey driver, which is available [here]("http://www.cakey.de/acerhk/"). Unfortunately there don't seem to be any ubuntu or debian pinary packages available, so you'll have to install it from source code.

---

