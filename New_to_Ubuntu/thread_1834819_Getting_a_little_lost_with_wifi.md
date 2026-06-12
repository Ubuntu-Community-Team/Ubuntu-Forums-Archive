---
title: "Getting a little lost with wifi"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by johncmolyneux on 2011-08-28
Hi,

I've got Ubuntu running from a live CD, just to have a good play with it before I decide whether to move over to it from Windows or partition and dual boot - whichever.

I'm having a real problem getting to grips with wifi though.  Ubuntu doesn't recognise wifi at all - it says it's not even enabled.

I've done a lot of searching for this, but there's so much information that it's become difficult to find what I'm actually looking for.

All I want to know is how to use my USB wifi dongle with Ubuntu.  I'd be very grateful if anyone could help me.

Thanks.

---

### Post by fdrake on 2011-08-28
run and post output of:
lsusb

---

### Post by anewguy on 2011-08-28
And if you don't know how to do that:
[LIST]
[*]Open a terminal window
[*]Type:  lsusb <press enter>
[*]Highlight the output with your mouse just as you would in Windows, click the right mouse key and click on copy.
[*]Come back here and post a reply, using right-mouse click and click on Paste to put the command output here.
[/LIST]

---

### Post by johncmolyneux on 2011-08-28
Okay - I managed to get an internet connection by tethering my phone, so was able to get the info for you...

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 016: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 001 Device 005: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 001 Device 003: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by bkratz on 2011-08-28
See this bug report, there is a solution in post 5, but it may be more than you want to do.

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/770232](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/770232)

The whole post is good. I will look a bit more to see if there is an easier one.


Here it is!

[http://ubuntuforums.org/showpost.php?p=10874897&postcount=9](http://ubuntuforums.org/showpost.php?p=10874897&postcount=9)

---

### Post by johncmolyneux on 2011-08-28
> **bkratz said:**
> See this bug report, there is a solution in post 5, but it may be more than you want to do.

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/770232](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/770232)

The whole post is good. I will look a bit more to see if there is an easier one.

Thanks man - I'll look into that.

---

### Post by HereInOz on 2011-08-28
I got the feeling that the bug had actually been fixed and released to the updates.  

If I am correct (been wrong a bit lately, so can't be too sure) you may find that, because the Live CD is the original release, it won't work in that, but if you install then run all the updates (with an ethernet cable), you may well find that the Ralink RT3072 chip will be found and work OK.

---

### Post by bkratz on 2011-08-28
> **johncmolyneux said:**
> Thanks man - I'll look into that.



Look at the edit in my post

---

