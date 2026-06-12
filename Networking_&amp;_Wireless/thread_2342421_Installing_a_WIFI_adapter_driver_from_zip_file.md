---
title: "Installing a WIFI adapter driver from zip file"
date: 2016-11-06
forum: Networking &amp; Wireless
---

### Post by angel mike on 2016-11-06
How do I install an ASUS Wifi Adapter Driver which I have downloaded as a  Zip file?

---

### Post by chili555 on 2016-11-06
You probably don't. I suspect that, as we've seen in many cases previously, the driver file Asus provides is old; older, in fact, than the driver included in Ubuntu by default or otherwise available.

Let's start by hearing more about your device. If it is a USB, open a terminal Ctrl+Alt+t and run and post:```
lsusb
```If it is PCI, then:```
lspci -nnk | grep 0280 -A2
```

---

### Post by wildmanne39 on 2016-11-06
Hi, please click on the wireless script in my signature and follow the directions for running the script with the adapter plugged in and posting the results here. 
Thanks

---

### Post by angel mike on 2016-11-06
Thanks chili555 and wild man for rapid response.I've posted the results of lsusb below and am working on the other which is more complicated.
```

~$ lsusb
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 006: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 001 Device 004: ID 04b8:013d Seiko Epson Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 045e:07f8 Microsoft Corp. Wired Keyboard 600 (model 1576)
Bus 002 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by chili555 on 2016-11-06
> 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]Your device should work with the built-in driver rtl8192cu. Is it not working as expected? Rather than try an antique driver hoping it will help, how about telling us what's not working.

There may be a conflict here with the driver rtl8xxxu. Please also post:```
lsmod | grep rtl
```

---

### Post by angel mike on 2016-11-06
I have updated the system as instructed by the wireless script and USB Adapter is connecting with blue light. Removed the wired connection but cannot connect by wifi - security code is WPA Personal and Strength 'Excellent'.
Run the the widget with and without the wired connection with USB plugged in. Output as follows
```

  	 	 	 	   $ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
 > chmod +x wireless-info && \
 > ./wireless-info
 --2016-11-06 23:09:05--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
 Resolving github.com (github.com)... failed: Temporary failure in name resolution.
 wget: unable to resolve host address ‘github.com’
 
 
 $ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
 > > chmod +x wireless-info && \
 > > ./wireless-info
 $: command not found
 michael@michael-RF786AA-ABU-SR2019UK-GB680:~$ --2016-11-06 23:09:05--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
 --2016-11-06: command not found
 michael@michael-RF786AA-ABU-SR2019UK-GB680:~$ Resolving github.com (github.com)... failed: Temporary failure in name resolution.
 bash: syntax error near unexpected token `('
 michael@michael-RF786AA-ABU-SR2019UK-GB680:~$ wget: unable to resolve host address ‘github.com’
 No command 'wget:' found, did you mean:
  Command 'wget' from package 'wget' (main)
 wget:: command not found


```
Thanks wild man

---

### Post by angel mike on 2016-11-07
Here is the post Chili555
```

$ lsmod | grep rtl
rtl8xxxu               69632  0
rtl8192cu              65536  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        49152  1 rtl8192cu
rtlwifi                69632  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              659456  4 rtl8xxxu,rtl_usb,rtlwifi,rtl8192cu
cfg80211              499712  2 mac80211,rtlwifi

```

---

### Post by chili555 on 2016-11-07
There are a very few drivers that both claim the same device, The driver rtl8192cu and the driver rtl8xxxu are two examples. They both claim your wireless device and, no doubt, conflict. Let's blacklist one and see if your wireless now performs as expected. Please open a terminal and do:

```
sudo -i
modprobe -r rtl8xxxu
echo "blacklist rtl8xxxu"  >>  /etc/modprobe.d/blacklist.conf
exit
```
It may take a reboot. Any improvement?

By the way, you haven't yet told us:> how about telling us what's not working.

---

### Post by angel mike on 2016-11-07
Chili555 that did it - I now have wifi via the ASUS USB-N13 Adapter !!!
Your the best - thanks for taking the time to solve the problem.
Regards Mike

---

### Post by chili555 on 2016-11-07
Awesome! Glad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

