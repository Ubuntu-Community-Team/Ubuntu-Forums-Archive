---
title: "Realtek b851 WiFi Card doesn't work in Ubuntu"
date: 2024-08-24
forum: Networking &amp; Wireless
---

### Post by bluesilent9 on 2024-08-24
Hello,

My wife recently bought a new computer (ASUS X1504VAP-NJ815W) and I tried to install Kubuntu LTS on it. Originally after installation the computer would go to a blank screen after reboots, however I fixed this fault by updating to the latest packages using a USB to Ethernet adapter. I am now trying to get the inbuilt WiFi card up and running but am running into issues. lspci reports the card as:

[FONT=monospace][COLOR=#000000]*0000:01:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b851*

[/COLOR][/FONT]I then googled this b851 and it seems that it should be part of the rtw89 driver found here:

[https://github.com/lwfinger/rtw89](https://github.com/lwfinger/rtw89)

So I followed the installation instructions. However, when I run "make" as recommended in the readme, I get the following error:

[FONT=monospace][COLOR=#000000]**/home/XXXX/rtw89/core.c:**[/COLOR][COLOR=#000000] In function ‘[/COLOR][COLOR=#000000]**rtw89_core_register_hw**[/COLOR][COLOR=#000000]’: [/COLOR]
[COLOR=#000000]**/home/XXXX/rtw89/core.c:4678:37:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#ff5454]**error: **[/COLOR][COLOR=#000000]‘[/COLOR][COLOR=#000000]**WIPHY_FLAG_DISABLE_WEXT**[/COLOR][COLOR=#000000]’ undeclared (first use in this function) [/COLOR]
 4678 |                 hw->wiphy->flags |= [COLOR=#ff5454]**WIPHY_FLAG_DISABLE_WEXT**[/COLOR][COLOR=#000000]; [/COLOR]
      |                                     [COLOR=#ff5454]**^~~~~~~~~~~~~~~~~~~~~~~**[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#000000]**/home/XXXX/rtw89/core.c:4678:37:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#54ffff]**note: **[/COLOR][COLOR=#000000]each undeclared identifier is reported only once for each function it[/COLOR]
 appears in 
make[3]: *** [scripts/Makefile.build:243: /home/XXXX/rtw89/core.o] Error 1 
make[2]: *** [/usr/src/linux-headers-6.8.0-31-generic/Makefile:1926: /home/XXXX/rtw89] Error 2 
make[1]: *** [Makefile:240: __sub-make] Error 2 
make[1]: Leaving directory '/usr/src/linux-headers-6.8.0-31-generic' 
make: *** [Makefile:104: all] Error 2

Any help would be greatly appreciated.

Cheers.
[/FONT]

---

### Post by jeremy31 on 2024-08-24
See the wireless script link in my signature and post results

---

### Post by bluesilent9 on 2024-08-30
Hi,

Thanks for the instruction. Was busy over the last week but I'm now I'm working on this issue again. I just did a fresh install of Kubuntu LTS 24.04.1 and although most issues I had seem to have now been fixed, the Wifi is still not working correctly. As requested I have run the Wireless Info Script you suggested (On the latest 24.04.1 LTS and the following is a link to the results on Pastebin:

[https://pastebin.com/x0SAGqty](https://pastebin.com/x0SAGqty)

Cheers

---

### Post by jeremy31 on 2024-08-30
What happens if you ```
sudo modprobe -v rtw89_8851be
```

---

### Post by bluesilent9 on 2024-08-30
No change. I thought I seen something move for a split second in the tray, but I checked network connections after running this command and only the USB Ethernet connection is there.

---

### Post by jeremy31 on 2024-08-30
I think something very strange is happening and not sure of the cause.  It shows the correct kernel drivers were loaded at some point but they aren't in use, so it might take a kernel update to fix

---

### Post by bluesilent9 on 2024-08-30
Should I raise a bug report on launchpad with this information or is there anything else I can try?

---

### Post by jeremy31 on 2024-08-30
A bug report would be helpful, please post a link here

---

### Post by bluesilent9 on 2024-08-30
Bug Report raised:

[https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/2078533](https://bugs.launchpad.net/ubuntu/+source/network-config/+bug/2078533)

---

### Post by jeremy31 on 2024-09-06
Is there any way to get dmesg logs or something on the bug report?  I see you had issues with apport not wanting to do anything

---

### Post by bluesilent9 on 2024-09-09
I uploaded the pastebin link to the dmesg output I collected onto the bug report. You can also access it here: [https://pastebin.com/bDr3eeke](https://pastebin.com/bDr3eeke)

---

### Post by jeremy31 on 2024-09-09
Try resetting the BIOS.  Might have to power off, remove power cord, then hold power button for 30 seconds

---

### Post by bluesilent9 on 2024-09-09
Done. Wifi card still doesn't show up.

---

### Post by jeremy31 on 2024-09-09
Dang, I found a post on Arch Linux forums that said it worked, maybe a BIOS reset to defaults or remove the CMOS battery will work

---

### Post by bluesilent9 on 2024-09-10
I might try going into the BIOS and manually resetting it via the GUI over the next couple of days and also reinstalling the CMOS battery.

---

### Post by bluesilent9 on 2024-09-14
OK, I got it fixed but I'm not 100% sure how it was fixed. Earlier I followed your instruction, turned it on and it wasn't working. I then went into the BIOS, reset to defaults and tested it but the WiFi card was still not working. Today I decided to open the laptop up to try and find the CMOS battery, but it looks like you need to disassemble about 90% of this laptop just to get to the CMOS battery (I'm assuming it's behind the motherboard like some other ASUS laptops, because it's not visible when I open the cover). I then decided to close it up without fully disassembling it and write back to you what I'd done so far, however I noticed that the WiFi was suddenly working. Thanks for your help.

---

### Post by praseodym on 2024-10-27
SecureBoot ist turned off? Please show 

sudo dmesg | grep rtw

---

