---
title: "HP 15 series laptop no Wi-Fi"
date: 2020-01-11
forum: Networking &amp; Wireless
---

### Post by saiyuki on 2020-01-11
Hi guys. After a long period offline I decided to get a laptop, an HP 15-1000na. Unknown to me I find there are no Linux drivers for the built-in RTL 8821CE network hardware this laptop has. It's not something I was conscience of looking out for when deciding on the laptop, I assumed all the hardware for the laptop would be available in linux. So. As no Linux distro out of the box supports the RTL8821CE and rather than go through the process of making 3rd party drivers, would it be possible just to use a USB Wi-Fi Dongle that has Linux support.

I assume that just by attaching the Dongle prior to Linux installation, the Dongle would show up automatically, and for this to work without any issues, which Dongle could be recommended.

Regards

---

### Post by jeremy31 on 2020-01-11
If Secure Boot is disabled, download and install [https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/rtl8821ce/+files/rtl8821ce-dkms_5.2.5.2.1.30816.20190425-0ubuntu1_all.deb](https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/rtl8821ce/+files/rtl8821ce-dkms_5.2.5.2.1.30816.20190425-0ubuntu1_all.deb)

---

### Post by saiyuki on 2020-01-11
Hi. Thank you very much jeremy31. Install was flawless.

Regards

---

### Post by dan3712 on 2020-01-26
I've been trying to get this WiFi card working for a while now, and this did the trick.  Thank you!

-Dan

---

