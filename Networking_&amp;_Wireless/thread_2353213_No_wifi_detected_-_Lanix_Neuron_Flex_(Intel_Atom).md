---
title: "No wifi detected - Lanix Neuron Flex (Intel Atom)"
date: 2017-02-20
forum: Networking &amp; Wireless
---

### Post by elecu on 2017-02-20
Hi, may you help me please with this problem?

I have a Notebook 2 in 1, UEFI with bios in 32 bits and 64 bits proccesor, I already install Ubuntu Gnome 16.10 and works fine but I have any problems that I read that are normal with intel atom.

One is the wifi internal adapter, I'm usuing an external usb adapter just now and I dont found information about mi notebook, i tried this tutorial [https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md) but in my notebook sudo cp /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113 /lib/firmware/brcm/brcmfmac43340-sdio.txt don' t exists.

ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Bucle local)
        RX packets 22881  bytes 1502511 (1.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 22881  bytes 1502511 (1.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

Don' t show my internal wifi adapter.

Any suggestions please? Excuse me for my english, ty.

---

### Post by wildmanne39 on 2017-02-20
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

---

