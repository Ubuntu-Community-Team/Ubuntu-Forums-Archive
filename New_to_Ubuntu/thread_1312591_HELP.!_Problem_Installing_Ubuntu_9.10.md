---
title: "HELP.! Problem Installing Ubuntu 9.10"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by nicofaller on 2009-11-03
**the ubiquity failed and crashed on desktop while I was trying to Install Ubuntu 9.10.? I took a screenshot of the notification. Please help!**

---

### Post by kellemes on 2009-11-03
> **nicofaller said:**
> **the ubiquity failed and crashed on desktop while I was trying to Install Ubuntu 9.10.? I took a screenshot of the notification. Please help!**

Have you restarted the install-procedure?

---

### Post by nicofaller on 2009-11-03
Yes I have retried 10 times.. I would always get stuck @ 5% upon installation and then crash to desktop and then get the 2 notifications that I attached...

---

### Post by kellemes on 2009-11-03
I know it sucks but reading some threads it seems this issue can be bypassed by using the liveCD to partition your system with GParted and let the installer simply mount those partitions.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/460121]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/460121")

---

### Post by nicofaller on 2009-11-03
KelLeMes: What do I do w/ GParted.? In GParted, I can see my 320Gb HD and my 8Gb FlashDrive. I want to install a persistent Ubuntu on my 320Gb. or is it better to install it on my 8Gb and use the 320Gb as a regular External HD to save big files like movies and stuff..? 

What do you think..?

---

### Post by kellemes on 2009-11-03
Personal preference I guess..

Just an example..

1 swap-partition twice as big as your amount of ram with a max of 2Gb (my rule of thumb)
25Gb (mounted at /) .. plenty of room to experiment.
35Gb (mounted at /home)

If you wish you can create one big partition of what's left and have it mount at /mnt/data (just made this up myself, you can name it /mnt/mydisk or whatever you want)

You can have these partitions formatted ext4. A swap-partition you won't be able to format, it has it's own file-system.
Unless you need the "data-partition" to be shared across other os's you can format it ext4 also..

[COLOR="Red"]**EDIT**:
Have you tried installing without your flashdrive inserted?
I remember the ubiquity-issue your having has to do with specific flashdrives insterted during installtime.
I'd give it a shot.[/COLOR]

---

### Post by nicofaller on 2009-11-03
KELLEMES: I want to install a Persistent UBUNTU on my 320Gb External HD, coz my INTERNAL Hard Drive is busted and is irreparable. 

How do I do that.? is there any step by step process..? I now have Karmic Koala 9.10.

---

