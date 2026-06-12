---
title: "[lubuntu] Setting up wifi card dwa-131"
date: 2017-11-19
forum: Networking &amp; Wireless
---

### Post by patxih on 2017-11-19
Hello,

Although I am not new to Ubuntu, I am experiencing some issues while trying to set up the external wifi card dwa-131 version E1.

I  currently have lubuntu 16.04 running in a virtual machine with  Virtualbox. The machine is correctly configured so the wifi card will be  connected as a USB device to Ubuntu.

However, after trying several solutions found in Google, such as:

```
rm -r rtl8192eu-linux-driver
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
cd rtl8192eu-linux-driver
make
sudo make install
sudo modprobe 8192eu
```

 ```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt update
sudo apt install rtl8192eu-dkms
```

I have also tried to install the driver rtl8192cu. After installing this driver, the system is able to get the name of the network but it is unable to connect to any of them.

This is also the pastebin after executing the wireless script of this forum: [http://paste.ubuntu.com/25997585/](http://paste.ubuntu.com/25997585/)

Do you know why this is happening? Thank you.

---

