---
title: "Unable to see (and thus connect) to wireless internet"
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by Suchetana on 2015-06-27
I am running Ubuntu 14.04 on my HP Desktop. Earlier I was able to connect to Wi-fi from my system. Then I kept fidgeting with settings here and there to mke my desktop a wifi hotspot. Somehow managed to do something and here I am, no wireless connection shows up. I am only able to connect through wired connection.
Suggestions?

I ran a few commands that were asked in many posts of similar queries. the results can be seen here:

[http://askubuntu.com/questions/641245/wifi-no-longer-showing-up-working-on-ubuntu-14-04-desktop](http://askubuntu.com/questions/641245/wifi-no-longer-showing-up-working-on-ubuntu-14-04-desktop)

---

### Post by chili555 on 2015-07-07
Now that the driver loads, do you have a wireless interface, ideally wlan0?```
iwconfig
```Let's see what other data we can find that is helpful:```
rfkill list all
dmesg | grep -e wlan -e rt2

```Thanks.

---

### Post by Suchetana on 2015-07-08
iwconfig output:
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
[/code


rfkill list all
[code]0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no[/code

[code]
dmesg | grep -e wlan -e rt2
y [0x00000068]
[169516.044244] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169516.044257] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169517.661546] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169519.262841] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169519.262853] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169520.880143] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169522.481434] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169522.481446] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169524.098740] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169525.700033] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169525.700046] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169527.317340] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169528.918629] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169528.918641] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169530.535934] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169532.137226] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169532.137239] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169533.754460] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169535.355775] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169535.355787] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169536.977036] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169538.578318] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169538.578323] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169540.195726] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169541.796950] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169541.796962] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169543.418324] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169545.023566] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169545.023579] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169546.640865] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169548.254209] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169548.254217] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169549.871538] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169551.472825] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169551.472837] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169553.090128] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169554.691378] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169554.691384] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169556.308726] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169557.910016] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169557.910029] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169559.527275] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169561.128615] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169561.128628] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169562.745919] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169564.347212] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169564.347225] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169565.964517] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169567.569722] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169567.569734] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169569.195121] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169570.796326] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169570.796331] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169572.417658] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169574.018963] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169574.018975] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169575.636261] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169577.241547] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169577.241559] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169578.866909] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169580.468215] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169580.468228] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169582.105495] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169583.714758] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169583.714763] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169585.344152] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169586.949446] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169586.949458] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169588.566689] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169590.172043] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169590.172053] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169591.789349] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169593.390545] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169593.390551] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169595.011904] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169596.621179] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169596.621191] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169598.238555] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169599.847740] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169599.847755] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169601.469109] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169603.070375] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169603.070381] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169604.691724] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169606.312956] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169606.312977] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169607.930304] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169609.531625] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169609.531637] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169611.148878] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169612.754199] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169612.754203] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169614.391480] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169615.996839] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169615.996851] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169617.614186] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169619.215444] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169619.215456] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169620.840738] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169622.442008] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169622.442012] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169624.059385] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169625.664661] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169625.664669] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169627.281985] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169628.891221] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169628.891233] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169630.512490] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169632.113832] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169632.113838] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169633.747163] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169635.356477] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169635.356487] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169636.973804] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169638.575096] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169638.575109] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169640.192398] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169641.793693] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169641.793706] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169643.410976] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169645.020296] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169645.020308] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169646.641603] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169648.250912] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169648.250925] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169649.868209] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169651.469499] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169651.469511] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169653.086805] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169654.688096] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169654.688108] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169656.305398] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169657.914698] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169657.914711] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169659.531959] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169661.133246] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169661.133258] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169662.750598] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169664.351838] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169664.351843] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169665.977136] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169667.586381] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169667.586385] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169669.207697] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169670.817016] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169670.817021] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169672.434365] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169674.039662] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169674.039667] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169675.656930] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169677.262216] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169677.262231] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169678.879536] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169680.488862] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169680.488867] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169682.110176] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169683.719515] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169683.719527] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169685.348817] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169686.954020] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169686.954024] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169688.571427] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169690.176619] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169690.176624] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169691.809995] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169693.411262] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169693.411269] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169695.028547] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169696.633858] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169696.633868] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169698.263189] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169699.872549] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169699.872561] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169701.493856] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169703.095151] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169703.095164] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169704.712366] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169706.313673] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169706.313685] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169707.930968] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169709.532273] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169709.532284] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169711.149614] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169712.750895] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169712.750900] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169714.368243] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169715.969489] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169715.969494] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169717.586782] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169719.188081] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169719.188093] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169720.809438] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169722.426744] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169722.426756] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169724.044052] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169725.645342] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169725.645355] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169727.266616] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169728.879922] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169728.879935] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169730.501255] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169732.106499] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169732.106505] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169733.727832] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169735.337109] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169735.337117] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169736.970457] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169738.575771] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169738.575784] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169740.197053] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169741.822348] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169741.822361] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169743.439697] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169745.040992] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169745.041005] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169746.658301] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169748.259585] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169748.259598] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169749.876891] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169751.478178] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169751.478189] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169753.099425] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169754.700783] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169754.700795] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169756.318050] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169757.927315] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169757.927327] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169759.544687] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169761.149987] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169761.150000] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169762.767291] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169764.376585] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169764.376597] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169765.993893] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169767.595185] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169767.595198] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169769.220450] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169770.821721] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169770.821733] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169772.451127] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169774.056398] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169774.056410] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169775.677636] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169777.282966] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169777.282978] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169778.900221] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169780.501566] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169780.501578] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169782.118900] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169783.720196] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169783.720208] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169785.337499] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169786.942675] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[169786.942680] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169788.564104] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
```

---

### Post by chili555 on 2015-07-09
> [169786.942680] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[169788.564104] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]I have Googled this extensively and have found but two interesting ideas. First, it may be actually a hardware fault. Can you check to see if the device is seated properly in its slot? If this is a desktop computer, can you try a different PCI slot? Of course, please follow all the usual precautions if you decide to open up and work inside your computer.

Second, I read a post that suggested loading the driver module later might help. Let's blacklist it so it doesn't load at all on boot:```
sudo -i
echo "blacklist rt2800pci  >>  /etc/modprobe.d/blacklist.conf
exit
```Now reboot. After you log in and the desktop comes up, load the module:```
sudo modprobe rt2800pci
```Check for error messages:```
dmesg | grep rt2
```If it helps, we'll make another change to make it automatic.

---

### Post by Suchetana on 2015-07-10
still getting error message 
```
suchetana@suchetana-500-101in:~$ dmesg | grep rt2
[    9.662823] rt2800pci 0000:03:00.0: enabling device (0100 -> 0102)
[    9.662939] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[    9.668403] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   14.379551] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   14.460395] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   16.099378] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   17.716683] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   17.716688] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   19.430015] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   21.031307] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   21.031311] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   22.652639] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   24.261902] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   24.261906] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   25.915240] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   27.528599] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   27.528604] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   29.145903] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   30.747194] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   30.747198] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   32.364500] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   33.965787] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   33.965791] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   35.583096] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   37.184388] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   37.184393] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   38.813671] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   40.422972] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   40.422977] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   42.044306] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   43.657587] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   43.657591] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   45.294933] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   46.896171] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   46.896175] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   48.517463] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   50.142800] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   50.142804] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   51.768152] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   53.377446] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   53.377451] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   55.010765] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   56.648054] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   56.648059] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   58.289410] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   59.890653] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   59.890658] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   61.516011] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   63.117303] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   63.117307] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   65.142939] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   66.744230] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   66.744235] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   68.365535] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   69.966806] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   69.966810] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   71.668171] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   73.277442] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   73.277446] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   74.906801] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   76.512070] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   76.512078] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   78.149416] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   79.758690] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   79.758695] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   81.391994] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   82.993316] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   82.993320] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   84.610698] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   86.219931] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   86.219936] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   87.837235] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   89.446596] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   89.446609] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   91.075836] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   92.681164] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   92.681176] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   94.306465] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   95.907805] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   95.907819] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   97.533117] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   99.142387] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   99.142398] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  100.763694] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  102.372992] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  102.373005] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
```
 

Not sure if i would open the desktop and check for hardware issues. I mean this thing will get fixed once I reinstall the operating software, that is for sure. Had happened before. Reinstalling the OS had rectified it. Now i just don't want to go through a reinstall process, hence wondering about any software rectification

---

### Post by chili555 on 2015-07-10
> still getting error message 
suchetana@suchetana-500-101in:~$ dmesg | grep rt2
[ [COLOR="#FF0000"]9.662823[/COLOR]] rt2800pci 0000:03:00.0: enabling device (0100 -> 0102)
[ 9.662939] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[ 9.668403] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[ 14.379551] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'Unless you are running an SSD and have the fastest fingers in the world, at 9.6 seconds into boot, rt2800pci is loading. That suggests it isn't blacklisted correctly or is loaded elsewhere. Let's see:```
cat /etc/modprobe.d/blacklist.conf | tail -n5
cat /etc/modules | tail -n5
```> I mean this thing will get fixed once I reinstall the operating software, that is for sure. Had happened before. Reinstalling the OS had rectified it. Does it work properly if you run the live DVD or USB?

---

### Post by Suchetana on 2015-07-10
cat /etc/modprobe.d/blacklist.conf | tail -n5# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
#blacklist rt2800pci
#blacklist rt2800pci


 cat /etc/modules | tail -n5
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp
rtc

---

### Post by Bucky Ball on 2015-07-11
Please use code tags for terminal output. See the last link in my signature. Neater, easier to manage, space-saving.

---

### Post by chili555 on 2015-07-11
> # continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
#blacklist rt2800pci
#blacklist rt2800pciIn order for our technique to be tested and hopefully work, the blacklist needs to be uncommented and therefore effective. Please do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last lines to read:```
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800pci
```Proofread carefully, save and close the text editor. Reboot. Your wireless shouldn't be working. Now manually load the module:```
sudo modprobe rt2800pci
```Either your wireless springs to life and we'll amend a file to make it persistent; or it doesn't and we'll check the log for messages:```
dmesg | grep rt2
```> I mean this thing will get fixed once I reinstall the operating software, that is for sure. Had happened before. Reinstalling the OS had rectified it.Does it work properly if you run the live DVD or USB? If so, I'd back up and reinstall.

---

### Post by Suchetana on 2015-07-14
Things remain the same as before.
```

dmesg | grep rt2
[   87.815832] rt2800pci 0000:03:00.0: enabling device (0100 -> 0102)
[   87.815936] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   87.819495] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   87.824725] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   87.868561] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   89.482693] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   91.087955] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   91.087968] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   92.765343] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   94.366561] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   94.366572] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   95.987894] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   97.589168] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[   97.589181] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   99.206533] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  100.823796] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  100.823809] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  102.449086] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  104.054454] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  104.054467] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  105.671758] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  107.273047] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  107.273061] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  108.890341] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  110.491594] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  110.491606] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)

```


It does work if I reinstall with a live USB. But the reason why I do not want to go for it is it would involve lot of reinstalling software packages

---

### Post by Bucky Ball on 2015-07-14
Have a look at answer number 153 [here]("http://askubuntu.com/questions/17823/how-to-list-all-installed-packages") (and 509 above it gives other options).

```
aptitude search '~i!~M'
```

... appears to list all things you installed, not everything installed. This will be handy if you do need to reinstall perhaps ...

---

### Post by Suchetana on 2015-07-15
Thanks but I seriously do not want to go into reinstalling if I can..

> **Bucky Ball said:**
> Have a look at answer number 153 [here]("http://askubuntu.com/questions/17823/how-to-list-all-installed-packages") (and 509 above it gives other options).

```
aptitude search '~i!~M'
```

... appears to list all things you installed, not everything installed. This will be handy if you do need to reinstall perhaps ...

---

