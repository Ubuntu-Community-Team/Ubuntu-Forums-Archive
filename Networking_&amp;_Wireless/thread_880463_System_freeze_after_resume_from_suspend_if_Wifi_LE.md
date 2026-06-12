---
title: "System freeze after resume from suspend if Wifi LED on Intel 4965AGN card enabled"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by lamborghiniwang on 2008-08-05
I having been running Ubuntu Hardy 64bit on my Thinkpad T61p since it came out in April and most things seems to run fine except the wireless LED does not working.
I found two solutions on [**_ThinkWiki_**]("http://thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61#Wireless_activity_LED"). One of them is to install the linux-backport-module, and the other one is to compile the up-to-date compact-wireless driver. However, I found that although both of these solutions does solve the LED problem, they both make the network unstable after the system resume from suspend for a few times (exactly twice if I compile the compact-wireless driver). So I did some test on my machine and I found that if I run:
```

sudo modprobe -r iwl4965; sleep 5; sudo modprobe iwl4965; sleep 60

```
for a few consecutive times, the system would freeze while the networkmanager is trying to connect to the Wifi AP and I have to manually switch off the wifi button in the front size of my laptop to make the system start to respond again, but if I switch on the wifi button on again without a reboot, the same symptom would show up again.

I dig into the dmesg log file, and it turns out, for some reason, after I remove/reload the iwl4965 a few times, the removing process would fail to disable the 4965AGN card, i.e. the following message
```

Aug  3 06:34:50 Bumble kernel: [14683.297461] ACPI: PCI interrupt for device 0000:00:1d.0 disabled

```
wouldn't show up when I remove the iwl4965 module if it has already been remove/reload a few times (exactly twice for the up-to-date compact-wireless driver, 3-5 times if I use the linux-backport-module). I suspect that when the iwl4965 module is loaded again (for example after the machine resume from suspend), it would re-enable the already enabled wireless card and causes the problem.

This problem doesn't show up if I do not install neither the linux-backport-module nor the self-compiled compact-wireless driver. However, in that case, the wifi LED is off permanently.

I am running the default 2.6.24-19 kernel.
Any suggestions?

---

### Post by lamborghiniwang on 2008-08-08
huh..., am I the only one who gets this problem?

---

