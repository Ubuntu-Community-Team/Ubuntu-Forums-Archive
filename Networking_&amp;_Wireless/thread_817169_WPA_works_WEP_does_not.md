---
title: "WPA works WEP does not?"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Mackintire on 2008-06-03
Hello all,

I 'm a bit of a noob so please bare with me.

I have a HP 8510P notebook (santarose chipset) with a 4965agn wireless card. I can connect to any unencypted site or any WPA/WPA2 location without issue. However I can not connect to any accesspoint using WEP? I can see WEP accesspoints but they never connect.
 
 Yes I am using iwlwifi and the default network manager.

Any ideas?



A second question is does anyone know if the iwlwifi driver has been updated so that the wireless light works on Notebooks under Ubuntu 8.04? I saw over at the Gentoo forums that they are waiting for that driver to show up in the respositories. Is that true here too?

---

### Post by SpaceCowboyMA on 2008-06-03
Would be interested if you learn of any fix.  I have same issue with a Broadcom:

[FONT="System"][SIZE="1"]$ lspci -vvn |grep 43 -A7
0c:00.0 0280: 14e4:4312 (rev 01)
	Subsystem: 1028:0007
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f9ffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
$ lsmod | grep b43
b43                   115104  0 
rfkill                  8592  2 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    32260  1 b43
$[/SIZE][/FONT]

I've seen some posts pointing the finger at the kernel but as this was a fresh Hardy install I have no old kernels to boot to.  Mine is 2.6.24-16-generic.  I can connect fine to open and WPA APs but with WEP get some message about authentication and I never get an ip address from dhcp.  I can bounce between associated and not on any WEP AP as long as I keep entering the passphrase:

[FONT="System"][SIZE="1"]Jun  2 14:22:14 ullt kernel: [  658.052154] wlan0: Initial auth_alg=0
Jun  2 14:22:14 ullt kernel: [  658.052169] wlan0: authenticate with AP 00:15:63:23:e2:b0
Jun  2 14:22:14 ullt kernel: [  658.052206] wlan0: Initial auth_alg=0
Jun  2 14:22:14 ullt kernel: [  658.052211] wlan0: authenticate with AP 00:15:63:23:e2:b0
Jun  2 14:22:14 ullt kernel: [  658.056885] wlan0: RX authentication from 00:15:63:23:e2:b0 (alg=0 transaction=2 status=0)
Jun  2 14:22:14 ullt kernel: [  658.056896] wlan0: authenticated
Jun  2 14:22:14 ullt kernel: [  658.056901] wlan0: associate with AP 00:15:63:23:e2:b0
Jun  2 14:22:14 ullt kernel: [  658.058175] wlan0: authentication frame received from 00:15:63:23:e2:b0, but not in authenticate state - ignored
Jun  2 14:22:14 ullt kernel: [  658.060417] wlan0: RX ReassocResp from 00:15:63:23:e2:b0 (capab=0x431 status=0 aid=139)
Jun  2 14:22:14 ullt kernel: [  658.060427] wlan0: associated
Jun  2 14:22:14 ullt kernel: [  658.060435] wlan0: switched to short barker preamble (BSSID=00:15:63:23:e2:b0)
Jun  2 14:22:14 ullt kernel: [  658.060511] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Jun  2 14:22:14 ullt kernel: [  658.060518] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Jun  2 14:22:14 ullt kernel: [  658.060523] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Jun  2 14:22:14 ullt kernel: [  658.060529] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Jun  2 14:23:01 ullt kernel: [  672.895822] wlan0: deauthenticate(reason=3)
Jun  2 14:23:19 ullt kernel: [  679.123857] wlan0: Initial auth_alg=0
Jun  2 14:23:19 ullt kernel: [  679.123868] wlan0: authenticate with AP 00:15:63:23:e2:b0
Jun  2 14:23:19 ullt kernel: [  679.124266] wlan0: Initial auth_alg=0
Jun  2 14:23:19 ullt kernel: [  679.124272] wlan0: authenticate with AP 00:15:63:23:e2:b0
Jun  2 14:23:19 ullt kernel: [  679.126092] wlan0: RX authentication from 00:15:63:23:e2:b0 (alg=0 transaction=2 status=0)
Jun  2 14:23:19 ullt kernel: [  679.126101] wlan0: authenticated
Jun  2 14:23:19 ullt kernel: [  679.126106] wlan0: associate with AP 00:15:63:23:e2:b0
Jun  2 14:23:19 ullt kernel: [  679.130060] wlan0: authentication frame received from 00:15:63:23:e2:b0, but not in authenticate state - ignored
Jun  2 14:23:19 ullt kernel: [  679.135310] wlan0: RX ReassocResp from 00:15:63:23:e2:b0 (capab=0x431 status=0 aid=140)
Jun  2 14:23:19 ullt kernel: [  679.135320] wlan0: associated
Jun  2 14:23:19 ullt kernel: [  679.135330] wlan0: switched to short barker preamble (BSSID=00:15:63:23:e2:b0)
Jun  2 14:23:19 ullt kernel: [  679.135413] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
Jun  2 14:23:19 ullt kernel: [  679.135419] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
Jun  2 14:23:19 ullt kernel: [  679.135425] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
Jun  2 14:23:19 ullt kernel: [  679.135431] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
Jun  2 14:24:08 ullt kernel: [  695.576147] wlan0: deauthenticate(reason=3)
...
[/SIZE][/FONT]

---

