---
title: "Broadcom BCM4321 [14e4:4328] (rev 03) - Wireless not working on Xubuntu 18.04.3 LTS"
date: 2019-09-03
forum: Networking &amp; Wireless
---

### Post by te0k on 2019-09-03
[ATTACH]283926[/ATTACH]

Hi there, 

I'm running Xubuntu 18 on my old iMac. Before fully updating the system, my wireless connection was a bit slow, but worked. Since the full upgrade it no longer works. I've been testing quite a lot of solutions that I found around the internet, but none of them seem to have worked at all.

```

04:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Apple Inc. AirPort Extreme [106b:0088]

```

I've run the wireless info script, you can find its output attached on a tar.gz on this thread or on pastebin:

[https://pastebin.com/iWSjkJ5J](https://pastebin.com/iWSjkJ5J)

Thanks a lot in advance,

---

### Post by te0k on 2019-09-08
I thought it was a better idea to start from scratch than to mention the countless things I've tried. Is there any information I should provide besides the one I already provided?

---

### Post by mörgæs on 2019-09-08
Have you tried the method described [here]("https://ubuntuforums.org/showthread.php?t=2214110")?

---

### Post by te0k on 2019-09-08
> **mörgæs said:**
> Have you tried the method described [here]("https://ubuntuforums.org/showthread.php?t=2214110")?

My exact device ([14e4:4328] (rev 03)) isn't on the list, but yes, I have tried to install both bcmwl-kernel-source and firmware-b43-installer. Having only one of them installed at the time.

Special cases seem to be talking about really old distros, was hoping for someone with Ubuntu 18 and the same driver to show up. 

Perhaps I'll have to reinstall on an old distro after all.

Thanks!

---

### Post by jeremy31 on 2019-09-08
You should look at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)

---

### Post by te0k on 2019-09-11
Finally!!! 

Thank you so much!

The regulatory domain was already changed from a previous post that I saw.

So it must've been disabling power saving in Network Manager, set IPv6 to Ignore in Network Manager or the Router Wifi settings. I have a feeling it was the last option.

I'll set the topic as solved.

Thanks again!

---

