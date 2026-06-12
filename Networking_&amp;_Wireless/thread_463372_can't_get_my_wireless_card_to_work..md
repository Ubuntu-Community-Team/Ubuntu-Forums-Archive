---
title: "can't get my wireless card to work."
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by lhamil64 on 2007-06-03
Hey i am running ubuntu 6.06 on a laptop that was just laying around the house.

anyway, i have a wireless card that worked on windows (once i installed the drivers lol) but it won't let me on the internet on linux.  the two lights on it blink the same way that they blinked when it was connected with windows. i looked up my wireless card in the list that is stickied there and i copied the links and stuff from all the entries about my card

ill post the model number later i don't have it with me right now.

---

### Post by gunbladeiv on 2007-06-03
can you give me your wireless device name?

---

### Post by linux noooob on 2007-06-03
try madwifi (if you have any problems ask because i have had all of them and resolved them).
sorry for the crappy spelling

---

### Post by lhamil64 on 2007-06-04
ok i found the card LOL

the model is:

D-Link
DWL-G630

if you need any more info just ask

---

### Post by stchman on 2007-06-04
> **lhamil64 said:**
> ok i found the card LOL

the model is:

D-Link
DWL-G630

if you need any more info just ask

Give us an lspci output.  The DWL-G630 used several different chipsets.  It could be a TI, an Atheros , a Broadcom, etc.

---

### Post by lhamil64 on 2007-06-04
can you tell me how to do that LOL

---

### Post by super hawk on 2007-06-04
Start up Ubuntu, go into Programs - Accessories - Terminal and type "lspci" (No quotation marks), copy the output to as text document, log on to Windows/Mac/other operating system on computer with internet access and post the contents.

---

### Post by gunbladeiv on 2007-06-04
> **lhamil64 said:**
> can you tell me how to do that LOL

do command lspci at your konsole/terminal.  Then you'll see all your pci devices.paste it here so that we can help you.

---

### Post by lhamil64 on 2007-06-05
ok here is what i got when i typed it in:
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
0000:00:09.0 Communication controller: Agere Systems WinModem 56k (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
0000:02:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)


hopefully i didn't mess something up (i have to hook up a seperate eithernet adapter card to get on the internet with an eithernet cable)

---

### Post by stchman on 2007-06-06
> **lhamil64 said:**
> ok here is what i got when i typed it in:
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
0000:00:09.0 Communication controller: Agere Systems WinModem 56k (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
0000:02:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)


hopefully i didn't mess something up (i have to hook up a seperate eithernet adapter card to get on the internet with an eithernet cable)

Ok you have a Atheros wireless card.  You have a couple of options.

1.  Install Feisty.  Feisty supports Atheros out of the box with restricted drivers.
2.  Install the madwifi drivers.  Use my procedure to do it here [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

The madwifi drivers worked on my laptop running Edgy.  When I upgraded to Feisty the card worked out of the box.

The procedure I have also has a script that does everything you need to.  Make sure you run the script in a root terminal.  The script also install network manager as well.  The script will reboot the PC for you.

This should work.

---

