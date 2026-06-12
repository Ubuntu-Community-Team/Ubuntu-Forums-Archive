---
title: "Wubi Ubuntu 10.10 won't suspend"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by piroteknix on 2011-03-03
Hey all,

I'm a very new user of Ubuntu. I've messed around with a few distros for fun in the past, but I haven't seriously used Ubuntu until this week.

I installed Ubuntu 10.10 using Wubi on my Lenovo ThinkPad R400 with Windows XP. Suspend worked for the first few days. Then I installed the Macbuntu theme [[http://sourceforge.net/projects/macbuntu/]](http://sourceforge.net/projects/macbuntu/]) (which changes not only appearance but how a few things function as well). Since I installed the theme, suspend hasn't worked.

I've tried closing the laptop, suspending from the shut-down menu, and suspending from terminal, but all have the same result: the power light blinks, the computer *sounds* like it's suspending, and the screen goes black. But it never suspends fully. The backlight remains on, the wireless turns back on, and when the mouse is moved, it "wakes" to the password screen, as if the screen had only been locked.

Attempting to suspend via keyboard shortcut *sometimes* produces the following pop-up message:

```
Failed to suspend
Computer failed to suspend.
Failure was reported as: Cannot suspend
```

I've read up a little on this problem. According to a few four-year-old archived forum posts, Wubi had an issue with suspend/hibernate, but I don't know if it was ever solved. I also found this thread [[http://ubuntuforums.org/showthread.php?t=505890]](http://ubuntuforums.org/showthread.php?t=505890]) but it didn't really help me; admittedly, I'm a little too green to understand it .

Any and all help will be greatly appreciated! Thanks!

---

### Post by Frogs Hair on 2011-03-03
The swap partition in a Wubi installation is not large enough to support suspend or hibernate .A Wubi installation was intended to be used on a trial basis .

If you want Ubuntu at full function a traditional dual boot is the best option.

---

### Post by bcbc on 2011-03-03
Suspend should work. If it's not then there is some other issue. 

Only hibernate doesn't work on wubi - but that's just because it uses a swap file (not a partition) and hibernate doesn't work on any ubuntu install with a swap file (except [this method]("http://ubuntuforums.org/showthread.php?t=1042946")).

---

### Post by piroteknix on 2011-03-03
Yep, as I mentioned, suspend worked for a few days on Wubi.

---

### Post by bcbc on 2011-03-03
> **piroteknix said:**
> Yep, as I mentioned, suspend worked for a few days on Wubi.

Do you get any 'interesting' messages in /var/log/syslog when you try?

---

### Post by piroteknix on 2011-03-04
> **bcbc said:**
> Do you get any 'interesting' messages in /var/log/syslog when you try?

Hi bcbc,

I've never deal with /var/log/syslog before but here is the "suspend"-related message from my latest attempt.

```
Mar  4 17:27:52 ubuntu kernel: [  457.830118] PM: Entering mem sleep
Mar  4 17:27:52 ubuntu kernel: [  457.830232] Suspending console(s) (use no_console_suspend to debug)
Mar  4 17:27:52 ubuntu kernel: [  457.987658] PM: suspend of drv:psmouse dev:serio2 complete after 156.968 msecs
Mar  4 17:27:52 ubuntu kernel: [  457.990376] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Mar  4 17:27:52 ubuntu kernel: [  457.995181] sd 0:0:0:0: [sda] Stopping disk
Mar  4 17:27:52 ubuntu kernel: [  458.060056] tpm_tis 00:0a: tpm_transmit: tpm_send: error -5
Mar  4 17:27:52 ubuntu kernel: [  458.060068] legacy_suspend(): pnp_bus_suspend+0x0/0x90 returns -5
Mar  4 17:27:52 ubuntu kernel: [  458.060074] PM: Device 00:0a failed to suspend: error -5
Mar  4 17:27:52 ubuntu kernel: [  458.296403] PM: suspend of drv:sd dev:0:0:0:0 complete after 306.029 msecs
Mar  4 17:27:52 ubuntu kernel: [  458.296436] PM: suspend of drv:scsi dev:target0:0:0 complete after 305.990 msecs
Mar  4 17:27:52 ubuntu kernel: [  458.296456] PM: suspend of drv:scsi dev:host0 complete after 305.714 msecs
Mar  4 17:27:52 ubuntu kernel: [  458.296467] PM: Some devices failed to suspend
Mar  4 17:27:52 ubuntu kernel: [  458.296963] sd 0:0:0:0: [sda] Starting disk
Mar  4 17:27:52 ubuntu kernel: [  458.405725] i2400m_usb 2-3:1.0: device rebooted: reinitializing driver
Mar  4 17:27:52 ubuntu kernel: [  458.405763] i2400m_usb 2-3:1.0: Failed to issue 'Enter power save' command: -47
```

---

### Post by bcbc on 2011-03-04
No idea, but this link is from a similar computer and a similar error. [http://kubuntuforums.net/forums/index.php?topic=3115634.0;wap2]("http://kubuntuforums.net/forums/index.php?topic=3115634.0;wap2")

Might give you some ideas where to start.

---

### Post by piroteknix on 2011-03-04
What do you know? That seemed to the the trick! I'm having no issues suspending through any method now. Thank you so much bcbc!

---

