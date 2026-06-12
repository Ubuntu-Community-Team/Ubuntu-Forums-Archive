---
title: "Mt7601u Driver Issue"
date: 2019-11-27
forum: Networking &amp; Wireless
---

### Post by mdriwach on 2019-11-27
Hello , 
I have an Issue zith getting work the wifi dongle mt7601u(little bit old) the driver existe but not working and this is what i get when i plug-in wireless pen 
(it seems like the system recognize the driver at first but after he get erros starting from line " TX DMA did not stop")
i hope find some help 
and thankyou so much 


```
dmesg
```
```
[  281.951503] mt7601u 1-3:1.0: Vendor request req:07 off:0080 failed:-71
[  282.111752] mt7601u 1-3:1.0: Vendor request req:02 off:0080 failed:-71
[  282.271147] mt7601u 1-3:1.0: Vendor request req:02 off:0080 failed:-71
[  282.271220] mt7601u: probe of 1-3:1.0 failed with error -110
[  282.271495] usb 1-3: USB disconnect, device number 15
[  282.543141] usb 1-3: new high-speed USB device number 16 using xhci_hcd
[  282.708199] usb 1-3: New USB device found, idVendor=148f, idProduct=7601, bcdDevice= 0.00
[  282.708203] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  282.708206] usb 1-3: Product: 802.11 n WLAN
[  282.708209] usb 1-3: Manufacturer: MediaTek
[  282.708211] usb 1-3: SerialNumber: 1.0
[  282.835882] usb 1-3: reset high-speed USB device number 16 using xhci_hcd
[  282.988049] mt7601u 1-3:1.0: ASIC revision: 76010001 MAC revision: 76010500
[  282.991475] mt7601u 1-3:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[  283.429840] mt7601u 1-3:1.0: EEPROM ver:0c fae:00
[  283.731414] mt7601u 1-3:1.0: rx urb failed: -71
[  283.731465] mt7601u 1-3:1.0: rx urb failed: -71
[  283.731528] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  283.731532] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  283.731588] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  283.731591] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  283.731657] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  283.731660] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  283.731808] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  283.731811] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  283.731859] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  283.731861] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  283.731864] mt7601u 1-3:1.0: Error: mt7601u_mcu_wait_resp timed out
[  283.891093] mt7601u 1-3:1.0: Vendor request req:07 off:0080 failed:-71
[  284.055074] mt7601u 1-3:1.0: Vendor request req:02 off:0080 failed:-71
[  284.215779] mt7601u 1-3:1.0: Vendor request req:02 off:0080 failed:-71
[  284.215850] mt7601u: probe of 1-3:1.0 failed with error -110
[  284.216141] usb 1-3: USB disconnect, device number 16
[  284.487785] usb 1-3: new high-speed USB device number 17 using xhci_hcd
[  284.649342] usb 1-3: New USB device found, idVendor=148f, idProduct=7601, bcdDevice= 0.00
[  284.649346] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  284.649349] usb 1-3: Product: 802.11 n WLAN
[  284.649352] usb 1-3: Manufacturer: MediaTek
[  284.649353] usb 1-3: SerialNumber: 1.0
[  284.775271] usb 1-3: reset high-speed USB device number 17 using xhci_hcd
[  284.928226] mt7601u 1-3:1.0: ASIC revision: 76010001 MAC revision: 76010500
[  284.932503] mt7601u 1-3:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[  285.378192] mt7601u 1-3:1.0: EEPROM ver:0c fae:00
[  285.616424] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  285.616433] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:2-1!
[  285.616498] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  285.616514] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:2-1!
[  285.616567] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  285.616570] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:2-1!
[  285.616639] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  285.616642] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:2-1!
[  285.616718] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  285.616721] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:2-1!
[  285.616724] mt7601u 1-3:1.0: Error: mt7601u_mcu_wait_resp timed out
[  285.779536] mt7601u 1-3:1.0: Vendor request req:07 off:0080 failed:-71
[  285.939756] mt7601u 1-3:1.0: Vendor request req:02 off:0080 failed:-71
[  286.099135] mt7601u 1-3:1.0: Vendor request req:02 off:0080 failed:-71
[  286.099206] mt7601u: probe of 1-3:1.0 failed with error -110
[  286.099571] usb 1-3: USB disconnect, device number 17
[  286.379117] usb 1-3: new high-speed USB device number 18 using xhci_hcd
[  286.541669] usb 1-3: New USB device found, idVendor=148f, idProduct=7601, bcdDevice= 0.00
[  286.541674] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  286.541677] usb 1-3: Product: 802.11 n WLAN
[  286.541679] usb 1-3: Manufacturer: MediaTek
[  286.541681] usb 1-3: SerialNumber: 1.0
[  286.671293] usb 1-3: reset high-speed USB device number 18 using xhci_hcd
[  286.827802] mt7601u 1-3:1.0: ASIC revision: 76010001 MAC revision: 76010500
[  286.831257] mt7601u 1-3:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[  287.264614] mt7601u 1-3:1.0: EEPROM ver:0c fae:00
[  287.568607] mt7601u_complete_rx: 10 callbacks suppressed
[  287.568613] mt7601u 1-3:1.0: rx urb failed: -71
[  287.568653] mt7601u 1-3:1.0: rx urb failed: -71
[  287.568691] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  287.568694] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  287.568730] mt7601u 1-3:1.0: rx urb failed: -71
[  287.568747] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  287.568763] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  287.568807] mt7601u 1-3:1.0: rx urb failed: -71
[  287.568823] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  287.568827] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  287.568884] mt7601u 1-3:1.0: rx urb failed: -71
[  287.568919] mt7601u 1-3:1.0: rx urb failed: -71
[  287.568988] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  287.568998] mt7601u 1-3:1.0: rx urb failed: -71
[  287.569009] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  287.569012] mt7601u 1-3:1.0: Error: MCU resp urb failed:-71
[  287.569014] mt7601u 1-3:1.0: Error: MCU resp evt:0 seq:5-4!
[  287.569017] mt7601u 1-3:1.0: Error: mt7601u_mcu_wait_resp timed out
[  287.731781] mt7601u 1-3:1.0: Vendor request req:07 off:0080 failed:-71
[  287.891123] mt7601u 1-3:1.0: Vendor request req:02 off:0080 failed:-71
[  288.051760] mt7601u 1-3:1.0: Vendor request req:02 off:0080 failed:-71
[  288.051833] mt7601u: probe of 1-3:1.0 failed with error -110
[  288.052122] usb 1-3: USB disconnect, device number 18
[  288.323097] usb 1-3: new high-speed USB device number 19 using xhci_hcd
[  288.486145] usb 1-3: New USB device found, idVendor=148f, idProduct=7601, bcdDevice= 0.00
[  288.486150] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  288.486153] usb 1-3: Product: 802.11 n WLAN
[  288.486155] usb 1-3: Manufacturer: MediaTek
[  288.486157] usb 1-3: SerialNumber: 1.0
[  288.615857] usb 1-3: reset high-speed USB device number 19 using xhci_hcd
[  288.768092] mt7601u 1-3:1.0: ASIC revision: 76010001 MAC revision: 76010500
[  288.771526] mt7601u 1-3:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[  289.217904] mt7601u 1-3:1.0: EEPROM ver:0c fae:00
[  289.607488] ieee80211 phy11: Selected rate control algorithm 'minstrel_ht'
[  289.735405] mt7601u 1-3:1.0 wlx000f008c5b99: renamed from wlan0
[  298.878840] usb 1-3: USB disconnect, device number 19
[  298.879646] mt7601u 1-3:1.0: Error: submit URB dir:128 ep:1 failed:-19
[  298.895699] mt7601u 1-3:1.0: Warning: TX DMA did not stop!
[  302.895491] mt7601u 1-3:1.0: Warning: MAC TX did not stop!
[  305.311774] mt7601u 1-3:1.0: Warning: MAC RX did not stop!
[  305.311777] mt7601u 1-3:1.0: Warning: RX DMA did not stop!
[  305.683186] usb 1-3: new high-speed USB device number 20 using xhci_hcd
[  305.844675] usb 1-3: New USB device found, idVendor=148f, idProduct=7601, bcdDevice= 0.00
[  305.844679] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  305.844682] usb 1-3: Product: 802.11 n WLAN
[  305.844684] usb 1-3: Manufacturer: MediaTek
[  305.844686] usb 1-3: SerialNumber: 1.0
[  305.971929] usb 1-3: reset high-speed USB device number 20 using xhci_hcd
[  306.124748] mt7601u 1-3:1.0: ASIC revision: 76010001 MAC revision: 76010500
[  306.128200] mt7601u 1-3:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[  306.562309] mt7601u 1-3:1.0: EEPROM ver:0c fae:00
[  306.955436] ieee80211 phy12: Selected rate control algorithm 'minstrel_ht'
[  306.975293] mt7601u 1-3:1.0 wlx000f008c5b99: renamed from wlan0
[  338.812435] usb 1-3: USB disconnect, device number 20
[  338.813215] mt7601u 1-3:1.0: Error: submit URB dir:128 ep:1 failed:-19
[  338.851825] mt7601u 1-3:1.0: Warning: TX DMA did not stop!
[  342.864249] mt7601u 1-3:1.0: Warning: MAC TX did not stop!
[  345.279673] mt7601u 1-3:1.0: Warning: MAC RX did not stop!
[  345.279676] mt7601u 1-3:1.0: Warning: RX DMA did not stop!
[  345.647765] usb 1-3: new full-speed USB device number 21 using xhci_hcd
[  345.806127] usb 1-3: not running at top speed; connect to a high speed hub
[  345.827832] usb 1-3: New USB device found, idVendor=148f, idProduct=7601, bcdDevice= 0.00
[  345.827836] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  345.827839] usb 1-3: Product: 802.11 n WLAN
[  345.827841] usb 1-3: Manufacturer: MediaTek
[  345.827843] usb 1-3: SerialNumber: 1.0
[  345.955956] usb 1-3: reset full-speed USB device number 21 using xhci_hcd
[  346.128659] mt7601u 1-3:1.0: ASIC revision: 76010001 MAC revision: 76010500
[  346.155890] mt7601u 1-3:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[  347.179621] mt7601u 1-3:1.0: EEPROM ver:0c fae:00
[  347.916959] mt7601u 1-3:1.0: rx urb failed: -71
[  347.917077] mt7601u 1-3:1.0: rx urb failed: -71
[  347.917162] mt7601u 1-3:1.0: rx urb failed: -71
[  347.917238] mt7601u 1-3:1.0: rx urb failed: -71
[  347.917318] mt7601u 1-3:1.0: rx urb failed: -71
[  347.917402] mt7601u 1-3:1.0: rx urb failed: -71
[  347.917480] mt7601u 1-3:1.0: rx urb failed: -71
[  347.917564] mt7601u 1-3:1.0: rx urb failed: -71
[  347.917688] mt7601u 1-3:1.0: rx urb failed: -71
[  347.917775] mt7601u 1-3:1.0: rx urb failed: -71
[  348.075161] mt7601u 1-3:1.0: Vendor request req:02 off:101c failed:-71
[  348.239226] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  348.399813] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  348.559132] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  348.719817] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  348.879818] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  349.039208] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  349.199705] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  349.359799] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  349.519217] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  349.679827] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  349.839205] mt7601u 1-3:1.0: Vendor request req:07 off:0500 failed:-71
[  349.839224] mt7601u 1-3:1.0: Error: Time out with reg 00000500
[  349.839229] mt7601u 1-3:1.0: Error: RF write 05:03 failed:-110!!
[  349.999542] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  350.159800] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  350.319818] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  350.479823] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  350.639308] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  350.799840] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  350.959817] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  351.119143] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  351.291160] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  351.451801] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  351.611122] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  351.771816] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  351.931795] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  352.095823] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  352.255815] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  352.415208] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  352.575175] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  352.735833] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  352.895098] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  353.055785] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  353.215821] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  353.375725] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  353.535572] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  353.695190] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  353.855823] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  354.015820] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  354.175173] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  354.335824] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  354.495808] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  354.655806] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  354.815821] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  354.975173] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  355.135816] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  355.295791] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  355.455829] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  355.615180] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  355.775169] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  355.935772] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  356.095817] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  356.259351] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  356.419822] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  356.579814] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  356.739801] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  356.899816] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  357.059131] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  357.219822] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  357.379203] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  357.539144] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  357.699152] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  357.859167] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  358.019821] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  358.179199] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  358.339838] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  358.499170] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  358.659137] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  358.819724] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  358.983813] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  359.143156] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  359.303785] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  359.463538] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  359.623088] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  359.783777] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  359.943144] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  360.103099] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  360.263136] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  360.427770] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  360.587823] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  360.751129] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71
[  360.911119] mt7601u 1-3:1.0: Vendor request req:07 off:101c failed:-71


```

---

### Post by mdriwach on 2019-11-28
Ububtu version 19.10 
With kernel 5.4

---

### Post by jeremy31 on 2019-11-28
Sure you have 5.4 kernel and not 5.3?

---

### Post by mdriwach on 2019-11-28
Yes i have upgraded the kernel today jist to fix this issue and nothing new !

---

### Post by jeremy31 on 2019-11-28
Reboot into the 5.3 kernel and remove the 5.4.  I can fix this in 5.3 as I have downloaded the source code but it will take some time to upload the fix to github

---

### Post by mdriwach on 2019-11-28
Thankyou So much for your help yes now i got back to kernel 5.3
just addition i had  extracted a lib/firmware/mediatek/mt7601u  from kerenl 5.4 
and modified file phy.c by following a tutorial on github and install it 
after it worked just few seconds and the errors getting back this journal of events 
(but now i use 5.3)+
```
[    3.176494] mt7601u 1-4:1.0: ASIC revision: 76010001 MAC revision: 76010500
[    3.302272] mt7601u 1-4:1.0: EEPROM ver:0c fae:00
[    3.726116] usbcore: registered new interface driver mt7601u
[    3.761759] mt7601u 1-4:1.0: rx urb failed: -71
[    3.763043] mt7601u 1-4:1.0: rx urb failed: -71
[    3.763133] mt7601u 1-4:1.0: rx urb failed: -71
[    3.763187] mt7601u 1-4:1.0: rx urb failed: -71
[    3.763245] mt7601u 1-4:1.0: rx urb failed: -71
[    3.763301] mt7601u 1-4:1.0: rx urb failed: -71
[    3.763357] mt7601u 1-4:1.0: rx urb failed: -71
[    3.763420] mt7601u 1-4:1.0: rx urb failed: -71
[    3.763483] mt7601u 1-4:1.0: rx urb failed: -71
[    3.763535] mt7601u 1-4:1.0: rx urb failed: -71
[    3.975457] mt7601u 1-4:1.0 wlx000f008c5b99: renamed from wlan0
[    5.158645] mt7601u 1-4:1.0: Error: MCU response pre-completed!
[    5.158698] mt7601u 1-4:1.0: Error: MCU resp urb failed:-71
[    5.158702] mt7601u 1-4:1.0: Error: MCU resp evt:0 seq:a-9!
[    5.475427] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    5.651153] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    5.815165] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    5.983126] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    6.159298] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    6.323103] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    6.487128] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    6.647116] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    6.807139] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    6.967137] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    7.127112] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    7.287136] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    7.447144] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    7.607136] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    7.775124] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    7.947163] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    8.107192] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    8.275108] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    8.435124] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    8.595129] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    8.755149] mt7601u 1-4:1.0: Vendor request req:07 off:101c failed:-71
[    8.807135] mt7601u 1-4:1.0: Error: BBP read 42 failed:-110!!
[   11.931643] mt7601u 1-4:1.0: ASIC revision: 76010001 MAC revision: 76010500
[   11.959572] mt7601u 1-4:1.0: Firmware Version: 0.1.00 Build: 7640 Build time: 201302052146____
[   13.005680] mt7601u 1-4:1.0: EEPROM ver:0c fae:00
[   13.307140] mt7601u_complete_rx: 6 callbacks suppressed
[   13.307146] mt7601u 1-4:1.0: rx urb failed: -71
[   13.307171] mt7601u 1-4:1.0: Error: MCU resp urb failed:-71
[   13.307175] mt7601u 1-4:1.0: Error: MCU resp evt:0 seq:f-e!
[   13.307192] mt7601u 1-4:1.0: rx urb failed: -71
[   13.307237] mt7601u 1-4:1.0: Error: MCU resp urb failed:-71
[   13.307240] mt7601u 1-4:1.0: Error: MCU resp evt:0 seq:f-e!
[   13.307271] mt7601u 1-4:1.0: rx urb failed: -71
[   13.307317] mt7601u 1-4:1.0: Error: MCU resp urb failed:-71
[   13.307319] mt7601u 1-4:1.0: Error: MCU resp evt:0 seq:f-e!
[   13.307356] mt7601u 1-4:1.0: rx urb failed: -71
[   13.307400] mt7601u 1-4:1.0: Error: MCU resp urb failed:-71
[   13.307402] mt7601u 1-4:1.0: Error: MCU resp evt:0 seq:f-e!
[   13.307436] mt7601u 1-4:1.0: rx urb failed: -71
[   13.307478] mt7601u 1-4:1.0: Error: MCU resp urb failed:-71
[   13.307481] mt7601u 1-4:1.0: Error: MCU resp evt:0 seq:f-e!
[   13.307483] mt7601u 1-4:1.0: Error: mt7601u_mcu_wait_resp timed out
[   13.475144] mt7601u 1-4:1.0: Vendor request req:07 off:0080 failed:-71
[   13.635366] mt7601u 1-4:1.0: Vendor request req:02 off:0080 failed:-71
[   13.799119] mt7601u 1-4:1.0: Vendor request req:02 off:0080 failed:-71
[   13.799183] mt7601u: probe of 1-4:1.0 failed with error -110


```

---

### Post by jeremy31 on 2019-11-29
Ok ```
sudo apt install git build-essential dkms
git clone https://github.com/jeremyb31/mt7601u-5.3.git
sudo dkms add ./mt7601u-5.3
sudo dkms install mt7601u/1.0
```

Reboot

Check ```
mokutil --sb-state
```
If it says Secure Boot is enabled, you will need to go into BIOS settings and disable Secure Boot

---

### Post by mdriwach on 2019-11-29
Fixeed!!!

---

### Post by mdriwach on 2019-11-29
Thankyou So much for your help 
And you great work here 
!!!!

---

### Post by cycleguy55 on 2019-12-10
> **jeremy31 said:**
> Ok ```
sudo apt install git build-essential dkms
git clone https://github.com/jeremyb31/mt7601u-5.3.git
sudo dkms add ./mt7601u-5.3
sudo dkms install mt7601u/1.0
```

Reboot

Check ```
mokutil --sb-state
```
If it says Secure Boot is enabled, you will need to go into BIOS settings and disable Secure Boot

This worked for me - THANKS!

---

