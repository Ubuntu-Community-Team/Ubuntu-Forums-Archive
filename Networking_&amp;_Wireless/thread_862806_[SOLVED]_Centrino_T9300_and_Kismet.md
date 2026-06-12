---
title: "[SOLVED] Centrino T9300 and Kismet"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by MR2Quick on 2008-07-17
I'm trying to run kismet and im unsure which driver i should load for the chipset in the laptop.  The chip is a Centrino T9300 ABGN

I don't know which one it falls under listed from the kismet website:

> ipw2100         Intel/Centrino      Linux       ipw2100-0.44+
                    [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)
                    The Linux IPW2100/Centrino drivers for 802.11b cards
                    now support rfmon, so here's support for them.  They act
                    more or less like any other wireless interface would.

    ipw2200         Intel/Centrino      Linux       ipw2200-1.0.4+
                    [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
                    The Linux IPW2200/Centrino drivers for 802.11bg cards
                    support rfmon as of 1.0.4 and firmware 2.3.  
                    Signal level reporting requires radiotap be turned on
                    in the makefile while compiling the driver.  Noise levels
                    are not reported.

    ipw2915         Intel/Centrino      Linux       ipw2200-1.0.4+
                    [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
                    The Linux IPW2200/Centrino drivers for 802.11bga cards
                    support rfmon as of 1.0.4 and firmware 2.3.  
                    This is the same as ipw2200 but defaults to scanning the
                    802.11a channel range in addition to 802.11b/g.
                    Signal level reporting requires radiotap be turned on
                    in the makefile while compiling the driver.  Noise levels
                    are not reported.

    ipw3945         Intel/Centrino      Linux       ipw3945
                    [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)
                    The Linux IPW3945/Centrino drivers for Intel Core
                    802.11bga cards.

    ipwlivetap      Intel/Centrino      Linux       ipw2200/3945
                    [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
                    [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)
                    The ipw3945 and patched ipw2200 drivers support a 
                    special mode which allows monitor-mode style sniffing
                    while remaining associated.  Channel hopping is not
                    possible, as the card is still associated to a 
                    specific AP, but single-channel IDS and sniffing can
                    be accomplished.  See the ipw driver mailing list
                    archives for information about patching your drivers.

    iwl3945         Intel/Centrino      Linux       iwl3945
                    Intel's new IPW drivers using the mac80211 kernel
                    layer.

    iwl4965         Intel/Centrino      Linux       iwl4965
                    Intel's new IPW drivers using the mac80211 kernel
                    layer.



Any and all help is greatly appreciated!

---

### Post by MR2Quick on 2008-07-18
Found the answer: iwl4965

---

### Post by MR2Quick on 2008-07-21
And just as a heads up to anyone who's interested, this chipset does not allow monitor mode or allow de-auth packet creation.

---

