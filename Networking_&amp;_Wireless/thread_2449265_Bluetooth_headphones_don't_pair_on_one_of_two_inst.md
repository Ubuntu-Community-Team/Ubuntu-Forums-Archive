---
title: "Bluetooth headphones don't pair on one of two installs"
date: 2020-08-23
forum: Networking &amp; Wireless
---

### Post by awildthorp on 2020-08-23
I have two computers. Both are running Ubuntu 20.04, but this issue occurs on 18.04 as well. My bluetooth headphones (Beats Solo 3) connect fine to my laptop, but pairing attempts on my desktop time out. I have confirmed that this is a software issue by trying to pair from a live USB of 20.04: pairing times out on both computers. Both devices have bluetooth through `iwlwifi`, and the diver is configured the same on both devices. The laptop doesn't seem to have any kernel extensions that the desktop doesn't have (verified with `sudo lsmod | grep blue`. I must have done something at some time to configure my laptop's bluetooth controller to connect to the headphones, but it must have been some time ago and I've forgotten it. Does anyone have experience with these headphones, or perhaps know where I may be able to find configuration differences? 

Thanks in advance.

- Andrew

---

