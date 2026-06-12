---
title: "hp 620 bluetooth issue"
date: 2023-01-13
forum: Networking &amp; Wireless
---

### Post by endreveh on 2023-01-13
I couldn't get bluetooth to work on my old hp 620 notebook (rt3090).
At first I tried to install the official driver. Since it is a .rpm file I tried to use Alien but it couldn't install the package, because even though the file name contains that it is for i586 alien thinks that it is for i386 matchines.
Next I have foun an old thread ([https://ubuntuforums.org/showthread.php?t=1761370](https://ubuntuforums.org/showthread.php?t=1761370)) but the old links aren't working, or the drivers what I was able to download were also for i386.
My last idea is to use the official windows drivers somehow, but it's beyond my abilities.

Does anyone have an idea what I can do to solve this problem?

---

### Post by guiverc on 2023-01-13
You mention Lubuntu, but no what release you're asking about, nor what kernel stack choice you're using (if it's a LTS release).

If you need special *drivers*, as *drivers* are just kernel modules; and all Ubuntu releases have kernel stack choices; the easiest option is to try the other *kernel stack *choice. If you're not using *closed source* kernel modules (eg. some video *drivers*), both stacks can co-exist on boxes; meaning it's not that difficult to try that.  If you don't want to install anything; using 20.04 for example; there are ISOs that contain kernels of 5.4, 5.8, 5.11, 5.13 & 5.15 meaning you have multiple kernel choices to try/test using only *live* media for that one release (ie. 20.04 LTS).

I don't know your hardware, and didn't look it up, as starting point to me is knowing what software stack you're using, and the *release details* are the first detail I like to know.

---

### Post by endreveh on 2023-01-14
The missing infos: I have installed Lubuntu 22.10.
The offical site with the drivers and hardware infos: [https://support.hp.com/hu-hu/drivers/selfservice/hp-620-notebook-pc/4158863](https://support.hp.com/hu-hu/drivers/selfservice/hp-620-notebook-pc/4158863)

---

