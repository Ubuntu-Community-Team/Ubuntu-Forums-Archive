---
title: "Wireless driver disables mobile broadband."
date: 2014-06-25
forum: Networking &amp; Wireless
---

### Post by pitoleusz on 2014-06-25
Hi. I have an Asus x550c laptop, Kubuntu 14.04 with Atheros wifi card, module  ath9k, which demands to aplly such workaround: echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf, to work. But when I've done it my USB dongle Huawei e3131 stopped working, it's not visible in  system  using console nor by KDE's device manager not mentioning that there's no internet available.  But  usb modem worked without any problems before I've made changes which allowed me to use my wifi. So now, I can use only mobile broadband, but wifi unavailable or in opposite using only wifi, after applaying "patch" but then without mobile net, not even Huawei's dongle  as pendrive. My dream is to be able to work with both and disabling/enabling them only through KDE's network managment not by wrting/deleting proper file for wifi and restarting PC each time I want to change my net provider.  Maybe you know how to fix it?

---

### Post by varunendra on 2014-06-26
Welcome to the forums pitoleusz!

I don't think that workaround (wapf=1) should interfere with USB devices, but let's take a close look at it.

Open a terminal (Ctrl-Alt-T) > plug in the USB modem > wait for about 30 seconds > run the following commands in the terminal -
```
lsusb
dmesg | tail -40
route -n
nm-tool
```

Do this with both situations (with and without the "wapf=1" workaround), and post back the command outputs from both situations. Mention clearly in your post which set of outputs is from which situation.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

**PS:**
In the meanwhile, you may also try "wapf=4" instead of value "1", although I doubt it is going to make any difference.

---

### Post by pitoleusz on 2014-06-26
It's odd and very confusing. While working on my laptop that problem occured for a few days and today everything works as it should. Really feel stupid now but nevertheless I made as you suggested and if, I hope not, the problem return I will post the results. Thank you.

---

