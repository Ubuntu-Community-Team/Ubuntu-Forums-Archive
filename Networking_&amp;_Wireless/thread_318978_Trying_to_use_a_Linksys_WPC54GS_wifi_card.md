---
title: "Trying to use a Linksys WPC54GS wifi card"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by LordExcelsior on 2006-12-14
Newb Alert.  I have very little knowledge of Ubuntu, or even Linux for that matter.   So I just ask that if you can be as descriptively as possible, it would be very appreciated.

I picked up said card for my laptop at a Best Buy a while ago.  I then made a few searches and I chose ndiswrapper as the way to go.  I tried to install it, but I am having problems left and right, mainly because I don't think I am using the right commands, or I must be doing something wrong.

So if someone could give me a little walkthough, or recomend and easier method I would be very grateful.

Thank you!

UPDATE:  Ok, I noticed that Automatix has ndiswrapper, so I installed using that, and now it runs.  The problem is.  It says that my hardware is not present.

SECOND UPDATE:  Ok, it says that the hardware is now present, but I am stuck on what to do next as the card still refuses to work.

---

### Post by LordExcelsior on 2006-12-15
I'm still having dificulties trying to get my card to work, and since I fell off the front page, I'd figure a good bump is in order.

---

### Post by LordExcelsior on 2006-12-16
Still trying to get an answer.

---

### Post by jd4x4 on 2006-12-16
I'm in the same boat (sorry, I wish I had an answer). I'm a newb like you & have just installed XUbuntu on my IBM A20m laptop w/Linksys card.

I'll add that I'm guessing this has someting to do with all of the Broadcom 43xx stuff I'm seeing, but I'm reluctant to just jump in and try something until I understand what's going on.

I used the alternate install CD (of XUbuntu), and I got a couple of messages during the install that I didn't write down, but it went past anyway. I think it has bearing on the problem because it said something about not being able to find BCM43xx.(some file extension). If there is an install log file and anyone can tell me where to find it, I'll post what it says.

The card seems to be detected, but it's not seeing my wireless access point. The card works fine in Win XP.

I'm not pressed to get it working, since I'm "just looking" at Linux at the moment so if it would help I'd be willing to wipe out the linux partition & reinstall, this time writing the info down. I'd rather figure out the way it should have been installed rather than "just get it working", anyway.

---

### Post by jd4x4 on 2006-12-17
Nobody interested... just as well. Fixed mine by going to:
  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)
and:
  [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Not sure how/why I missed the WiFi Docs but isn't it usually the case that the answer is in the instructions?! :-)

Followed the step-by-step in the second link and it was resolved in step 4b (after a restart).

---

### Post by LordExcelsior on 2006-12-18
> **jd4x4 said:**
> Nobody interested... just as well. Fixed mine by going to:
  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)
and:
  [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Not sure how/why I missed the WiFi Docs but isn't it usually the case that the answer is in the instructions?! :-)

Followed the step-by-step in the second link and it was resolved in step 4b (after a restart).
Thanks so much JD!  I finally have everything up and running!

I used the second link and my problem was solved on 4b also! ^-^

---

### Post by chaofan on 2007-01-31
EDIT:
Ooops, wrong thread, sorry...

---

