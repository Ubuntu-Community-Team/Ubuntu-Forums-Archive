---
title: "network problem error message"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by stmartin on 2008-01-08
Hi! I just recently installed Ubuntu 6.06 LTS on Intel Pentium system. I have broadband connection (adsl modem D-link DSL-360T). I found the Ethernet card, recognized by ubuntu in networking panel. I did
```
sudo pppoeconf
``` and configured correctly. Then I did ```
 pon dsl-provider
``` and activated my broadband connection. Then I found it slow. So I disabled IPv6 by doing ```
sudo gedit /etc/modprobe.d/aliases
``` and replacing "ipv6" with "off", then I made reboot. It was working all fine (faster than before), so I tried to open some pages, like wikipedia.org or ubuntuforums.org, but it didn't worked. It seems like it only works for google.com. I tried to Add/Remove some programs, when I pressed reload I got this message (same message, when I try to update ubuntu via update manager). I tried even to open imageshack.us to upload the screen shot, but I couldn't (so I used my digital camera and uploaded with my other windows xp operating system). Can anyone help me?

---

