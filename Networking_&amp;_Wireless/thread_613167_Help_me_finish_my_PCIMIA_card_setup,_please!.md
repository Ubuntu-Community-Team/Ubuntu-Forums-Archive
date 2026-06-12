---
title: "Help me finish my PCIMIA card setup, please!"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by Bally on 2007-11-14
Well I am happy to be posting this via my 3com pcimia card, freshly installed using ndiswrapper, seems stable and fast and secure!.....cool

But here's my problem:

I want to load the ndiswrapper on boot, (I am using modprobe command after boot at the moment.) How do i do this?

I have seen posts refering to editing etc/modprobe.d, I have located the folder on my system but the files there do not seem relevant to the ndiswrapper module, and none seem like a generic file for module loading.

So i guess I just create a file with a relevant name ("ndiswrapper") and (please correct me here...) enter somthing like:

ndiswrapper (do i need to include a "-m" here?)

Will a simple reboot then sort the problem or do I need to instruct the system to force the effect.

If I am totally off base here please correct me, yes I am a recent windows convert hence no issues with wireless configurations, just new to linux fundamentals!

Bally

---

### Post by mnemosyne on 2007-11-14
I found a relevant reply here:
[http://ubuntuforums.org/showthread.php?t=537132]("http://ubuntuforums.org/showthread.php?t=537132")
It seems to be the right answer to your problem.:)

---

