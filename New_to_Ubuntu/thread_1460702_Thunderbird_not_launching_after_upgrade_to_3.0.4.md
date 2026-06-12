---
title: "Thunderbird not launching after upgrade to 3.0.4"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by rockhen on 2010-04-23
Thunderbird has decided not to start up now after it was upgraded to 3.0.4 on a recent dist-upgrade so is there any way I can go back to 3.0.3? I have searched high and ruddy low for a solution as I have emails in Thunderbird I now can't read. If I put Thunderbird in a terminal, it starts, but it's a freash version and asks me to set up an account. Give up!!!:confused:

---

### Post by lidex on 2010-04-23
I would try running it with a new profile and if it works start importing your old data singly. Something in your old profile may be the culprit.
Alt+F2
```
thunderbird -P
```
Also look here:
[http://www.getsatisfaction.com/mozilla_messaging/topics/thunderbird_will_not_open_drivin_me_crazy]("http://www.getsatisfaction.com/mozilla_messaging/topics/thunderbird_will_not_open_drivin_me_crazy")
How was this installed BTW?

---

### Post by lidex on 2010-04-24
Bug Report with workaround:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/563893]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/563893")

---

