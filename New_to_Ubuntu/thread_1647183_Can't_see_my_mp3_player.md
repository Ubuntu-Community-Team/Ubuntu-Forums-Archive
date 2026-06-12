---
title: "Can't see my mp3 player"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by ohrange on 2010-12-16
I have an unbranded mp3 player which works fine in vista when I plug it into the USB port. In Ubuntu nothing happens when I plug it in and I can't find it anywhere. I don't really know how to look for it either :P

Any help greatly appreciated.

---

### Post by NightwishFan on 2010-12-16
Easy way to get information is:

1. Plug in your mp3 player.
2. Open Applications -> Accessories -> Terminal
3. Type the following and push enter.
```
dmesg
```
4. Post the output here, particularly the last few lines. However you might want to put code tags around it. (The # in the toolbar when posting)

---

### Post by ohrange on 2010-12-16
```
[  830.751057] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  835.082569] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  839.402547] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  843.621383] sd 5:0:0:0: [sdb] Unhandled error code
[  843.621389] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  843.621394] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[  843.621407] end_request: I/O error, dev sdb, sector 16776696
[  843.621413] Buffer I/O error on device sdb, logical block 2097087
[  843.740211] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  848.052376] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  852.380077] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  856.710067] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  861.042585] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  865.350099] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  869.560363] sd 5:0:0:0: [sdb] Unhandled error code
[  869.560370] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  869.560378] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[  869.560397] end_request: I/O error, dev sdb, sector 16776696
[  869.560405] Buffer I/O error on device sdb, logical block 2097087
[  869.682567] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  874.000095] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  878.340066] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  882.652587] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  886.980071] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  891.300069] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  895.526339] sd 5:0:0:0: [sdb] Unhandled error code
[  895.526347] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  895.526355] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[  895.526374] end_request: I/O error, dev sdb, sector 16776696
[  895.526382] Buffer I/O error on device sdb, logical block 2097087
[  895.650109] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  899.952586] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  904.302621] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  908.610073] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  912.930063] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  917.270633] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  921.450297] sd 5:0:0:0: [sdb] Unhandled error code
[  921.450303] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  921.450309] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[  921.450322] end_request: I/O error, dev sdb, sector 16776688
[  921.450328] Buffer I/O error on device sdb, logical block 2097086
[  921.570076] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  925.920066] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  930.230096] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  934.552605] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  938.891229] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  943.202605] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  947.423259] sd 5:0:0:0: [sdb] Unhandled error code
[  947.423266] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  947.423271] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[  947.423284] end_request: I/O error, dev sdb, sector 16776688
[  947.423291] Buffer I/O error on device sdb, logical block 2097086
[  947.542577] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  951.852540] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  956.192579] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  960.510134] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  964.820091] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  969.162606] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  973.353297] sd 5:0:0:0: [sdb] Unhandled error code
[  973.353303] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  973.353309] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[  973.353322] end_request: I/O error, dev sdb, sector 16776696
[  973.353328] Buffer I/O error on device sdb, logical block 2097087
[  973.472567] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  977.812588] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  982.131367] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  986.460073] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  990.790090] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  995.112498] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[  999.313185] sd 5:0:0:0: [sdb] Unhandled error code
[  999.313191] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  999.313197] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[  999.313209] end_request: I/O error, dev sdb, sector 16776696
[  999.313215] Buffer I/O error on device sdb, logical block 2097087
[  999.432338] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1003.762568] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1008.081366] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1012.400082] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1016.730072] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1021.062569] usb 5-2: reset full speed USB device using uhci_hcd and address 2
[ 1025.262172] sd 5:0:0:0: [sdb] Unhandled error code
[ 1025.262180] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 1025.262188] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 1025.262207] end_request: I/O error, dev sdb, sector 16776696
[ 1025.262215] Buffer I/O error on device sdb, logical block 2097087
[ 2814.792609] usb 5-2: USB disconnect, address 2
[ 2838.102578] usb 2-2: new high speed USB device using ehci_hcd and address 3
[ 2844.662620] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[ 2844.662633] hub 2-0:1.0: hub_port_status failed (err = -32)
[ 2844.870111] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 2845.170072] usb 5-2: new full speed USB device using uhci_hcd and address 3
[ 2845.446808] scsi6 : usb-storage 5-2:1.0
[ 2846.447692] scsi 6:0:0:0: Direct-Access     Generic  Audio   Product  v2.0 PQ: 0 ANSI: 2
[ 2846.448849] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 2846.455659] sd 6:0:0:0: [sdb] 8388352 1024-byte logical blocks: (8.58 GB/7.99 GiB)
[ 2846.458655] sd 6:0:0:0: [sdb] Write Protect is off
[ 2846.458662] sd 6:0:0:0: [sdb] Mode Sense: 20 00 00 00
[ 2846.458668] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2846.467663] sd 6:0:0:0: [sdb] 8388352 1024-byte logical blocks: (8.58 GB/7.99 GiB)
[ 2846.470656] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2846.470667]  sdb:
[ 2846.484665] sd 6:0:0:0: [sdb] 8388352 1024-byte logical blocks: (8.58 GB/7.99 GiB)
[ 2846.487664] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2846.487674] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 2846.632556] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2850.990077] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2855.250132] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2859.570077] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2863.912442] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2868.352571] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2872.574627] sd 6:0:0:0: [sdb] Unhandled error code
[ 2872.574635] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2872.574644] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[ 2872.574663] end_request: I/O error, dev sdb, sector 16776688
[ 2872.574672] Buffer I/O error on device sdb, logical block 2097086
[ 2872.752544] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2877.012588] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2881.330061] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2885.652547] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2889.990081] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2894.310068] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2898.510578] sd 6:0:0:0: [sdb] Unhandled error code
[ 2898.510584] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2898.510589] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[ 2898.510603] end_request: I/O error, dev sdb, sector 16776688
[ 2898.510609] Buffer I/O error on device sdb, logical block 2097086
[ 2898.632576] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2902.952570] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2907.292563] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2911.610074] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2915.940074] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2920.251830] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2924.454542] sd 6:0:0:0: [sdb] Unhandled error code
[ 2924.454547] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2924.454552] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 2924.454565] end_request: I/O error, dev sdb, sector 16776696
[ 2924.454572] Buffer I/O error on device sdb, logical block 2097087
[ 2924.570067] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2928.920074] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2933.231684] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2937.552570] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2941.880071] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2946.210075] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2950.416511] sd 6:0:0:0: [sdb] Unhandled error code
[ 2950.416517] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2950.416522] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 2950.416536] end_request: I/O error, dev sdb, sector 16776696
[ 2950.416542] Buffer I/O error on device sdb, logical block 2097087
[ 2950.540079] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2954.860083] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2959.181501] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2963.502569] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2967.830073] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2972.160106] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2976.370478] sd 6:0:0:0: [sdb] Unhandled error code
[ 2976.370484] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2976.370490] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 2976.370503] end_request: I/O error, dev sdb, sector 16776696
[ 2976.370509] Buffer I/O error on device sdb, logical block 2097087
[ 2976.490088] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2980.802587] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2985.140072] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2989.460074] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2993.780067] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 2998.112578] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3002.324447] sd 6:0:0:0: [sdb] Unhandled error code
[ 3002.324453] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3002.324458] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 3002.324471] end_request: I/O error, dev sdb, sector 16776696
[ 3002.324478] Buffer I/O error on device sdb, logical block 2097087
[ 3002.442559] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3006.750072] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3011.072592] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3015.410061] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3019.730105] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3024.060070] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3028.271411] sd 6:0:0:0: [sdb] Unhandled error code
[ 3028.271417] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3028.271422] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 3028.271435] end_request: I/O error, dev sdb, sector 16776696
[ 3028.271441] Buffer I/O error on device sdb, logical block 2097087
[ 3028.390093] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3032.702565] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3037.040090] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3041.350077] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3045.690859] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3050.020074] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3054.211379] sd 6:0:0:0: [sdb] Unhandled error code
[ 3054.211385] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3054.211390] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 3054.211403] end_request: I/O error, dev sdb, sector 16776696
[ 3054.211410] Buffer I/O error on device sdb, logical block 2097087
[ 3054.330068] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3058.651275] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3062.980082] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3067.310072] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3071.640087] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3075.952561] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3080.166346] sd 6:0:0:0: [sdb] Unhandled error code
[ 3080.166351] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3080.166357] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 3080.166370] end_request: I/O error, dev sdb, sector 16776696
[ 3080.166376] Buffer I/O error on device sdb, logical block 2097087
[ 3080.302574] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3084.610241] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3088.930097] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3093.250095] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3097.582370] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3101.912592] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3106.112312] sd 6:0:0:0: [sdb] Unhandled error code
[ 3106.112318] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3106.112323] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[ 3106.112336] end_request: I/O error, dev sdb, sector 16776688
[ 3106.112342] Buffer I/O error on device sdb, logical block 2097086
[ 3106.230092] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3110.560072] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3114.870074] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3119.210070] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3123.530095] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3127.910077] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3132.204278] sd 6:0:0:0: [sdb] Unhandled error code
[ 3132.204284] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3132.204290] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[ 3132.204303] end_request: I/O error, dev sdb, sector 16776688
[ 3132.204309] Buffer I/O error on device sdb, logical block 2097086
[ 3132.322590] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3136.640075] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3140.960067] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3145.290086] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3149.612571] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3153.931375] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3158.140247] sd 6:0:0:0: [sdb] Unhandled error code
[ 3158.140253] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3158.140258] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 3158.140271] end_request: I/O error, dev sdb, sector 16776696
[ 3158.140277] Buffer I/O error on device sdb, logical block 2097087
[ 3158.260067] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3162.590613] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3166.920384] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3171.232570] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3171.520076] Skipping EDID probe due to cached edid
[ 3175.572562] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3179.880075] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3184.102219] sd 6:0:0:0: [sdb] Unhandled error code
[ 3184.102225] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3184.102231] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 3184.102244] end_request: I/O error, dev sdb, sector 16776696
[ 3184.102251] Buffer I/O error on device sdb, logical block 2097087
[ 3184.222576] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3188.532627] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3192.862317] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3197.180078] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3201.512576] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3205.842264] usb 5-2: reset full speed USB device using uhci_hcd and address 3
[ 3210.045182] sd 6:0:0:0: [sdb] Unhandled error code
[ 3210.045188] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3210.045194] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[ 3210.045207] end_request: I/O error, dev sdb, sector 16776696
[ 3210.045213] Buffer I/O error on device sdb, logical block 2097087
[ 4351.232630] Skipping EDID probe due to cached edid
[ 4696.532544] CE: hpet increased min_delta_ns to 7500 nsec
[ 6192.712667] Skipping EDID probe due to cached edid
[ 7385.040131] usb 5-2: USB disconnect, address 3
[ 7670.892609] Skipping EDID probe due to cached edid
[ 8257.624083] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 8257.628581] SGI XFS Quota Management subsystem
[ 8257.636325] JFS: nTxBlock = 8192, nTxLock = 65536
[ 8257.661297] NTFS driver 2.1.29 [Flags: R/O MODULE].
[ 8257.681395] QNX4 filesystem 0.2.3 registered.
[ 8257.710670] Btrfs loaded
[ 8287.157724] udev[19290]: starting version 163
[ 8294.794639] type=1400 audit(1292555105.527:15): apparmor="STATUS" operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" pid=19365 comm="apparmor_parser"
[ 8294.869565] type=1400 audit(1292555105.597:16): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=19366 comm="apparmor_parser"
[ 8294.869740] type=1400 audit(1292555105.597:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=19366 comm="apparmor_parser"
[ 8294.869851] type=1400 audit(1292555105.597:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=19366 comm="apparmor_parser"
[ 8295.160514] type=1400 audit(1292555105.897:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=19369 comm="apparmor_parser"
[ 8295.160829] type=1400 audit(1292555105.897:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=19369 comm="apparmor_parser"
[ 8295.739313] type=1400 audit(1292555106.467:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=19370 comm="apparmor_parser"
[ 8300.159708] type=1400 audit(1292555110.887:22): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=19367 comm="apparmor_parser"
[ 8300.161221] type=1400 audit(1292555110.897:23): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=19367 comm="apparmor_parser"
[ 8300.162231] type=1400 audit(1292555110.897:24): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=19367 comm="apparmor_parser"
[ 8300.265546] type=1400 audit(1292555110.997:25): apparmor="STATUS" operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" pid=19406 comm="apparmor_parser"
[ 8300.341040] type=1400 audit(1292555111.077:26): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=19407 comm="apparmor_parser"
[ 8300.341212] type=1400 audit(1292555111.077:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=19407 comm="apparmor_parser"
[ 8300.341321] type=1400 audit(1292555111.077:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=19407 comm="apparmor_parser"
[ 8300.620500] type=1400 audit(1292555111.357:29): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=19410 comm="apparmor_parser"
[ 8300.620802] type=1400 audit(1292555111.357:30): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=19410 comm="apparmor_parser"
[ 8300.705310] type=1400 audit(1292555111.437:31): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/tcpdump" pid=19411 comm="apparmor_parser"
[ 8305.631291] type=1400 audit(1292555116.367:32): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=19408 comm="apparmor_parser"
[ 8305.632664] type=1400 audit(1292555116.367:33): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=19408 comm="apparmor_parser"
[ 8305.633692] type=1400 audit(1292555116.367:34): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-thumbnailer" pid=19408 comm="apparmor_parser"
[ 8324.362592] type=1400 audit(1292555135.097:35): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=19608 comm="apparmor_parser"
[ 8324.362975] type=1400 audit(1292555135.097:36): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=19608 comm="apparmor_parser"
[ 8707.680123] Skipping EDID probe due to cached edid
[11187.860115] usb 2-2: new high speed USB device using ehci_hcd and address 4
[11194.402606] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[11194.402618] hub 2-0:1.0: hub_port_status failed (err = -32)
[11194.610111] hub 2-0:1.0: unable to enumerate USB device on port 2
[11194.920083] usb 5-2: new full speed USB device using uhci_hcd and address 4
[11195.204836] scsi7 : usb-storage 5-2:1.0
[11196.205719] scsi 7:0:0:0: Direct-Access     Generic  Audio   Product  v2.0 PQ: 0 ANSI: 2
[11196.206894] sd 7:0:0:0: Attached scsi generic sg2 type 0
[11196.214695] sd 7:0:0:0: [sdb] 8388352 1024-byte logical blocks: (8.58 GB/7.99 GiB)
[11196.217681] sd 7:0:0:0: [sdb] Write Protect is off
[11196.217688] sd 7:0:0:0: [sdb] Mode Sense: 20 00 00 00
[11196.217692] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[11196.226691] sd 7:0:0:0: [sdb] 8388352 1024-byte logical blocks: (8.58 GB/7.99 GiB)
[11196.229681] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[11196.229692]  sdb:
[11196.242704] sd 7:0:0:0: [sdb] 8388352 1024-byte logical blocks: (8.58 GB/7.99 GiB)
[11196.245699] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[11196.245709] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[11196.392596] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11200.670097] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11205.060094] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11209.462579] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11213.772585] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11218.112574] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11222.303640] sd 7:0:0:0: [sdb] Unhandled error code
[11222.303646] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11222.303651] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[11222.303664] end_request: I/O error, dev sdb, sector 16776688
[11222.303670] Buffer I/O error on device sdb, logical block 2097086
[11222.422594] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11226.750071] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11231.070217] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11235.400071] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11239.730096] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11244.052574] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11248.260609] sd 7:0:0:0: [sdb] Unhandled error code
[11248.260615] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11248.260621] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[11248.260634] end_request: I/O error, dev sdb, sector 16776688
[11248.260640] Buffer I/O error on device sdb, logical block 2097086
[11248.380076] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11252.701714] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11257.020101] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11261.350085] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11265.670077] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11270.002578] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11274.200570] sd 7:0:0:0: [sdb] Unhandled error code
[11274.200576] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11274.200581] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11274.200594] end_request: I/O error, dev sdb, sector 16776696
[11274.200601] Buffer I/O error on device sdb, logical block 2097087
[11274.322587] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11278.650095] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11282.980113] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11287.302550] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11291.620110] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11295.950084] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11300.150540] sd 7:0:0:0: [sdb] Unhandled error code
[11300.150547] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11300.150552] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11300.150565] end_request: I/O error, dev sdb, sector 16776696
[11300.150571] Buffer I/O error on device sdb, logical block 2097087
[11300.270085] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11304.610067] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11308.920092] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11313.250073] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11317.570066] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11321.900070] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11326.115508] sd 7:0:0:0: [sdb] Unhandled error code
[11326.115514] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11326.115520] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11326.115533] end_request: I/O error, dev sdb, sector 16776696
[11326.115539] Buffer I/O error on device sdb, logical block 2097087
[11326.230117] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11330.542606] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11334.870117] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11339.190073] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11343.530072] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11347.850083] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11352.051482] sd 7:0:0:0: [sdb] Unhandled error code
[11352.051490] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11352.051498] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11352.051517] end_request: I/O error, dev sdb, sector 16776696
[11352.051525] Buffer I/O error on device sdb, logical block 2097087
[11352.170088] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11356.490083] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11360.822569] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11365.140078] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11369.472597] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11373.790330] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11378.001443] sd 7:0:0:0: [sdb] Unhandled error code
[11378.001449] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11378.001454] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11378.001468] end_request: I/O error, dev sdb, sector 16776696
[11378.001474] Buffer I/O error on device sdb, logical block 2097087
[11378.120127] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11382.440365] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11386.780107] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11391.112621] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11395.430113] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11399.760955] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11403.963409] sd 7:0:0:0: [sdb] Unhandled error code
[11403.963415] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11403.963420] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11403.963433] end_request: I/O error, dev sdb, sector 16776696
[11403.963439] Buffer I/O error on device sdb, logical block 2097087
[11404.080098] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11408.390075] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11412.720072] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11417.052575] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11421.382060] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11425.702570] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11429.902374] sd 7:0:0:0: [sdb] Unhandled error code
[11429.902380] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11429.902386] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11429.902399] end_request: I/O error, dev sdb, sector 16776696
[11429.902405] Buffer I/O error on device sdb, logical block 2097087
[11430.032630] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11434.350074] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11438.670107] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11443.000080] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11447.332603] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11451.640071] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11455.860344] sd 7:0:0:0: [sdb] Unhandled error code
[11455.860350] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11455.860355] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[11455.860368] end_request: I/O error, dev sdb, sector 16776688
[11455.860375] Buffer I/O error on device sdb, logical block 2097086
[11455.980102] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11460.302575] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11464.620095] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11468.940099] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11473.282570] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11477.590097] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11481.800324] sd 7:0:0:0: [sdb] Unhandled error code
[11481.800332] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11481.800340] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe f8 00 00 01 00
[11481.800359] end_request: I/O error, dev sdb, sector 16776688
[11481.800368] Buffer I/O error on device sdb, logical block 2097086
[11481.920079] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11486.240104] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11490.570094] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11494.900095] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11499.232609] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11503.552588] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11507.765281] sd 7:0:0:0: [sdb] Unhandled error code
[11507.765287] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11507.765292] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11507.765305] end_request: I/O error, dev sdb, sector 16776696
[11507.765312] Buffer I/O error on device sdb, logical block 2097087
[11507.882595] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11512.192592] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11516.520071] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11520.842568] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11525.172568] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11529.500075] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11533.702266] sd 7:0:0:0: [sdb] Unhandled error code
[11533.702274] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11533.702282] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11533.702304] end_request: I/O error, dev sdb, sector 16776696
[11533.702310] Buffer I/O error on device sdb, logical block 2097087
[11533.821759] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11538.140074] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11542.472560] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11546.790107] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11551.130094] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11555.440093] usb 5-2: reset full speed USB device using uhci_hcd and address 4
[11559.651203] sd 7:0:0:0: [sdb] Unhandled error code
[11559.651208] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[11559.651214] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 7f fe fc 00 00 01 00
[11559.651226] end_request: I/O error, dev sdb, sector 16776696
[11559.651232] Buffer I/O error on device sdb, logical block 2097087
```

---

### Post by NightwishFan on 2010-12-16
This line here seems to suggest the system does not know how to read the file system.
```
[11559.651232] Buffer I/O error on device sdb, logical block 2097087
```

I am not sure where to go from there, did you partition the device yourself?

---

### Post by ohrange on 2010-12-16
Nope, I just got it out of the packet yesterday and haven't done anything with it yet.

---

### Post by NightwishFan on 2010-12-16
I am not sure then, sorry. :( If it is a common player usually they just work for me.

---

### Post by ohrange on 2010-12-17
> **NightwishFan said:**
> I am not sure then, sorry. :( If it is a common player usually they just work for me.

Thanks for trying :)

---

### Post by NightwishFan on 2010-12-17
Sure if I think of anything, I will get back to you.

Does the device show up in System -> Administration -> Disk Utility? Also, does it show up on the side in Rhythmbox Music Player?

---

### Post by ohrange on 2010-12-17
No, it doesn't show up in either.

---

### Post by ohrange on 2010-12-17
Anyone else have any ideas?

---

### Post by thatguruguy on 2010-12-17
I've never heard of an unbranded mp3 player.  It has no brand at all?  None? No company made it?

Did you make it yourself out of spare parts in your basement?

---

### Post by laus_deo on 2010-12-17
> Did you make it yourself out of spare parts in your basement?

lol, that would be pretty cool. But anyway, I had this happen to me for a little bit too. With a newish ipod, ubuntu would only recognize about one out of every 3-5 time I plugged it in. As time went on it got better, but I'm not quite sure what was up with that.

---

### Post by rockerphil on 2010-12-17
here's what i would do. open up a terminal and run this command

```
sudo fdisk -l
```

that will list your partition table. most mp3 players are picked up as a removable hard drive. on a single drive computer the internal drive will show up as /dev/sda and the mp3 player will be /dev/sdb, but the mp3 player will always be the entry at the bottom of the list. you may try manually mounting the mp3 player through the terminal. to do this simply make a directory in your home folder for it to mount to, for example ~/mp3. you can do this in the terminal by running

```
mkdir ~/mp3
```

then simply use the mount command to mount the drive to your newly created folder, for example, if your mp3 player is /dev/sdb and you made the folder ~/mp3 you would run this command to mount the drive

```
sudo mount /dev/sdb1 ~/mp3
```

you should then be able to access the mp3 player's file system through your standard file manager, such as Nautilus in Gnome. hope this helps,

Phil

edit: don't forget that when you're finished adding/removing the files on your mp3 player that you need to eject the device from the file system. this can be done either with the eject command, for example

```
sudo eject /dev/sdb1
```

or with the umount command (please take careful not of the fact that there is no N in this command, it's simply umount, not unmount) for example,

```
sudo umount /dev/sdb1
```

---

### Post by Chronon on 2010-12-17
> **thatguruguy said:**
> I've never heard of an unbranded mp3 player.  It has no brand at all?  None? No company made it?

Did you make it yourself out of spare parts in your basement?

Lots of unbranded players come out of China and are styled to appear like name-brand players.

---

### Post by ohrange on 2010-12-17
> **rockerphil said:**
> here's what i would do. open up a terminal and run this command

```
sudo fdisk -l
```

that will list your partition table. most mp3 players are picked up as a removable hard drive. on a single drive computer the internal drive will show up as /dev/sda and the mp3 player will be /dev/sdb, but the mp3 player will always be the entry at the bottom of the list. you may try manually mounting the mp3 player through the terminal. to do this simply make a directory in your home folder for it to mount to, for example ~/mp3. you can do this in the terminal by running

```
mkdir ~/mp3
```

then simply use the mount command to mount the drive to your newly created folder, for example, if your mp3 player is /dev/sdb and you made the folder ~/mp3 you would run this command to mount the drive

```
sudo mount /dev/sdb1 ~/mp3
```

you should then be able to access the mp3 player's file system through your standard file manager, such as Nautilus in Gnome. hope this helps,

Phil

edit: don't forget that when you're finished adding/removing the files on your mp3 player that you need to eject the device from the file system. this can be done either with the eject command, for example

```
sudo eject /dev/sdb1
```

or with the umount command (please take careful not of the fact that there is no N in this command, it's simply umount, not unmount) for example,

```
sudo umount /dev/sdb1
```

This seems to be the device here:
```
Disk /dev/sdc: 8589 MB, 8589672448 bytes
64 heads, 32 sectors/track, 4095 cylinders
Units = cylinders of 2048 * 1024 = 2097152 bytes
Sector size (logical/physical): 1024 bytes / 1024 bytes
I/O size (minimum/optimal): 1024 bytes / 1024 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?      379950      937327  1141509631   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       82368     1027695  1936028240   65  Novell Netware 386
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      913029     1858355  1936028192   79  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/sdc4   ?     1409025     1409052       55499    d  Unknown
Partition 4 does not end on cylinder boundary.
```

If I try to mount any the partitions I get this:
```
mount: special device /dev/sdc1 does not exist

```

---

### Post by Chronon on 2010-12-17
It seems to not have a partition table.

Maybe this helps?
[http://groups.google.com/group/alt.os.linux.suse/browse_thread/thread/ac1094fda4a3b428/7572f00025438a37?q=hotplug+usb+9.2+fstab+group:*suse*&_done=%2Fgroups%3Fq%3Dhotplug+usb+9.%202+fstab+group:*suse*%26qt_s%3DSearch+Gro%3Cbr%20/%3Eups%26&_doneTitle=Back+to+Search](http://groups.google.com/group/alt.os.linux.suse/browse_thread/thread/ac1094fda4a3b428/7572f00025438a37?q=hotplug+usb+9.2+fstab+group:*suse*&_done=%2Fgroups%3Fq%3Dhotplug+usb+9.%202+fstab+group:*suse*%26qt_s%3DSearch+Gro%3Cbr%20/%3Eups%26&_doneTitle=Back+to+Search)

can you mount /dev/sdc directly?

---

### Post by Hamchan on 2010-12-17
I have a Sansa mp3 player that will only be recognized in Linux when I change the usb settings in the player. I have to change the usb mode to MSC.

Have you checked the settings in your unbranded mp3 player? Perhaps your player works similar to mine.

---

### Post by Chronon on 2010-12-18
You can only mount a player in MSC mode (it's the only way for it to behave as a UMS device).  If your player can't be forced into MSC mode then you won't be able to mount it.

---

### Post by ohrange on 2010-12-18
> **Chronon said:**
> It seems to not have a partition table.

Maybe this helps?
[http://groups.google.com/group/alt.os.linux.suse/browse_thread/thread/ac1094fda4a3b428/7572f00025438a37?q=hotplug+usb+9.2+fstab+group:*suse*&_done=%2Fgroups%3Fq%3Dhotplug+usb+9.%202+fstab+group:*suse*%26qt_s%3DSearch+Gro%3Cbr%20/%3Eups%26&_doneTitle=Back+to+Search](http://groups.google.com/group/alt.os.linux.suse/browse_thread/thread/ac1094fda4a3b428/7572f00025438a37?q=hotplug+usb+9.2+fstab+group:*suse*&_done=%2Fgroups%3Fq%3Dhotplug+usb+9.%202+fstab+group:*suse*%26qt_s%3DSearch+Gro%3Cbr%20/%3Eups%26&_doneTitle=Back+to+Search)

can you mount /dev/sdc directly?

Your link is a bit over my head. If I try ```
sudo mount /dev/sdc ~/mp3
```

it asks for my password, which I enter, and then the normal prompt disappears and nothing happens.

---

### Post by ohrange on 2010-12-18
> **Chronon said:**
> It seems to not have a partition table.

Maybe this helps?
[http://groups.google.com/group/alt.os.linux.suse/browse_thread/thread/ac1094fda4a3b428/7572f00025438a37?q=hotplug+usb+9.2+fstab+group:*suse*&_done=%2Fgroups%3Fq%3Dhotplug+usb+9.%202+fstab+group:*suse*%26qt_s%3DSearch+Gro%3Cbr%20/%3Eups%26&_doneTitle=Back+to+Search](http://groups.google.com/group/alt.os.linux.suse/browse_thread/thread/ac1094fda4a3b428/7572f00025438a37?q=hotplug+usb+9.2+fstab+group:*suse*&_done=%2Fgroups%3Fq%3Dhotplug+usb+9.%202+fstab+group:*suse*%26qt_s%3DSearch+Gro%3Cbr%20/%3Eups%26&_doneTitle=Back+to+Search)

can you mount /dev/sdc directly?

Oh, that worked actually :) It was just taking a long time.
So will I have to do that every time I plug it in?

---

### Post by Chronon on 2010-12-18
Yes, you will have to manually mount your player until we can figure out how to tell Ubuntu that it should do this.  (It seems that the lack of partition table confuses udev and prevents automounting from happening.)  Perhaps someone who sees this will know how to force automounting.

Maybe adding it to fstab will work.  If so, it's worth following this post:
[http://ubuntuforums.org/showthread.php?t=1498130](http://ubuntuforums.org/showthread.php?t=1498130)

---

