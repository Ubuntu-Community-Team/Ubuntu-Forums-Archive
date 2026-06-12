---
title: "NIC not detected on install, can't get to work on boot"
date: 2005-05-10
forum: Networking &amp; Wireless
---

### Post by BillWarren on 2005-05-10
Hi, I'm new to Ubuntu and really look forward to using a reportedly great Debian distro.  I can't get my NIC going.  I've read a number of the threads here, but I think my problem is at a lower level.

The network card is not detected during the install of 5.04, so I proceeded without it reading somewhere that someone got it working after install.

On boot, I have tried the following:

"lspci -v" gives no mention of a network card.

"lsmod" doesn't give any entry that appears NIC related, though I don't know exactly what I'm looking for.

I manually added eth0 to the /etc/network/interfaces file, but "sudo ifup eth0" gives what I'm guessing is the most telling error:
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
<same error repeated>
Bind socket to interface: No such device

The LiveCD (also 5.04) also does not recognize the card.  The card was recognized by Mandrake 10.1 and Libranet 2.8.1, as well as BeOS 1.1DevEd.  I want Ubuntu b/c it's debian based (my intro was Fink's use of dselect for MacOSX), it's up to date (unlike the free version of Libranet), and I don't want to run Windoze (we're mostly a mac OS X outfit).

Relevant Specs:
Dell Dimension XPS R400 (P2 400MHz)
As far as I know it's the stock NIC, though I inherited the machine. (Dell's service tag configuration details didn't appear to yield helpful NIC data)

Should I try Warty?  Seems like a number of posts indicated their eth0 had problems only after upgrading.

---

### Post by BillWarren on 2005-05-10
Follow-up:

I just reinstalled Libranet 2.8.1, and the Ethernet module being used is "ne" - ISA NE2000/NE1000

---

### Post by tonym on 2005-05-11
I also had problems getting Ubuntu to pick up my network card, although the Live CD was OK.  Assuming "ne" is the correct module try adding it to your /etc/modules file.

Or to test:

modprobe ne
/etc/init.d/networking restart          ( or is it "network" - not at a Linux machine so can't check).

If you reinstall,  at the stage when the installer is about to search for the network use alt/f2 to switch to another console and "modprobe ne".  Switch back to the installer and contunue.

---

### Post by BillWarren on 2005-05-11
[QUOTE=tonym]Assuming "ne" is the correct module try adding it to your /etc/modules file.

If you reinstall,  at the stage when the installer is about to search for the network use alt/f2 to switch to another console and "modprobe ne".  Switch back to the installer and contunue.[/QUOTE]

I did both these things, and now it works.  THANK YOU!

---

### Post by Fugee on 2005-06-20
[QUOTE=tonym]
If you reinstall,  at the stage when the installer is about to search for the network use alt/f2 to switch to another console and "modprobe ne".  Switch back to the installer and contunue.[/QUOTE]
I tried  that and it works like a charm. Except now I have only one problem. I have to open a terminal and type "modprobe ne" everytime I boot up to get network connectivity. Is there any way to make sure it connects without having to manually connect everytime?

---

### Post by 1sy8 on 2005-06-20
Just add ne at the end of your /etc/modules file .. Hope this helps !

---

