---
title: "Wicd takes a long time to autoconnect"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by flaggh on 2008-05-21
I'm running Hardy64 and have an Atheros AR5418 installed using madwifi.  Since I started using Wicd I'm having much more success connecting to my network, but the problem is it takes a really long time to autoconnect when I initially turn on my computer or resume it from sleep.  If I open the Wicd gui I can see that its not even trying to connect right away.  Instead I have to click Connect if I'm in a hurry to surf the net.

I see that there is a 80-wicd-connect script in /etc/acpi/resume.d and I tried adding sleep 5 to the beginning of it thinking that maybe madwifi needed an extra couple of seconds to load before wicd could autoconnect but that did not seem to help.  I also see that there is a 99-madwivi-bgscan script so should I change the wicd script to 99 too?

```
harlan@harlan-macbook:~$ cat /etc/acpi/resume.d/80-wicd-connect.sh
#!/bin/sh
# Bring wifi network interface back up.

sleep 5
/opt/wicd/autoconnect.py

```
```

harlan@harlan-macbook:~$ cat /etc/acpi/resume.d/99-madwifi-bgscan.sh 
#!/bin/sh
/sbin/iwpriv ath0 bgscan 0

```

Any ideas?

---

