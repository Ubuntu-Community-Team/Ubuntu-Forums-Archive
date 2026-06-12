---
title: "lost my wirless connection with ubuntu 19.04 upgrade"
date: 2019-10-09
forum: Networking &amp; Wireless
---

### Post by newblank25 on 2019-10-09
I upgraded to ubuntu 19.04 recently and lost my wireless access with RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller. I saw on the web that this a known issue. Will this issue be fixed with the release of ubuntu 19.10 which I will upgrade to. If that is the case then I'm ok with that. If not I'm using a USB device which works 99% of the time. I would rather  use the one that is installed. Can anybody walk me thru proper way to get resolved the problem. THX

.

---

### Post by chili555 on 2019-10-09
> lost my wireless access with RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller. As the name implies, this is an ethernet adapter, not wireless.

Let's find out what wireless device you have. Please open a terminal and run:```
lspci -nnk | grep 0280 -A3
rfkill list all
```Post the result.

---

### Post by newblank25 on 2019-10-10
spci -nnk | grep 0280 -A3
-p7-1456c:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
this is output

---

### Post by chili555 on 2019-10-10
> 
spci -nnk | grep 0280 -A3
It was supposed to be:```
[COLOR="#FF0000"]l[/COLOR]spci -nnk | grep 0280 -A3
```Are you saying that there was no output at all?

Is the wireless enabled in the BIOS/EFI?

---

### Post by newblank25 on 2019-10-10
is the 1st one lspci -nnk [COLOR=#000000][FONT=&quot]| grep 020 -A3? is this correct? When i copied it & put into terminal i got no answer.when i did the other one i got this 
[/FONT][/COLOR]Command 'spci' not found, did you mean:


  command 'spc' from deb supercat (0.5.6-1)
  command 's2ci' from deb scheme2c (2012.10.14-1ubuntu1)
  command 'lspci' from deb pciutils (1:3.5.2-1ubuntu2)
  command 'sci' from deb scheme2c (2012.10.14-1ubuntu1)
  command 'xpci' from deb xdiagnose (3.8.9)
what should i do? thx

---

### Post by newblank25 on 2019-10-10
i tried this  and it shows nmcli dDEVICE           TYPE      STATE        CONNECTION 
wlx34e894a79180  wifi      connected    41BAD8     
enp3s0           ethernet  unavailable  --         
lo               loopback  unmanaged    --  
does this mean network manager has to be reinstalled?
i'm using a external plugin device right now for internet access now. thx

---

### Post by chili555 on 2019-10-13
> does this mean network manager has to be reinstalled?No. It is, as far as I can tell, unrelated. 

So far, your internal wireless card is not recognized at all by the operating system. Again, is there an option in the BIOS/EFI to enable or disable wireless? Please check. If there is none, the I strongly suspect that the internal device is defective; that is, broken.

---

### Post by praseodym on 2019-10-13
Please show

```
lspci -nnk
lsusb
pccardctl info
cat /sys/bus/sdio/devices/*
cat /sys/bus/sdio/devices/*/uevent
```

---

