---
title: "Slow to connect to home wifi - speed fine - other networks fine"
date: 2014-03-23
forum: Networking &amp; Wireless
---

### Post by mattotoole on 2014-03-23
I'm having trouble connecting to my home network.  It often takes several minutes.  Once it's connected, the speed is fine.  I have no trouble with other networks, only this one.

I'm using 12.04 LTS on a Thinkpad T400.  Router/modem is a Zoom from Time Warner.  AFAICT it's 802.11g and WPA/WPA2

I'm wondering about interference from nearby networks.  How do I check that?  (And why isn't there an included GUI tool for that?)

---

### Post by chili555 on 2014-03-23
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP.  I suggest either channel 1 or 11. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit. If these changes do not help, let's look at the driver for your device. In order to do so, please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by mattotoole on 2014-03-23
chili555,

That did work.  Thanks!

Would love to know what was wrong and why only this network gave me trouble...

BTW I'm in SC too right now.

Thanks again.

---

### Post by chili555 on 2014-03-23
It is hard to tell the exact step that worked. In my few years of experience, I have honed a few techniques and these are a few that often, not always, have a good result.

It's spring in SC! Time to start thinking about the beach.

---

