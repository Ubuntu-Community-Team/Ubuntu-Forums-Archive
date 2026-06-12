---
title: "What happens when I try to boot Ubuntu Netbook Remix"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by RebeccaHowarth on 2010-02-21
I get the following:

init:  udevtrigger main process (421) terminated with status 1
init:  networking post-stop process (422) terminated with status 1
init:  udevmonitor main process (420) killed by TERM signal
fsk from util-linux-ng 2.16
/dev/loop0:clean, 129466/1073152 files, 681125/4286464 blocks
init:  networking main process (453) terminated with status 1

What is this problem, and how do I correct it?

---

### Post by RebeccaHowarth on 2010-02-21
Also, I am running this on an Acer Aspire 5517.

---

### Post by RebeccaHowarth on 2010-02-22
Anybody?

---

### Post by mikechant on 2010-02-22
Here's a solution that worked for someone, but it's maybe a bit intimidating if you're not used to the command line:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/433943](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/433943)

This seems to be a fairly popular and sucessful fix though - I've come across it a few times. Basically it's a bit complex because you're applying a fix to a system you can't boot.

Obviously I can't vouch for this, not having used it myself!

---

### Post by RebeccaHowarth on 2010-03-06
Thanks very much.  I'm not too easily intimidated, so I'll give it a go.

---

