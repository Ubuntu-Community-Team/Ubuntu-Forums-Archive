---
title: "Removing Screenlet Window Frame"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by libohound on 2009-03-03
All,

I'm very new to the Ubuntu experience, so any advice you provide, please break it down to me idiot-style. Thank you.

I just installed the Screenlets app and have added the calendar to my desktop. My issue is that I can't figure out how to remove the window frame or title bar or whatever you want to call it. I've installed CCSM, but can't figure out how to manipulate it in a way that will allow me to remove the border for the Screenlet window only (I don't want to remove every decoration).

Any ideas? Thank you kindly.

---

### Post by libohound on 2009-03-04
Hello? Any ideas?

---

### Post by skymera on 2009-03-04
Remove the border for the screenlet app?

Or for the calender screenlet itself?

---

### Post by libohound on 2009-03-04
Either would work. I've only got the calendar Screenlet up now, but should I decide to add more, it might be handy to just remove them from the Screenlet app altogether.

---

### Post by libohound on 2009-03-05
*nudge*

---

### Post by libohound on 2009-03-05
C'mon, people! You mean to tell me that there's no solution to this problem? Really? Really?

---

### Post by libohound on 2009-03-26
Please ... there must be a solution. I've read everything I can find on the subject, but nothing is fixing the problem. I thought you guys were supposed to be the best of the best.

---

### Post by VCoolio on 2009-03-26
Hi, sorry, I just stumbled upon your question. In CCSM, go to the Window Decoration plugin. In the field called "decoration window" fill in: 
any & !class=xxx
This means: decorate every window (any) and don't decorate windows of class xxx. Just figure out what to fill in for xxx. You can press the + button on the right of the entry field and grab the desklet. Just see what it is called and fill it in. Good luck!

---

### Post by libohound on 2009-03-27
> **VCoolio said:**
> Hi, sorry, I just stumbled upon your question. In CCSM, go to the Window Decoration plugin. In the field called "decoration window" fill in: 
any & !class=xxx
This means: decorate every window (any) and don't decorate windows of class xxx. Just figure out what to fill in for xxx. You can press the + button on the right of the entry field and grab the desklet. Just see what it is called and fill it in. Good luck!

Thank you so much for the reply, but sadly, it didn't work. In fact, I haven't been able to get CCSM to do anything for me ... at all. I think it could be because I'm running Hardy Heron on a Dell 12 netbook with only 1GB of RAM, but ... that shouldn't hinder CCSM's ability to remove a window decoration, should it?

---

### Post by VCoolio on 2009-03-27
Dude, I'm running Intrepid with 512 Mb RAM, this sure is not your problem. I also had compiz doing its thing in Hardy. Do you have compiz running as your window manager then? What if you run compiz --replace and then try your luck? It's my last shot btw, I'm no expert on this. At least your thread has been bumped this way, maybe someone else has a solution.

---

### Post by libohound on 2009-03-27
> **VCoolio said:**
> Dude, I'm running Intrepid with 512 Mb RAM, this sure is not your problem. I also had compiz doing its thing in Hardy. Do you have compiz running as your window manager then? What if you run compiz --replace and then try your luck? It's my last shot btw, I'm no expert on this. At least your thread has been bumped this way, maybe someone else has a solution.

Pardon my ignorance, but ... how do you set Compiz as your window manager?

---

### Post by VCoolio on 2009-03-27
Dunno, went automatically for me I guess. But check [this]("http://damumbl.byteholder.de/blog/?p=44") out. Don't blame your ignorance, it seems not to be that straightforward.

---

