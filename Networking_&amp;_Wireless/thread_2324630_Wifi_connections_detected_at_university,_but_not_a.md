---
title: "Wifi connections detected at university, but not at home?"
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by Viral_Mistry on 2016-05-15
I have upgraded to 16.04 and had some problems with laptop suspending, so I updated my kernel to 4.4.8. Everything else fixed, the wifi was disconnecting so I decided to update my wifi drivers. I downloaded the latest iwlwifi 3160 and stuck it in /lib/firmware.

Now, what's strange is that when I'm on the log-in screen, the wifi connections are listed but as soon as I log in they all disappear. Somehow, when I'm at university I can connect to pretty much any of the connections around me. So what is going on?

My dmesg looks like

> 
$ dmesg | grep iwlwifi

[   10.770214] iwlwifi 0000:07:00.0: enabling device (0000 -> 0002)
[   10.770689] iwlwifi 0000:07:00.0: Unsupported splx structure
[   11.378649] iwlwifi 0000:07:00.0: Driver unable to support your firmware API. Driver supports v17, firmware is v12.
[   11.591790] iwlwifi 0000:07:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[   12.122274] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[   12.122358] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   12.122602] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   12.981485] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[   29.957827] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   29.958073] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   30.065823] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   30.066076] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled


I tried attaching the wireless-info file that the sticky suggested but it won't seem to let me. If you need it please say. Otherwise, any help is appreciated.

---

### Post by jeremy31 on 2016-05-15
If you still have the wireless-info.txt file, you can copy the contents and use paste.ubuntu.com and then just post the URL

---

### Post by Viral_Mistry on 2016-05-15
Here it is fam

[http://paste.ubuntu.com/16445237/](http://paste.ubuntu.com/16445237/)

---

### Post by jeremy31 on 2016-05-15
You might have to run the script again at home and post new results.  It may be caused by a network manager bug in 16.04 so your issues at home might be fixed with ```
systemctl restart NetworkManager.service
```

---

### Post by Viral_Mistry on 2016-05-15
> **jeremy31 said:**
> You might have to run the script again at home and post new results.  It may be caused by a network manager bug in 16.04 so your issues at home might be fixed with ```
systemctl restart NetworkManager.service
```

I've tried this but it doesn't seem to do anything. I wasn't aware of this network manager bug though, going to have a look into it.

---

### Post by Viral_Mistry on 2016-05-16
Just an update, I've managed to connect to my home wifi through nmtui. In place of the wifi icon in the menu bar there's an up/down icon, and if I click on it, it doesn't display any connections despite the fact I am connected to one as I type.

I've also noticed that if I go into a guest session, the wifi list does appear and I can see my usual connection, but clicking on it won't connect me. Again, using nmtui gets me through. But the issue seems to be that when I'm on my account, the connections are not displayed at all. What could be the reasons for this?

---

