---
title: "Ubuntu 18.04.4 LTS, Intel Wireless 9560 not found"
date: 2020-03-17
forum: Networking &amp; Wireless
---

### Post by pabbas on 2020-03-17
I have an Asus Vivobook S13 S330FA. It showed no Wi-Fi adapter found in Settings.

This is the pastebin: [https://pastebin.com/BQ7rx6CB](https://pastebin.com/BQ7rx6CB)

I've tried to install older kernel to no avail. Rfkill showed nothing blocked as well.

dmesg | grep iwl showing failed to load firmware chunk.

Can anybody please help enlighten me.

Thanks

---

### Post by chili555 on 2020-03-21
> [    7.694909] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error
[    7.695141] iwlwifi 0000:00:14.3: Master Disable Timed Out, 100 usec
[    7.707706] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110Please check here: [https://askubuntu.com/questions/1218141/dell-vostro-5490-no-wifi-in-ubuntu-18-04](https://askubuntu.com/questions/1218141/dell-vostro-5490-no-wifi-in-ubuntu-18-04)

---

### Post by pabbas on 2020-03-26
Thanks, I haven't try the link yet because I haven't turn on this laptop for about a week. Today I just got a chance to use it again and the wirless network work fine. But alas, now the bluetooth is not working LOL. But I can live without bluetooth mouse for now.

Thanks again

---

