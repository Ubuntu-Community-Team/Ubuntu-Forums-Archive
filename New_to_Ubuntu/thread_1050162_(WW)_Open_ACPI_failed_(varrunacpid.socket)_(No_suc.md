---
title: "(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by pluckypigeon on 2009-01-25
It may be petty but I'm just fine tuning my xorg.conf and I was wondering if there is a way I can stop it looking for the acpid daemon.

Thanks in advance.

---

### Post by BrianB2 on 2010-05-03
This has happened with all subsequent releases, up to and including lucid. It also seems to occur on other distributions. Most people eventually shrug and ignore the warning.

It seems there is a race condition between acpid and Xorg as they are starting. Xorg tries to connect to the socket before acpid has created it.

It also seems as if later versions of Xorg poll for the missing socket and connect within a few seconds, but do not post a message to say the connection has been successful.

If acpid is running (it should have started automatically), then Xorg will have silently connected to the socket and you can safely ignore the warning.

---

### Post by afrodeity on 2010-05-25
Most of my errors seem to be about the race which happens after the much vaunted plymouth boot. Definitely calls for a rethink about the underlying architecture, or an application which will pipe everthing correctly in the absence of a duel core processor. Am I right in assuming you also got a single core?

---

### Post by virtualnite on 2010-06-05
I am also seeing this warning with Intel Core 2 Duo in Lucid x64

---

### Post by afrodeity on 2010-11-28
Getting an "Open ACPI failed (/var/run/acpid.socket) (No such file or directory" message every boot is quite annoying. Any way to fix this?

---

### Post by mascip on 2013-01-16
More than 2 years later, but it might help others get rid of the warning.

As indicated here: [https://bbs.archlinux.org/viewtopic.php?id=64039](https://bbs.archlinux.org/viewtopic.php?id=64039)

I installed these packages:
sudo apt-get install acpi acpid hal
And i created a /etc/rc.conf file, with this inside:
DAEMONS=(hal acpid)

And the warning is gone.

---

