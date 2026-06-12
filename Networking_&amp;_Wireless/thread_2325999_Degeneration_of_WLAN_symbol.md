---
title: "Degeneration of WLAN symbol"
date: 2016-05-27
forum: Networking &amp; Wireless
---

### Post by Roland_Msl on 2016-05-27
Acer ES1-331.COYK - Ubuntu 16.0.4 LTS

When I start new, a WLAN symbol appears top right like in Android.
Clicking on the icon, there is a list of available WLANs.

But after waking up from Suspend to RAM, there is a degeneration.

Instead of the WLAN iconl, there is a arrow up and down icon.
Clicking on the icon, there is no list of WLANs.

How can I solve this without rebooting?

---

### Post by chili555 on 2016-05-27
Does the symbol reappear if you do, from the terminal:```
sudo service network-manager restart
```If so, please check here: [http://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130](http://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130)

---

### Post by Roland_Msl on 2016-05-27
Thanks.

It happens not at each wake up from Suspend.

It could be, it happens only, when the Suspend mode was invoked by the set inactivity time.

sudo service network-manager restartworked. Now I continue with Your link.

---

### Post by Roland_Msl on 2016-06-03
Great!

After it worked good on my new Acer ES1-331-C0YK, I was just at my old ASUS UL30A notebook.

This notebook was 2010 purchased with Windows 7 and had since years the same problem, no WLAN after waking up from suspend.
This problem remained under Windows unresolved.

Now I just tested this method, it works!

This advanced not to one of my favorite arguments to use Linux instead of Windows.
5 minutes to find a solution, where I never found the solution under Windows.

---

