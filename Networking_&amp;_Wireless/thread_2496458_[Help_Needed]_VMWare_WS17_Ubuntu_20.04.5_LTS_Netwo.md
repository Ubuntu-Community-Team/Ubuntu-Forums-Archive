---
title: "[Help Needed] VMWare WS17 Ubuntu 20.04.5 LTS Network No Connection"
date: 2024-03-28
forum: Networking &amp; Wireless
---

### Post by denniswu28 on 2024-03-28
See [https://pastebin.ubuntu.com/p/KP8YXxptRY/](https://pastebin.ubuntu.com/p/KP8YXxptRY/) for the script result.
I used NAT option in VMWare.

Will provide anything if needed.

---

### Post by TheFu on 2024-03-29
A few guesses.  I don't use VMware stuff and the last time I saw VMware Workstation was around 2000.

Use the virtio NIC in the VM Network settings. No need to emulate a fake NIC with any Linux VM.  The real hardware has nothing at all to do with what the VM sees. Everything is emulated.

Inside the VM, don't use wireless or expect wireless to work.  The report says the wired interface is disabled and the wireless one is enabled. That won't work.

---

