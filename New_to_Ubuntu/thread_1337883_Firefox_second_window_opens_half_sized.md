---
title: "Firefox second window opens half sized"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by damontallen on 2009-11-25
I just upgraded from 9.04 to 9.10 and now when I open a second window of Firefox it can't be made full size. [http://imgur.com/3vF5T.jpg]("http://imgur.com/3vF5T.jpg") The first time I opened Firefox the first window didn't open full size and couldn't be resized but that went away after a reboot.  Now the first window opens fine, its just the second window.

These are the addons I am running [http://imgur.com/ItfmN.jpg]("http://imgur.com/ItfmN.jpg") but they are the same ones I was using before.  I usually end up running two windows because I leave one window open for email and work while the second window is just for surfing.  Any idea about how to fix this?  I've rebooted a few times since and tried using Swiftfox but it has the same problem.

---

### Post by AndThenWhat on 2009-11-25
First, I would suggest disabling all add-ons and restarting Firefox in order to determine that they are not the cause of the problem.

Also, this sounds like a similar problem:

[http://forums.techguy.org/web-email/565957-firefox-opens-half-size-window.html](http://forums.techguy.org/web-email/565957-firefox-opens-half-size-window.html)

Solution was deleting a localstore.rdf file?

---

### Post by damontallen on 2009-11-25
Well, deleting the localstore.rdf file did not work but disabling all of the addons did.  It turns out that Tab Mix Plus is the culprit.  I don't know why though because it was working in 9.04.  Well the solution is disabling Tab Mix Plus.

Thanks for your help.

---

