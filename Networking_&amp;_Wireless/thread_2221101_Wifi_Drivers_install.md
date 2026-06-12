---
title: "Wifi Drivers install"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by Hamdaan_Hassan on 2014-04-30
How to install wifi dongle drivers ubuntu14.04 ?

---

### Post by papibe on 2014-04-30
Hi Hamdaan_Hassan.

Wifi drivers are preinstalled for most wireless chipsets like atheros, Intel, etc.

I'd recommend just plug in your dongle and see what happens. There are some dongles that may require updrading or even downloading the latest driver.

If it doesn't work. Please open a terminal, and paste this command in the terminal:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

Regards.

---

