---
title: "WIFI is so slow with Ubuntu 20.04.2 LTS in notebook HP"
date: 2021-05-31
forum: Networking &amp; Wireless
---

### Post by ivancsir on 2021-05-31
Hi folks, wifi on my notebook is so slow, and idk how to do, i tried all but i cant fix that. My network controller: is ```
[COLOR=#242729][FONT=-apple-system]02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723DE 802.11b/g/n PCIe Adapter [10ec:d723][/FONT][/COLOR]
```

Im missing a lot of mgbs, for example in my house i have 12 MG and my notebook received 1 MG, i cant open anything. But if i connect with ethernet, the notebook recieved all Mbit/s. Pls i need help. Thx

[ATTACH]288584[/ATTACH]

Look that. From 100 mgb/s.....
[ATTACH=CONFIG]288592[/ATTACH]

---

### Post by VMC on 2021-05-31
```
nmcli d wifi
``` This should if indication of signal strength.

---

### Post by ivancsir on 2021-06-01
Hey bro, im now on a friend house. He have 20 mgb/s and im receiving only 10 mgb/s.

Tomba_3 is the wifi

```
IN-USE  BSSID              SSID           MODE   CHAN  RATE        SIGNAL  BARS>*       
        58:D9:D5:60:A3:69  Tomba_3        Infra  8     270 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;>
        68:FF:7B:7E:D1:90  Tomba          Infra  8     195 Mbit/s  49      &#9602;&#9604;__>
        60:32:B1:CA:1B:25  NAVARRO_EXT    Infra  11    130 Mbit/s  42      &#9602;&#9604;__>
        68:FF:7B:7E:D0:13  NAVARRO        Infra  11    195 Mbit/s  32      &#9602;&#9604;__>
        E0:41:36:DC:6B:EE  Speedy-DC6BEC  Infra  1     130 Mbit/s  29      &#9602;___>
        D8:0D:17:F3:7F:03  Martin         Infra  10    195 Mbit/s  29      &#9602;___>
        70:4F:57:F1:DD:0E  Galindo        Infra  2     270 Mbit/s  20      &#9602;___>
```

---

### Post by ivancsir on 2021-06-04
Someone can help me? pls

---

### Post by chili555 on 2021-06-04
It appears that you have thrown everything that is suggested in various forums at this problem. Most of them are incorrect. First:

> [/etc/modprobe.d/rtl8723de.conf]
options rtl8723de ant_sel=1

You are not using the driver rtl8723de. Let’s remove the file:

```
sudo rm /etc/modprobe.d/rtl8723de.conf
```

Next:

> [/etc/modprobe.d/rtw_8723de.conf]
options DRIVER 11n_disable=1?

This is meaningless; let’s remove it:

```
sudo rm /etc/modprobe.d/rtw_8723de.conf

```
Next:

> [/etc/modprobe.d/rtw88_8723de.conf]
options rtw88_8723de 11n_disable=1?

The driver has no such manipulable parameter; let’s remove it:

```
sudo rm etcmodprobe.d/rtw88_8723de.conf

```
Now:

> libkmod: ERROR ../libkmod/libkmod-config.c:716 conf_files_filter_out: Directories inside directories are not supported: /etc/modprobe.d/50-rtl8723de.conf

You are not using the driver rtl8723de. Let’s remove the file:
 
```
sudo rm /etc/modprobe.d/50-rtl8723de.conf

```
You have two possibly conflicting drivers installed. 

> ##### lsmod #############################

8723de               1695744  0
rtw88_8723de           16384  0

Let’s blacklist one and see if the performance improves:

```
sudo -i
echo “blacklist rtw88_8723de”  >>  /etc/modprobe.d/blacklist.conf
exit
```

Reboot and tell us if there is any improvement.

---

### Post by ivancsir on 2021-06-07
Hey bro, i tried all that you explain, the perfomance is the same.

---

### Post by chili555 on 2021-06-07
> **ivancsir said:**
> Hey bro, i tried all that you explain, the perfomance is the same.Let's change the blacklist:

```
sudo nano /etc/modprobe.d/blacklist.conf

```
Change the line:

```
blacklist rtw88_8723de
```

To read:

```
blacklist 8723de
```

Save (Ctrl+o followed by Enter) and exit (Ctrl+x followed by Enter) the text editor. Reboot and tell us if there is any improvement. If there is none, please run and post a new wireless_info as you did above. Please be certain that you do not accidently post the old original.

---

### Post by ivancsir on 2021-06-07
Thx for your time bro. The perfomance is the same. Wireless info attachment.
[ATTACH]288625[/ATTACH]

---

### Post by ivancsir on 2021-06-25
Hi, someone can help me?

---

