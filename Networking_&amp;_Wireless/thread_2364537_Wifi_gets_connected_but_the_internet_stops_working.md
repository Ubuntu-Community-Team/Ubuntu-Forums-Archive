---
title: "Wifi gets connected but the internet stops working after some minutes"
date: 2017-06-24
forum: Networking &amp; Wireless
---

### Post by leonardkalov on 2017-06-24
I am on Xubuntu 16.04.2 on the Ideapad 110 laptop. At first I never  encountered any problems with the internet as I was on ethernet almost  always, but now that I have to use the WiFi, I have ended up with  severely irritating problems. The internet stops working altogether  after about five or seven minutes and sometimes the WiFi menu becomes  unresponsive so a full restart then becomes required. When the internet  stops working, I can't ping anything or even visit 192.168.0.1.

Here is the output from the "wireless script": [http://paste.ubuntu.com/24939297/](http://paste.ubuntu.com/24939297/)

I  also noticed that this problem isn't just specific to me but is common  to many other users of Ideapad on Ubuntu. The suggested solution is to  try:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```

But  this doesn't solve anything, and for me, it made the internet stop  working much earlier instead. Also, I noticed that I didn't encounter  this problem with some other kinds of WiFI and it seems that this seems  to come up on my new one, perhaps there is a problem with the frequency  being too large (>5GHz) and the system then starts using something  like 2GHz?

Or is it a firmware problem? it seems very likely that it is, since ath10k_pci keeps crashing intermittently and my wifi card is Qualcomm Atheros, and similar issues have been reported on it. Here is the output of that:

> PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [17aa:383b]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lenovo Device [17aa:4035]
    Kernel driver in use: ath10k_pci
[   17.360304] ath10k_pci 0000:02:00.0: pci irq msi interrupts 1 irq_mode 0 reset_mode 0
[   17.790401] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   19.751430] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 17aa:4035) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   19.751434] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   19.850796] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   32.754874] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  106.652470] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  451.532323] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  650.016348] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 25a768ea-038e-4e86-997c-b7cd466b77a5)
[  650.016414] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 17aa:4035) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[  650.016444] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[  650.018471] ath10k_pci 0000:02:00.0: firmware register dump:
[  650.018496] ath10k_pci 0000:02:00.0: [00]: 0x05020000 0x000015B3 0x00985B3A 0x00955B31
[  650.018520] ath10k_pci 0000:02:00.0: [04]: 0x00985B3A 0x00060730 0x00000004 0x00000001
[  650.018537] ath10k_pci 0000:02:00.0: [08]: 0x00955A00 0x00438A0C 0x004510FC 0x00420970
[  650.018556] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00952CD0 0x00952CE6
[  650.018580] ath10k_pci 0000:02:00.0: [16]: 0x00952CC4 0x0091080D 0x00000000 0x0091080D
[  650.018596] ath10k_pci 0000:02:00.0: [20]: 0x40985B3A 0x0040E788 0x00400000 0x00421888
[  650.018620] ath10k_pci 0000:02:00.0: [24]: 0x809BF546 0x0040E7E8 0x00426470 0xC0985B3A
[  650.018638] ath10k_pci 0000:02:00.0: [28]: 0x809B90D8 0x0040E958 0x00000018 0x0042E9E8
[  650.018658] ath10k_pci 0000:02:00.0: [32]: 0x809B859A 0x0040E9A8 0x0040E9CC 0x00428D74
[  650.018679] ath10k_pci 0000:02:00.0: [36]: 0x8091D252 0x0040E9C8 0x00000000 0x00000001
[  650.018702] ath10k_pci 0000:02:00.0: [40]: 0x809EDD7B 0x0040EA78 0x00437544 0x00429428
[  650.018718] ath10k_pci 0000:02:00.0: [44]: 0x809EB6A6 0x0040EA98 0x00437544 0x00000001
[  650.018736] ath10k_pci 0000:02:00.0: [48]: 0x80911210 0x0040EAE8 0x00000010 0x004041D0
[  650.018761] ath10k_pci 0000:02:00.0: [52]: 0x80911154 0x0040EB28 0x00400000 0x00000000
[  650.018777] ath10k_pci 0000:02:00.0: [56]: 0x8091122D 0x0040EB48 0x00000000 0x00400600
[  651.975779] ath10k_pci 0000:02:00.0: device successfully recovered
[ 1243.479637] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[ 1243.582276] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[ 1248.836997] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[ 2014.744437] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[ 2207.290113] ath10k_pci 0000:02:00.0: firmware crashed! (uuid ac7a0ab5-e9da-47d4-8517-da9d2f9d26af)
[ 2207.290129] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 17aa:4035) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[ 2207.290133] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2207.292134] ath10k_pci 0000:02:00.0: firmware register dump:
[ 2207.292141] ath10k_pci 0000:02:00.0: [00]: 0x05020000 0x000015B3 0x00985B3A 0x00955B31
[ 2207.292145] ath10k_pci 0000:02:00.0: [04]: 0x00985B3A 0x00060730 0x00000004 0x00000000
[ 2207.292149] ath10k_pci 0000:02:00.0: [08]: 0x00955A00 0x00438A0C 0x004510FC 0x00420970
[ 2207.292152] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00952CD0 0x00952CE6
[ 2207.292156] ath10k_pci 0000:02:00.0: [16]: 0x00952CC4 0x0091080D 0x00000000 0x0091080D
[ 2207.292159] ath10k_pci 0000:02:00.0: [20]: 0x40985B3A 0x0040E788 0x00400000 0x00421888
[ 2207.292163] ath10k_pci 0000:02:00.0: [24]: 0x809BF546 0x0040E7E8 0x00426470 0xC0985B3A
[ 2207.292166] ath10k_pci 0000:02:00.0: [28]: 0x809B90D8 0x0040E958 0x00000018 0x0042E9E8
[ 2207.292170] ath10k_pci 0000:02:00.0: [32]: 0x809B859A 0x0040E9A8 0x0040E9CC 0x00428D74
[ 2207.292173] ath10k_pci 0000:02:00.0: [36]: 0x8091D252 0x0040E9C8 0x00000000 0x00000001
[ 2207.292177] ath10k_pci 0000:02:00.0: [40]: 0x809EDD7B 0x0040EA78 0x00437544 0x00429428
[ 2207.292180] ath10k_pci 0000:02:00.0: [44]: 0x809EB6A6 0x0040EA98 0x00437544 0x00000001
[ 2207.292183] ath10k_pci 0000:02:00.0: [48]: 0x80911210 0x0040EAE8 0x00000010 0x004041D0
[ 2207.292187] ath10k_pci 0000:02:00.0: [52]: 0x80911154 0x0040EB28 0x00400000 0x00000000
[ 2207.292190] ath10k_pci 0000:02:00.0: [56]: 0x8091122D 0x0040EB48 0x00000000 0x00400600
[ 2209.248043] ath10k_pci 0000:02:00.0: device successfully recovered



I would EXTREMELY appreciate  it if someone could look carefully into this problem and help me out  here, you have no idea how much I'd thank you for it!

---

### Post by praseodym on 2017-06-24
dmesg shows firewall blocks?! Try
```

sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by Hadaka on 2017-06-24
Hi, and also please do from a working wired connection..
```
sudo apt-get update
 sudo apt-get dist-upgrade
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
```
```
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
```
sudo iw reg set MY
sudo sed -i 's/=.*/=MY/' /etc/default/crda
```
Remove wired connection...boot and test wireless.
Thanks

---

### Post by leonardkalov on 2017-06-24
> **praseodym said:**
> dmesg shows firewall blocks?! Try
```

sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

This isn't related to firewalls at all. I disabled them and the problem still remained, and the problem arises even on live USB distros.

---

### Post by leonardkalov on 2017-06-24
> **Hadaka said:**
> Hi, and also please do from a working wired connection..
```
sudo apt-get update
 sudo apt-get dist-upgrade
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
```
```
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
```
sudo iw reg set MY
sudo sed -i 's/=.*/=MY/' /etc/default/crda
```
Remove wired connection...boot and test wireless.
Thanks

I did everything you asked and it did not solve the problem. The internet still stops working for many minutes :/

---

### Post by jeremy31 on 2017-06-24
It might be a firmware issue that was recently discovered by one of the developers.
```
cd /lib/firmware/ath10k/QCA9377/hw1.0
sudo mv board-2.bin board-2.bin.bak
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA9377/hw1.0/board-2.bin
```

Reboot
It seems some of the entries in the board-2.bin had duplicates but I don't know if it would cause the firmware crash or not [https://github.com/kvalo/ath10k-firmware/commit/2ddb8208b087ae586ec146ce80a9d64d7f01d5b8](https://github.com/kvalo/ath10k-firmware/commit/2ddb8208b087ae586ec146ce80a9d64d7f01d5b8)

---

### Post by leonardkalov on 2017-06-24
> **jeremy31 said:**
> It might be a firmware issue that was recently discovered by one of the developers.
```
cd /lib/firmware/ath10k/QCA9377/hw1.0
sudo mv board-2.bin board-2.bin.bak
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA9377/hw1.0/board-2.bin
```

Reboot
It seems some of the entries in the board-2.bin had duplicates but I don't know if it would cause the firmware crash or not [https://github.com/kvalo/ath10k-firmware/commit/2ddb8208b087ae586ec146ce80a9d64d7f01d5b8](https://github.com/kvalo/ath10k-firmware/commit/2ddb8208b087ae586ec146ce80a9d64d7f01d5b8)

I had tried this already and it didn't end up fixing the problem unfortunately. I am still very confused, what else do you think could possibly be causing this strange issue?

---

### Post by jeremy31 on 2017-06-24
I would have guessed power management as the new Atheros cards don't usually perform well with it on.  That board-2.bin file has only been around for four days.
I would also set the wifi router to channel 1 rather than 6 or auto and see if you can set the channel width to 20 MHz rather than 20/40 auto and see if it performs better

---

