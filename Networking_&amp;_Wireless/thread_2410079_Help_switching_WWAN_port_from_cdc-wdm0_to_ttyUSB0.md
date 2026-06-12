---
title: "Help switching WWAN port from cdc-wdm0 to ttyUSB0 ???"
date: 2019-01-10
forum: Networking &amp; Wireless
---

### Post by Muzafsh on 2019-01-10
Hi,


I have an internal device "HP lt2523 Mobile Broadband Device" on my "HP Elitebook 2570p".


This WWAN(LTE) module was working fine until last week. but after my distro pushed some updates its character has changed and as a result i am unable to make a successful data connection any longer.


Please find information of my setup ... things that could help you to provide a solution.


Going by the "Modem Manager GUI" application turns out the time that data used to connect successfully the device port was "ttyUSB" ...


But currently the same application lists this device's port as "cdc-wdm0" ... turns out this isn't let me make a successful data connection through this device anymore.




Please find snapshot of what i have stated ...


THIS STATE DOES NOT LET ME CONNECT TO DATA !
[ATTACH=CONFIG]282170[/ATTACH]




THIS STATE LETS ME CONNECT TO DATA SUCCESSFULLY !!!
[ATTACH=CONFIG]282171[/ATTACH]


Please find other outputs for my device ...


```
usb-devices
T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=03f0 ProdID=421d Rev=00.00
S:  Manufacturer=Novatel Wireless, Inc.
S:  Product=HP lt2523 Mobile Broadband Device
S:  SerialNumber=359789040033051
C:  #Ifs= 7 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 6 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=qmi_wwan
I:  If#= 7 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=qmi_wwan
```




**the command "mmcli -L" and its output**




when its bound as "cdc-wdm0"
```
Found 1 modems:
    /org/freedesktop/ModemManager1/Modem/0 [Novatel Wireless Incorporated] 4051
```


when its bound as "ttyUSB0"
```
Found 1 modems:
	/org/freedesktop/ModemManager1/Modem/0 [Novatel Wireless Incorporated] E371 WWAN
```






**the command "mmcli --simple-status -m /org/freedesktop/ModemManager1/Modem/0" and its output ...**


when its bound as "cdc-wdm0"
```
/org/freedesktop/ModemManager1/Modem/0
  -------------------------
  Status |          state: 'registered'
         | signal quality: '76' (recent)
         |          bands: 'egsm, dcs, pcs, g850, utran-1, utran-5, utran-2'
         |    access tech: 'umts'
  -------------------------
  3GPP   |   registration: 'home'
         |  operator code: '40471'
         |  operator name: 'BSNL MOBILE'
         |   subscription: 'unknown'
```


when its bound as "ttyUSB0"
```
/org/freedesktop/ModemManager1/Modem/0
  -------------------------
  Status |          state: 'connected'
         | signal quality: '80' (recent)
         |          bands: 'unknown'
         |    access tech: 'umts'
  -------------------------
  3GPP   |   registration: 'home'
         |  operator code: '40471'
         |  operator name: 'BSNL MOBILE'
         |   subscription: 'unknown'

```




**the command "nmcli d" and its output ...**




when its bound as "cdc-wdm0"
```
DEVICE    TYPE      STATE         CONNECTION 
cdc-wdm0  gsm       disconnected  --         
wlo1      wifi      disconnected  --         
enp0s25   ethernet  unavailable   --         
vmnet1    ethernet  unmanaged     --         
vmnet8    ethernet  unmanaged     --         
lo        loopback  unmanaged     --
```


when its bound as "ttyUSB0"
```
DEVICE   TYPE      STATE         CONNECTION   
ttyUSB0  gsm       connected     BSNL/CellOne 
ppp0     ppp       disconnected  --           
wlo1     wifi      disconnected  --           
enp0s25  ethernet  unavailable   --           
vmnet1   ethernet  unmanaged     --           
vmnet8   ethernet  unmanaged     --           
lo       loopback  unmanaged     --     

```




**the command "ls -al /dev/serial/by-id" and its output ...**


when its bound as "cdc-wdm0"
```
drwxr-xr-x 2 root root 140 Jan  8 20:21 .
drwxr-xr-x 4 root root  80 Jan  8 20:21 ..
lrwxrwxrwx 1 root root  13 Jan  8 20:21 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root  13 Jan  8 20:21 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root  13 Jan  8 20:21 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root  13 Jan  8 20:21 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if03-port0 -> ../../ttyUSB3
lrwxrwxrwx 1 root root  13 Jan  8 20:21 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if04-port0 -> ../../ttyUSB4
```


when its bound as "ttyUSB0"
```
total 0
drwxr-xr-x 2 root root 140 Jan  8 20:57 .
drwxr-xr-x 4 root root  80 Jan  8 20:57 ..
lrwxrwxrwx 1 root root  13 Jan  8 20:57 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root  13 Jan  8 20:57 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root  13 Jan  8 20:57 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root  13 Jan  8 20:57 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if03-port0 -> ../../ttyUSB3
lrwxrwxrwx 1 root root  13 Jan  8 20:57 usb-Novatel_Wireless__Inc._HP_lt2523_Mobile_Broadband_Device_359789040033051-if04-port0 -> ../../ttyUSB4

```




**the command "ls -l /sys/bus/usb/drivers/cdc_wdm/" and its output ...**




when its bound as "cdc-wdm0"
```
total 0
--w------- 1 root root 4096 Jan  8 20:24 bind
lrwxrwxrwx 1 root root    0 Jan  8 20:24 module -> ../../../../module/cdc_wdm
-rw-r--r-- 1 root root 4096 Jan  8 20:24 new_id
-rw-r--r-- 1 root root 4096 Jan  8 20:24 remove_id
--w------- 1 root root 4096 Jan  8 20:24 uevent
--w------- 1 root root 4096 Jan  8 20:24 unbind
```


when its bound as "ttyUSB0"
```
total 0
--w------- 1 root root 4096 Jan  8 21:28 bind
lrwxrwxrwx 1 root root    0 Jan  8 21:28 module -> ../../../../module/cdc_wdm
-rw-r--r-- 1 root root 4096 Jan  8 21:28 new_id
-rw-r--r-- 1 root root 4096 Jan  8 21:28 remove_id
--w------- 1 root root 4096 Jan  8 20:57 uevent
--w------- 1 root root 4096 Jan  8 21:28 unbind
```




**the command "ls -l /sys/bus/usb/drivers/qmi_wwan/" and its output ...**




when its bound as "cdc-wdm0"
```
total 0
lrwxrwxrwx 1 root root    0 Jan  8 20:28 1-1.5:1.6 -> ../../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6
lrwxrwxrwx 1 root root    0 Jan  8 20:28 1-1.5:1.7 -> ../../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.7
--w------- 1 root root 4096 Jan  8 20:28 bind
lrwxrwxrwx 1 root root    0 Jan  8 20:28 module -> ../../../../module/qmi_wwan
-rw-r--r-- 1 root root 4096 Jan  8 20:28 new_id
-rw-r--r-- 1 root root 4096 Jan  8 20:28 remove_id
--w------- 1 root root 4096 Jan  8 20:21 uevent
--w------- 1 root root 4096 Jan  8 20:28 unbind
```


when its bound as "ttyUSB0"
```
total 0
lrwxrwxrwx 1 root root    0 Jan  8 21:30 1-1.5:1.6 -> ../../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6
lrwxrwxrwx 1 root root    0 Jan  8 21:30 1-1.5:1.7 -> ../../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.7
--w------- 1 root root 4096 Jan  8 21:30 bind
lrwxrwxrwx 1 root root    0 Jan  8 21:30 module -> ../../../../module/qmi_wwan
-rw-r--r-- 1 root root 4096 Jan  8 21:30 new_id
-rw-r--r-- 1 root root 4096 Jan  8 21:30 remove_id
--w------- 1 root root 4096 Jan  8 20:57 uevent
--w------- 1 root root 4096 Jan  8 21:30 unbind
```

---

### Post by Muzafsh on 2019-01-10
I need help to switch this port from "cdc-wdm0" to "ttyUSB0" so i can successfully connect to the data over WWAN ...


Kindly provide the commands in the order its to be run so as to make this switch !!!


thanks for looking.

---

