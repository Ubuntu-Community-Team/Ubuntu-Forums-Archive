---
title: "AC600 dongle stopped working"
date: 2021-03-24
forum: Networking &amp; Wireless
---

### Post by UncleMonty on 2021-03-24
I am running Ubuntu 20.04. 

I recently started using a sudo wifi ac600. It's worked fine for the last few weeks, then suddenly stopped working. The drivers are installed, and it works fine on a mac mini. 

sudo dkms status
rtl8821ce, v5.5.2_34066.20200325, 5.8.0-45-generic, x86_64: installed
rtl8821ce, v5.5.2_34066.20200325, 5.8.0-48-generic, x86_64: installed

---

### Post by morrownr on 2021-03-27
Uncle,

Unless I snoozed and missed something, which is possible, you are running Ubuntu 20.10. The reason I know is that the v5.8 kernel was standard on 20.10 and the v5.4 kernel was and still is standard on 20.04.

Did your problem start after that 5.8.0-48 kernel showed up?

Maybe booting to the previous kernel could give us an idea where things went wrong:

[https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](https://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version)

Also, there is a wireless info script that you can find here:

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Running it and posted the results would shine a light on some info that could help.

---

