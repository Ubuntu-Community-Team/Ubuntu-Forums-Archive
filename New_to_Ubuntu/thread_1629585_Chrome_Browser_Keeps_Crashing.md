---
title: "Chrome Browser Keeps Crashing"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by luckylucky on 2010-11-23
[COLOR="Red"]************************************* 
EDIT: Please help, this issue is not resolved.  Please skip to post #5.  Thanks
************************************* [/COLOR]



I've got an unusual problem - unusual in that it spontaneously manifested in two OSes (on the same machine).

Starting chromium-browser (Google's chrome browser) and then going to any page causes it to crash by the whole program just closing.  Even attempted to have two tabs open because if you close a single tab it usually closes the browser session, thus hoping to see an "awe snap" page, but unfortunately even that bad page doesn't show up.  Browser just shuts down.

It is spontaneously (today) doing this on two versions of Ubuntu.  Ubuntu 10.10, and Peppermint OS Ice (an ubuntu derivative).  They are both on the same computer, acer aspire one D255, but aside from residing on the same machine they are separate partitions independent of each other.  The point is that aside from some weird hardware failure, which could be possible though unlikely as this is a brand new machine (two weeks), I don't see any other software possibilities as they are segregated.  Alternate idea: is it possible that an update was released today that crashed chrome?

In ubuntu 10.10 I tried to remove & reinstall chrome by using this:
```
sudo apt-get purge chromium-browser
sudo apt-get install chromium-browser
```
Basically no change.  What is bizarre is that all my bookmarks were still there, which I would have thought that with a purge they'd be gone.  Maybe my personal data wasn't erased?


Anyhow, I'm at a loss.  Any ideas?  Causes?  More importantly solutions?

---

### Post by luckylucky on 2010-11-23
Update:

Rebooted into peppermint to try there.  First tried and still broken.  Then I did (all sudo apt-get) remove, then autoremove, then purge, then update, then upgrade, then installed.

Guess what.  I'm writing this update in chrome (in peppermint).  Will now log back into ubuntu 10.10 and redo the above.  Will post results in about 15 minutes.

---

### Post by luckylucky on 2010-11-23
[COLOR="Red"]Need help please
[/COLOR]

So I'm back, but not with the expected news.  I'm using firefox to post this in ubuntu 10.10.  

Again, peppermint is fixed.  Chrome in ubuntu still failed after running the above mentioned sequence twice.

Please, anyone got suggestions?

---

### Post by luckylucky on 2010-11-26
bump

---

### Post by luckylucky on 2010-12-03
[COLOR="Red"]Please help

Chrome Browser is NOT working in Ubuntu

Did all the above things and I'm stuck without the browser.

Looking forward to seeing a reply

Thank you[/COLOR]

---

### Post by ozarkman on 2010-12-27
I have the same problem. started a week or two ago with random crashes now chrome wont stay open at all.

---

### Post by rburkartjo on 2010-12-28
just a suggestion are you using chrome or chromium. why not try installing chromium and then install ubuntu tweak if you dont have it installed yet. go to the source center in ubuntu tweak and check the daily builds of chromium. been doing this for about a year and never had a problem. good luck

---

