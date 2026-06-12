---
title: "Flash for Youtube"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by zorrofox on 2009-10-24
Hello everyone.

I've just performed a full install (as opposed to a dual-boot) of Ubuntu 9.04 and I can't get Youtube to play videos. What Flash package should I be downloading and installing?

Scratch that. Reboot sorted the problem. If I knew how to delete this thread I would. Sorry for the inconvenience.

---

### Post by dunkar70 on 2009-10-24
The link below will take you to the page describing Flash.

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by Hosmion on 2009-10-24
The .deb is the easiest to download..  If that doesn't work (which it didn't for me,) type this in Terminal:

```
sudo apt-get install flashplugin-nonfree
```

I tried the code above but it didn't work for me for some reason, but maybe you will have more luck than I :D

---

### Post by philinux on 2009-10-24
> **zorrofox said:**
> Hello everyone.

I've just performed a full install (as opposed to a dual-boot) of Ubuntu 9.04 and I can't get Youtube to play videos. What Flash package should I be downloading and installing?

Scratch that. Reboot sorted the problem. If I knew how to delete this thread I would. Sorry for the inconvenience.

64 or 32 bit install?

---

### Post by zorrofox on 2009-10-24
Got it guys. .deb worked for me too but only after I'd installed the restricted packages. Thanks again.

---

