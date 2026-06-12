---
title: "How can I disable the updater for ubuntu 8.04 live cd"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-01-08
This is a strange question, but I am trying to find a way to disable the update notifier for ubuntu 8.04 Live CD. I customized my own version and I wrote a start up script for it, saying to killall update-notifier when it first boots up, but 1-5 hours down the line I will see a  baloon pop up in the top right hand corner of my screen saying that packages are needing to be install, Anyone have a fix for this, or is it impossible to fix without screwing something else up.

Thanks in advance.

---

### Post by gsmanners on 2010-01-08
It's not impossible of course, but bear in mind that you are choosing to do something that could become a security risk (depending on how you use your machine):

sudo apt-get remove update-notifier ubuntu-desktop

---

### Post by Captain_tux on 2010-01-09
Is simply ignoring and choosing not to update out of the realm of possibilities?

---

### Post by ericeclifford on 2010-01-11
> **gsmanners said:**
> It's not impossible of course, but bear in mind that you are choosing to do something that could become a security risk (depending on how you use your machine):

sudo apt-get remove update-notifier ubuntu-desktop

Ya I noticed that, is removing these packages harmful?

---

### Post by slakkie on 2010-01-11
> **ericeclifford said:**
> Ya I noticed that, is removing these packages harmful?

No.

The ubuntu-desktop package is a meta-package, and the notifier thing just notifies you. So.. I don't see any issues in removing them.

However, I do think there is an option which tells you not to notify you or check for updates. I don't use gnome, don't have the thing displayed or installed, but it should be there if memory serves me well.

---

