---
title: "*smh* sound doesn't work... again"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by adobrakic on 2009-01-04
Not sure why, but sound just randomly stopped working. Usually a simple restart fixes this, but nope.. not this time.

Not really sure what codes I can enter to check out what's wrong.
So...any ideas?
:D

---

### Post by sledge73 on 2009-01-04
post output of $lspci & maybe I can help. open terminal & type lspci.

---

### Post by adobrakic on 2009-01-04
```

ado@ado-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
ado@ado-desktop:~$ 

```

---

### Post by sledge73 on 2009-01-04
do you have external speakers pluged in???

---

### Post by sledge73 on 2009-01-04
first off try alsagui. install from synaptic or source. if that dont work check this out --> [http://ubuntuforums.org/archive/index.php/t-31567.html](http://ubuntuforums.org/archive/index.php/t-31567.html)

---

### Post by adobrakic on 2009-01-04
> 
do you have external speakers pluged in???


Yessir, 5.1 surround sound.. if that matters.

> 
first off try alsagui. install from synaptic or source.


I searched in synaptic for 'alsagui,' but nothing came up, did you mean alsamixergui? If so, I have that already.

> 
if that dont work check this out --> [http://ubuntuforums.org/archive/index.php/t-31567.html](http://ubuntuforums.org/archive/index.php/t-31567.html)


Thanks, I'll check it out.

--edit--

That seems to lead me to an explanation for getting sound if it never worked. 
Instead of troubleshooting, it's explaining how to set up sound. If that makes sense.
:x

--supah edit--
My prophecies came true, the sound randomly came back of rebooting.
:)

---

