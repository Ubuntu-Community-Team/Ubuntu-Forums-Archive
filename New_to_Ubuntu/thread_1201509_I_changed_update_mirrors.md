---
title: "I changed update mirrors"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by DarinB on 2009-07-01
i messed up my system by rm a list.d
lost my medibuntu reinstalled it,,,,
i was also recommended to use best mirror for my area 
since then..... i get no error messages but no auto updates,,,,,,, it is set to receive them?
1. when is update day i remember it used to be thursday or does that only apply to the canonical site updates, and not to ie ....mirror.cc.columbia.edu....????????

---

### Post by tarps87 on 2009-07-01
I don't know when the updates are released on the canonical server, but it is up to the mirror you are using to when they are updated, in most cases it is the same day.
This will be one of the variables you will have to take into account when you work out which mirror is best for you.

When you say that automatic updates do not, does it work when you try a manual update?

---

### Post by DarinB on 2009-07-01
every time i click manual updates there are many things available like cups etc, in the past with the cononical servers those would have come up as a auto update. so i am not sure what is happening if the individual mirrors do auto updates?
so the short of it yes it does manual update but that is a pain to remember to do that.

---

### Post by tarps87 on 2009-07-01
That rules out any mirror configuration problems, I believe automatic updates should work with all mirrors.
This is not the ideal solution but you can try changing the mirror, maybe back to the main one just to test the automatic updates. If you check manually to make sure there are updates and set the update interval to daily (I don't think it goes any lower) this will speed up debugging.
Other than that I don't know, I will do some reading on the subject and post back if I discover anything

---

### Post by DarinB on 2009-07-01
it was set to daily i will hold off a week i get antsy and haven't gone more than a 3 days. but i did find updates each time. i will get back in a week to see if they come up thanks. if you find anything new out please let me know. Thank you

---

### Post by tarps87 on 2009-07-01
I have found a bug report and a work around here:
[https://answers.launchpad.net/ubuntu/+question/75268](https://answers.launchpad.net/ubuntu/+question/75268)

I will test it when I get home, the corn solution should be fine as long as you restrict only root to editing the file.

---

### Post by DarinB on 2009-07-01
i found this from the post above but i have no idea how to use it or if it is a good idea???????
and what is cron it as root????
doing something like this got me in trouble after i broke my updates by adding PlayDeb..... which i also got from here??????????????


[I]I can recommend creating a script:

#!/bin/bash
sudo apt-get update
sudo apt-get -y --force-yes dist-upgrade
sudo apt-get clean

Then cron it (as root) to run every day at say 4am (assuming you leave your computer on 24/7). This is how I do mine. Its not especially graceful or neat but it works. If you get no other replies I suggest you use this but I am sure there is a cleaner way to do it. I simply dont use gui stuff enough to be familiar with ubuntu's autoupdate regime.[/I]

---

