---
title: "Worked! rt61 WPAPSK on kernel 2.6.18"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by WatsonJX on 2006-11-01
Driver:  rt61-cvs-2006102914 legacy
Kernel:  2.6.18 no SMP, no PREEMPT
Card:    Airlink101 AWLH3026 PCI
0000:00:09.0 Network controller: RaLink: Unknown device 0301
AP:      D-link DI-524

One tiny typo to fix:

rtmp_info.c:
RTMPWPAAddKeyProc()

line 3525:
// 1. Check BSSID, if not current BSSID or Bcast, return NDIS_STATUS_FAILURE
if ((memcmp(pKey->BSSID, BROADCAST_ADDR, ETH_ALEN) != 0) &&
(memcmp(pKey->BSSID, pAd->PortCfg.Bssid, ETH_ALEN) == 0))
return(NDIS_STATUS_FAILURE);

The test for second memcmp() should be '!='. 

Then build the module: make, make install as usual.

Put following in /etc/network/interfaces

# the wireless interface
iface ra0 inet dhcp
pre-up iwconfig ra0 essid Your-AP
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="yourpassphrase"
pre-up iwpriv ra0 set TxRate=0

put in your /etc/modprobe.d/alias
alias ra0 rt61

Then ifup ra0 can bring it up.

Have fun.

---

### Post by layl on 2006-11-02
1. which release ? Dapper ?Edgy ?
2. can You please post content of /etc/Wireless/RTA61STA/rta61sta.dat ?
3. did You play in any manner with wpa_supplicant ?  or not ? what version of wpa_supplicant do You have (no matter what release)

---

### Post by WatsonJX on 2006-11-02
1. which release ? Dapper ?Edgy ?

It worked on Dapper, and still works after dist-upgrade to Edgy.
The kernel matters. I compiled 2.6.18 vanilla, No SMP, no PREEMPT. Distro doesn't matter much. 2.6.19-rc3 has new WIRELESS_EXT v21 and probably doesn't work.

2. can You please post content of /etc/Wireless/RTA61STA/rta61sta.dat ?

I get this following the download link on rt2400.sf.net. Didn't change anything in it. My machine is off I am unable to post it here.

3. did You play in any manner with wpa_supplicant ? or not ? what version of wpa_supplicant do You have (no matter what release)

No. WPAPSK is good enough for my home use. No need to trouble myself with 802.1X supplicant.

---

