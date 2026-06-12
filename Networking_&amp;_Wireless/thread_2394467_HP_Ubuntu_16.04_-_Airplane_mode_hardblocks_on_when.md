---
title: "HP Ubuntu 16.04 - Airplane mode hardblocks on when laptop sleeps/closes"
date: 2018-06-16
forum: Networking &amp; Wireless
---

### Post by prykor on 2018-06-16
I have a HP Pavilion Notebook.

I recently installed Ubuntu 16.04 and have been having issues with airplane mode turning on and not being able to be reversed.

When my laptop first boots, wifi works fine and I can switch airplane mode on/off. (F12 on my machine is airplane mode instead of wifi)
However, as soon as the laptop closes/sleeps, airplane mode turns on and cannot be turned off through either F12 or the network screen.

```
sudo rfkill list all
``` returns wifi - softblocked: no, hardblocked: yes
I have tried ```
sudo rfkill unblock all
``` but it does not work.

How can I stop airplane mode turning on when the laptop sleeps? And what might be causing this?

---

