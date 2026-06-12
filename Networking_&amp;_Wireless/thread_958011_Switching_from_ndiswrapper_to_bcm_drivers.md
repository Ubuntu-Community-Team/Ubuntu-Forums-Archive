---
title: "Switching from ndiswrapper to bcm drivers"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by Blue_Alien on 2008-10-24
I would like to switch from ndiswrapper to bcm drivers. The problem is that the computer has no Ethernet port. I have both drivers installed but how do I make the computer use bcm drivers instead?

---

### Post by Ayuthia on 2008-10-24
> **Blue_Alien said:**
> I would like to switch from ndiswrapper to bcm drivers. The problem is that the computer has no Ethernet port. I have both drivers installed but how do I make the computer use bcm drivers instead?

Which version of Ubuntu are you using?  If you are using Hardy or newer, you can try the following:
```
sudo modprobe -r ndiswrapper b43 ssb bcm43xx wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

If you are using Gutsy or older:
```
sudo modprobe -r ndiswrapper bcm43xx
sudo modprobe bcm43xx
sudo ifconfig wlan0 up
sudo iwlist scan
```

This is just a test to see if the bcm43xx/b43 driver is working.

If it does not work, please post the results of the following:
```
lspci -nn
lshw -C network
uname -a
cat /etc/issue.net
```This will help provide more information about what you are using.

---

### Post by Blue_Alien on 2008-10-24
I am using xubuntu 8.04.1 and thanks for the speedy reply.

---

### Post by Blue_Alien on 2008-10-24
When I get to the sudo ifconfig wlan0 up I get the error SIOCSIFFLAGS: No such file or directory

---

### Post by Ayuthia on 2008-10-24
You might try:
sudo ifconfig eth0 up

If that does not work, you can try:
```
sudo /etc/init.d/networking restart
```
I am not for sure which logical name your wireless card is so I was guessing.  Usually it is wlan0 or else eth1.  However, in your case you don't have a wired card so it will most likely default down to eth0.

Hope that helps.

---

### Post by Blue_Alien on 2008-10-25
I tried sudo ifconfig wlan0 up for eth0 and eth1 after sudo /etc/init.d/networking restart but wlan0 gave me the same error and eth0 and eth1 both said ERROR while getting interface flags: No such device. Also my card is BCM4318

---

### Post by Ayuthia on 2008-10-25
I think that I might need a little more information.  Did you install b43-fwcutter?  If you are not sure, can you post the results of:
```
ls /lib/firmware
```There should be a b43 directory in there.

Can you also post your lspci -nn and uname -r results?

---

### Post by Blue_Alien on 2008-10-25
It looks like b43legacy is installed and is highlighted blue but when I had my internet working on it I did install fwcutter in synaptic. I will get those other things in a bit.

---

### Post by Blue_Alien on 2008-10-25
First
```
2.6.24-19-generic     bcm43xx_initval05.fw  bcm43xx_microcode11.fw
b43legacy             bcm43xx_initval06.fw  bcm43xx_microcode2.fw
bcm43xx_initval01.fw  bcm43xx_initval07.fw  bcm43xx_microcode4.fw
bcm43xx_initval02.fw  bcm43xx_initval08.fw  bcm43xx_microcode5.fw
bcm43xx_initval03.fw  bcm43xx_initval09.fw  bcm43xx_pcm4.fw
bcm43xx_initval04.fw  bcm43xx_initval10.fw  bcm43xx_pcm5.fw

```

then
```
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:06.0 Multimedia audio controller [0401]: ESS Technology ES1988 Allegro-1 [125d:1988] (rev 12)
00:06.1 Communication controller [0780]: ESS Technology ESS Modem [125d:1989] (rev 12)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:0a.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev 80)
00:0a.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev 80)
01:00.0 VGA compatible controller [0300]: S3 Inc. 86C270-294 Savage/MX-MV [5333:8c10] (rev 11)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

and last
```
2.6.24-19-generic

```

---

### Post by Ayuthia on 2008-10-25
Ok.  It looks like you are trying to use the bcm43xx driver.  If that is the case, please try:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe bcm43xx
sudo ifconfig wlan0 up
```It might also be eth0.

The information that you posted shows that you have installed the bcm43xx firmware but not the b43 firmware.  However, I don't recall the 4318 card liking the b43 driver in Hardy.

---

### Post by Blue_Alien on 2008-10-25
Hey thank you very much it finally works!

---

### Post by kmolnar on 2008-11-07
Thanks - this worked for me too. Finally free of ndiswrapper! (No offense to Andres Salomon, heh)

---

