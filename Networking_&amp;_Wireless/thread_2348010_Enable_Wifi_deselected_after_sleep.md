---
title: "Enable Wifi deselected after sleep"
date: 2016-12-30
forum: Networking &amp; Wireless
---

### Post by WanderingOak on 2016-12-30
I have a relatively new installation of 16.04 on a HP 15 Laptop. After switching to xfce and xubuntu, my wifi goes out when my system goes to sleep. It's a relatively simple fix, selecting 'Enable wifi' from the network connection menu in the upper right corner. However, I would like to resolve this problem. I've already tried searching the forums, and came across a possible workaround [here]("https://ubuntuforums.org/showthread.php?t=1444398"), but it doesn't seem to work. I updated my /etc/default/acpi-support with SKIP_INTERFACES="wlan0", but I still lose my wifi on sleep, or when the screen is closed. 

Anybody have any ideas as to where I can look next?

---

### Post by jeremy31 on 2016-12-30
See the wireless script link in my signature and post the results.  Then put it in sleep and run ```
./wireless-info
``` before enabling wifi and post your broken results

---

### Post by WanderingOak on 2016-12-30
Here is the wireless-info.tar.gz. The forum flaked out on me for a bit.

---

### Post by WanderingOak on 2016-12-30
Here is the wireless-info.txt file generated after putting the system to sleep and running ./wireless-info with the wifi still disabled.

---

### Post by jeremy31 on 2016-12-31
Can you try Ubuntu 16.10 and see if the condition is fixed?  A bug report may need to be filed against linux to get the issue fixed correctly in 16.04

---

### Post by praseodym on 2016-12-31
Try this solution with rtl8188ee instead of ath10k_pci in that script:

[https://ubuntuforums.org/showthread.php?t=2347801&page=2&p=13588728#post13588728](https://ubuntuforums.org/showthread.php?t=2347801&page=2&p=13588728#post13588728)

---

### Post by WanderingOak on 2017-01-01
Well I upgraded to 16.10, and I still have to manually turn wifi on after sleep. I also tried praseodym's suggestion of working with /lib/systemd/system-sleep/wakeon_suspend.sh to no effect.

Any more ideas?

---

### Post by WanderingOak on 2017-01-03
Here is the latest wireless-info.tar.gz .[ATTACH]273023[/ATTACH]

---

### Post by WanderingOak on 2017-02-11
Well, one of the latest updates corrected the issue. Thanks to everybody for the help.

---

