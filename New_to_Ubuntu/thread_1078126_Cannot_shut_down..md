---
title: "Cannot shut down."
date: 2009-02-23
forum: New to Ubuntu
---

### Post by vaslat29 on 2009-02-23
Hi
I installed Ubuntu through Wubi. It has been installed alright and I can boot into the OS through dual boot. The other OS is Vista which I would like to use as little as possible in the future.
Now when I try to shut down though Ubuntu, it starts shutting down but then stops and presents a blank screen with the curser blinking.

Any solutions anyone. The easiest one would probably be to re-install - but is there any other alternative to this.

---

### Post by x33a on 2009-02-23
might be due to alsa.

take a look here:

[https://answers.launchpad.net/ubuntu/+question/49799](https://answers.launchpad.net/ubuntu/+question/49799)

---

### Post by Locke_99GS on 2009-02-23
A neat new bug that was introduced in the 8.10 official release. It is a conflict between ALSA and the network. (I don't see how they're not mutually exclusive) They added some more kludge to circumvent the issue, and the kludgepatch is included in the updates.

Update your Ubuntu install, and you'll be able to shutdown properly.

edit: to verify (as this kludgepatch should have been included in the updates iso's) unplug your network or turn off your router just prior to shutting down. If it shut's down successfully, this is your issue.

---

### Post by vaslat29 on 2009-03-15
> **Locke_99GS said:**
> A neat new bug that was introduced in the 8.10 official release. It is a conflict between ALSA and the network. (I don't see how they're not mutually exclusive) They added some more kludge to circumvent the issue, and the kludgepatch is included in the updates.

Update your Ubuntu install, and you'll be able to shutdown properly.

edit: to verify (as this kludgepatch should have been included in the updates iso's) unplug your network or turn off your router just prior to shutting down. If it shut's down successfully, this is your issue.
Lokde
I actually disabled the wireless adaptor on my laptop before shutting down and it worked (or rather it shut down!). But when I installed updates (there were 270 of them!) and tried shutting down it said kernel panic. So I have re-installed and am back to square one.

---

### Post by bumanie on 2009-03-15
Try > sudo shutdown -h now in terminal

---

### Post by Locke_99GS on 2009-03-16
I'd try updating again - I'll post back in a few with a link to the work-around. 
edit: hmmm, I can't seem to find it. Essentially, it just shutdown the network prior to shutting down ALSA.

> **bumanie said:**
> Try  in terminal

Really? Did you really just say that?

Please, read the entire thread.

---

