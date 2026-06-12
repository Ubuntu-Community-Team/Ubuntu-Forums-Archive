---
title: "D-link G604-T: Ubuntu d/top hangs, so does router"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by miker999 on 2008-03-26
Hi,

(I'm quite a newbie wrt Linux/Ubuntu/Networks, so my responses to technical questions will have to be guided by: tell me what to run & I'll paste the results here!)

I've just installed Gutsy on my PC; one small disk dedicated to winXP, the larger one to Ubuntu.

In XP, the router works fine.
In Ubuntu, after an unobserved time period, but no more than an hour, the desk-top freezes and the router's LEDs go into a "I'm not working" pattern. I *think* this happens after using the package manager.

Having upgraded the firmware to the last available (& that's 2005) yesterday, the problem persists.

I've taken no action to set up this router in Ubuntu, which seemed to find & use the thing automatically during installation.

A helping hand would be much appreciated here!    :)

Regards

Michael

---

### Post by dstew on 2008-03-26
Does the router work with Ubuntu? That is, you can use it to connect to the internet and/or home network? How is your Ubuntu network adapter set up (DHCP or static? Correct subnet, DNS, gateway?)

---

### Post by miker999 on 2008-03-26
Hi, thanks for asking ... I'll answer as best I can:

Yes, the router works ok with Ubuntu for a while & then seems to lock up.
I say 'seems' because when the desktop freezes, I don't get another go at using it, have to use MagicNumbers to re-boot.

Certainly can access the Internet -- not tried to access the other PC, which is turned off mostly.
Successfully downloaded packages etc & used browser.

You won't believe how little I know -- but I think DHCP, not static -- I'm guessing all the rest is ok because it's the same configuration as I use when on WinXP & no problems then at all.

As I say, it's okay for a while, then the desktop freezes & the 'wlan' light on the router stops flickering (flickering is its normal, working state) and goes solid.
So, a guess would be that the router has received something it doesn't like ...? and that something comes from a Ubuntu session? Another thread has mentioned throttling down the speed (somewhere), maybe so as not to hit the router too hard?
The router, btw, is direct wired into the PC running Ubuntu (or XP) just as it's 'always' been.

I'm currently at home, with the system we're discussing, so if there are any diagnostics you'd like me to run, now's the time ....:)
 (it's 18:50 here, London UK -- I see you're still in Maryland daytime.)

Regards

Michael

---

### Post by dstew on 2008-03-26
Sounds like the main issue is with your Ubuntu system. I doubt it is a router problem. When Ubuntu freezes, it causes the router to go crazy.

In a case like this, you need to look at the Ubuntu system logs to see if you can find a clue as to the cause of the crashes. The system logs are in the /var/log directory. There are a whole bunch of different log files, which are just text files that store system messages. Some have different emphases, some only get messages from certain applications. [Here is more information]("https://help.ubuntu.com/community/LinuxLogFiles#head-0bd50e0180f3ae040234d8a4b37eef68e2c63ec4") on the Linux logging system that Ubuntu uses.

In your particular case, you should examine the kernel log /var/log/kern.log and the system log /var/log/syslog. Probably a good place to start would be the tail of the last system log:```
tail /var/log/syslog.0
```

---

### Post by miker999 on 2008-03-27
Hi DStew,

Thanks for the reply. I would have replied earlier, but encountered other issues ..... leading to a complete re-install.    :(

(had downloaded & installed an ATI video driver & the first boot (last night) had Ubuntu inform me it was a 'restricted' driver. I enabled it & after the requested re-boot, everything worked fine -- except for a completely blank screen. Great.)

So, this evening I'll start again ... there doesn't seem to be any reason to expect this post's original issue to disappear, so I'll check the logs you suggested & post the result here.

This time I'll keep my own log, too!

Thanks again,


Michael

---

### Post by miker999 on 2008-03-27
This is using same wireless router, in Ubuntu, after new install.
michael@michael-desktop:~$ tail /var/log/syslog.0
Mar 26 20:36:29 michael-desktop kernel: [   35.340000] eth0: no IPv6 routers present
Mar 26 20:36:35 michael-desktop gdm[5275]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Mar 26 20:36:35 michael-desktop gdm[5275]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Mar 26 20:36:35 michael-desktop gdm[5275]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
Mar 26 20:36:42 michael-desktop hcid[5218]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Mar 26 20:36:42 michael-desktop hcid[5218]: Default authorization agent (:1.19, /org/bluez/auth) registered
Mar 26 20:36:44 michael-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Mar 26 20:36:44 michael-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Mar 26 20:41:16 michael-desktop anacron[5336]: Job `cron.daily' started
Mar 26 20:41:16 michael-desktop anacron[5987]: Updated timestamp for job `cron.daily' to 2008-03-26


Any use?

Michael

---

### Post by miker999 on 2008-03-27
here's a bit of /var/log/kern.log:
Mar 27 17:34:26 michael-desktop kernel: [    0.612000] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 27 17:34:26 michael-desktop kernel: [    0.612000] pnp: PnP ACPI init
Mar 27 17:34:26 michael-desktop kernel: [    0.612000] ACPI: bus type pnp registered
Mar 27 17:34:26 michael-desktop kernel: [    0.616000] pnp: PnP ACPI: found 12 devices
Mar 27 17:34:26 michael-desktop kernel: [    0.616000] ACPI: ACPI bus type pnp unregistered
Mar 27 17:34:26 michael-desktop kernel: [    0.616000] PnPBIOS: Disabled by ACPI PNP
Mar 27 17:34:26 michael-desktop kernel: [    0.616000] PCI: Using ACPI for IRQ routing
Mar 27 17:34:26 michael-desktop kernel: [    0.616000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
.
.
.
Mar 27 17:34:26 michael-desktop kernel: [   22.288000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Mar 27 17:34:26 michael-desktop kernel: [   22.288000] apm: disabled - APM is not SMP safe.
Mar 27 17:34:27 michael-desktop kernel: [   22.488000] Failure registering capabilities with primary security module.


I didn't note anything else ....

Michael

---

### Post by dstew on 2008-03-27
Do you have the same freezing problem you had before?

---

### Post by miker999 on 2008-03-27
No, I've left the system pretty much as installed.

There are updates waiting & I haven't tried to download any specific drivers (printer, sound, ATI video).

So far, so good.

I'll download/install the notified updates now: Open Office & Gnome games
(not that I want the games, but want to avoid the nagging!)

Total is 80.8MB -- it'll be interesting to see if that traffic triggers the fault ...

Report back later

Michael

---

### Post by miker999 on 2008-03-27
Ok, that worked & connection & desk-top remain working.

Going to search out a Canon ip4500 driver next ... install that & see.

Unless you have any other suggestions?

Michael

---

### Post by miker999 on 2008-03-27
Printer driver installed ok, re-booted & can print now -- which is nice.

Not so bothered about no 3D, so I guess getting 'sound' working is next up ... that would also be nice. :)

Michael

---

### Post by dstew on 2008-03-27
Sounds like you're doing great. I don't know much about sound issues, so if you have some, maybe start a new thread. Good luck.

---

### Post by miker999 on 2008-03-28
Just locked up again. Only things open were 'terminal' & Firefox.
Hadn't run a thing otherwise than 'more' & dmesg to look at logs.

I do recall it was Firefox that was running in one of the earlier incidents, too.
(version 2.0.0.13)
I've checked the logs since re-booting & see no messages at about lock-up time.

Maybe I'll check out another browser: Opera, I'm thinking.

Michael

---

### Post by miker999 on 2008-03-28
Googled '+firefox +hangs in +ubuntu' and guess what? 94,000 hits.  :)

[http://ubuntuforums.org/showthread.php?t=580491&highlight=firefox+hang+gutsy+flash](http://ubuntuforums.org/showthread.php?t=580491&highlight=firefox+hang+gutsy+flash)

Seems to be a firefox + flash issue.

I'll stick with Opera for now -- Ubuntu: too many issues already:
'Sound' looks like it will be a disappointing journey, too, judging by the number of posts on its being silent!

However, I'll try to keep in mind the elephant in the room -- MicroSoft :rolleyes: is the alternative!

Regards

Michael    .........    :-#

---

