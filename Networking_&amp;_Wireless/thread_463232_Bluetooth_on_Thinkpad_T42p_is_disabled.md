---
title: "Bluetooth on Thinkpad T42p is disabled"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by tsantos on 2007-06-03
I've been looking on the forums for a while now and I keep finding people how have their bluetooth turned on and can't find devices.  I'm one step behind.  I can't get my bluetooth in my thinkpad to turn on.  I'm running Feisty.  When I run Windows blutooth works fine.

I've done apt-get installs for all of the related bluetooth packages found on everyone elses' trouble reports.

When I run the following, it says that it's disabled:

```

cat /proc/acpi/ibm/bluetooth
status:         disabled
commands:       enable, disable

```

How can I get it enabled?  I see that it says that it accepts "commands" but I'm not sure how to send commands to it.

-Tom-

---

### Post by miscreanity on 2007-06-30
This is relatively simple. In a terminal session, type:

sudo su
echo "enable" > /proc/acpi/ibm/bluetooth
exit

The bluetooth LED should light up.

---

