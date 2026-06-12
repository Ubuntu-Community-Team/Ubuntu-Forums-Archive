---
title: "Lenovo L15 - no wlan found"
date: 2021-07-13
forum: Networking &amp; Wireless
---

### Post by miodas007 on 2021-07-13
I have problem with WIFI on Lenovo L15 (on Windows everything works fine). Device detected on the windows is Realtek RTL8852AE WiFi 6 802.11ax PCIe

I have the newest BIOS:
```
sudo dmidecode -s bios-version
R19ET35W (1.19 )
```

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0f0
       version: 0e
       serial: 38:f3:ab:e0:14:8d
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-59-generic duplex=full ip=192.168.0.45 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:36 ioport:3400(size=256) memory:fd614000-fd614fff memory:fd600000-fd603fff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:fd500000-fd5fffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


```


```

lspci -nn | grep 0280
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8852]


```

---

### Post by chili555 on 2021-07-13
Your device uses the driver rtw89pci. Let’s build it. From the terminal:

```
sudo apt update
sudo apt install build-essential git
git clone https://github.com/lwfinger/rtw89.git
cd rtw89
make 
sudo make install
sudo mkdir /usr/lib/firmware/rtw89
cp rtw8852a_fw.bin  /usr/lib/firmware/rtw89
sudo modprobe rtw89pci

```
Your wireless should now be working.

After each kernel version update, you must rebuild:

```
cd ~/rtw89
make clean
git pull
make
sudo make install
sud modprobe rtw89pci
```

Please retain the files and these instructions for that time.

---

### Post by miodas007 on 2021-07-13
```
sudo mkdir /usr/lib/firmware/rtw89
cp rtw8852a_fw.bin  /usr/lib/firmware/rtw89
```

I had rtw8852a_fw.bin file under rtw89 directory previously - and I when t tried :
```

sudo modprobe rtw89pci
```
I've got:
```

modprobe: FATAL: Module rtw89pci not found.

```

But following by your advice I build it from this repo, overwrite driver and modprobe works fine !! Thanks.

---

### Post by chili555 on 2021-07-13
> I build it from this repo, overwrite driver and modprobe works fine !! Awesome! Glad it's working as expected.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by greentofuscramble on 2021-07-23
Hello, I'm having the same problem on my Lenovo Legion 7 with the same wifi card. I tried all the steps and I get an error on the last step: "sudo modprobe rtw89pci." The error reads:

> modprobe: ERROR: could not insert 'rtw89pci': Operation not permitted 

Can you help me resolve this? Thank you!

Edit: Nevermind problem solved when i disabled SecureBoot in bios. No more error message and now wifi works!! Thank you!!!

---

### Post by matthewhorizon on 2021-11-19
After make I have:


```

user@user-pc:~/Documents/rtw89$ make
make -C /lib/modules/5.13.0-21-generic/build M=/home/user/Documents/rtw89 modules
make[1]: Entering directory '/usr/src/linux-headers-5.13.0-21-generic'
  CC [M]  /home/user/Documents/rtw89/core.o
  CC [M]  /home/user/Documents/rtw89/debug.o
  CC [M]  /home/user/Documents/rtw89/mac80211.o
  CC [M]  /home/user/Documents/rtw89/mac.o
  CC [M]  /home/user/Documents/rtw89/phy.o
  CC [M]  /home/user/Documents/rtw89/fw.o
  CC [M]  /home/user/Documents/rtw89/rtw8852a.o
  CC [M]  /home/user/Documents/rtw89/rtw8852a_table.o
  CC [M]  /home/user/Documents/rtw89/rtw8852a_rfk.o
  CC [M]  /home/user/Documents/rtw89/rtw8852a_rfk_table.o
  CC [M]  /home/user/Documents/rtw89/cam.o
  CC [M]  /home/user/Documents/rtw89/efuse.o
  CC [M]  /home/user/Documents/rtw89/regd.o
  CC [M]  /home/user/Documents/rtw89/coex.o
  CC [M]  /home/user/Documents/rtw89/ps.o
  CC [M]  /home/user/Documents/rtw89/sar.o
  CC [M]  /home/user/Documents/rtw89/ser.o
  CC [M]  /home/user/Documents/rtw89/util.o
  LD [M]  /home/user/Documents/rtw89/rtw89core.o
  CC [M]  /home/user/Documents/rtw89/pci.o
  LD [M]  /home/user/Documents/rtw89/rtw89pci.o
  MODPOST /home/user/Documents/rtw89/Module.symvers
  CC [M]  /home/user/Documents/rtw89/rtw89core.mod.o
  LD [M]  /home/user/Documents/rtw89/rtw89core.ko
  BTF [M] /home/user/Documents/rtw89/rtw89core.ko
Skipping BTF generation for /home/user/Documents/rtw89/rtw89core.ko due to unavailability of vmlinux
  CC [M]  /home/user/Documents/rtw89/rtw89pci.mod.o
  LD [M]  /home/user/Documents/rtw89/rtw89pci.ko
  BTF [M] /home/user/Documents/rtw89/rtw89pci.ko
Skipping BTF generation for /home/user/Documents/rtw89/rtw89pci.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-5.13.0-21-generic'
```

```

user@user-pc:~/Documents/rtw89$ sudo make install
make -C /lib/modules/5.13.0-21-generic/build M=/home/user/Documents/rtw89 modules
make[1]: Entering directory '/usr/src/linux-headers-5.13.0-21-generic'
make[1]: Leaving directory '/usr/src/linux-headers-5.13.0-21-generic'
cp: cannot stat 'rtl8852au*.bin': No such file or directory
make: *** [Makefile:61: install] Error 1
```
Any suggestions?

---

### Post by chili555 on 2021-11-20
> cp: cannot stat 'rtl8852au*.bin': No such file or directory
make: *** [Makefile:61: install] Error 1I assume this is a freshly cloned version of the driver; that is, in the last few weeks.

What, exactly do you have for firmware in the folder?

```
ls ~/Documents/rtw89 | grep bin

```
I have:

```
rtl8852au_config.bin
rtl8852au_fw.bin
rtw8852a_fw.bin

```If you do not have those, try to refresh the driver file:

```
cd ~/Documents/rtw89
git pull
ls | grep bin
```

Now do you have the firmware files? If so, try again:

```
make clean
make
sudo make install

```
Reboot.

---

