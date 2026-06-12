---
title: "Ubuntu 11.04: Session Restarting, Chrome Crashing?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by unknowngal on 2011-05-04
So these two random things happened today.

1. My Ubuntu session logged me off when this happened: I installed Forecastfox in Google Chrome, and just when I hit enter to input my zip code into the extension, Ubuntu logged me off. I had to sign in again.

2. Chrome, so far, has crashed twice I believe. It just closes, and I have to click on the Chrome icon to start it up again.

Now, I dunno if it's the computer...it's 86 degrees right now, though possibly cooler here indoors, maybe 80, so could the heat be overheating the computer, which in turn is causing Ubuntu to be a little flakey? Or is there some sort of bug in Ubuntu causing this?

Thank you for any answers sent my way!

---

### Post by richardjbattyjr on 2011-05-06
I am having a similar problem. Since I put 11.04 on my computer chrome has restarted to the login screen everytime I click on certain links.

---

### Post by rafaelcoelho on 2011-05-09
me too. since I upgraded to 11.04 gnome keeps crashing (go to the login screen), usually when I'm at Chrome

---

### Post by ancrum on 2011-05-11
Me too - and it's driving me crazy!

---

### Post by ancrum on 2011-05-11
I think I've solved my issue.  I removed Adblock Plus for Chrome as that seemed to crash Chrome.  It seems to be stable now....

---

### Post by everthonvaladao on 2011-05-27
My Ubuntu session was restarting too often, always when I'm using Chromium-browser. Digging the Web, I've found that, apparently, the culprit is the Chromium "Bookmark Sync" process. Disabling it should prevent such freezes from happening.

More info:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546871)
[http://www.google.com/support/forum/p/Chrome/thread?tid=7493a9fc196ea8be&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=7493a9fc196ea8be&hl=en)

---

### Post by kaefert66014235 on 2011-05-28
I have the same issue with the session crashing, but it doesn't seem to be related to chromium (although I use the sync features and I also have add-block) but it startet right after I installed calibre, the e-book library manager. Its really driving me crazy, it happens twice an hour or something.. the more often the more I use calibre.

EDIT: found the bug here:
[https://bugs.launchpad.net/ubuntu/+source/calibre/+bug/754886](https://bugs.launchpad.net/ubuntu/+source/calibre/+bug/754886)

---

### Post by jasonrisenburg on 2011-07-13
I am having the same problem.

---

