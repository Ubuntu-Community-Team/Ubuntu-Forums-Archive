---
title: "Ubuntu Print Server and Windows 7 Client"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by THAAG on 2009-12-01
I have done the following to set up an Ubuntu Print Server:

1.Installed Ubuntu 9.10 on an old Toshiba laptop. Overwrote XP, and Karmic is the dedicated OS. 
2. Connected the laptop (no wireless card) to my wireless router.
3. Connected the HP OfficeJet Pro 8500 All-In-One printer via USB to the Toshiba.
4. Successfully printed test page.

Everything works. Lovely OS. The shared drives on my XP and Win 7 laptops can be recognized on wireless LAN, etc. 

**BUT**

I have downloaded Samba and shared the printer on Ubuntu laptop.

On Win 7:

I cannot connect to the printer on Ubuntu from Win 7 Laptop over the wireless LAN. 
I have uninstalled and re-installed the latest driver.
I tried adding the printer via the add printer dialog. I get error 0x0000000d
When trying to use net use: LPT2: \\servername\printer (using my own parameters) I get system error 66, so I cannot add the printer as a local printer.

The only thing i can think of: Do I need to physoically connect the printer to the Win 7 laptop when I add the printer? Will it be recognized wirelessly after that.

I will try that next, but not optimistic....

Please help!

---

### Post by srt4play on 2009-12-01
The easiest way to do this is to use the generic postscript printer driver that comes with windows.  Set up the printer as an internet printer, the url is going to be something like this if my server is 192.168.1.3 and printer name is lexmark:

[http://192.168.1.3:631/printers/lexmark](http://192.168.1.3:631/printers/lexmark)

Use the print driver MS Publisher Imagesetter, it's in the "generic" manufacturer list.

---

### Post by LowSky on 2009-12-01
use CUPS to set up netowrk printing on the Ubuntu laptop
on the Ubuntu maching go to this address
[http://localhost:631/](http://localhost:631/)

fromthere use the Ubuntu machine admin (sudo account)then share the printer


maybe see this for additional help
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#WindowsXP%20Client%20Machine)

---

