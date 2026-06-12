---
title: "problem installing 8.04 (video graphics)"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by patchido on 2009-05-05
i have a dell XPS m1530, and a day ago a had installed 8.04 with an original cd, and everything was ok, i didnt have wireless and my touchpad wasnt working, it works but not properly at all, it moves really random the cursor, so i did updates via ethernet cable and manage to make the wireless card work through the harware drivers under administration, but there was also NVIDIA accelerator graphics not enabled, and when i enabled it, and rebotted OS it went kind of blank allthough i could hear logging into ubuntu, so now i reinstalled ubuntu, and did everything exept the graphics enable, what should i do???


thx btw

---

### Post by Didius Falco on 2009-05-05
Hi,

Open a Terminal shell and type ```
lspci | grep VGA
``` That's a "pipe" after spci, it's the upper-case part of the \ key on most keyboards.

Then post the output here. That command, BTW, tells you what graphics card you have. If you know *for sure* what it is, you can just post that.

---

### Post by patchido on 2009-05-05
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
trivi@trivi-laptop:~$

---

### Post by Didius Falco on 2009-05-05
Stand by - I use ATI, so I'm digging around trying to find out if that card can use the proprietary drivers under 9.04...

---

### Post by lavinog on 2009-05-05
I don't use nvidia either, but why not try the latest version of ubuntu (9.04). It might fix these issues.

---

### Post by Didius Falco on 2009-05-05
This thread may be useful to you.

[http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185](http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185)

And here is a Wiki page by Dell - I'd go with that thread first though...

[http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)

I hope this helps you out - sorry I couldn't be more help myself, but it's better to get advice from other Dell users.

Regards,

Didius

---

### Post by patchido on 2009-05-05
i try to enable them through the properties, the option none is selected, and when i select extra or normal it says, visual effects could not be enabled

any suggestions_

---

### Post by Catboy~ on 2009-05-05
I actually had this problem the other day...But I can't remember what I did to fix it :O

Have you made sure you're using the most up-to-date driver for your video card?

---

### Post by Didius Falco on 2009-05-05
> **patchido said:**
> i try to enable them through the properties, the option none is selected, and when i select extra or normal it says, visual effects could not be enabled

any suggestions_

Type this in a Terminal and post the results here:

```
lspci | grep VGA

```

---

### Post by overdrank on 2009-05-05
Threads merged

---

