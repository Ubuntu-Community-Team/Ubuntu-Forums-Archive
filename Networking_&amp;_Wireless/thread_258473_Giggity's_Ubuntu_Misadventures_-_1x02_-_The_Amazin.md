---
title: "Giggity's Ubuntu Misadventures - 1x02 - The Amazing Vanishing WiFi Interface."
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by Giggity on 2006-09-16
Yesterday, in Giggity's Ubuntu Misadventures, we learned how to correct the stubborn behavior of KDE after installing nVidia drivers.  Not being the type of person who keeps stable systems for long, I've gone and broke Ubuntu again.

This time, I installed MoBlock to hopefully prevent unwelcome connections in my P2P programs.  I rebooted and now ath0 (my wireless network interface since I installed Ubuntu) just doesn't exist, so I can't do anything on the internet.

Admittedly, this does effectively block unwelcome P2P exchanges, but at the expense of stopping any connections at all, which I don't believe was the author's intent.

I'm not entirely sure that MoBlock is responsible for this, but MoBlock is the only program I've installed since the last time Ubuntu worked perfectly.  Yesterday, however, I installed the nVidia drivers using Envy, but everything worked great in the 18 hours between that and installing MoBlock.

Any help would be most appreciated.  Does anyone know how I wrecked my OS this time? ](*,)

Find out soon on this edition of "Giggity's Ubuntu Misadventures"

---

### Post by hardyn on 2006-09-16
cant help you with your problem, but that would have to be the most well written post ever! ;)

---

### Post by Giggity on 2006-09-16
Thanks.  I must maintain my sense of humor, or I'll quickly go insane! =P~

---

### Post by Giggity on 2006-09-16
So I just tried reinstalling MadWiFi using the latest snapshot from [http://snapshots.madwifi.org/](http://snapshots.madwifi.org/) -- The instructions contained in the tarball were fairly simple to follow, and it's working fine now.

My trouble now is one of curiosity... I understand that the official nVidia drivers forced me to uninstall the restricted modules, but if that's what caused the problem, then why didn't I have any trouble immediately following the nVidia installation?  Why did 18 hours have to pass before the wireless network interface vanished?  I had rebooted enough times in the meantime, so I figure that something else must have caused the problem.

This is no longer a matter of urgency, but I'd still appreciate if someone could offer an explanation as to what might cause sudden malfunctions in wireless network interfaces, as it would help me to understand the structure of the operating system, and hopefully avoid similar problems in the future.

Thanks in advance for any input you might contribute.

---

