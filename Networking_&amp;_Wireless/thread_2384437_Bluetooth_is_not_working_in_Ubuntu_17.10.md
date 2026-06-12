---
title: "Bluetooth is not working in Ubuntu 17.10"
date: 2018-02-07
forum: Networking &amp; Wireless
---

### Post by daniel4128 on 2018-02-07
Hi. I recently installed ubuntu 17.10 on my hp 15 bs015dx laptop. My Bluetooth is not working correctly. I'm able to turn it on in the options page but nothing happens afterwards. The screen still says I should turn on the Bluetooth even though it is on. I use a realtek Bluetooth 4.2 adapter. Any help?

---

### Post by tinylagarto on 2018-02-07
Let us see if your Bluetooth adapter is being recognized.

Post the terminal output of:

```
lsusb | grep bluetooth
```

You could also try to restart the Bluetooth service:

```
sudo service bluetooth restart 



```

---

### Post by daniel4128 on 2018-02-08
I don't get an output when i type: ```
 lsusb | grep bluetooth 
``` Restarting the service did not work either.(Rebooted just to make sure, still not working). However, typing just ```
 lsusb 
``` gives me this output
 ```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f3:250e Elan Microelectronics Corp. 
Bus 001 Device 003: ID 05c8:0233 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by tinylagarto on 2018-02-08
Sorry, was my fault, the correct command is:
```
[COLOR=#000000]
lsusb | grep Bluetooth[/COLOR]
```

Maybe let us see if the service Bluetooth is running at all:

```
systemctl list-unit-files|grep -i bluetooth



```

The output on my machine looks like this and Bluetooth is working:

```
bluetooth.service                          enabled        
bluetooth.target                           static      

```

---

### Post by daniel4128 on 2018-02-08
```
lsusb | grep Bluetooth 
``` doesn't give me an output either. But ```
lsmod | grep blue
``` gives me this: 
```

bluetooth             540672  14 btrtl,hci_uart,btintel,btqca,bnep,btbcm,btusb
ecdh_generic           24576  1 bluetooth

```

I get the same output as yours when I type this command:
```
systemctl list-unit-files|grep -i bluetooth

```

---

### Post by jeremy31 on 2018-02-08
Hi daniel4128
You will likely have to wait for Realtek to release the firmware for this device to Linux as your wifi is fairly new and the bluetooth is integrated into that device.  I have no idea on when the release may happen

---

### Post by daniel4128 on 2018-02-09
Thanks, Jeremy. I guess I'll just have to wait.

---

