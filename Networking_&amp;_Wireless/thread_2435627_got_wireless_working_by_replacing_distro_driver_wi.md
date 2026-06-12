---
title: "got wireless working by replacing distro driver with one from intel - how do I report"
date: 2020-01-23
forum: Networking &amp; Wireless
---

### Post by dllahr on 2020-01-23
Hello

All the details are [here]("https://askubuntu.com/questions/1195743/wifi-drops-after-12-hours-cannot-recover-except-by-reboot/"), but briefly[INDENT]
[COLOR=#242729][FONT=Arial]We have an intel NUC running ubuntu. Using the wifi, after about ~1 day the connection drops, and when I check it cannot detect any Wifi (no SSID listed) when there are many. Tried turning wifi off and on (via GUI, via command line) no luck. Only "fix" currently is to reboot the entire system. 

[/FONT][/COLOR][/INDENT]
[COLOR=#242729][FONT=Arial]Ultimately fixed by replacing the driver with one downloaded from intel. In my case I downloaded iwlwifi-9000-pu-b0-jf-b0-34.618819.0.tgz from: [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What concerns me is that a file with the exact same name was already present from the Ubuntu 18.04 distribution.  I compared that with the one I downloaded with the distro version of the file with the same name (in /lib/firmware)  and the files were different.

Should I / how do I report this as a bug / something to be investigated for the distribution?

Thanks,
Dave[/FONT][/COLOR]

---

### Post by jeremy31 on 2020-01-23
See the wireless script link in my signature and post results

---

