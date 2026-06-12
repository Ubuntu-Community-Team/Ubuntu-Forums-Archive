---
title: "How to report problems"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by ciaopaulo on 2009-09-19
Hey Guys,

OK I've been trying Ubuntu for a few weeks now, and I've encountered a few crashes, system freezes, and mashed screens.

So how do I let the developers know? Are there files that I can send them after a (OS) crash/freeze so they can investigate the matter?

I know there's launchpad, but just going on and typing in "my computer just crashed" seems a bit useless.

---

### Post by jerrrys on 2009-09-19
you may want to search for answers first

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by kostkon on 2009-09-19
Yes, there is a faster way to do it. Check [this youtube vid]("http://www.youtube.com/watch?v=_6TISSCBolc"), if you can.

---

### Post by Paqman on 2009-09-19
> **ciaopaulo said:**
> 
So how do I let the developers know? Are there files that I can send them after a (OS) crash/freeze so they can investigate the matter?


You can enable apport to help you make automated submissions to Launchpad. You'll need a Launchpad account, then you'll have to [enable apport]("https://wiki.ubuntu.com/Apport#How%20to%20enable%20apport").

When the system detects a crash, apport will pop up and help you submit the problem, including attaching diagnostically useful reports. It'll also check for duplicates, and if you find someone has already reported the problem, you can auitomatically list yourself as being affected by it. If you want you can also subscribe to that bug to receive updates on progress.

---

### Post by ciaopaulo on 2009-09-20
OK That looks quite useful.

Will it auto send a report after a system crash?

I've had three kinds so far:

- Power cycle kind

- Screen freeze

- Screen mashed (looks a little like [this]("http://farm3.static.flickr.com/2412/1989607415_ca67df1c9b.jpg"))

---

