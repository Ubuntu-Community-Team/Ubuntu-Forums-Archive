---
title: "LG EXpress Wireless RF_kill problem"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by eaglek1 on 2008-03-19
Hello,
My laptop is a LG T1 Express 3224p, with ubuntu gutsy.

Today i formated the HDD and installed only ubuntu. After a couple of hours to configure i noticed that the wireless doesn't worked.

After reading about in several forums, i found that the problem was about the RF_kill switch that is off.
I'm with no pacience to reinstall win xp only to enable kill switch and then reformat all over again to install ubuntu.
ANy help will be appreciated.

Thanks,
Eaglek1.

>> dmidecode -s system-manufacturer
LG Electronics
>> dmidecode -s system-product-name
T1-3224P

>> cat  /sys/bus/pci/drivers/ipw3945/0000\:05\:00.0/rf_kill 
2
>> echo -n 1 > /sys/bus/pci/drivers/ipw3945/0000\:05\:00.0/rf_kill 
>> cat  /sys/bus/pci/drivers/ipw3945/0000\:05\:00.0/rf_kill 
3
>> uname -a
Linux eagleZion 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
>> dmesg
...
[ 2229.420000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[ 2231.192000] ipw3945: Radio Frequency Kill Switch is On:
[ 2231.192000] Kill switch must be turned off for wireless networking to work.
...

i tried 
>> sudo modprobe -r ipw3945
>> sudo modprobe ipw3945 disable=0
but remains the same.

also tried
>> modprobe fsam7400
>> echo 1 > /proc/driver/wireless/radio
>> dmesg 
...
[ 4762.816000] fsam7400: SW RF kill switch for Fujitsu Siemens Amilo M 7400, v0.4.0
[ 4762.816000] fsam7400: Copyright(c) 2004 zwobbl ;)
[ 4762.816000] fsam7400: no supported wireless hardware found
[ 4799.492000] fsam7400: module removed successfully
...

---

### Post by eaglek1 on 2008-03-20
Well i just solved it....
After installing win xp (which doesn't do the trick), i've installed vista which recognized the wireless with no problem. THen i deactivated the kill switch.

And now installed ubuntu again...

UFF... hard work :P

Regards to you all

---

