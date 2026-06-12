---
title: "earphone plugged sound still coming from headphones"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by divercetgd on 2010-08-25
hi everybody;
i am using ubuntu 10.04 and i still couldnt find solution to this sound problem..i am using msi computer, but i couldnt figure out my model, if someone can help me about that, i can give that information too..

---

### Post by lidex on 2010-08-25
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by divercetgd on 2010-09-10
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/635317](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/635317) this is my bug report. thank you again..when i was using ubuntu 8.04 or 8.10 i cant remember which one there was no problem like this..

---

### Post by JohnHeikkila on 2010-09-10
I can't see anything special in the bug report but "Soundcard not detected".

Click the audio sign at the notification area of your menu panel, then click Sound preferences. Check all the tabs (especially Output) if the audio is going into the headphones or into the Internal driver.

---

### Post by divercetgd on 2010-09-13
> **JohnHeikkila said:**
> I can't see anything special in the bug report but "Soundcard not detected".

Click the audio sign at the notification area of your menu panel, then click Sound preferences. Check all the tabs (especially Output) if the audio is going into the headphones or into the Internal driver.

if i change output to "analog headphones" no sound is coming from either of them. if i change it to "analog speakers" sound is coming from both.

---

### Post by lidex on 2010-09-14
According to the bug report, you should upgrade alsa drivers. Use the link in my sig.

---

