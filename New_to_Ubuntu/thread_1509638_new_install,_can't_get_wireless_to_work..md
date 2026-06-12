---
title: "new install, can't get wireless to work."
date: 2010-06-14
forum: New to Ubuntu
---

### Post by chedderslam on 2010-06-14
I have just installed 10.04.  I am trying to use a usb Azio 802.11 b/g Model: AWU254.  I cannot connect to the internet.

I have tried both dchp and a manual config.  I cannot ping anything except 127.0.0.1 with the adapter.

I have tried to follow some of the steps here:

[http://beginlinux.com/desktop_training/ubuntu/1096-ubuntu-wireless-setup](http://beginlinux.com/desktop_training/ubuntu/1096-ubuntu-wireless-setup)

When I go to network tools and select the adapter, the ip shows as 0.0.0.0

Please help.

---

### Post by spiky001 on 2010-06-14
Hi the 1st thing you should do is update system via update manager, I wold connect a ethernet cable to do that

---

### Post by ken631 on 2010-06-14
Yeah I had that problem too with an internal wifi card on a lap, practically pulled my hair out then I rebooted the system and guess what I worked. After a couple of hours of trying and practically giving up.  I did have to do some tweaks, connected with an eth cable, downloaded some drivers. Then after rebooting it worked.

---

### Post by chedderslam on 2010-06-14
Ok, downloading now.  Didn't see any updates for the wireless adapter though.

Thank you for the help.

---

### Post by spiky001 on 2010-06-14
When updates are done if still not working go to System Administration then Hardware drivers see if it can find them

---

### Post by chedderslam on 2010-06-14
Ok, I can connect to the router but cannot bring up a page in ff or ping google.com

Settings:
static ip(192.168 etc)
DNS:
68.87.68.166
Search Domain:
(blank - what goes here, does it matter?)

---

### Post by zkriesse on 2010-06-14
Just so you know, I've found that doing the "Try the LiveCD" option will help as it's using your original system settings (Windows and such) so it is more likely to pop up and ask to install a proprietary drive for the wireless if needed. If it does install it then proceed with the Ubuntu Installation. When it's done and you've rebooted it should have the wireless working just fine. Just a thought.

---

### Post by spiky001 on 2010-06-14
is that with a wire or wireless?

---

### Post by zkriesse on 2010-06-14
Wireless....thats what happened for me though...not saying it will happen for somebody else.

---

### Post by chedderslam on 2010-06-14
I wanted a clean install and killed the exising windows partition.  Also, this computer was never set up for my wireless network.  I just got it from someone.

---

### Post by chedderslam on 2010-06-14
> **spiky001 said:**
> is that with a wire or wireless?

I'm sorry.  I could get the internet with wired.  Downloaded updates and rebooted.  Checked for hardware drivers, none found.

Removed the wired, restarted.  Could connect via wireless to router, but not the internet.

---

### Post by spiky001 on 2010-06-14
can you ping google
can you see other networks
did you put right wep/wpa key? if so can you try router without security

---

### Post by chedderslam on 2010-06-14
cannot ping google.

disabled security for wifi, connected to router and got internet.

Turned back on settings and no go.
Router:
WPA2 Personal
TKIP

Ubuntu:
Security:
WPA and WPA2 Personal

Is that correct?

---

### Post by spiky001 on 2010-06-14
ok so now we know it,s the security causing prob! did you enter correct wpa? then it asks for password for network keyring did you enter correctly

---

### Post by chedderslam on 2010-06-14
Reboot fixed it.  Confusing.  Thanks for the help.

Is there some way to reinit stuff after making changes besides rebooting?

---

### Post by lkraemer on 2010-06-14
You should be able to do:
```

sudo /etc/init.d/networking restart

```

lk

---

