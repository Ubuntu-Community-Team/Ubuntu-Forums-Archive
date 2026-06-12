---
title: "wi-fi is disabled by hardware switch Ubuntu 15.10 (HP Elitebook 2530p)"
date: 2016-04-12
forum: Networking &amp; Wireless
---

### Post by iwan0000iwanov on 2016-04-12
Please, help! 

Checked every thread on wi-fi hard switch. Tried everything - nothing works. :(

Attached is the wireless-info.txt file. 

Looking forward to any help. 

Thanks in advance!

---

### Post by jeremy31 on 2016-04-12
Does the button for wifi to the right of the power switch work?  You could try it during boot if it doesn't work when Ubuntu is loaded

---

### Post by iwan0000iwanov on 2016-04-12
Hello, Jeremy31!

You mean the little button which looks like the letter "i" in a circle? Yes, it lights up at boot, like all other buttons.

---

### Post by jeremy31 on 2016-04-12
> **iwan0000iwanov said:**
> Hello, Jeremy31!

You mean the little button which looks like the letter "i" in a circle? Yes, it lights up at boot, like all other buttons.

Push it and see if it toggles the hard block

---

### Post by iwan0000iwanov on 2016-04-12
No, it doesn't :(. I tried already. I am sure it is the problem of the driver.

---

### Post by jeremy31 on 2016-04-12
Have you tried right away when booting before Grub or Ubuntu has loaded?

I would file a bug report about the wifi button not being able to toggle the hard block, start [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I will have one to report once 16.04 is released as the 4.4 kernel disables the wifi button on my Toshiba and I already know what caused it

---

