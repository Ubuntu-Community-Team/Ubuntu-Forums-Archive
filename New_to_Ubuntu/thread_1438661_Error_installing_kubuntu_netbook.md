---
title: "Error installing kubuntu netbook"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by browny254 on 2010-03-25
Hi, Im trying to install kubuntu netbook edition from a usb and it keeps coming up with an error (errno 5) when its trying to copy the install files at 37%. Is there anyway around this?

if not, can i create a new usb startup disk, while running a live version from a different usb drive and getting the iso from a 3rd usb drive? (does that make sense? :P)

---

### Post by browny254 on 2010-03-25
just a follow up...

lots of programs fail to run in live mode (such as dolphin), does this mean there could be a problem with the creation of the live disc and thus the installation, or is this normal?

---

### Post by undecim on 2010-03-25
I would check the MD5sum of the iso you donwloaded. If it's incorrect, download again.

If it is correct, then yes, you can make a new USB startup disk like you said. Though since you are installing a new system from a seemingly corrupt system, there is no guarantee that your new system will work.


[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by browny254 on 2010-03-26
Checked the MD5sum and it was good, so I recreated the usb disk and it has worked fine. Must have been a dodgy creation first time.

---

