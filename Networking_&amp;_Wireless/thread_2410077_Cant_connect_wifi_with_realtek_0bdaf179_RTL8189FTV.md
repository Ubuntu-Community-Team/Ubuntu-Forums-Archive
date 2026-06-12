---
title: "Cant connect wifi with realtek 0bda:f179 RTL8189FTV"
date: 2019-01-10
forum: Networking &amp; Wireless
---

### Post by yamijuan on 2019-01-10
Hi, i&#7743; not so good at linux and i have a [COLOR=#242729][FONT=Arial]0bda:f179 RTL8189FTV chip for wifi in windows but it does not work with ubuntu.

`lsusb` shows `[/FONT][/COLOR]  Bus 001 Device 004: ID 0bda:f179 Realtek Semiconductor Corp.[COLOR=#242729][FONT=Arial]`i have ubuntu 18.10[/FONT][/COLOR]

---

### Post by praseodym on 2019-01-10
Hi,

does LAN work? Install the driver via
```

sudo apt-get install git build-essential
git clone git://github.com/ulli-kroll/rtl8188fu
cd rtl8188fu
make
sudo make installfw
sudo modprobe cfg80211
sudo insmod rtl8188fu.ko
sudo make install
```
[https://github.com/ulli-kroll/rtl8188fu](https://github.com/ulli-kroll/rtl8188fu)

---

### Post by roquette28 on 2019-06-04
hi,

You save my life praseodym, my network now works!! 

But when i reinitialized my PC, i need make all again, are you know tell me what the problem?

Thks

---

### Post by praseodym on 2019-06-05
Try afterwards
```

sudo depmod -a
sudo update-initramfs -u
```

---

### Post by jeremy31 on 2019-06-05
I would use [https://github.com/kelebek333/rtl8188fu](https://github.com/kelebek333/rtl8188fu) as it has dkms support

---

### Post by d68088328 on 2019-06-25
this method did not help

---

### Post by chili555 on 2019-06-25
> **d68088328 said:**
> this method did not helpPlease start your own new thread and include in detail the steps you took that didn't work.

---

### Post by wargas-1 on 2019-07-19
[COLOR=#000000]You saved my life praseodym, my network now works and i got appreciation from my boss who's been working on this issue since days, and then I came and did this magic!! BOOM ISSUE SOLVED , 
But there is an **issue when we restart the system**, the _problem still exist_...and we have to *do the steps all again* from the beginning

\please provide me with a solution at the earliest
[/COLOR]

---

### Post by praseodym on 2019-07-19
Force the driver being loaded on boot up
```

echo rtl8188fu | sudo tee -a /etc/modules
```
Reboot. On the fly you can do
```

sudo modprobe -v rtl8188fu
```

---

### Post by jeremy31 on 2019-07-19
> **praseodym said:**
> Force the driver being loaded on boot up
```

echo rtl8188fu | sudo tee -a /etc/modules
```
Reboot. On the fly you can do
```

sudo modprobe -v rtl8188fu
```

Or they could do ```
cd rtl8188fu
sudo make install
```

Not sure why that detail was omitted from the instructions on the github readme

---

### Post by praseodym on 2019-07-20
Added to instruction above

---

### Post by wargas-1 on 2019-07-24
please explain in detail how can i implement this in my Ubuntu 18.04 LTS

---

### Post by chili555 on 2019-07-24
> **wargas-1 said:**
> please explain in detail how can i implement this in my Ubuntu 18.04 LTSThe instructions in post #2 above should do it.

---

### Post by wargas-1 on 2019-07-27
Can you please make it clear how to solve the problem even after restart.

---

### Post by chili555 on 2019-07-27
> **wargas-1 said:**
> Can you please make it clear how to solve the problem even after restart.Please try:

```
git clone https://github.com/kelebek333/rtl8188fu

sudo dkms add ./rtl8188fu

sudo dkms build rtl8188fu/1.0

sudo dkms install rtl8188fu/1.0

sudo cp ./rtl8188fu/firmware/rtl8188fufw.bin /lib/firmware/rtlwifi/

```

---

### Post by El Potro on 2019-08-09
Was anybody able to get it working in monitor mode?
I compiled the driver and it works, but I wasn't able to start the monitor mode. 
I even modified the makefile (as suggested [in this question]("https://askubuntu.com/questions/1062402/cant-find-wifi-drivers-for-0bdaf179-realtek-semiconductor-corp")) like so:

```
rtl8188fu/Makefile:

CONFIG_POWER_SAVING = n
CONFIG_WIFI_MONITOR = y
```

But still, it segfaults

---

### Post by dfrabu on 2019-09-07
> **praseodym said:**
> Hi,

does LAN work? Install the driver via
```

sudo apt-get install git build-essential
git clone git://github.com/ulli-kroll/rtl8188fu
cd rtl8188fu
make
sudo make installfw
sudo modprobe cfg80211
sudo insmod rtl8188fu.ko
sudo make install
```
[https://github.com/ulli-kroll/rtl8188fu](https://github.com/ulli-kroll/rtl8188fu)

THANK YOU MAN! You SAVED ME! It works perfectly!

---

