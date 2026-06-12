---
title: "Ad-hoc not working on T61 with Intel 4965"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by chessmani on 2008-06-23
Hello all,

I just bought a T61 and installed Kubuntu Hardy with everything upgraded. I would like to connect it on wireless to my Windows XP with ICS enabled.

I know the problem is not on the XP side because I have another laptop with kubuntu edgy and XP and the ad-hoc ICS connection is working fine with both.

The commands I use are:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 essid blabla
sudo ifconfig wlan0 up
sudo dhclient wlan0

After this, the dhclient does never discover an IP through the dhcp server on the XP host. It gives wlan0:avahi an ip, but it's not 192.168.0.x which it is supposed to be, and thus doesn't work.

So I'm unable to use ad-hoc on T61 with intel 4965.

Any suggestions?

Cheers.

Driver version: 1.2.25, from kernel 2.6.24-19

---

### Post by chessmani on 2008-06-24
Anybody?

---

### Post by chessmani on 2008-06-24
***UPDATE***

Comparing with my other laptop which has an ipw2200 and can connect correctly, I notice that with intel 4965 I can change to ad-hoc mode and associate it with the essid, but the **link quality** and **signal level** are both 0, so there's just no link.

I have installed linux-backports-modules-hardy as well, with no improvement.

---

### Post by chessmani on 2008-06-25
***New Update***

I have installed compat-wireless and the thing hasn't improved much. Now it connects intermitently, with an average of 91% of lost packets.

Really nobody has this problem? Nobody uses ad-hoc with 4965?

---

### Post by chessmani on 2008-07-09
Btw, is there any news about this? It still doesn't work...

---

### Post by rockhopper on 2008-07-18
I have a Dell XPS M1330 with the Intel 4965agn card. I, too, couldn't get Hardy to connect ad-hoc to a Vista host machine connected to the internet.


I tried the above method, and also the one at:
[http://www.debuntu.org/how-to-intel-wireless-4965-agn-with-ad-hoc-network-wep](http://www.debuntu.org/how-to-intel-wireless-4965-agn-with-ad-hoc-network-wep)

Sadly, no success :(

---

### Post by mdsouza on 2008-07-24
> **chessmani said:**
> 

Comparing with my other laptop which has an ipw2200 and can connect correctly

I have a machine with an ipw2200 that I am trying to connect to an XP ICS machine. You mentioned that you had an older laptop working, but was that in Edgy? Or did you manage to get it working in Hardy? Mine works with the networkmanager up to a point, it associates and assigns a 192.168 address from the XP DHCP. But this is where it stops working. I can not ping any other machines on the network. Any help would be appreciated. I have attempted to set this up manually using ipconfig/iwconfig without success as well. 

Thanks!

---

### Post by chessmani on 2008-08-05
It was with Edgy :/

---

### Post by midden on 2008-08-14
I also have a T61 running Edgy and cannot seem to create an ad-hoc network using the networkmanager or command line. After attempting to create the network here is the result from iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ComputerName"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```

No other devices detect the network. Any ideas?

---

### Post by chessmani on 2008-10-10
Just reporting, it seems that this problem is solved with the new kernel (2.6.27).

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=c46fbefa32c3c314884d3d3be27d0e1839de2c24](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=c46fbefa32c3c314884d3d3be27d0e1839de2c24)

---

### Post by hellfire_bg on 2008-10-20
Exactly how can i apply the above mentioned fix? First i compiled and installed kernel 2.6.27-2 thinking that the fix was included however this didn`t change things. Then i replaced iwl-core.h and iwl4965-base.c with the ones from the link you posted but then i couldn`t compile the kernel i got this error:

> drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl4965_commit_rxon’:
drivers/net/wireless/iwlwifi/iwl-agn.c:325: error: implicit declaration of function ‘iwl_clear_stations_table’
drivers/net/wireless/iwlwifi/iwl-agn.c:369: error: implicit declaration of function ‘iwl_set_tx_power’
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl4965_hw_get_beacon_cmd’:
drivers/net/wireless/iwlwifi/iwl-agn.c:509: error: implicit declaration of function ‘iwl_hw_set_rate_n_flags’
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl4965_set_mode’:
drivers/net/wireless/iwlwifi/iwl-agn.c:825: error: implicit declaration of function ‘iwl_scan_cancel_timeout’
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl4965_rx_card_state_notif’:
drivers/net/wireless/iwlwifi/iwl-agn.c:1250: error: implicit declaration of function ‘iwl_scan_cancel’
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl_setup_rx_handlers’:
drivers/net/wireless/iwlwifi/iwl-agn.c:1318: error: ‘iwl_rx_statistics’ undeclared (first use in this function)
drivers/net/wireless/iwlwifi/iwl-agn.c:1318: error: (Each undeclared identifier is reported only once
drivers/net/wireless/iwlwifi/iwl-agn.c:1318: error: for each function it appears in.)
drivers/net/wireless/iwlwifi/iwl-agn.c:1321: error: implicit declaration of function ‘iwl_setup_rx_scan_handlers’
drivers/net/wireless/iwlwifi/iwl-agn.c:1329: error: ‘iwl_rx_reply_rx_phy’ undeclared (first use in this function)
drivers/net/wireless/iwlwifi/iwl-agn.c:1330: error: ‘iwl_rx_reply_rx’ undeclared (first use in this function)
drivers/net/wireless/iwlwifi/iwl-agn.c:1332: error: ‘iwl_rx_reply_compressed_ba’ undeclared (first use in this function)
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl_alive_start’:
drivers/net/wireless/iwlwifi/iwl-agn.c:2081: error: implicit declaration of function ‘iwl_rf_kill_ct_config’
drivers/net/wireless/iwlwifi/iwl-agn.c:2095: error: ‘STATUS_MODE_PENDING’ undeclared (first use in this function)
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl4965_mac_add_interface’:
drivers/net/wireless/iwlwifi/iwl-agn.c:2775: error: ‘STATUS_MODE_PENDING’ undeclared (first use in this function)
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl4965_mac_config’:
drivers/net/wireless/iwlwifi/iwl-agn.c:2803: error: implicit declaration of function ‘iwl_radio_kill_sw_enable_radio’
drivers/net/wireless/iwlwifi/iwl-agn.c:2809: error: implicit declaration of function ‘iwl_radio_kill_sw_disable_radio’
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl4965_mac_hw_scan’:
drivers/net/wireless/iwlwifi/iwl-agn.c:3238: error: implicit declaration of function ‘iwl_scan_initiate’
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl4965_mac_ampdu_action’:
drivers/net/wireless/iwlwifi/iwl-agn.c:3433: error: implicit declaration of function ‘iwl_rx_agg_start’
drivers/net/wireless/iwlwifi/iwl-agn.c:3436: error: implicit declaration of function ‘iwl_rx_agg_stop’
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl_setup_deferred_work’:
drivers/net/wireless/iwlwifi/iwl-agn.c:4085: error: implicit declaration of function ‘iwl_setup_scan_deferred_work’
drivers/net/wireless/iwlwifi/iwl-agn.c: In function ‘iwl4965_pci_probe’:
drivers/net/wireless/iwlwifi/iwl-agn.c:4277: error: implicit declaration of function ‘iwl_set_hw_params’
make[5]: *** [drivers/net/wireless/iwlwifi/iwl-agn.o] Error 1
make[4]: *** [drivers/net/wireless/iwlwifi] Error 2
make[3]: *** [drivers/net/wireless] Error 2
make[2]: *** [drivers/net] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.27.2'
make: *** [debian/stamp/build/kernel] Error 2


---

