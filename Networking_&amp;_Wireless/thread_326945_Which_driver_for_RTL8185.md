---
title: "Which driver for RTL8185?"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by _tomcio on 2006-12-28
Hi!

Few days ago I installed wireless card (based on RTL8185) in my PC and I was very happy because Ubuntu 6.10 detected it and it works quite fine. However this card isn't supported well. Like I said it's working, but for example signal strenght isn't detected by system. Moreover it seems, that I'm not able to enable encrypted connection (gnome-tools doesn't provide any options for enabling encryption), maybe I can do it in text mode, but I have no idea ho to configure wireless cards via terminal (if someone can give me howto for it I'll be very happy).

My card is supported bu module r818x .Like I said I doesn't support some features of my card, so maybe it's better for me to use ndiswrapper. Maybe it will work better with my hardware?

---

### Post by balmar on 2006-12-28
> **_tomcio said:**
> Hi!

Few days ago I installed wireless card (based on RTL8185) in my PC and I was very happy because Ubuntu 6.10 detected it and it works quite fine. However this card isn't supported well. Like I said it's working, but for example signal strenght isn't detected by system. Moreover it seems, that I'm not able to enable encrypted connection (gnome-tools doesn't provide any options for enabling encryption), maybe I can do it in text mode, but I have no idea ho to configure wireless cards via terminal (if someone can give me howto for it I'll be very happy).

My card is supported bu module r818x .Like I said I doesn't support some features of my card, so maybe it's better for me to use ndiswrapper. Maybe it will work better with my hardware?

Hi,

I was just finishing typing this up... so maybe my story could help you or others. I have some moderate experience as lunix user, no experience with wireless, and an SMCWPCI-G wireless PCI card. This card comes in two versions of chipsets, Atheros and Realtek 8185, mine has the Realtek 8185. I installed Ubuntu Edgy Eft form the desktop-i386 CD on my PC. It recognized my card right away, and loaded the r818x module for it. Trying to set it up (**access point, mode managed, essid, key** (tried both with WEP encryption and with no encryption at all, both on router and on the PC)), but couldn'd get ip via dhclient. Browsing forums I read about many problems with r818x.

Ok, the other option is [_Ndiswrapper_]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). This card with this chipset is not listed in their [_list_]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"), but I gave it a try. Installed ndiswrapper-common and ndiswrapper-utils-1.18 from the CD, copied the Windows driver form the card's factory CD, loaded it with ndiswrapper. **Ndiswrapper -l** shows hardware present, driver is what it should be from the CD. First surprise: **depmod -a** and then **modprobe ndiswrapper** gives me pages of beeping error messages. (I read somewhere that there is a problem with the Ndiswrapper package on the Edgy Eft CD, but it might have also been incompatibility with the SMC factory driver.)

Ok, replaced the wireless by a wired card, plugged it in the rooter, downloaded Ndiswrapper and compiled it from source. It went fine, I put the wireless card back to the PC, loaded the Windows driver into Ndiswrapper (tried each WIN98, WIN2000, WINME, WINXP), **ndiswrapper -l** seemed ok, then **depmod -a** and **modprobe ndiswrapper**. This time no error messages, but a few seconds after **modprobe ndiswrapper** the whole system freezed out. This happened every time I tried the above drivers. This is kind of OK, since they warn everyone to expect the worst with a driver not yet tested with Ndiswrapper.

Once up there close to the router, I gave one more try to the r818x driver (the one originally set up by Edgy). The miracle happened: it worked! I tried a few times, **ifdown wlan0, ifup wlan0, reboot**, it always came back safely, and worked fine.

I took the machine back to its place (one floor and one room away), again no wireless connection. Sometimes it saw the wireless via **iwlist wlan0 scan**, but couldn't get dhclient working. I turned the machine so that the case itself was not between the card's antenna and the router. Once I got dhclient ok, but many times I didn't. At the same time a Windows laptop close to my machine showed 4 bars and good connection to the same network.

It turned out that the wireless router was not as difficult to move as I first thought, so I took it close to, but in front of the machine, still no luck with dhclient. I could only make the wireless work when the router was on the side or behind the machine, so that the router could clearly see the antenna.

I don't know if it's the card's weak performance or the r818x driver, but this stuff proved to be practically useless for a desktop PC in the corner of the room. I ended up taking out the wireless card and proceeding with the old-fashioned wired ethernet card.

I hope this might help, and also I'd be curious to find out if this weak performance is normal for a wireless card in a tower, the card was weak, or the r818x driver was not working perfectly...

---

### Post by _tomcio on 2006-12-28
Well, I think I won't try to instal ndiswrapper :p 

I found this driver: [http://rtl8180-sa2400.sourceforge.net/]("http://rtl8180-sa2400.sourceforge.net/")  and I downloaded the newest snapshot from CVS, which (like we can read on main page) should support RTL8185 based cards.

Now the most funny thing. I run 'make' in this folder, but it didn't compile anything it onle removed all files?! See:
```
**tomek@tomcio-desktop:~/Linux/Sterwoniki/wifi/rtl818x-newstack$ ls**
a                  LICENSE        r8180_hw.h       r8180_rtl8255.h
AUTHORS            Makefile       r8180_max2820.c  r8180_sa2400.c
CHANGES            r8180_93cx6.c  r8180_max2820.h  r8180_sa2400.h
COPYING            r8180_93cx6.h  r8180_pm.c       r8180_wx.c
CVS                r8180_core.c   r8180_pm.h       r8180_wx.h
ieee80211_crypt.h  r8180_gct.c    r8180_rtl8225.c  README
ieee80211.h        r8180_gct.h    r8180_rtl8225.h  README.adhoc
INSTALL            r8180.h        r8180_rtl8255.c  README.master
**tomek@tomcio-desktop:~/Linux/Sterwoniki/wifi/rtl818x-newstack$ make**
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/tomek/Linux/Sterwoniki/wifi/rtl818x-newstack MODVERDIR=/home/tomek/Linux/Sterwoniki/wifi/rtl818x-newstack modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.17-10-386'
rm: nie mo&#380;na usun&#261;&#263; `/home/tomek/Linux/Sterwoniki/wifi/rtl818x-newstack/CVS': Is a directory
make[1]: *** [crmodverdir] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.17-10-386'
make: *** [modules] B&#322;&#261;d 2
**tomek@tomcio-desktop:~/Linux/Sterwoniki/wifi/rtl818x-newstack$ ls**
CVS
tomek@tomcio-desktop:~/Linux/Sterwoniki/wifi/rtl818x-newstack$ 

```

Any idea how to fix it?! Maybe it's driver's author mstake?

---

### Post by luke411 on 2007-04-20
The driver is blacklisted in /etc/modprobe.d/blacklist file. I uncommented those two lines, that list the drivers and rebooted and my pc suddenly found the card. I cannot however, connect. I can see my AP with KWIFI Manager and the network settings allow me to set my ESSID and all of that but when I do, the network icon shows disconnected and nothing is on line.

---

### Post by svega85 on 2007-04-22
> **luke411 said:**
> The driver is blacklisted in /etc/modprobe.d/blacklist file. I uncommented those two lines, that list the drivers and rebooted and my pc suddenly found the card. I cannot however, connect. I can see my AP with KWIFI Manager and the network settings allow me to set my ESSID and all of that but when I do, the network icon shows disconnected and nothing is on line.

i un-blacklisted and mine looks like it works but only with wep not wpa

---

