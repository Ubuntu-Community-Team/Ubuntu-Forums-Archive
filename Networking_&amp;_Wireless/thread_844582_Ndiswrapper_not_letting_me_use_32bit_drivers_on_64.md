---
title: "Ndiswrapper not letting me use 32bit drivers on 64 bit system"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by m994301009 on 2008-06-29
As you can see from the title, I'm trying to use my 32-bit windows drivers for a TrendNet TEW-424UB wireless USB card (dongle?). Is there any way I could modify the drivers to allow me to use it on a 64-bit system? Because I'm sure it doesn't really matter for the driver, but its stopping me from using my wireless card.
The exact error is:
```

ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B

```
and here is a pastebin of my driver's .inf file:
[http://paste.ubuntu.com/23794/](http://paste.ubuntu.com/23794/)

my card also comes with X64 vista drivers, but ndiswrapper doesn't support vista drivers (gives "unknown symbol" errors) I tried using the Vista X64 driver, but it doesn't work.

EDIT: That error comes from part of the output of dmesg, for any that might be wondering.

---

### Post by livello on 2008-10-23
Have the same problem.
Ubuntu 8.10 amd64
Ndiswrapper 1.52 
EUB-862 USB 2.0 Atheros 5523 chipset inside
How to make it work under x86-64 Linux?

---

### Post by handydan918 on 2008-10-23
I think what you have here is a prime reason not to use 64bit O/S's at this time. The driver support is marginal at best.

---

### Post by livello on 2008-10-23
I found that different windows drivers for my WLAN card Senao EnGenius EUB-862 Ext USB 2.0 based on Atheros 5523:

1) Windows XP 07/27/2005 1.5.0.110 
ar5523.bin ar5523.sys athfmwdl.cat athfmwdl.inf net5523.cat net5523.inf 
Works fine on 32 bit Ubuntu
When using with 64-bit tells that needs 64-bit drivers instead of 32-bit

2) USB_Vista_2.1.0.20 
athrxusb.sys athrxusbext.cat athrxusb.inf
Doesn't work at all


Can anyone give me any suggestion how to solve the problem?

---

### Post by handydan918 on 2008-10-23
> **livello said:**
> I found that different windows drivers for my WLAN card Senao EnGenius EUB-862 Ext USB 2.0 based on Atheros 5523:

1) Windows XP 07/27/2005 1.5.0.110 
ar5523.bin ar5523.sys athfmwdl.cat athfmwdl.inf net5523.cat net5523.inf 
Works fine on 32 bit Ubuntu
When using with 64-bit tells that needs 64-bit drivers instead of 32-bit

2) USB_Vista_2.1.0.20 
athrxusb.sys athrxusbext.cat athrxusb.inf
Doesn't work at all


Can anyone give me any suggestion how to solve the problem?

Install a 32 bit O/S?

---

### Post by shoot0 on 2008-12-06
I have the same problem.Who can help me?

---

### Post by Ayuthia on 2008-12-06
Can you provide some information about your wireless card?  We will need to see the results of:
```
lspci -nn
```

---

### Post by KojakJack on 2008-12-19
hi,
I'm encountering similar problems. I have a connection but the signal strength is jumping.

Trendnet TEW-423PI wireless card

lspci -nn output:

05:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)

I would like to be able to use an appropriate 64 bit driver.
Tried ndiswrapper on a 32 bit system with same card, worked perfectly.

Is there a solution?

---

### Post by theozzlives on 2008-12-19
That's the only problem I have with 64 bit, in my case it's modem drivers.

---

