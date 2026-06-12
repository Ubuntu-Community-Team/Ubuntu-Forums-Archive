---
title: "Trying to get a 3Com PCMCIA modem to work"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by poltr1 on 2008-03-19
I have a 3Com 3CXEM556B PCMCIA modem/LAN card that I'm trying to use on a Dell Latitude CPxJ650GT laptop running Gutsy.  I plug the card in and the green LED on the edge of the card lights up, so I'm guessing the hardware is detected.

I tried using the scanModem utility and couldn't figure out its outputs.  I tried running *sudo wvdialconf /etc/wvdial.conf* and it couldn't find the modem.  I also tried running cardctl but it couldn't find the command.

I already have the card's drivers which I found on the 3Com web site, but no idea as to how to install them.

I'm also looking for cardctl, since it wasn't in /sbin.

Any help would be appreciated.

---

### Post by gordintoronto on 2008-03-21
Scanmodem creates a folder called Modem, and a file called ModemData.txt within the folder.  The first line of this should identify your modem.  Since you already know what type of modem it is, the only relevance of the scanModem output is to confirm that the card is visible to the computer.

Re driver installation: According to another post:
the file

3CXEM556.cis

has to be installed in /lib/3CXEM556.cis.

By the way, the only thing I found on the 3Com web site was Windows drivers.

I don't think you can do anything with wvdial until the driver is installed.

Good luck,
Gord

> **poltr1 said:**
> I have a 3Com 3CXEM556B PCMCIA modem/LAN card that I'm trying to use on a Dell Latitude CPxJ650GT laptop running Gutsy.  I plug the card in and the green LED on the edge of the card lights up, so I'm guessing the hardware is detected.

I tried using the scanModem utility and couldn't figure out its outputs.  I tried running *sudo wvdialconf /etc/wvdial.conf* and it couldn't find the modem.  I also tried running cardctl but it couldn't find the command.

I already have the card's drivers which I found on the 3Com web site, but no idea as to how to install them.

I'm also looking for cardctl, since it wasn't in /sbin.

Any help would be appreciated.

---

### Post by poltr1 on 2008-03-26
Thanks, gordintoronto.  I looked through ModemData.txt, and  I couldn't find anything in there that said the modem was detected by scanModem.  Which is puzzling, because pccardctl finds it when it's plugged in.  :confused:

Script started on Sat 22 Mar 2008 03:56:45 PM EDT
jim@tardis:~$ pccardctl ident
Socket 0:
  no product info available
Socket 1:
  product info: "3Com", "Megahertz 3CXEM556 B", "LAN + 56k Modem", ""
  manfid: 0x0101, 0x0035
  function: 6 (network)
jim@tardis:~$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="3Com"
PRODID_2="Megahertz 3CXEM556 B"
PRODID_3="LAN + 56k Modem"
PRODID_4=""
MANFID=0101,0035
FUNCID=6
jim@tardis:~$ exit

Script done on Sat 22 Mar 2008 03:57:10 PM EDT

I'm not sure where to find 3CXEM556.cis; that file wasn't contained in the
driver files I downloaded from 3Com's web site (which, as you mentioned, are probably for DOS and Windows).  

I also read someplace -- David Hinds' list, perhaps? -- that the 3c589_cs driver should work on this card.  (I only plan to use the modem part; I don't have the connector for the LAN part.)  But again, I couldn't find the how-to to install that driver.

---

