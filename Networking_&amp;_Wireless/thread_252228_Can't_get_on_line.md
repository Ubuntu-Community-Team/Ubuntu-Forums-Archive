---
title: "Can't get on line"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by CraftyCathy on 2006-09-06
Can some one please help me get on line. I can not figure out how to set every thing up. Don't know the 1st thing about it. 

I have Dapper Drake 6.06. Need to set up to go on line with a modem. 

Thank you... Cathy](*,)

---

### Post by meng on 2006-09-06
There are different sorts of modems. Perhaps you could let us know the make and model.

---

### Post by CraftyCathy on 2006-09-06
I don't know the make and model of the modem. It was in the computer when I got it. How would I find this out?

---

### Post by meng on 2006-09-06
Okay then I'm going to assume this is a PCI internal modem; you would plug a telephone line cord into that. In a terminal, type
lspci
and please post the output here. I don't know how to set up this sort of modem, but someone else might.

---

### Post by CraftyCathy on 2006-09-06
Post the output? Don't know what that is. Yes, its a modem you plug the phone line into.

---

### Post by meng on 2006-09-06
By post the output I mean, get the output and put it in a post on this forum so that others can see it. Granted, this is a little tricky on a machine that doesn't have other internet access. If you have a USB flash drive, you could do the following:

lspci > ~/Desktop/pci.txt

then a file called pci.txt should appear on your desktop (containing the output of - that is, the computer's response to - the command lspci). Drag it onto your USB drive then you can you your other computer to paste the contents of the file onto a post in this thread.

The alternative is for you to look through the computer's response to the command "lspci" and find for yourself the reference to a modem device. I'll leave it up to you.

---

### Post by CraftyCathy on 2006-09-11
Went to Applications/assessories/terminal. Typed in Ispci. This is what I got.

Bash:Ispci: Command not found.

I have been doing more searching and I think I have what you were asking for. 

HP Pavilion 8754C
V.90 56K PCI Modem
Cheetah
Supports V.90 & K56 Flex
Chipset Intel 810E

Let me know if this is what your needing to know.

---

### Post by tbonius on 2006-09-11
The are asking for [COLOR="DarkRed"]L[/COLOR]SPCI.. not [COLOR="DarkRed"]I[/COLOR]SPCI (in lower case letters)

lspci lists the detected PCI cards on your computer.  See what it spits back to find out of Linux detected the modem.

T

---

### Post by carontis on 2006-09-11
On that kind of pc I know are mounted two different types of internal modem: 
a Conexant and an Intel. You could try to open the pc and watch inside on a chip what is. I think it could be the best way to know more.

---

### Post by CraftyCathy on 2006-09-11
Ok, now that I typed in the correct letters, results came up... I had to copy this all by hand. I have Linux on another hard drive on here. I have to restart each time to go to each of them. Hope I did not make any mistakes.

0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory controller Hub] (rev 03)

0000:00:01.0 VGA Compatible controller:Intel Corporation 82810E DC-133 [Chipset Graphic Controller] (rev 03)

0000:00:1e.0 PCI bridge:Intel Corporation 82801AA PCI Bridge (rev 02)

0000:00:1f.0 ISA bridge:Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)

0000:00:1f.1 IDE Interface: Intel Corporation 82801AA IDE (rev 02)

0000:00:1f.2 UBC Controller: Intel Corporation 82801AA USB (rev 02)

0000:00:1f.3 MSBus: Intel Corporation 82801AA SMBUS (rev 02)

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA  AC'97 Audio (rev 02)

0000:01:09.0 Communication Controller: Agere System LT WinModem

0000:01:0a.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)

---

### Post by tbonius on 2006-09-12
0000:01:09.0 Communication Controller: Agere System LT WinModem

Ok.. so your modem shows up.. does it show up in your "Networking" menu?

Thom

---

### Post by CraftyCathy on 2006-09-12
Ok.. where would that be located?

---

### Post by CraftyCathy on 2006-09-12
And by the way, I have not seen that name before on here. I have had this computer for ?? years and first time I seen that name.

---

### Post by tbonius on 2006-09-12
What name are you referring to ..? The Agere Winmodem?  They are pretty common on most laptops.  If you are not sure where your Network Configuration utility is.. I suggest clicking around in the menus alot more.. and getting comfortable with the system before asking questions about where something is located.. considering it is harder to find the Ubuntu support forums than it is to find the Administrative Tools in Ubuntu.  I am not trying to be rude.. but it is a helpful suggestion.

T

---

