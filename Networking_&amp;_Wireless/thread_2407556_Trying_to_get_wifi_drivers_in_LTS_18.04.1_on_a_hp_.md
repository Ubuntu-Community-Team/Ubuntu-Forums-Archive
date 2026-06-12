---
title: "Trying to get wifi drivers in LTS 18.04.1 on a hp 14-ck0100ng"
date: 2018-12-05
forum: Networking &amp; Wireless
---

### Post by germbumafu on 2018-12-05
Hi! I am completely new to Ubuntu and Linux in general, and am sadly not that tech savvy. I recently decided to purchase the laptop named in the title (hp 14-ck0100ng) for use in college. So far, I am loving Ubuntu Budgie, but cannot get the wifi to work, even after updating everything using a LAN connection and supposedly having up-to-date drivers (and turning off secure booting as suggested in another thread when rebooting).

After a lot of time researching I found [this thread]("https://ubuntuforums.org/showthread.php?t=370108") and was able to generate [this]("http://paste.ubuntu.com/p/ky4g7qnNQ6/"). It looks like I have one of the problematic (according to a linux wiki I could find) Realtek drivers, the r8169, but what do I do with this knowledge? I´m stuck at this step and do not know how to go on. :confused:

I´m honestly afraid at this point that the device I wanted as a netbook and office device will now only perform as the latter, which worries me greatly. Any and all help would be appreciated, thank you!

---

### Post by howefield on 2018-12-05
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by chili555 on 2018-12-05
Here is your wireless device:> Realtek Semiconductor Co., Ltd. Device [10ec:d723]
	Subsystem: Hewlett-Packard Company Device [103c:8319]And here is the solution: [https://askubuntu.com/questions/983251/realtek-semiconductor-rtl8723de-device-d723-issue](https://askubuntu.com/questions/983251/realtek-semiconductor-rtl8723de-device-d723-issue)

Post back if you get stuck or need further guidance.

---

### Post by germbumafu on 2018-12-06
This worked for me, thank you!

---

### Post by chili555 on 2018-12-08
Please use thread tools at the top to mark Solved. The forum is on a bit of a roll here!

---

