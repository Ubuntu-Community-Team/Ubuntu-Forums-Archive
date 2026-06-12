---
title: "ndiswrapper - Wireless dropping out"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by Bonez56 on 2008-06-15
Hi All,

I am running Hardy AMD64 and using a TP-LINK USB wireless adapter.

By default, the wireless works and uses the rt73usb module to work, however I was experiencing random dropouts and limited speed problems, so I migrated over to using ndiswrapper and a windows driver.

I have a Billion ADSL router with built in wireless. Even now that i'm using ndiswrapper, the wireless connection still drops out. I am lucky to get 2 hours before a reboot is required to restore my connection.

I used to use WPA, but have since disabled all wireless security, hidden my SSID and started using MAC filtering.

I still seem to have all of these problems where by I have to reboot anywhere between 1 and 4 hours to get the wireless to start working again.

Am I doing something wrong, or can anyone suggest what I should do to try and get it to work?

Ubuntu is absolutely awesome apart from this problem, and there's no way in hell that i'm going back to Windows. I just need to sort out this issue so I can enjoy the experience!

Thanks
Bonez56

---

### Post by Bonez56 on 2008-06-21
Hi

Anyone? This is really starting to become annoying :mad:

---

### Post by munitor on 2008-06-21
I've got the same problem. Have tried to manage the connection with a couple of tactics, but they all fail after a few hours, requiring a manual restart. Very frustrating. The router is not what is dropping as I have set the certificate to never expire.

---

### Post by Dizzle7677 on 2008-06-21
:thoughts on the problem:

- Use a different windows driver ~ check for seg faults errors with dmesg.
- Check the dhcp lease time in the router settings.
- bring the interface down/up manually ~ do a dhcp client/renew for the interface after it bombs out.
-bad/weak signal.

see what sticks.

---

