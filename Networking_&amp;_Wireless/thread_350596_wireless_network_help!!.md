---
title: "wireless network help!!"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by thewhiteguy1 on 2007-01-31
i have a linksys wrt54ab wireless card in an older toshiba laptop running 6.06. It finds the wireless card 
[img]http://img363.imageshack.us/img363/5549/screenshotpw9.jpg[/img]
and i put in my wireless key...and its DHCP...
[img]http://img257.imageshack.us/img257/4966/screenshot1gc5.png[/img]
but yet its not connecting to the internet?? what am i doing wrong?

---

### Post by tturrisi on 2007-01-31
HEXADECIMAL, not Plain

---

### Post by thewhiteguy1 on 2007-02-01
umm thankyou.. but it didnt work.. its still not connecting to the internet...

---

### Post by mr4thjuly on 2007-02-01
Post the file named "interfaces" located in /etc/network. I don't think it is possible to reply to your post without reading the contents of that file.
Also post the output of lspci here

---

### Post by thewhiteguy1 on 2007-02-01
this is what the file

etc/network/interfaces says

# The loopback network interface 
auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-essid Snowman
wireless-key **********

auto ath0

---

### Post by thewhiteguy1 on 2007-02-01
oem@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:07.0 Communication controller: Agere Systems 56k WinModem (rev 01)
0000:00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
0000:00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)0000:02:00.0 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)


thats the lspci!

---

### Post by thewhiteguy1 on 2007-02-02
bump i need to get the wireless working

someone please help!!

---

### Post by tturrisi on 2007-02-02
I assume the security being used is WEP.
Net-admin only aupports WEP, not WPA.
Try using a hyphen after every 4 hex characters:
1234-5678-90

---

### Post by thewhiteguy1 on 2007-02-02
woohoo thanks alot that helped and it now works!!!

---

### Post by tturrisi on 2007-02-02
thewhiteguyWON!

---

