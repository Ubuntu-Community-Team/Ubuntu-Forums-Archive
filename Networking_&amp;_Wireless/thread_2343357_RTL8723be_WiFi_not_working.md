---
title: "RTL8723be WiFi not working"
date: 2016-11-15
forum: Networking &amp; Wireless
---

### Post by Neal_Gosalia on 2016-11-15
Hey, I am using an HP Pavilion ab214tx laptop. I had wifi issues on Ubuntu earlier, but were solved. Months after that I decided to change my distro and I am finally back to Ubuntu, but now I am unable to fix my wifi by updating the driver. I tried the dkms instaall method and also the sudo make install method. But I guess now my wlo1 interface is not detected anymore! I would be more than happy if someone could help! And please tell me if I need to provide any more information! Thank you!

---

### Post by wildmanne39 on 2016-11-15
Please try:
```
sudo modprobe -v rtl8723be ant_sel=2
```
does it come on?

---

### Post by Neal_Gosalia on 2016-11-15
Output:
```
 
insmod /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8723be': Required key not available
```

---

### Post by wildmanne39 on 2016-11-15
That is what I expected, that means you have to turn off secure boot, go into your bios and see if you can turn it of from their if not I will find the directions for doing it another way.

---

### Post by Neal_Gosalia on 2016-11-15
Yes I can. I'll do that and be right back

---

### Post by Neal_Gosalia on 2016-11-15
Thanks a lot! WiFi is fixed now! If I may ask, what does secure boot have to do with the Wi-Fi? 
Also, is there any "Thank you" button?

---

### Post by wildmanne39 on 2016-11-15
Secure boot stops all drivers from being loaded if is it not signed in the kernel, this is new in 16.04 an above.

There is not a thank you button, please use thread tools at the top of the page to mark the thread solved.
You can not turn it back on or it will stop the driver from loading again unless you create a key for the driver but that is more difficult.
Thanks

---

### Post by Neal_Gosalia on 2016-11-15
Thank you for explaining!

---

### Post by wildmanne39 on 2016-11-15
Your welcome!
Enjoy!

---

