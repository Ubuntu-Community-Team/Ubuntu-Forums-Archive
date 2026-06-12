---
title: "Problem loading firmware into IR dongle"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by regne v on 2008-11-01
I've upgraded ubuntu to intrepid and now I'm having a problem with a stir421x based IR dongle.

Whenever I plug the dongle I can see in dmesg messages like these (notice the "funny" characters):

```
[   11.099636] firmware: requesting 42101002.sb`{
[43504.016517] firmware: requesting 42101002.sb&#1085;&#65533;
[43504.514324] firmware: requesting 42101002.sb&#65533;&#65533;&#65533;
[44256.840563] firmware: requesting 42101002.sb&#36850;
```

and then

```
[43504.492047] STIR421X: Couldn't upload patch
```

I wrote some time ago [this [solved] post]("http://ubuntuforums.org/showthread.php?t=524631") for this dongle and it's been accurate for the last three versions of ubuntu.

Thanks for your time.

---

### Post by regne v on 2008-11-06
Bump!

---

### Post by regne v on 2008-11-11
I've tried to follow the steps since I plug the dongle till the "firmware: requesting" message because I think that the driver is passing to the firmware loader a misspelled name.

The problem is that I don't know the inners of the whole process and I've couldn't find a good guide about it so I can't track where the bug is.

Could someone, please, post a link to this?

---

### Post by regne v on 2008-12-19
I've just made a fresh install of ubuntu but the problem persists:
[FONT="Courier New"]
[   10.278118] firmware: requesting 42101002.sb&#65533;&#2017;
[/FONT]
Does anybody have a clue about this the "funny" characters at the end of the message?.

---

### Post by regne v on 2009-01-17
> **regne v said:**
> I've tried to follow the steps since I plug the dongle till the "firmware: requesting" message because I think that the driver is passing to the firmware loader a misspelled name.

The problem is that I don't know the inners of the whole process and I've couldn't find a good guide about it so I can't track where the bug is.

Could someone, please, post a link to this?

It's been [fixed in kernel]("http://bugzilla.kernel.org/show_bug.cgi?id=12397").

---

