---
title: "WiFi Hardware Malfunction"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by J0ris on 2008-03-16
Hi,

I've got an Acer TravelMate 4500 with Gutsy installed. Problem is that the Wifi no longer works. The Acer is one of those models that has a radio on/off switch in front. This has always worked flawlessly over the last year and a half until it just stopped. In between working and not working nothing in the configuration was changed. No new software installed, none removed. iwconfig presented me with a radio off for eth1 message. I finally decided this was a hardware problem and sent it to Acer. They couldn't detect anything wrong with it and sent it back. I turned it on and, despite the fact they claimed they hadn't done anything, wireless and the radio on/off button worked flawlessly again! Until two days later. Same problem: wireless does not work, iwconfig again presents me with the radio off bit and the switch in front is completely unresponsive. This was a couple of days ago and nothing has changed.
Now, my question is whether there is ANY chance this is a software problem and, if so, what can I do about it?

---

### Post by jeffus_il on 2008-03-16
Want to try enabling/disabling the wireless on/off button?
Try this thread:
[http://ubuntuforums.org/showthread.php?t=570953](http://ubuntuforums.org/showthread.php?t=570953)
I would try to disable the switch and enable radio and see if it works first.

---

### Post by J0ris on 2008-03-16
Will try as soon as I get back. Thanks!

---

### Post by J0ris on 2008-03-16
Well, I tried the following:
```
sudo echo 0 > /sys/bus/pci/drivers/ipw2200/x/rf_kill
```
Result: Permission Denied
My conclusion: rf_kill works on a 'hardware level'. See [http://forums.fedoraforum.org/archive/index.php/t-29269.html](http://forums.fedoraforum.org/archive/index.php/t-29269.html)

And apparently, the only way to get this going again is by running windows. I had cd bootable version from windows lying around so I put it in, run windows from the cd. Then simply restarted the system into gutsy again et voila! Wireless came on automatically!

This does explain why it worked again when it came back from Acer although they claimed they didn't repair anything. They run a plugged in Windows system to run diagnostics. However, I don't see how it explains that this hardware button for radio on/off all of a sudden stopped working if it isn't defective. Any ideas on this?

Thanks

---

### Post by PeteZA on 2008-03-30
Hi there, I am sitting with exactly the same problem, same laptop. Unfortunately I can't boot into windows so I am sitting with a bit of a problem... Anybody have any other ideas as to how else I can fix it?

---

