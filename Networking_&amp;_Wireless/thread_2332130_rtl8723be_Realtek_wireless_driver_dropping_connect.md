---
title: "rtl8723be: Realtek wireless driver dropping connection on 16.04.1"
date: 2016-07-28
forum: Networking &amp; Wireless
---

### Post by hue001t on 2016-07-28
I started using the 16.04 LTS version but I am having a weak wifi problem and it stops sometimes. Is there a version I can use that should have none of those issues? I am a very basic user who knows very little so I may have follow up questions. I am thankful for any responses.

I now have 16.04.1 but the connection still drops. There is some info below that I was asked to pull from the terminal.

---

### Post by papibe on 2016-07-28
Hi hue001t. Welcome to the forum ):P

Could you open a terminal, run these commands, and paste back the results? (you can copy/paste the text with your mouse):
```
lsb_release -a

uname -a
```
Regards.

---

### Post by hue001t on 2016-07-28
i will try to log in. I am using my tablet because of the wifi issue but I will try. ty I will/post back soon.

---

### Post by hue001t on 2016-07-28
```
hue001t@hue001t-HP-Stream-Notebook-PC-13:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
```
```
hue001t@hue001t-HP-Stream-Notebook-PC-13:~$ uname -a
Linux hue001t-HP-Stream-Notebook-PC-13 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```
hue001t@hue001t-HP-Stream-Notebook-PC-13:~$ ^C
hue001t@hue001t-HP-Stream-Notebook-PC-13:~$

---

### Post by papibe on 2016-07-28
Thanks. 

There's a newer update: 16.04.1. There are several wireless fixes (read [here]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/ChangeSummary/16.04.1")).

If possible, I'd recommend using a wired connection to upgrade to the newest version. If that gives you too much trouble, you may consider reinstalling the newer version (it is available on ubuntu.com).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by hue001t on 2016-07-28
thanks for your responce. Unfourtunatly I dont have a ethernet port. I will download the new version.

---

### Post by hue001t on 2016-07-30
The update seemed to work at first. Internet is a little faster and i was using it for a bit. I turned computer on starting going online for about 5 minutes and it said no internet connection again. Restart the computer and the wifi is working again.

---

### Post by papibe on 2016-07-31
Let's see what is your wireless hardware and driver.

Could you open a terminal run this command, and post back the result? (you can copy/paste the text with your mouse):
```
lspci -nnk | grep -iA2 net
```
Regards.

---

### Post by hue001t on 2016-08-02
The problem has continued now. The internet is working quicker since the update to 16.04.1 but still will lose wifi and i will have to shut down the computer and turn back on to get it working again. Once again thanks for the help. 
lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	DeviceName: Foxconn WLAN Realtek Sanji RTL8723BE bgn 1x1 + BT 4 LE PCIe+USB NGFF 2230 M.2 WW
	Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
	Kernel driver in use: rtl8723be
	Kernel modules: rtl8723be

---

### Post by papibe on 2016-08-02
Thanks.

Since you have the latest LTS version of Ubuntu, and thus the driver, I'd recommend focusing on the performance and reliability of the driver itself.

I'm not an expert on that driver, but we have several people on the forum that might help. I'd recommend you to change the tittle of the thread to something like:

**rtl8723be: Realtek wireless driver dropping connection on 16.04.1**

Regards.

P.S.: change title: edit your post and then go advance.

---

### Post by wildmanne39 on 2016-08-02
*Thread moved to **Networking & Wireless**.*

---

