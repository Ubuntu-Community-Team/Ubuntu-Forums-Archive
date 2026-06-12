---
title: "WiFi connection problems following ufei install"
date: 2013-11-16
forum: Networking &amp; Wireless
---

### Post by S Hartwell on 2013-11-16
I had been waiting since I got my new computer to install Ubuntu. Of course Windows8 had to make the whole process insanity. I was able today to get verything running alongside each other through the GRUB menu and I'm quite happy, aside from one problem. The WiFi on my Ubuntu install doesn't work - It'll connect,connect,connect, disconnect. I'd read switching to WPA2 Personal might help so I changed my router settings(using same encryption key) and now it proclaims connecting,connecting,connecting, enter encryption key.

I have disabled both SecureBoot and enabled CSM for Legacy mode. These actions have not fixed whatever wireless error I'm encountering. This leads me to believe it's just a bad install, and I will try reinstalling with Legacy Mode engaged.


I suspect it is UFEI blocking Ubuntu's path to the WiFi intergrated card since I can't run any USB drives from it(such as a EHDD that has some .deb files on it.)

Can anybody help me?

Ps: My computer Make is Acer Aspire AT3-100-EF20.

---

### Post by praseodym on 2013-11-17
Please show the terminal outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
route -n
```

---

### Post by S Hartwell on 2013-11-17
Following a reinstallation of Ubuntu it seems all my partitons have been rewritten. No EFI partition,etc. Can't install Win7 since it 'can't be installed to GPT disk.'

I'm guessing I need to fix something with the partitions since I can't boot to HDD anymore. UFEI and Windows8 has really made a mess of everything I knew about computers...

---

