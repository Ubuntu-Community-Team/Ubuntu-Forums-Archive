---
title: "Google gadgets malfunction"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by ms2756 on 2009-01-06
Hi all,

So I just installed ggl-gtk. I have a really nice sidebar with a calendar and live-feed. But when I click on anything, there is a small square window popping on the left that goes blink-blink-blank. Anybody has same problem? Or a similar one.

Possible source of error, although I might sound like a total noob, I did:

sudo apt-get purge firefox
sudo apt-get install firefox
sudo apt-get install firefox-ubuntu-it-menu

I'm not sure if the above helps. Any ideas?

Thanks in advance.

---

### Post by Michael.Godawski on 2009-01-06
hey,

a screen-shot of  the blink-blink would help :D.

Applications > Accessories > Take Screenshoot. Set a delay time to reproduce the error and take a picture of it.

What is your graphic card by the way?

---

### Post by ms2756 on 2009-01-06
Uploaded.
Just a quick question: how do you put stuff in the pretty boxes and put images right in the reply? Where can I find more info like that? And please don't send me to Ubuntu FAQ - just came from there.

---

### Post by ms2756 on 2009-01-06
Ok, I can't attach it because it is too big, inserting image can come only from the internet (or is there a link to make it upload from my PC?)

Anyways, this is unrelated help, but I still appreciate it :)

---

### Post by ju2wheels on 2009-01-26
Im having the same problem but havent tried any testing to see what could be the cause. In general its a rendering issue that may be related to compiz as is typical with these sorts of graphics issues.

It happens to all windows that are launched by a widget except for the widget itself and its options configuration panel. Once a widget launches a second window it blinks like hell as if it were a strobe light.

---

### Post by ju2wheels on 2009-01-26
Heres the issue in action: [Video on tinypic]("http://tinypic.com/player.php?v=elemp3&s=5")

---

### Post by ju2wheels on 2009-01-27
Just an FYI they have release a new version that fixed the problem.

You can get 0.10.5 from getdeb.net and it should resolve the blinking issue.

---

