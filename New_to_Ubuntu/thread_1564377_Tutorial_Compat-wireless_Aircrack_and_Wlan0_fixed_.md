---
title: "Tutorial Compat-wireless Aircrack and Wlan0 fixed permanently on channel -1"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by Tracy177 on 2010-08-30
This tutorial is for people who have got wireless card with  chip supported by compat-wireless there for the last few months was an issue with compat-wireless and wlan0 mon0 being fixed on channel -1.

i have ubuntu 10.10 and kernel 2.6.35.19 but i tested it also on 2.6.34 and 2.6.32

i will try to explain how to do it if u have like me zd1211 chip 




download latest compat from [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

 [COLOR=Red]next u need is patch for zd1211[/COLOR]

--- drivers/net/wireless/zd1211rw/zd_mac.c   2010-01-12 18:24:21.000000000 +0200
+++ drivers/net/wireless/zd1211rw/zd_mac.c   2010-01-12 18:41:21.000000000 +0200
@@ -220,14 +220,19 @@ void zd_mac_clear(struct zd_mac *mac)
 static int set_rx_filter(struct zd_mac *mac)
 {
    unsigned long flags;
-   u32 filter = STA_RX_FILTER;
+   struct zd_ioreq32 ioreqs[] = {
+      {CR_RX_FILTER, STA_RX_FILTER},
+      { CR_SNIFFER_ON, 0U },
+   };
 
    spin_lock_irqsave(&mac->lock, flags);
-   if (mac->pass_ctrl)
-      filter |= RX_FILTER_CTRL;
+   if (mac->pass_ctrl) {
+      ioreqs[0].value |= 0xFFFFFFFF;
+      ioreqs[1].value = 0x1;
+   }
    spin_unlock_irqrestore(&mac->lock, flags);
 
-   return zd_iowrite32(&mac->chip, CR_RX_FILTER, filter);
+   return zd_iowrite32a(&mac->chip, ioreqs, ARRAY_SIZE(ioreqs));
 }
 
 static int set_mc_hash(struct zd_mac *mac)
@@ -814,7 +819,8 @@ int zd_mac_rx(struct ieee80211_hw *hw, c
    /* Caller has to ensure that length >= sizeof(struct rx_status). */
    status = (struct rx_status *)
       (buffer + (length - sizeof(struct rx_status)));
-   if (status->frame_status & ZD_RX_ERROR) {
+   if ((status->frame_status & ZD_RX_ERROR) || 
+      (status->frame_status & ~0x21)) {
       if (mac->pass_failed_fcs &&
             (status->frame_status & ZD_RX_CRC32_ERROR)) {
          stats.flag |= RX_FLAG_FAILED_FCS_CRC;
@@ -827,7 +833,8 @@ int zd_mac_rx(struct ieee80211_hw *hw, c
    stats.freq = zd_channels[_zd_chip_get_channel(&mac->chip) - 1].center_freq;
    stats.band = IEEE80211_BAND_2GHZ;
    stats.signal = status->signal_strength;
-
+   stats.signal = stats.signal - 90;
+   
    rate = zd_rx_rate(buffer, status);
 
    /* todo: return index in the big switches in zd_rx_rate instead */
@@ -1154,7 +1161,7 @@ struct ieee80211_hw *zd_mac_alloc_hw(str
    hw->wiphy->bands[IEEE80211_BAND_2GHZ] = &mac->band;
 
    hw->flags = IEEE80211_HW_RX_INCLUDES_FCS |
-          IEEE80211_HW_SIGNAL_UNSPEC;
+          IEEE80211_HW_SIGNAL_DBM;
 
    hw->wiphy->interface_modes =
       BIT(NL80211_IFTYPE_MESH_POINT) |


[COLOR=Red]next patch u need is mac patch:[/COLOR]

diff --git a/net/mac80211/tx.c b/net/mac80211/tx.c
index 0855cac..221bed6 100644
--- a/net/mac80211/tx.c
+++ b/net/mac80211/tx.c
@@ -677,11 +677,19 @@ int tid;
 
    /*
     * Packet injection may want to control the sequence
-    * number, if we have no matching interface then we
-    * neither assign one ourselves nor ask the driver to.
+    * number, so if an injected packet is found, skip
+    * renumbering it. Also make the packet NO_ACK to avoid
+    * excessive retries (ACKing and retrying should be
+    * handled by the injecting application).
+    * FIXME This may break hostapd and some other injectors.
+    * This should be done using a radiotap flag.
     */
-   if (unlikely(info->control.vif->type == NL80211_IFTYPE_MONITOR))
+   if (unlikely((info->flags & IEEE80211_TX_CTL_INJECTED) &&
+      !(tx->sdata->u.mntr_flags & MONITOR_FLAG_COOK_FRAMES))) {
+      if (!ieee80211_has_morefrags(hdr->frame_control))
+         info->flags |= IEEE80211_TX_CTL_NO_ACK;
       return TX_CONTINUE;
+   }
 
    if (unlikely(ieee80211_is_ctl(hdr->frame_control)))
       return TX_CONTINUE;


[COLOR=Red]next u need is this patch[/COLOR] 

commit fffd6e63ea75850dafbf2ccfb38a4189f43c0282
Author: Maxim Levitsky <maximlevitsky@xxxxxxxxx>
Date:   Tue Jun 1 15:43:21 2010 +0300

    wireless: allow to retrieve the channel set on monitor interface
    
    This will allow to preserve compatibility with userspace
    
    Signed-off-by: Maxim Levitsky <maximlevitsky@xxxxxxxxx>

diff --git a/net/wireless/chan.c b/net/wireless/chan.c
index b01a6f6..09d979b 100644
--- a/net/wireless/chan.c
+++ b/net/wireless/chan.c
@@ -49,9 +49,12 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev,
 {
    struct ieee80211_channel *chan;
    int result;
+   struct wireless_dev *mon_dev = NULL;
 
-   if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR)
+   if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR) {
+      mon_dev = wdev;
       wdev = NULL;
+   }
 
    if (wdev) {
       ASSERT_WDEV_LOCK(wdev);
@@ -76,5 +79,8 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev,
    if (wdev)
       wdev->channel = chan;
 
+   if (mon_dev)
+      mon_dev->channel = chan;
+
    return 0;
 }

------------------------------------------------------------------------------------------

now  copy those patches to your compat directory save as a text file name it whatever u want to i named it first one x second one c and  third one d 

cd compat directory 

and apply it by first one;   patch -Np0 -i x
second one;                       patch -Np1 -i c
and third;                            patch -Np1 -i d

everything should be ok nothing will fail. 

next step make and sudo make install after it finished 
still from compat directory sudo make wlunload and sudo make btunload 
than modprobe zd1211rw or whatever card u have and test it airmon-ng start wlan0(or whatever u got)
aireplay-ng -9 mon0 
and airodump-ng mon0 u wont see anymore channel being fixed on -1 

tested on 2.6.35 tested ok 2.6.34 on backtrack and lucid 10.04 internet and aircrack work without any problem 

thanks to this man Author: Maxim Levitsky

if u have rt73 iwl4965 iwl5100 or any other chip supported by compat-wireless u dont need to apply zd1211 patch 

ps and always remember to have device firmware in your firmware directory

---

### Post by alohs on 2010-08-31
Your approach didnt work for me the third patch wasn't applyable, without him the card was fixed on channel -1.

My workaround:

Download: 
> wget [http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch](http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch)
wget [http://patches.aircrack-ng.org/zd1211rw-inject+dbi-fix-2.6.26.patch](http://patches.aircrack-ng.org/zd1211rw-inject+dbi-fix-2.6.26.patch)
newest compat wireless[COLOR=Red]

[COLOR=Black]Now Apply both patches to the compat-wireless, and continue like in your tutorial.[/COLOR]

EDIT: narf just worked on the first look when, i tried this airreplay-ng -9 mon0 (it hopped through the channels), but i cant make an Fakeauth on an specified channel.
[/COLOR]

---

### Post by alohs on 2010-08-31
How to get zd1211rw Driver working
---------------------------------

1.Download:
newest compat-wireless
([http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch))?
[http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch](http://patches.aircrack-ng.org/mac80211_2.6.32.2-wl_frag+ack_radiotap.patch)
[http://patches.aircrack-ng.org/zd1211rw-inject+dbi-fix-2.6.26.patch](http://patches.aircrack-ng.org/zd1211rw-inject+dbi-fix-2.6.26.patch)


2.Extract compat-wireless
3.Copy patches into compat-wireless dir
4.Apply them
       --4.1 patch -Np0 zd1211rw-inject+dbi-fix-2.6.26.patch
       --4.2 patch -Np1 mac80211_2.6.32.2-wl_frag+ack_radiotap.patch
5.Manually apply following changes to /net/wireless/chan.c (the patch didnt work for me)
> ###########################################################################################
diff --git a/net/wireless/chan.c b/net/wireless/chan.c
index b01a6f6..09d979b 100644
--- a/net/wireless/chan.c
+++ b/net/wireless/chan.c
@@ -49,9 +49,12 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev,
{
struct ieee80211_channel *chan;
int result;
+ struct wireless_dev *mon_dev = NULL;

- if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR)
+ if (wdev && wdev->iftype == NL80211_IFTYPE_MONITOR) {
+ mon_dev = wdev;
wdev = NULL;
+ }

if (wdev) {
ASSERT_WDEV_LOCK(wdev);
@@ -76,5 +79,8 @@ int cfg80211_set_freq(struct cfg80211_registered_device *rdev,
if (wdev)
wdev->channel = chan;

+ if (mon_dev)
+ mon_dev->channel = chan;
+
return 0;
}
#####################################################################################6. Select Driver
       --6.1 ./scripts/driver-select zd1211rw
7. Compile compat-wireless
       --7.1 make
       --7.2 make install
8.Load module
       --8.1 make wlunload
       --8.2 modprobe -i zd1211rw
9.Reboot!

---

