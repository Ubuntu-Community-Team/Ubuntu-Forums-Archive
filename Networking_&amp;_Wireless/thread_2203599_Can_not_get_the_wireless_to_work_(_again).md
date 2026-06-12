---
title: "Can not get the wireless to work ( again)"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by mr best buy on 2014-02-04
I have an older  HP pavilion ze4900. I installed Lubunutu on it.  Then I ran the command  down vote
	


lspci -nn

this told me my broadcom was B43

So I downloaded the broadcom file  from [https://dl.dropbox.com/u/58267392/b43.zip](https://dl.dropbox.com/u/58267392/b43.zip)

I put it on by desktop.
I ran the command 



sudo mkdir /lib/firmware/b43


Then I ran theis command
sudo cp Desktop/b43/*  /lib/firmware/b43

The message I got was there was no life or place as desktop
The message is CP:  cannot stat  'Desktop/b43/*'  so such file or directory

So I am suck. What should I do next.....????




sudo modprobe -r b43 && sudo modprobe b43

Your wireless should now be working.

[https://dl.dropbox.com/u/58267392/b43.zip](https://dl.dropbox.com/u/58267392/b43.zip)

If this is not your device ID, please post it and we'll proceed.

---

### Post by westie457 on 2014-02-04
Could you post the ouptut of ```
lspci -vnn
``` to give us more of a clue which version of the B43xx chip you have?

---

### Post by mr best buy on 2014-02-04
02 : 06.0  Network conto;;er  [ 0280 ] : Broadcom Coporation BCM4306 802.11b/g wireless LAN controler  [ 14e4 : 4320 ] ( rev 03 )

---

### Post by mr best buy on 2014-02-04
john@john-hp-pavilion-ze4900-PR299UA-ABA:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:05.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
john@john-hp-pavilion-ze4900-PR299UA-ABA:~$ ^C
john@john-hp-pavilion-ze4900-PR299UA-ABA:~$ ^C
john@john-hp-pavilion-ze4900-PR299UA-ABA:~$

---

### Post by mr best buy on 2014-02-04
When I try to manually  unpack the B42 folder to lib/firmware/b43  I get a missage that  I do not have enought permission.  So I change my account type to administrator. Still the same problem. everything I try to  do in this respect I do not have the permission...even if my account type is administrator....Any ideas???

---

### Post by chili555 on 2014-02-04
Please try:```
sudo cp [COLOR="#FF0000"]~/[/COLOR]Desktop/b43/* /lib/firmware/b43
```If you computer uses a different language, Desktop may be named something else; skrifborð for example.

---

### Post by mr best buy on 2014-02-04
I tried it it the name of desktop and the name you supplied. still no luck.  when i try it manually it will not give me permission

---

### Post by chili555 on 2014-02-04
> **mr best buy said:**
> I tried it it the name of desktop and the name you supplied. still no luck.  when i try it manually it will not give me permissionWhat is the result of: ```
cd ~/Desktop && ls
```

---

### Post by mr best buy on 2014-02-04
CP cannot stat  /desktop/b43/*  :  no such file or directory

---

### Post by chili555 on 2014-02-04
> **mr best buy said:**
> CP cannot stat  /desktop/b43/*  :  no such file or directoryThat's not what I asked for. What is the result of:


```
cd ~/Desktop && ls
```Not desktop but ~/Desktop

---

### Post by mr best buy on 2014-02-04
bash: cd:  /desktop:  no such file or directory

---

### Post by chili555 on 2014-02-04
Please read my post again. Not desktop but ~/Desktop. Please carefully type this command into the terminal or even better, copy and paste it:```
cd ~/Desktop && ls
```That funny ~ is on the left side of my US keyboard on the same key with ` and just to the left of 1.

Do not try to install the firmware yet. Just show me the result of the command I asked for, please.

---

### Post by mr best buy on 2014-02-04
The result is b43 (in blue) and b43.zip (in red)
When I try to manually unzip it, the message is I do not have the privilege. Howere my account says I am the administrator

---

### Post by mr best buy on 2014-02-04
I copied your command and it worked.  Now that the command worked, what is the next step to do. the command that worked was  sudo cp /Desktop/b43/* lib/firmware/b43.

Now what next to get the wireless to work? thanks

---

### Post by chili555 on 2014-02-04
> the command that worked was sudo cp /Desktop/b43/* lib/firmware/b43.
I hope it was actually sudo cp /Desktop/b43/* [COLOR="#FF0000"]** /**[/COLOR]lib/firmware/b43. You can use the arrow keys in the terminal to recall your last several commands. Please verify. If so, then do:```
sudo modprobe -r b43 && sudo modprobe b43
```Your wireless should come to life:```
iwconfig
```If not, check for errors:```
dmesg | grep b43
```

---

### Post by mr best buy on 2014-02-04
I rebooted and it is working. Thank you so much

---

