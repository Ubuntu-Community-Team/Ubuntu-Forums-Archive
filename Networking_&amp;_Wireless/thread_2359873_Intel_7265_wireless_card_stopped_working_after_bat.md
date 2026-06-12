---
title: "Intel 7265 wireless card stopped working after battery died"
date: 2017-04-29
forum: Networking &amp; Wireless
---

### Post by Jesse_Evers on 2017-04-29
Hi All,

I was working on my laptop, and forgot to plug it in, so it died. When I rebooted, the wifi was no longer working. The wireless card (an Intel AC 7265) shows up in the results of lspci -v and sudo lshw -C network, although the latter shows it as "UNCLAIMED." However, ifconfig, iwconfig, and ip link all fail to show the card. I tried enabling the proprietary driver in the Additional Drivers section of Software and Updates, but that didn't work.

Here's a link to the pastebin from the diagnostics script: [http://paste.ubuntu.com/24477263/](http://paste.ubuntu.com/24477263/)

This is a pretty serious problem for me, because I have a huge deliverable due next week that I need this laptop to work on, so any help is much appreciated.

Thanks!

---

### Post by RobGoss on 2017-04-29
Hello and welcome to the forum, after researching a bit I came across this post at Ask Ubuntu it may be what your looking for to resolve your wireless issue please see here: [https://askubuntu.com/questions/786053/wireless-7265-not-working-on-ubuntu-16-04-asus-k401u](https://askubuntu.com/questions/786053/wireless-7265-not-working-on-ubuntu-16-04-asus-k401u)

---

### Post by Jesse_Evers on 2017-04-29
Thanks! I had found that as well...unfortunately, it didn't work for me. There was no output from rfkill list when I ran it, and sudo rfkill unblock all didn't do anything as far as I could tell. The person's situation in that post is also somewhat different from mine -- when I run ifconfig -a, my card does not show up.

Also, not sure if this is relevant, but I just noticed that the screen on my laptop no longer wakes from sleep when I close the lid and then open it again.

Any other thoughts?

---

### Post by jeremy31 on 2017-04-29
What happens if you ```
sudo modprobe -v iwlwifi
```

I will bet that you see something about iwlwifi not found, if you do, reboot and press the Shift key until the Grub Menu appears, scroll down to Advanced Options, then scroll down to the first listed kernel that is not 4.4.0-75 and boot into the old kernel where everything should work then try
```
sudo apt-get install --reinstall linux-image-extra-4.4.0-75-generic
```
Hopefully that will complete without errors and then you should be able to reboot normally

---

### Post by Jesse_Evers on 2017-04-29
Awesome, that worked! Thanks! However, now my alternative WM/DE options aren't showing up when I go to sign in. Is that related to reinstalling the kernel?

---

### Post by jeremy31 on 2017-04-29
That shouldn't be affected by the kernel and all we reinstalled were some kernel modules.  I suspect you may have lost power while updates were being installed

---

