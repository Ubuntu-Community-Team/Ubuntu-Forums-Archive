---
title: "RT2500 and Ubuntu (Not The Usual...)"
date: 2005-08-06
forum: Networking &amp; Wireless
---

### Post by ThePotato on 2005-08-06
Okay,
So I've found the excellent SerialMonkey drivers and Ubuntu Howto's located [Here](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page) and [Here](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/) respectively.  Now, I have a slightly different question to the usual.

My PC is upstairs in my bedroom, safely ensconsed in it's little area.  I have a MSI PC54G2 card with the above named chipset which connects me to the wireless router downstairs.  This allows me to use my laptop around the house too (which is currently away, making life a tad harder).  So, I have a spare 40GB drive sat in my PC and I'd like to install Ubuntu on it.  No worries.  However, off the bat of course, it won't detect my wireless card, hence the need for the drivers.  In the Howto, I need to 'apt-get' a fair few things, which of course, without a working internet connection, I can't do.  I have looked for the relevent .deb packages online and downloaded them from the Debian website (as I believe that Ubuntu is a derivitive of Debian), and burnt them to a CD.  I'd like to know two things:  A) If I have all the correct ones and B) Where to put them when Ubuntu is installed so that I can reference them properly as per the Howto.  If anyone can help with this, and perhaps give me a slightly re-jigged Howto to show and example of the new commands, I'd be most grateful.

PACKAGES:

1) kdebase_3.3.2-1_all.deb
2) libqt3-dev_3.3.4-3_amd64.deb
3) linux-headers-2.6.12-1-amd64-generic_2.6.12-1_amd64.deb
4) qt3-dev-tools_3.3.4-3_amd64.deb
5) And of course the drivers: rt2500-cvs-daily.tar.gz

---

