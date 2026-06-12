---
title: "Dell D630 Lubuntu Bluetooth problem"
date: 2015-02-07
forum: Networking &amp; Wireless
---

### Post by Christopher_Buckin on 2015-02-07
Hi, I'm very new to the linux world (meaning I'm still pretty clumsy getting around) but anyhow, I have installed Lubuntu 14.10 to reinvigorate my dell D630 laptop. I have been trying to get the bluetooth working in order to connect to a logitech bluetooth audio receiver. I installed the bluetooth manager and everytime I try to run it, it says the bluetooth needs to be enabled, which I click the enable button. Nothing happens. I've googled around and it seems the bluetooth needs to be turned on in windows, but I no longer have windows installed or the ability to install it on this machine. Is there any other way to get this to work or a wiki somewhere I could follow? Thanks for your time. Christopher

---

### Post by jeremy31 on 2015-02-07
Lets get some info about your hardware, open terminal(CTRL + ALT +t) and use mouse/touchpad to copy and paste commands and output from the terminal
```
rfkill list
```
```
lsmod | grep bluetooth
```
```
lspci -nnk | grep -iA2 net
```
```
lsusb
```

---

