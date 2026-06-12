---
title: "Eth0 not recognized"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by campos on 2006-09-09
Hi Guys!

This is my first post and I'm new in Ubuntu, well I installed Ubuntu 6.06 LTS in a Pentium 3, I'm trying to connect to the internet but I can't, I have a Cable conection with comcast, I'm using a router to connect to the internet.

Well when I go to the network admin seccion there is a text:

Connections:

Modem Conection, 

I just see modem conection but I don't see ethernet conection or eth0 thing, my pentium 3 has a ethernet card, it was working fine with windows xp but with ubuntu it doesn't work, it seens that ubuntu doesn't recognize my ethernet card, I heard about some drivers but I'm really new in this, can somebody please give me a hand? I will thank you very much.

---

### Post by Uluen on 2006-09-09
What's the output of ```
$ lspci
```

On this computer the relevant parts are
```
0000:02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:02:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 10)
```

Also try ```
$ dmesg | grep eth
```

---

### Post by campos on 2006-09-09
Thank you for your reply, well the output of $ lspci is:

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
0000:00:0e.0 Communication controller: 3Com Corp, Modem Division WinModem
0000:00:10.0 Mass storage controller: Promise Technology, Inc. PDC20262 (FastTrak66/Ultra66) (rev 01)
0000:01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo Banshee (rev 03)


I also tried: $ dmesg | grep eth   and it says:

[  668.084299] Driver 'sd' needs updating - please use bus_type methods


I hope you can help me with this...

---

### Post by tbonius on 2006-09-09
Dmesg is returning info about "eth" in that kernel message as:

[ 668.084299] Driver 'sd' needs updating - please use bus_type m[COLOR="Sienna"]eth[/COLOR]ods

As far as lspci.. it looks like the kernel isnt picking up your ethernet interface.. what type of card is it again?  Maybe we could find the right kernel module for it and get it going?

T

---

### Post by campos on 2006-09-09
Hey, thanks for your reply... well my ethernet card is:

SMC 83C795QF P

C9804

6H81-58-7


That's all it says,

---

### Post by campos on 2006-09-10
somebody please?

---

### Post by campos on 2006-09-11
Hey tbonius can you please help me? :(

---

### Post by engti on 2006-09-11
try going to where ur drivers are located

and typing

*sudo modprobe forcedeth*

that should load the driver

then run

*sudo dhclient eth0*

i have a detailed checklist u can consult, but i can send it to you only after i get home.

Good Luck :)

---

### Post by campos on 2006-09-12
thanks for your reply engti...

can you please send me the "detailed checklist", I will thank you and I will try what you told me.

---

### Post by tbonius on 2006-09-12
detailed checklist?

```
user@host$ sudo lsmod
```

paste output in a reply to this post

```
user@host$ sudo ifconfig -a
```

paste output in a reply to this post

```
user@host$ sudo cat /etc/network/interfaces
```

paste output in a reply to this post

```
user@host$ sudo modprobe forcedeth
user@host$ sudo dhclient eth0
```

paste output in a reply to this post

T

---

