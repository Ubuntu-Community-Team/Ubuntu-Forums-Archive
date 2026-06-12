---
title: "External Hard Drive not detected on Ubuntu 10.04"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by linuxfreak65 on 2011-08-29
Hello to the community.  I am new to both Linux and Ubuntu.  My problem is that Ubuntu 10.04 is not detecting and auto mounting my external hard drive after a re-install of Ubuntu 10.04.  Before the re-install, the OS easily detected and mounted the external hard drive in question.  Thinking it might be a USB problem, I inserted a flash drive in one of the usb ports, Ubuntu detected it immediately.  I ran out of ideas on how to solve this.  Any help would be very much appreciated as I have important documents and photos on the external drive, thanks. :KS

---

### Post by pjd99 on 2011-08-30
Open a terminal, plug the drive in (switch on if necessary) and post the output of:

```

dmesg | tail

```There should be some references to a sdX device, where X is b,c,d etc, some information about the device and why it won't automount. You may need more of the dmesg output as well, so you can run it without the "| tail" part to get the whole log.

---

### Post by linuxfreak65 on 2011-08-30
Here is what I got after pasting command in the terminal:

[ 4085.538636] sr 51:0:0:0: Attached scsi generic sg2 type 5
[ 4085.543823] cdrom: issuing MRW back ground format suspend
[ 4146.145283] usb 2-2.4: new full speed USB device using uhci_hcd and address 53
[ 4146.271454] usb 2-2.4: configuration #1 chosen from 1 choice
[ 4146.293734] scsi52 : SCSI emulation for USB Mass Storage devices
[ 4146.301539] usb-storage: device found at 53
[ 4146.301544] usb-storage: waiting for device to settle before scanning
[ 4149.527894] usb 2-2.4: USB disconnect, address 53
[ 5531.845562] usb 2-2.4: new full speed USB device using uhci_hcd and address 54
[ 5531.875549] hub 2-2:1.0: unable to enumerate USB device on port 4

but what does it all mean?
Thanks, pjd99

---

### Post by linuxfreak65 on 2011-08-30
I could not find an sdX device like you said in the entire log

Terminal:

> [ 2092.117494] scsi27 : SCSI emulation for USB Mass Storage devices
[ 2092.124900] usb-storage: device found at 28
[ 2092.124905] usb-storage: waiting for device to settle before scanning
[ 2097.126812] usb-storage: device scan complete
[ 2097.129152] scsi scan: INQUIRY result too short (5), using 36
[ 2097.129164] scsi 27:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2113.525614] usb 2-2.4: USB disconnect, address 28
[ 2113.527817] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2113.528262] sr 27:0:0:0: Attached scsi CD-ROM sr1
[ 2113.528407] sr 27:0:0:0: Attached scsi generic sg2 type 5
[ 2174.137612] usb 2-2.4: new full speed USB device using uhci_hcd and address 29
[ 2174.263780] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2174.281961] scsi28 : SCSI emulation for USB Mass Storage devices
[ 2174.289145] usb-storage: device found at 29
[ 2174.289150] usb-storage: waiting for device to settle before scanning
[ 2179.290107] usb-storage: device scan complete
[ 2179.293083] scsi scan: INQUIRY result too short (5), using 36
[ 2179.293095] scsi 28:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2195.694006] usb 2-2.4: USB disconnect, address 29
[ 2195.696422] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2195.698440] sr 28:0:0:0: Attached scsi CD-ROM sr1
[ 2195.699250] sr 28:0:0:0: Attached scsi generic sg2 type 5
[ 2256.305558] usb 2-2.4: new full speed USB device using uhci_hcd and address 30
[ 2256.431725] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2256.452510] scsi29 : SCSI emulation for USB Mass Storage devices
[ 2256.456824] usb-storage: device found at 30
[ 2256.456829] usb-storage: waiting for device to settle before scanning
[ 2261.458050] usb-storage: device scan complete
[ 2261.461029] scsi scan: INQUIRY result too short (5), using 36
[ 2261.461040] scsi 29:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2277.860213] usb 2-2.4: USB disconnect, address 30
[ 2277.865118] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2277.865911] sr 29:0:0:0: Attached scsi CD-ROM sr1
[ 2277.866729] sr 29:0:0:0: Attached scsi generic sg2 type 5
[ 2277.871430] cdrom: issuing MRW back ground format suspend
[ 2338.469510] usb 2-2.4: new full speed USB device using uhci_hcd and address 31
[ 2338.595671] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2338.615675] scsi30 : SCSI emulation for USB Mass Storage devices
[ 2338.619875] usb-storage: device found at 31
[ 2338.619881] usb-storage: waiting for device to settle before scanning
[ 2343.617995] usb-storage: device scan complete
[ 2343.620974] scsi scan: INQUIRY result too short (5), using 36
[ 2343.620985] scsi 30:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2360.018492] usb 2-2.4: USB disconnect, address 31
[ 2360.020988] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2360.021800] sr 30:0:0:0: Attached scsi CD-ROM sr1
[ 2360.022614] sr 30:0:0:0: Attached scsi generic sg2 type 5
[ 2420.637452] usb 2-2.4: new full speed USB device using uhci_hcd and address 32
[ 2420.763617] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2420.781762] scsi31 : SCSI emulation for USB Mass Storage devices
[ 2420.788935] usb-storage: device found at 32
[ 2420.788941] usb-storage: waiting for device to settle before scanning
[ 2425.789942] usb-storage: device scan complete
[ 2425.792918] scsi scan: INQUIRY result too short (5), using 36
[ 2425.792929] scsi 31:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2442.193852] usb 2-2.4: USB disconnect, address 32
[ 2442.195979] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2442.196275] sr 31:0:0:0: Attached scsi CD-ROM sr1
[ 2442.196411] sr 31:0:0:0: Attached scsi generic sg2 type 5
[ 2502.805394] usb 2-2.4: new full speed USB device using uhci_hcd and address 33
[ 2502.931560] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2502.951514] scsi32 : SCSI emulation for USB Mass Storage devices
[ 2502.960901] usb-storage: device found at 33
[ 2502.960906] usb-storage: waiting for device to settle before scanning
[ 2507.961885] usb-storage: device scan complete
[ 2507.964864] scsi scan: INQUIRY result too short (5), using 36
[ 2507.964876] scsi 32:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2524.366887] usb 2-2.4: USB disconnect, address 33
[ 2524.369156] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2524.369936] sr 32:0:0:0: Attached scsi CD-ROM sr1
[ 2524.370741] sr 32:0:0:0: Attached scsi generic sg2 type 5
[ 2584.973341] usb 2-2.4: new full speed USB device using uhci_hcd and address 34
[ 2585.099502] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2585.119692] scsi33 : SCSI emulation for USB Mass Storage devices
[ 2585.124068] usb-storage: device found at 34
[ 2585.124073] usb-storage: waiting for device to settle before scanning
[ 2590.125843] usb-storage: device scan complete
[ 2590.128814] scsi scan: INQUIRY result too short (5), using 36
[ 2590.128825] scsi 33:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2606.524982] usb 2-2.4: USB disconnect, address 34
[ 2606.529189] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2606.529977] sr 33:0:0:0: Attached scsi CD-ROM sr1
[ 2606.530783] sr 33:0:0:0: Attached scsi generic sg2 type 5
[ 2606.535492] cdrom: issuing MRW back ground format suspend
[ 2667.137284] usb 2-2.4: new full speed USB device using uhci_hcd and address 35
[ 2667.263452] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2667.285058] scsi34 : SCSI emulation for USB Mass Storage devices
[ 2667.289169] usb-storage: device found at 35
[ 2667.289174] usb-storage: waiting for device to settle before scanning
[ 2672.289774] usb-storage: device scan complete
[ 2672.292751] scsi scan: INQUIRY result too short (5), using 36
[ 2672.292761] scsi 34:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2688.690661] usb 2-2.4: USB disconnect, address 35
[ 2688.693145] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2688.693931] sr 34:0:0:0: Attached scsi CD-ROM sr1
[ 2688.694750] sr 34:0:0:0: Attached scsi generic sg2 type 5
[ 2749.305227] usb 2-2.4: new full speed USB device using uhci_hcd and address 36
[ 2749.431405] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2749.454137] scsi35 : SCSI emulation for USB Mass Storage devices
[ 2749.459698] usb-storage: device found at 36
[ 2749.459703] usb-storage: waiting for device to settle before scanning
[ 2754.457712] usb-storage: device scan complete
[ 2754.460695] scsi scan: INQUIRY result too short (5), using 36
[ 2754.460705] scsi 35:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2770.858716] usb 2-2.4: USB disconnect, address 36
[ 2770.861143] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2770.861928] sr 35:0:0:0: Attached scsi CD-ROM sr1
[ 2770.862741] sr 35:0:0:0: Attached scsi generic sg2 type 5
[ 2831.473160] usb 2-2.4: new full speed USB device using uhci_hcd and address 37
[ 2831.598335] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2831.618441] scsi36 : SCSI emulation for USB Mass Storage devices
[ 2831.622743] usb-storage: device found at 37
[ 2831.622748] usb-storage: waiting for device to settle before scanning
[ 2836.621661] usb-storage: device scan complete
[ 2836.624643] scsi scan: INQUIRY result too short (5), using 36
[ 2836.624654] scsi 36:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2853.022126] usb 2-2.4: USB disconnect, address 37
[ 2853.024601] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2853.025384] sr 36:0:0:0: Attached scsi CD-ROM sr1
[ 2853.026186] sr 36:0:0:0: Attached scsi generic sg2 type 5
[ 2853.031305] cdrom: issuing MRW back ground format suspend
[ 2913.642118] usb 2-2.4: new full speed USB device using uhci_hcd and address 38
[ 2913.767276] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2913.788276] scsi37 : SCSI emulation for USB Mass Storage devices
[ 2913.792571] usb-storage: device found at 38
[ 2913.792576] usb-storage: waiting for device to settle before scanning
[ 2918.793606] usb-storage: device scan complete
[ 2918.797011] scsi scan: INQUIRY result too short (5), using 36
[ 2918.797022] scsi 37:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 2935.194582] usb 2-2.4: USB disconnect, address 38
[ 2935.197026] sr1: scsi3-mmc drive: 0x/0x caddy
[ 2935.197807] sr 37:0:0:0: Attached scsi CD-ROM sr1
[ 2935.198615] sr 37:0:0:0: Attached scsi generic sg2 type 5
[ 2995.806062] usb 2-2.4: new full speed USB device using uhci_hcd and address 39
[ 2995.932225] usb 2-2.4: configuration #1 chosen from 1 choice
[ 2995.952585] scsi38 : SCSI emulation for USB Mass Storage devices
[ 2995.956917] usb-storage: device found at 39
[ 2995.956922] usb-storage: waiting for device to settle before scanning
[ 3000.957550] usb-storage: device scan complete
[ 3000.960648] scsi scan: INQUIRY result too short (5), using 36
[ 3000.960660] scsi 38:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3017.358021] usb 2-2.4: USB disconnect, address 39
[ 3017.360775] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3017.361554] sr 38:0:0:0: Attached scsi CD-ROM sr1
[ 3017.362427] sr 38:0:0:0: Attached scsi generic sg2 type 5
[ 3017.367397] cdrom: issuing MRW back ground format suspend
[ 3077.974004] usb 2-2.4: new full speed USB device using uhci_hcd and address 40
[ 3078.103174] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3078.124150] scsi39 : SCSI emulation for USB Mass Storage devices
[ 3078.128448] usb-storage: device found at 40
[ 3078.128454] usb-storage: waiting for device to settle before scanning
[ 3083.129498] usb-storage: device scan complete
[ 3083.132473] scsi scan: INQUIRY result too short (5), using 36
[ 3083.132483] scsi 39:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3099.530152] usb 2-2.4: USB disconnect, address 40
[ 3099.533865] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3099.534654] sr 39:0:0:0: Attached scsi CD-ROM sr1
[ 3099.540329] sr 39:0:0:0: Attached scsi generic sg2 type 5
[ 3160.137952] usb 2-2.4: new full speed USB device using uhci_hcd and address 41
[ 3160.268141] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3160.288483] scsi40 : SCSI emulation for USB Mass Storage devices
[ 3160.296568] usb-storage: device found at 41
[ 3160.296574] usb-storage: waiting for device to settle before scanning
[ 3165.297437] usb-storage: device scan complete
[ 3165.300636] scsi scan: INQUIRY result too short (5), using 36
[ 3165.300647] scsi 40:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3181.698391] usb 2-2.4: USB disconnect, address 41
[ 3181.700817] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3181.701595] sr 40:0:0:0: Attached scsi CD-ROM sr1
[ 3181.702395] sr 40:0:0:0: Attached scsi generic sg2 type 5
[ 3181.707810] cdrom: issuing MRW back ground format suspend
[ 3242.305893] usb 2-2.4: new full speed USB device using uhci_hcd and address 42
[ 3242.432078] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3242.452500] scsi41 : SCSI emulation for USB Mass Storage devices
[ 3242.456891] usb-storage: device found at 42
[ 3242.456897] usb-storage: waiting for device to settle before scanning
[ 3247.457382] usb-storage: device scan complete
[ 3247.460656] scsi scan: INQUIRY result too short (5), using 36
[ 3247.460667] scsi 41:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3263.858204] usb 2-2.4: USB disconnect, address 42
[ 3263.860671] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3263.861448] sr 41:0:0:0: Attached scsi CD-ROM sr1
[ 3263.862260] sr 41:0:0:0: Attached scsi generic sg2 type 5
[ 3324.473831] usb 2-2.4: new full speed USB device using uhci_hcd and address 43
[ 3324.600002] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3324.620314] scsi42 : SCSI emulation for USB Mass Storage devices
[ 3324.624412] usb-storage: device found at 43
[ 3324.624417] usb-storage: waiting for device to settle before scanning
[ 3329.625325] usb-storage: device scan complete
[ 3329.628639] scsi scan: INQUIRY result too short (5), using 36
[ 3329.628650] scsi 42:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3346.026231] usb 2-2.4: USB disconnect, address 43
[ 3346.028655] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3346.029434] sr 42:0:0:0: Attached scsi CD-ROM sr1
[ 3346.030238] sr 42:0:0:0: Attached scsi generic sg2 type 5
[ 3346.035657] cdrom: issuing MRW back ground format suspend
[ 3406.641792] usb 2-2.4: new full speed USB device using uhci_hcd and address 44
[ 3406.767950] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3406.788197] scsi43 : SCSI emulation for USB Mass Storage devices
[ 3406.792813] usb-storage: device found at 44
[ 3406.792819] usb-storage: waiting for device to settle before scanning
[ 3411.793271] usb-storage: device scan complete
[ 3411.796642] scsi scan: INQUIRY result too short (5), using 36
[ 3411.796654] scsi 43:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3428.194272] usb 2-2.4: USB disconnect, address 44
[ 3428.196764] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3428.197542] sr 43:0:0:0: Attached scsi CD-ROM sr1
[ 3428.198405] sr 43:0:0:0: Attached scsi generic sg2 type 5
[ 3488.809739] usb 2-2.4: new full speed USB device using uhci_hcd and address 45
[ 3488.935887] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3488.960389] scsi44 : SCSI emulation for USB Mass Storage devices
[ 3488.964413] usb-storage: device found at 45
[ 3488.964418] usb-storage: waiting for device to settle before scanning
[ 3493.965214] usb-storage: device scan complete
[ 3493.968351] scsi scan: INQUIRY result too short (5), using 36
[ 3493.968363] scsi 44:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3510.365386] usb 2-2.4: USB disconnect, address 45
[ 3510.367258] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3510.368092] sr 44:0:0:0: Attached scsi CD-ROM sr1
[ 3510.368260] sr 44:0:0:0: Attached scsi generic sg2 type 5
[ 3570.973675] usb 2-2.4: new full speed USB device using uhci_hcd and address 46
[ 3571.099837] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3571.120134] scsi45 : SCSI emulation for USB Mass Storage devices
[ 3571.123946] usb-storage: device found at 46
[ 3571.123951] usb-storage: waiting for device to settle before scanning
[ 3576.124057] usb-storage: device scan complete
[ 3576.127163] scsi scan: INQUIRY result too short (5), using 36
[ 3576.127175] scsi 45:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3592.525607] usb 2-2.4: USB disconnect, address 46
[ 3592.527807] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3592.528258] sr 45:0:0:0: Attached scsi CD-ROM sr1
[ 3592.528402] sr 45:0:0:0: Attached scsi generic sg2 type 5
[ 3592.533008] cdrom: issuing MRW back ground format suspend
[ 3653.141644] usb 2-2.4: new full speed USB device using uhci_hcd and address 47
[ 3653.267806] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3653.288164] scsi46 : SCSI emulation for USB Mass Storage devices
[ 3653.292545] usb-storage: device found at 47
[ 3653.292551] usb-storage: waiting for device to settle before scanning
[ 3658.294105] usb-storage: device scan complete
[ 3658.297078] scsi scan: INQUIRY result too short (5), using 36
[ 3658.297090] scsi 46:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3674.693565] usb 2-2.4: USB disconnect, address 47
[ 3674.695931] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3674.696225] sr 46:0:0:0: Attached scsi CD-ROM sr1
[ 3674.696365] sr 46:0:0:0: Attached scsi generic sg2 type 5
[ 3735.313564] usb 2-2.4: new full speed USB device using uhci_hcd and address 48
[ 3735.439725] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3735.456258] scsi47 : SCSI emulation for USB Mass Storage devices
[ 3735.464152] usb-storage: device found at 48
[ 3735.464157] usb-storage: waiting for device to settle before scanning
[ 3740.466045] usb-storage: device scan complete
[ 3740.469028] scsi scan: INQUIRY result too short (5), using 36
[ 3740.469039] scsi 47:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3756.865988] usb 2-2.4: USB disconnect, address 48
[ 3756.868411] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3756.869172] sr 47:0:0:0: Attached scsi CD-ROM sr1
[ 3756.869967] sr 47:0:0:0: Attached scsi generic sg2 type 5
[ 3756.875368] cdrom: issuing MRW back ground format suspend
[ 3817.477497] usb 2-2.4: new full speed USB device using uhci_hcd and address 49
[ 3817.603664] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3817.623648] scsi48 : SCSI emulation for USB Mass Storage devices
[ 3817.627850] usb-storage: device found at 49
[ 3817.627855] usb-storage: waiting for device to settle before scanning
[ 3822.635183] usb-storage: device scan complete
[ 3822.638036] scsi scan: INQUIRY result too short (5), using 36
[ 3822.638048] scsi 48:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3839.037836] usb 2-2.4: USB disconnect, address 49
[ 3839.040387] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3839.041169] sr 48:0:0:0: Attached scsi CD-ROM sr1
[ 3839.041982] sr 48:0:0:0: Attached scsi generic sg2 type 5
[ 3839.047359] cdrom: issuing MRW back ground format suspend
[ 3899.641442] usb 2-2.4: new full speed USB device using uhci_hcd and address 50
[ 3899.767628] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3899.784627] scsi49 : SCSI emulation for USB Mass Storage devices
[ 3899.791824] usb-storage: device found at 50
[ 3899.791830] usb-storage: waiting for device to settle before scanning
[ 3904.789934] usb-storage: device scan complete
[ 3904.792916] scsi scan: INQUIRY result too short (5), using 36
[ 3904.792926] scsi 49:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 3921.189771] usb 2-2.4: USB disconnect, address 50
[ 3921.192449] sr1: scsi3-mmc drive: 0x/0x caddy
[ 3921.193227] sr 49:0:0:0: Attached scsi CD-ROM sr1
[ 3921.194077] sr 49:0:0:0: Attached scsi generic sg2 type 5
[ 3981.809380] usb 2-2.4: new full speed USB device using uhci_hcd and address 51
[ 3981.935556] usb 2-2.4: configuration #1 chosen from 1 choice
[ 3981.955815] scsi50 : SCSI emulation for USB Mass Storage devices
[ 3981.959956] usb-storage: device found at 51
[ 3981.959961] usb-storage: waiting for device to settle before scanning
[ 3986.957880] usb-storage: device scan complete
[ 3986.960856] scsi scan: INQUIRY result too short (5), using 36
[ 3986.960868] scsi 50:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 4003.363067] usb 2-2.4: USB disconnect, address 51
[ 4003.364443] sr1: scsi3-mmc drive: 67x/141x writer dvd-ram xa/form2 cdda tray
[ 4003.365223] sr 50:0:0:0: Attached scsi CD-ROM sr1
[ 4003.366015] sr 50:0:0:0: Attached scsi generic sg2 type 5
[ 4003.370467] cdrom: issuing MRW back ground format suspend
[ 4063.977360] usb 2-2.4: new full speed USB device using uhci_hcd and address 52
[ 4064.103502] usb 2-2.4: configuration #1 chosen from 1 choice
[ 4064.123457] scsi51 : SCSI emulation for USB Mass Storage devices
[ 4064.127652] usb-storage: device found at 52
[ 4064.127658] usb-storage: waiting for device to settle before scanning
[ 4069.132317] usb-storage: device scan complete
[ 4069.134836] scsi scan: INQUIRY result too short (5), using 36
[ 4069.134848] scsi 51:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 4085.534572] usb 2-2.4: USB disconnect, address 52
[ 4085.537043] sr1: scsi3-mmc drive: 0x/0x caddy
[ 4085.537833] sr 51:0:0:0: Attached scsi CD-ROM sr1
[ 4085.538636] sr 51:0:0:0: Attached scsi generic sg2 type 5
[ 4085.543823] cdrom: issuing MRW back ground format suspend
[ 4146.145283] usb 2-2.4: new full speed USB device using uhci_hcd and address 53
[ 4146.271454] usb 2-2.4: configuration #1 chosen from 1 choice
[ 4146.293734] scsi52 : SCSI emulation for USB Mass Storage devices
[ 4146.301539] usb-storage: device found at 53
[ 4146.301544] usb-storage: waiting for device to settle before scanning
[ 4149.527894] usb 2-2.4: USB disconnect, address 53
[ 5531.845562] usb 2-2.4: new full speed USB device using uhci_hcd and address 54
[ 5531.875549] hub 2-2:1.0: unable to enumerate USB device on port 4
[ 5592.257903] usb 2-2.4: new full speed USB device using uhci_hcd and address 55
[ 5592.384091] usb 2-2.4: configuration #1 chosen from 1 choice
[ 5592.391614] scsi53 : SCSI emulation for USB Mass Storage devices
[ 5592.391851] usb-storage: device found at 55
[ 5592.391855] usb-storage: waiting for device to settle before scanning
[ 5597.389389] usb-storage: device scan complete
[ 5597.392370] scsi scan: INQUIRY result too short (5), using 36
[ 5597.392381] scsi 53:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 5613.794368] usb 2-2.4: USB disconnect, address 55
[ 5613.797229] sr1: scsi3-mmc drive: 0x/0x caddy
[ 5613.798165] sr 53:0:0:0: Attached scsi CD-ROM sr1
[ 5613.799360] sr 53:0:0:0: Attached scsi generic sg2 type 5
[ 5613.804424] cdrom: issuing MRW back ground format suspend
[ 5674.421846] usb 2-2.4: new full speed USB device using uhci_hcd and address 56
[ 5674.548027] usb 2-2.4: configuration #1 chosen from 1 choice
[ 5674.566197] scsi54 : SCSI emulation for USB Mass Storage devices
[ 5674.571824] usb-storage: device found at 56
[ 5674.571829] usb-storage: waiting for device to settle before scanning
[ 5679.569335] usb-storage: device scan complete
[ 5679.572665] scsi scan: INQUIRY result too short (5), using 36
[ 5679.572678] scsi 54:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 5695.970520] usb 2-2.4: USB disconnect, address 56
[ 5695.972898] sr1: scsi3-mmc drive: 0x/0x caddy
[ 5695.973681] sr 54:0:0:0: Attached scsi CD-ROM sr1
[ 5695.974480] sr 54:0:0:0: Attached scsi generic sg2 type 5
[ 5756.589795] usb 2-2.4: new full speed USB device using uhci_hcd and address 57
[ 5756.715955] usb 2-2.4: configuration #1 chosen from 1 choice
[ 5756.737105] scsi55 : SCSI emulation for USB Mass Storage devices
[ 5756.741465] usb-storage: device found at 57
[ 5756.741470] usb-storage: waiting for device to settle before scanning
[ 5761.741277] usb-storage: device scan complete
[ 5761.744345] scsi scan: INQUIRY result too short (5), using 36
[ 5761.744356] scsi 55:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 5778.142172] usb 2-2.4: USB disconnect, address 57
[ 5778.144660] sr1: scsi3-mmc drive: 0x/0x caddy
[ 5778.145440] sr 55:0:0:0: Attached scsi CD-ROM sr1
[ 5778.146248] sr 55:0:0:0: Attached scsi generic sg2 type 5
[ 5778.152124] cdrom: issuing MRW back ground format suspend
[ 5838.757732] usb 2-2.4: new full speed USB device using uhci_hcd and address 58
[ 5838.883896] usb 2-2.4: configuration #1 chosen from 1 choice
[ 5838.905002] scsi56 : SCSI emulation for USB Mass Storage devices
[ 5838.909143] usb-storage: device found at 58
[ 5838.909149] usb-storage: waiting for device to settle before scanning
[ 5843.909225] usb-storage: device scan complete
[ 5843.912556] scsi scan: INQUIRY result too short (5), using 36
[ 5843.912569] scsi 56:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 5860.310043] usb 2-2.4: USB disconnect, address 58
[ 5860.313187] sr1: scsi3-mmc drive: 0x/0x caddy
[ 5860.313984] sr 56:0:0:0: Attached scsi CD-ROM sr1
[ 5860.314780] sr 56:0:0:0: Attached scsi generic sg2 type 5
[ 5920.925679] usb 2-2.4: new full speed USB device using uhci_hcd and address 59
[ 5921.051846] usb 2-2.4: configuration #1 chosen from 1 choice
[ 5921.072072] scsi57 : SCSI emulation for USB Mass Storage devices
[ 5921.076485] usb-storage: device found at 59
[ 5921.076490] usb-storage: waiting for device to settle before scanning
[ 5926.077166] usb-storage: device scan complete
[ 5926.080349] scsi scan: INQUIRY result too short (5), using 36
[ 5926.080360] scsi 57:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 5942.477977] usb 2-2.4: USB disconnect, address 59
[ 5942.480896] sr1: scsi3-mmc drive: 0x/0x caddy
[ 5942.481671] sr 57:0:0:0: Attached scsi CD-ROM sr1
[ 5942.482483] sr 57:0:0:0: Attached scsi generic sg2 type 5
[ 6003.089646] usb 2-2.4: new full speed USB device using uhci_hcd and address 60
[ 6003.215810] usb 2-2.4: configuration #1 chosen from 1 choice
[ 6003.236150] scsi58 : SCSI emulation for USB Mass Storage devices
[ 6003.240950] usb-storage: device found at 60
[ 6003.240955] usb-storage: waiting for device to settle before scanning
[ 6008.246891] usb-storage: device scan complete
[ 6008.250112] scsi scan: INQUIRY result too short (5), using 36
[ 6008.250124] scsi 58:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 6024.649931] usb 2-2.4: USB disconnect, address 60
[ 6024.652723] sr1: scsi3-mmc drive: 0x/0x caddy
[ 6024.653627] sr 58:0:0:0: Attached scsi CD-ROM sr1
[ 6024.653905] sr 58:0:0:0: Attached scsi generic sg2 type 5
[ 6024.658085] cdrom: issuing MRW back ground format suspend
[ 6085.257568] usb 2-2.4: new full speed USB device using uhci_hcd and address 61
[ 6085.383732] usb 2-2.4: configuration #1 chosen from 1 choice
[ 6085.401864] scsi59 : SCSI emulation for USB Mass Storage devices
[ 6085.407198] usb-storage: device found at 61
[ 6085.407203] usb-storage: waiting for device to settle before scanning
[ 6090.406523] usb-storage: device scan complete
[ 6090.409030] scsi scan: INQUIRY result too short (5), using 36
[ 6090.409042] scsi 59:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 6106.809532] usb 2-2.4: USB disconnect, address 61
[ 6106.812966] sr1: scsi3-mmc drive: 0x/0x caddy
[ 6106.813741] sr 59:0:0:0: Attached scsi CD-ROM sr1
[ 6106.814547] sr 59:0:0:0: Attached scsi generic sg2 type 5
[ 6167.425510] usb 2-2.4: new full speed USB device using uhci_hcd and address 62
[ 6167.551687] usb 2-2.4: configuration #1 chosen from 1 choice
[ 6167.572480] scsi60 : SCSI emulation for USB Mass Storage devices
[ 6167.576918] usb-storage: device found at 62
[ 6167.576923] usb-storage: waiting for device to settle before scanning
[ 6172.578001] usb-storage: device scan complete
[ 6172.580981] scsi scan: INQUIRY result too short (5), using 36
[ 6172.580993] scsi 60:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 6188.977978] usb 2-2.4: USB disconnect, address 62
[ 6188.980798] sr1: scsi3-mmc drive: 0x/0x caddy
[ 6188.981578] sr 60:0:0:0: Attached scsi CD-ROM sr1
[ 6188.982376] sr 60:0:0:0: Attached scsi generic sg2 type 5
[ 6249.593454] usb 2-2.4: new full speed USB device using uhci_hcd and address 63
[ 6249.720624] usb 2-2.4: configuration #1 chosen from 1 choice
[ 6249.740149] scsi61 : SCSI emulation for USB Mass Storage devices
[ 6249.743942] usb-storage: device found at 63
[ 6249.743947] usb-storage: waiting for device to settle before scanning
[ 6254.741946] usb-storage: device scan complete
[ 6254.744921] scsi scan: INQUIRY result too short (5), using 36
[ 6254.744933] scsi 61:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 6271.139912] sr1: scsi3-mmc drive: 0x/0x caddy
[ 6271.140196] sr 61:0:0:0: Attached scsi CD-ROM sr1
[ 6271.140337] sr 61:0:0:0: Attached scsi generic sg2 type 5
[ 6271.140720] usb 2-2.4: USB disconnect, address 63
[ 6331.757400] usb 2-2.4: new full speed USB device using uhci_hcd and address 64
[ 6331.883565] usb 2-2.4: configuration #1 chosen from 1 choice
[ 6331.908061] scsi62 : SCSI emulation for USB Mass Storage devices
[ 6331.912937] usb-storage: device found at 64
[ 6331.912942] usb-storage: waiting for device to settle before scanning
[ 6336.913887] usb-storage: device scan complete
[ 6336.916866] scsi scan: INQUIRY result too short (5), using 36
[ 6336.916878] scsi 62:0:0:0: CD-ROM            DMI      USB2.0 CD-ROM    1.15 PQ: 0 ANSI: 0
[ 6353.318814] usb 2-2.4: USB disconnect, address 64
[ 6353.321138] sr1: scsi3-mmc drive: 0x/0x caddy
[ 6353.321922] sr 62:0:0:0: Attached scsi CD-ROM sr1
[ 6353.322751] sr 62:0:0:0: Attached scsi generic sg2 type 5


If you see the problem please let me know, thanks.

---

### Post by pjd99 on 2011-08-30
Something isn't right there. TBH I'm not sure, do you have access to another computer to try it with?

The power supply for the external could be failing (based on the timing of the detect and disconnect), but that would be very coincidental as the OS is what has changed...

I'm guessing there's no sdX devices because of the SCSI emulation, so was assigned an srX instead. I'm not sure, but hdX was for PATA, sdX for SATA, so maybe srX for SCSI.... CD drives are also reported in a srX way. Any problems with a cd drive at all? Clutching at straws here, hopefully somebody with more knowledge about these things can lend a hand.

---

### Post by Hakunka-Matata on 2011-08-30
Try this:  [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by linuxfreak65 on 2011-08-30
I hope the files in the external hard drive are not corrupt upon re-installation the OS.  The power adapter seem to turn the external drive on so I don't think it is a lack of power.

---

### Post by linuxfreak65 on 2011-08-30
I installed through synaptic "mount manager" and there is no external device there, but if I insert a usb flash drive it shows up on the manager, which is consistent with what I got through commands - not being detected.

---

### Post by linuxfreak65 on 2011-08-30
If I type in the terminal "mount", then I get the following;

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rickchow/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rickchow)

If you guys can figure this out what this means, let me know, thanks.

---

### Post by Hakunka-Matata on 2011-08-30
> Configuring Automounting

 To enable or disable automount open a terminal and type gconf-editor followed by the [Enter] key. 
Browse to /apps/nautilus/preferences/media_automount. 
The media_automount  key controls whether to automatically mount media. If set to true, then  Nautilus will automatically mount media such as user-visible hard disks  and removable media on start-up and media insertion. 
There is another key /apps/nautilus/preferences/media_automount_open.  This controls whether to automatically open a folder for automounted  media. This key can also be set in the Nautilus (file manager) window.  From the Edit menu in Nautilus select Preferences and then select the Media tab.  
If  set to true, then Nautilus will automatically open a folder when media  is automounted. This only applies to media where no known x-content/*  type was detected; for media where a known x-content type is detected,  the user configurable action will be taken instead. This can be  configured as shown below. 
That is in the link I provided in post #6, go there to learn more.

---

### Post by linuxfreak65 on 2011-08-30
Thanks Hakunka, I went to that site that you suggested.  I entered the gconf-editor.  I browsed to Browse to /apps/nautilus/preferences/media_automount.  It was already checked, indicating a yes.  In addition,  /apps/nautilus/preferences/media_automount_open is also checked, indicating a yes.

Is it possible that Ubuntu 10.04 does not detect the drive is because maybe the drivers for the external hard drive is corrupt?

---

