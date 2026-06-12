---
title: "Wifi card not working"
date: 2018-01-29
forum: Networking &amp; Wireless
---

### Post by nalle2 on 2018-01-29
Hi
So I have a X405U (Asus Vivobook) and no wifi card shows up.

lshw:
```
           *-network UNCLAIMED
                description: Network controller
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: ioport:d000(size=256) memory:ef000000-ef00ffff

```

lsusb:
Bus 001 Device 003: ID 13d3:3526 IMC Networks 

Can someone point me in the right direction?


Thank you!

EDIT: Running latest Kubuntu, and updated everything. Spanking new installation.

---

### Post by chili555 on 2018-01-29
We need just a bit more information. Please run and post:```
lspci -nnk | grep 0280
```

---

### Post by nalle2 on 2018-01-29
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]

---

### Post by chili555 on 2018-01-29
Please try the solution here: [https://askubuntu.com/questions/994150/ubuntu-16-04-on-hp-envy-ae000-wifi-problems](https://askubuntu.com/questions/994150/ubuntu-16-04-on-hp-envy-ae000-wifi-problems)

Note that you have the same 10ec:b822 device.

---

### Post by nalle2 on 2018-01-29
thanks man! i shall try this later tonight!
is this some kind of thing that could go to **** when installing new updates (like kernel updates and such) ?

---

### Post by chili555 on 2018-01-29
Not ****, exactly, but you *will* need to re-compile when Update Manager installs a later kernel version and after the requested reboot.

I suggested that you try it first to make sure that it actually works as expected before I added the re-compile caveat.

---

### Post by nalle2 on 2018-01-29
thanks, seem to be working!

---

### Post by chili555 on 2018-01-29
Awesome Glad it's working.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

As mentioned, after a kernel update, re-compile:```
cd rtlwifi-next
make clean
make
sudo make install
sudo modprobe rtl8822be
```

---

### Post by praseodym on 2018-01-29
Alternatively, you could use the extended branch using dkms instead:
```

git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```

---

### Post by avinal on 2018-09-09
modprobe: ERROR: could not insert 'rtl8822be': Exec format error I am getting this error message on my HP Pavilion cd-0087tu .everything else is same ..I mean the drivers and network card .

---

### Post by chili555 on 2018-09-09
> **avinal said:**
> modprobe: ERROR: could not insert 'rtl8822be': Exec format error I am getting this error message on my HP Pavilion cd-0087tu .everything else is same ..I mean the drivers and network card .I suggest that you start your own new question. I doubt that you will get much support posting to a thread that is already marked Solved.

---

### Post by coffeecat on 2018-09-09
@avinal, a little over 4 weeks ago you hijacked another thread marked as solved here: [https://ubuntuforums.org/showthread.php?t=2392454&p=13791210&viewfull=1#post13791210](https://ubuntuforums.org/showthread.php?t=2392454&p=13791210&viewfull=1#post13791210)

In that thread chili555 suggested that you start your own thread in which you should include a wifi diagnostics report from the wireless info script. It appears that you have ignored chili555's excellent advice, but instead have hijacked a second solved thread with the same problem and failed to provide the diagnostics report. If you do really want help, please start your own thread, and post the wireless info as described here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) .

I shall now close this old and solved thread to prevent further unnecessary necromancing hijackings.

Thread closed.

---

