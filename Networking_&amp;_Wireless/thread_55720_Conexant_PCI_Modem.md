---
title: "Conexant PCI Modem?"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by kingducttape on 2005-08-10
Hello,
Today I was setting up Ubuntu on my girlfriend's computer (an old Dell Dimension 2100). I picked Ubuntu since I am a Debian nut (apt-get addict) and I've had good luck in the past getting Ubuntu onto some pretty bizarre hardware with almost no snags. (I love it on my iBook!) The only snag I hit today was with the modem.

The modem itself is a Conexant HCF 56k data/fax, and looks to be from around '99. When I ran the installer, it didn't detect any network hardware at all, and I ended up just skipping that part and fixing the hosts file with the system name mapped to 127.0.0.1 so that everything would run fine. When we tried to set up the modem, autodetect again failed. Using /dev/modem as the port, we couldn't activate the interface at all, and using other items in the list, it would activate instantly, but never really do anything (such as dial).

I can't claim to be an expert on modems under Linux -- almost all of the boxes I've set up were net installs over ethernet cards. In browsing the forums I've heard the term "Winmodem" tossed around. Assuming that's a 'doze only modem? If this modem will indeed run under Ubuntu, what do I need to do to get it set up? (there's no way to get internet on this machine, but I can transfer drivers to it via floppy or CD).

Thanks in advance!

---

### Post by jasmuz on 2005-08-10
Winmodems in Linux are quite tricky, but feel these links out:

[https://wiki.ubuntu.com/BinaryDriverHowto/SmartLinkModem](https://wiki.ubuntu.com/BinaryDriverHowto/SmartLinkModem)

[http://linmodems.org/](http://linmodems.org/)

---

### Post by kingducttape on 2005-08-10
Figured it out! It is indeed a Winmodem, and a site called [Linuxant](http://www.linuxant.com/) has drivers for Conexant HSF and HCF modems. Not ideal, as to get more than 1.4kbit speeds you need to buy a license, since they had to pay Conexant to license their proprietary code (unfortunate reality it is), but it'll get the job done.

EDIT: Whups, that's 14.4Kbps, not 1.4! Now THAT's a slow modem! :)

---

