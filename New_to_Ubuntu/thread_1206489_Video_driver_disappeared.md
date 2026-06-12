---
title: "Video driver disappeared?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by random turnip on 2009-07-07
Ok, so i installed Ubuntu last night and on the live CD everything seemed to be working (even the wireless, which was something that didn't work at all in 8.10) including Ubuntu recognizing the video card to get my full screen res.
However, after the installation, i booted up to the default res, no surprise, went into drivers, and my nvidia driver which worked perfectly before wasn't in the list so i'm stuck with the default res and everything is huge.
Any ideas?

---

### Post by overdrank on 2009-07-07
> **random turnip said:**
> Ok, so i installed Ubuntu last night and on the live CD everything seemed to be working (even the wireless, which was something that didn't work at all in 8.10) including Ubuntu recognizing the video card to get my full screen res.
However, after the installation, i booted up to the default res, no surprise, went into drivers, and my nvidia driver which worked perfectly before wasn't in the list so i'm stuck with the default res and everything is huge.
Any ideas?

Hi and what is the model of the graphics card?
You may try and update your system, system, administration, update manager or ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by random turnip on 2009-07-07
Sorry, updating did the job, now my Ubuntu is fully ready to use.
[solved]

---

