---
title: "Connect to wireless network at boot, before login?"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by neocookie on 2007-01-12
We're setting up an ubuntu machine as a development box/server, and have connected it to our wireless network. However, the machine will only connect to the network once a user has logged into the system and entered their password into the keychain (to retrieve the wireless password).

This machine is going to be headless, sat in a corner somewhere, so I need to get wireless working before login so we can reboot the machine and expect to have it connect to the network once booted.

I also need to make sure that the machine keeps trying to connect to the wireless network should the connection drop.

How can I do this?

---

### Post by neocookie on 2007-01-29
Nobody able to help with this one?

---

### Post by casaschi on 2007-01-29
You might want to look at the wifi-radar package.
It can be set to start on boot as one of the /etc/init.d services and might be able to connect you before anyone logs in.

---

