---
title: "How to get Netgear WG511T in monitor mode"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by Siph0n on 2007-05-05
I just bought a Netgear WG511T wireless network card for my laptop. It worked directly out of the box, which was awesome!, and the reason I bought this card :).... Then I tried to put it into monitor mode, and I get this 

```
iwconfig ath0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Operation not permitted.

```

Here is the output of my iwconfig command if that helps...

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"xxxxx"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/94  Signal level=-60 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Siph0n on 2007-05-05
Oh I didn't say my question :) How can I get my card into monitor mode? :) I see other people have got this card to go into monitor mode, and this was also one of the reasons I got this card :) Any help would be very appreciated! :)

---

### Post by chili555 on 2007-05-05
Did you sudo that command? Are you certain the card supports monitor mode? Check:```
sudo iwpriv ath0
```Does it report it is capable of monitor mode?

---

### Post by Siph0n on 2007-05-05
Oh, I didn't run it as sudo before... When I run the iwconfig ath0 mode monitor as sudo I get,

```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.

```

When I run sudo iwpriv ath0 I get,

```
ath0      Available private ioctls :
          setoptie         (8BEE) : set 256 byte  & get   0      
          getoptie         (8BEF) : set   0       & get 256 byte 
          setkey           (8BF2) : set  60 byte  & get   0      
          delkey           (8BF4) : set   7 byte  & get   0      
          setmlme          (8BF0) : set  42 byte  & get   0      
          addmac           (8BF6) : set   1 addr  & get   0      
          delmac           (8BF8) : set   1 addr  & get   0      
          kickmac          (8BFE) : set   1 addr  & get   0      
          wds_add          (8BFA) : set   1 addr  & get   0      
          wds_del          (8BFC) : set   1 addr  & get   0      
          setchanlist      (8BE6) : set  32 byte  & get   0      
          getchanlist      (8BE7) : set   0       & get  32 byte 
          getchaninfo      (8BED) : set   0       & get 2044 byte 
          mode             (8BE2) : set   6 char  & get   0      
          get_mode         (8BE3) : set   0       & get   6 char 
          setwmmparams     (8BE4) : set   4 int   & get   0      
          getwmmparams     (8BE5) : set   3 int   & get   1 int  
          cwmin            (0001) : set   3 int   & get   0      
          get_cwmin        (0001) : set   2 int   & get   1 int  
          cwmax            (0002) : set   3 int   & get   0      
          get_cwmax        (0002) : set   2 int   & get   1 int  
          aifs             (0003) : set   3 int   & get   0      
          get_aifs         (0003) : set   2 int   & get   1 int  
          txoplimit        (0004) : set   3 int   & get   0      
          get_txoplimit    (0004) : set   2 int   & get   1 int  
          acm              (0005) : set   3 int   & get   0      
          get_acm          (0005) : set   2 int   & get   1 int  
          noackpolicy      (0006) : set   3 int   & get   0      
          get_noackpolicy  (0006) : set   2 int   & get   1 int  
          setparam         (8BE0) : set   2 int   & get   0      
          getparam         (8BE1) : set   1 int   & get   1 int  
          authmode         (0003) : set   1 int   & get   0      
          get_authmode     (0003) : set   0       & get   1 int  
          protmode         (0004) : set   1 int   & get   0      
          get_protmode     (0004) : set   0       & get   1 int  
          mcastcipher      (0005) : set   1 int   & get   0      
          get_mcastcipher  (0005) : set   0       & get   1 int  
          mcastkeylen      (0006) : set   1 int   & get   0      
          get_mcastkeylen  (0006) : set   0       & get   1 int  
          ucastciphers     (0007) : set   1 int   & get   0      
          get_uciphers     (0007) : set   0       & get   1 int  
          ucastcipher      (0008) : set   1 int   & get   0      
          get_ucastcipher  (0008) : set   0       & get   1 int  
          ucastkeylen      (0009) : set   1 int   & get   0      
          get_ucastkeylen  (0009) : set   0       & get   1 int  
          keymgtalgs       (0015) : set   1 int   & get   0      
          get_keymgtalgs   (0015) : set   0       & get   1 int  
          rsncaps          (0016) : set   1 int   & get   0      
          get_rsncaps      (0016) : set   0       & get   1 int  
          hostroaming      (000C) : set   1 int   & get   0      
          get_hostroaming  (000C) : set   0       & get   1 int  
          privacy          (000D) : set   1 int   & get   0      
          get_privacy      (000D) : set   0       & get   1 int  
          countermeasures  (000E) : set   1 int   & get   0      
          get_countermeas  (000E) : set   0       & get   1 int  
          dropunencrypted  (000F) : set   1 int   & get   0      
          get_dropunencry  (000F) : set   0       & get   1 int  
          wpa              (000A) : set   1 int   & get   0      
          get_wpa          (000A) : set   0       & get   1 int  
          driver_caps      (0010) : set   1 int   & get   0      
          get_driver_caps  (0010) : set   0       & get   1 int  
          maccmd           (0011) : set   1 int   & get   0      
          wmm              (0012) : set   1 int   & get   0      
          get_wmm          (0012) : set   0       & get   1 int  
          hide_ssid        (0013) : set   1 int   & get   0      
          get_hide_ssid    (0013) : set   0       & get   1 int  
          ap_bridge        (0014) : set   1 int   & get   0      
          get_ap_bridge    (0014) : set   0       & get   1 int  
          inact            (0017) : set   1 int   & get   0      
          get_inact        (0017) : set   0       & get   1 int  
          inact_auth       (0018) : set   1 int   & get   0      
          get_inact_auth   (0018) : set   0       & get   1 int  
          inact_init       (0019) : set   1 int   & get   0      
          get_inact_init   (0019) : set   0       & get   1 int  
          abolt            (001A) : set   1 int   & get   0      
          get_abolt        (001A) : set   0       & get   1 int  
          dtim_period      (001C) : set   1 int   & get   0      
          get_dtim_period  (001C) : set   0       & get   1 int  
          bintval          (001D) : set   1 int   & get   0      
          get_bintval      (001D) : set   0       & get   1 int  
          doth             (001E) : set   1 int   & get   0      
          get_doth         (001E) : set   0       & get   1 int  
          doth_pwrtgt      (001F) : set   1 int   & get   0      
          get_doth_pwrtgt  (001F) : set   0       & get   1 int  
          doth_reassoc     (0020) : set   1 int   & get   0      
          compression      (0021) : set   1 int   & get   0      
          get_compression  (0021) : set   0       & get   1 int  
          ff               (0022) : set   1 int   & get   0      
          get_ff           (0022) : set   0       & get   1 int  
          turbo            (0001) : set   1 int   & get   0      
          get_turbo        (0001) : set   0       & get   1 int  
          xr               (0023) : set   1 int   & get   0      
          get_xr           (0023) : set   0       & get   1 int  
          burst            (0024) : set   1 int   & get   0      
          get_burst        (0024) : set   0       & get   1 int  
          doth_chanswitch  (8BE8) : set   2 int   & get   0      
          pureg            (0025) : set   1 int   & get   0      
          get_pureg        (0025) : set   0       & get   1 int  
          ar               (0026) : set   1 int   & get   0      
          get_ar           (0026) : set   0       & get   1 int  
          wds              (0027) : set   1 int   & get   0      
          get_wds          (0027) : set   0       & get   1 int  
          bgscan           (0028) : set   1 int   & get   0      
          get_bgscan       (0028) : set   0       & get   1 int  
          bgscanidle       (0029) : set   1 int   & get   0      
          get_bgscanidle   (0029) : set   0       & get   1 int  
          bgscanintvl      (002A) : set   1 int   & get   0      
          get_bgscanintvl  (002A) : set   0       & get   1 int  
          mcast_rate       (002B) : set   1 int   & get   0      
          get_mcast_rate   (002B) : set   0       & get   1 int  
          coverageclass    (002C) : set   1 int   & get   0      
          get_coveragecls  (002C) : set   0       & get   1 int  
          countryie        (002D) : set   1 int   & get   0      
          get_countryie    (002D) : set   0       & get   1 int  
          scanvalid        (002E) : set   1 int   & get   0      
          get_scanvalid    (002E) : set   0       & get   1 int  
          regclass         (003B) : set   1 int   & get   0      
          get_regclass     (003B) : set   0       & get   1 int  
          dropunenceapol   (003C) : set   1 int   & get   0      
          get_dropunencea  (003C) : set   0       & get   1 int  
          shpreamble       (003D) : set   1 int   & get   0      
          get_shpreamble   (003D) : set   0       & get   1 int  
          rssi11a          (002F) : set   1 int   & get   0      
          get_rssi11a      (002F) : set   0       & get   1 int  
          rssi11b          (0030) : set   1 int   & get   0      
          get_rssi11b      (0030) : set   0       & get   1 int  
          rssi11g          (0031) : set   1 int   & get   0      
          get_rssi11g      (0031) : set   0       & get   1 int  
          rate11a          (0032) : set   1 int   & get   0      
          get_rate11a      (0032) : set   0       & get   1 int  
          rate11b          (0033) : set   1 int   & get   0      
          get_rate11b      (0033) : set   0       & get   1 int  
          rate11g          (0034) : set   1 int   & get   0      
          get_rate11g      (0034) : set   0       & get   1 int  
          uapsd            (0035) : set   1 int   & get   0      
          get_uapsd        (0035) : set   0       & get   1 int  
          sleep            (0036) : set   1 int   & get   0      
          get_sleep        (0036) : set   0       & get   1 int  
          qosnull          (0037) : set   1 int   & get   0      
          pspoll           (0038) : set   1 int   & get   0      
          eospdrop         (0039) : set   1 int   & get   0      
          get_eospdrop     (0039) : set   0       & get   1 int  
          markdfs          (003A) : set   1 int   & get   0      
          get_markdfs      (003A) : set   0       & get   1 int  
          setiebuf         (8BEA) : set 1032 byte  & get   0      
          getiebuf         (8BE9) : set   0       & get 1032 byte 
          setfilter        (8BEC) : set   4 byte  & get   0      

```

If one WG511T network card can go into monitor mode, shouldn't all of them? Thanks for the quick response before! :)

---

### Post by Siph0n on 2007-05-05
I tried doing sudo iwpriv ath0 mode 0, sudo iwpriv ath0 mode 1, etc all the way to 5, but I dont know what that did. iwconfig still says its in Managed mode no matter what number I use...

---

### Post by chili555 on 2007-05-05
Perhaps this will help, especially the last post: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/62106](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/62106)

---

### Post by Siph0n on 2007-05-05
WOW Thanx!!! :) That worked!!!!! :) I was googling all morning lol...........

---

