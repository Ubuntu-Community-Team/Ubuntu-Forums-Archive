---
title: "Asus U32U wifi disable,"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by richard56 on 2014-05-28
Hi, i just updated to ubuntu 14.04 from 12.04 but my wifi is not working any more, I tried rfkill unblock all/1 but nothing seem to work, I’ve spent hour researching the issue online but nothing seems to work, is there any one that can help me or guide me in the right direction? or anyone experiencing a similar issue??
thanks in advanced, any help will be much appreciated.

```
richard@richard-U32U:~$ rfkill list
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

### Post by chili555 on 2014-05-30
Please open a terminal and run:```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```Reboot and let us hear your report.

---

### Post by Pio_Stu on 2014-08-06
After a lost afternoon trying and looking for a solution your tip has done it for me on my ASUS U32U.
Thank you very much and thank you very much another thousand times.
Also thanks for Ubuntu and many thanks to all involved in the forum and the Ubuntu comunity.

---

