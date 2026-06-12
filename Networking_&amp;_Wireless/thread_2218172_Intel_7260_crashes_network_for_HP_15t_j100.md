---
title: "Intel 7260 crashes network for HP 15t j100"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by manxon10 on 2014-04-19
Hi all,

Recently I installed Ubuntu for my new laptop, everything went fine up to the point where I started to work using the wireless interface, everyone in the network started to complain about connectivity issues. Thing is that when I connect to the net, about 5mins after a sustained ping to google ramdonly fails for everyone and if I disable networking the ping works fine. I have read some post regading this, my wireless interface is  Intel Corporation Wireless 7260 using iwlwifi in rev 73, I run the update and upgrade commands as suggested but no luck with the issue. I also replace the driver file using the instructions here [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi) to make sure I have the latest one. Please check the attached wireless info.

What commands can I run to determine what is going on? I reviewed the syslog but nothing help full there. Can you please give me some advise?

Thank you

Julian

---

### Post by varunendra on 2014-04-20
Observation #1 - Your router/access-point is using 'TKIP' with WPA2 - which is a non-standard combination which shouldn't be allowed in the first place. Please change the encryption algorithm to AES (CCMP), leaving the encryption type to WPA2. TKIP is required by WPA(1) and should be avoided due to being an inefficient algorithm.

Please try that and post back the result.

And by the way, the script report is incomplete. From where it is broken indicates that you probably ran it with 'sh'. Please run it without 'sh' (e.g. **./wireless_script**) or with 'bash' (e.g. **bash wireless_script**). Some of its commands are not compatible with 'sh'.

**PS:**
For reference to a newer (tested many times now) firmware : [http://ubuntuforums.org/showpost.php?p=12924319](http://ubuntuforums.org/showpost.php?p=12924319)

---

### Post by praseodym on 2014-04-20
Install the latest firmware for this card:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.127_all.deb)

and reboot.

---

