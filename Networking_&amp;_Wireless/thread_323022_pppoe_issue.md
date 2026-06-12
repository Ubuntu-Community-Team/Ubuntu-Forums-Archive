---
title: "pppoe issue"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by mendingo84 on 2006-12-21
hi there guys! here is my problem:
 i have an pppoe connection wich i configure using the "sudo pppoeconf" command. when asked, i choose for the connection to start at boot time but...surprise, it doesn't, so i have to go through the annoying steps of running pppoeconf each time i boot. strange fact is that i didn't have this problem till now, and i can't understand why it all worked well for a time but now it doesn't anymore.
 anyone help plz?

---

### Post by xbadger on 2007-02-12
see if u have /etc/ppp/pppoe_on_boot.sh

if not write in a file that(without quotas), save it as pppoe_on_boot.sh and then put it there
run pppoeconf. should work

"
#!/bin/sh

PATH=/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin
export PATH

modprobe -q pppoe

exec pppd call dsl-provider
"

---

### Post by rostfrei on 2007-06-13
Hello!

I have the same problem. I have Ubuntu 7.04 server edition. I configured ADSL connection without a hitch and in **pppoeconf** I checked to start PPPoE on boot. Unfortunately when I reboot the machine my ADSL does not come up. It looks like file /etc/ppp/pppoe_on_boot is not executed on boot. If I execute script manually, PPPoE comes back to life again and I can see something with **plog**

What am I doing wrong. I tried **pppoeconf** again and again, but it just doesn't work!

Best regards,
Rostfrei

---

### Post by rostfrei on 2007-06-14
Hello!

I actually found out that PPPoE daemon is started after reboot. If I check network devices with **ifconfig[B] I can see [B]ppp0** created. Its true that command **plog** does not output anything, but that's probably because log was not written if started while booting. The only problem is, that **/etc/resolv.conf** is not populated with DNS addresses that are received from ISP when ADSL connection is created. I manually edited /etc/resolv.conf file and added name servers. Now everything works ok even when machine is rebooted.

Regards,

---

