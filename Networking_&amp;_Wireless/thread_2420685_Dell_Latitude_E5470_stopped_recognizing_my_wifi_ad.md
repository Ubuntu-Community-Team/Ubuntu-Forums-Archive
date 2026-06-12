---
title: "Dell Latitude E5470 stopped recognizing my wifi adapter."
date: 2019-06-08
forum: Networking &amp; Wireless
---

### Post by eddugo on 2019-06-08
I installed Gnome multi writer using synaptic.  Didn't like it so i removed it using synaptic and now 18.04 does not recognize my wifi adapter. Outputs are posted here:
[http://paste.ubuntu.com/p/h2nMVkfq6N/](http://paste.ubuntu.com/p/h2nMVkfq6N/)
Thank you.

Ed

---

### Post by TheFu on 2019-06-09
Can you boot from a "Try Ubuntu" media (flash storage or DVD) and see if the wifi works?  Trying to determine if the HW failed or if it is just a SW issue.

```

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

Does your Dell have a slider on the side to disable bluetooth and wifi?  It usually shows "red" when locked. Slide it to hide the red. 
Some models have a Fn+F{number} method to accomplish the same result. Toggle that - look for the little antenna on the function keys.
And perhaps the wifi was disabled in the BIOS. Check that.

I'm betting that you've already checked those 3 things, but it is worth mentioning for later lurkers to check.

---

### Post by eddugo on 2019-06-09
Good morning.  The wifi slider in settings will not go on.  I just did a live distro and wifi does not work so I am guessing my adapter is shot.  I have been using Ubuntu  for 12 years but I have never had much trouble so I don't really know that much.  I don't know what to do with the code you posted.  thank you.  Ed

---

### Post by jeremy31 on 2019-06-09
Try ```
echo "blacklist dell-laptop" | sudo tee /etc/modprobe.d/dell-laptop.conf
```
Reboot

---

### Post by eddugo on 2019-06-09
That did it.  Not only did my internal adapter come to life, but now an Alfa AWUS036H v5 long range USB adapter that i gave up on last year, also works.  Thank you for you time and expertise. I will mark this solved. Ed

---

### Post by TheFu on 2019-06-09
blacklist dell-laptop?  That fix has been around since 2012 [https://ubuntuforums.org/showthread.php?t=1957419](https://ubuntuforums.org/showthread.php?t=1957419) . First I've heard of it.  And I've had 2 Dell laptops, not latitudes, since then!  

There's no substitute for direct experience.

---

### Post by jeremy31 on 2019-06-09
I think this is a new issue and may have been fixed with [https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/platform/x86/dell-laptop.c?id=6cc13c28da5beee0f706db6450e190709700b34a](https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/platform/x86/dell-laptop.c?id=6cc13c28da5beee0f706db6450e190709700b34a) as the bug report indicates an issue with rfkill on a Latitude

---

