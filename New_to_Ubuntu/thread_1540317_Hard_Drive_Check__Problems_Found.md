---
title: "Hard Drive Check | Problems Found"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-07-27
Ubuntu just ran its routine hard drive check, and I stupidly cancelled it. When I did, it said something to the effect of, "Serious problems found in / directory." So then I scheduled another check after one boot and rebooted the computer. This time, nothing was found (and the check was unexpectedly brief). Could the error message have been triggered by me cancelling the check? Are there other tests that I should run? Is my drive in trouble?

---

### Post by cariboo on 2010-07-27
You can always check the health of your hard drive by going to System-Administration-Disk Utility and select one of your hard drives, then select Smart Data. IT will give you more information than you want to know. :)

---

### Post by EnigmaticCoder on 2010-07-27
Well the self tested outputted "Completed OK." I want to run the "Check Filesystem" test, but it throws an error, "Device not ready." How do I run "Check Filesystem?"

---

### Post by OnlineBuddy on 2010-07-27
> **EnigmaticCoder said:**
> Well the self tested outputted "Completed OK." I want to run the "Check Filesystem" test, but it throws an error, "Device not ready." How do I run "Check Filesystem?"
.
.
you should run live cd and do error checking from there..

---

### Post by sandyd on 2010-07-27
> **EnigmaticCoder said:**
> Ubuntu just ran its routine hard drive check, and I stupidly cancelled it. When I did, it said something to the effect of, "Serious problems found in / directory." So then I scheduled another check after one boot and rebooted the computer. This time, nothing was found (and the check was unexpectedly brief). Could the error message have been triggered by me cancelling the check? Are there other tests that I should run? Is my drive in trouble?
it was triggered by canceling the check. When the check is cancled, fsck (the filesystem checker) flips out, and assumes that it was canceled due to a HD error.
you can disable the check if it bothers you, though it isn't reccomended.

disabling can be done through
```

sudo tune2fs -c **[number of boots/check]** /dev/sda1
```just set the number of boots to 0. and replace "/dev/sda1" with your linux partition

---

### Post by EnigmaticCoder on 2010-07-27
> **carlee said:**
> it was triggered by canceling the check. When the check is cancled, fsck (the filesystem checker) flips out, and assumes that it was canceled due to a HD error.

That's what I wanted to know. Thread solved.

---

