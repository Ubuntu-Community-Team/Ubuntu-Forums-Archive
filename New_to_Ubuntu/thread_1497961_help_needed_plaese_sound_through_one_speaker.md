---
title: "help needed plaese sound through one speaker"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by scooterstew on 2010-05-31
hi i need help,ive just installed ubuntu 10.04, this is the first time i have ever used ubuntu...
i have sound coming through one speaker only ,i havent got a clue what i am doing...please give some advice!!!
thanks in advance....

---

### Post by genis200 on 2010-05-31
I'll need the specifications of your sound card.

---

### Post by fooman on 2010-05-31
have you checked the obvious things like the speaker connections and the balance settings?  first of course,  double check your connections both on the speakers themselves, and where they connect to your pc.

for the balance....look in the top panel and left-click on the speaker/volume icon.  choose "sound preferences".

in the sound preferences window,  click "output" and move the balance slider accordingly.

---

### Post by scooterstew on 2010-05-31
hi there,
thanks for your reply...the sound card is a via envoy card...
ive just noticed that if i use my built in sound on the motherboard it works fine through both speakers...
so obviously a problem with my sound card!!!
i have tried moving sliders etc...but no go...

---

### Post by scooterstew on 2010-05-31
it must be a problem with my sound card clashing with ubuntu 10.04...
it comes up as a vti1720/24 envy 24 pt/ht....multi channel audio controller on the sound preferences...
i know that it uses a via chip...and thats all i can remember about it...
it worked fine with xp..and i used via envy drivers for it...
any ideas?

---

### Post by scooterstew on 2010-05-31
anybody there at all?

---

### Post by boombox1387 on 2010-09-27
Sorry you didn't get any responses, scooterstew.  I'm just bumping this topic a bit because I'm having a related issue, and it would be nice to know how to go about debugging.

I'm not at my computer right now, so I can't check to see what exactly the problem is, but here's what I remember:  One day, my Diamond Xtreme Sound sound card randomly stopped working when I unplugged my headphones and plugged my speakers back in.  After some fiddling, I figured out that if I plug the main speaker cable (green) into the surround sound spot (orange), I can get sound to come through the right speaker if I set the device to either 4.1 or 5.1 surround sound (in Ubuntu's Sound Preferences).

I assumed that my sound card was a lost cause until last night, when I removed it and switched back to the motherboard's built-in sound.  This also did not work with Ubuntu, unless I plug the green speaker cable into the microphone input (red), which again results in only the right speaker working.  I switched back to the sound card and started up Windows, which had no problem playing audio correctly to both speakers.

So I'm really confused.  This means that my sound card isn't dead, and the issue seems to be Ubuntu-specific.  However, it probably isn't a driver issue in my case because roughly the same problem happens with two completely different sound cards.

Anyway, I don't mean to hijack this thread... I'm not really looking for answers, but some more info on how to debug this would probably be useful for both me and scooterstew.  Thanks!

---

