---
title: "need help installing acx100 drivers for wireless usb"
date: 2005-07-23
forum: Networking &amp; Wireless
---

### Post by fkacct on 2005-07-23
Hi, I have been trying to install the drivers for a dwl-120+ wireless usb networking card, but I get the following message when running the install scripts:

--  imac@imac:~/acx10057/scripts$ sudo ./start_net
--  using wlan0.
--  Module successfully inserted.
--  Error: Failed to create device: wlan0...bailing.

when I RE-type "./start_net", I get:

--  imac@imac:~/acx10057/scripts$ sudo ./start_net
--  using wlan0.
--  insmod: error inserting './../src/acx_usb.ko': -1 File exists
--  Error while inserting module! Bailing...

I checked the log at /var/log/syslog and i get this:  

Jul 21 00:49:18 localhost kernel: acx_usb: no version for "struct_module" found: kernel tainted.
Jul 21 00:49:19 localhost kernel: Initializing acx100 WLAN USB kernel module
Jul 21 00:49:19 localhost kernel: loading firmware ACX100_USB.bin
Jul 21 00:49:19 localhost kernel: Requesting firmware image 'ACX100_USB.bin'
Jul 21 00:49:19 localhost kernel: No firmware image was provided. Check your hotplug scripts
Jul 21 00:49:19 localhost kernel: Reading firmware image '/usr/share/acx/ACX100_USB.bin'
Jul 21 00:49:19 localhost kernel: Allocated 42324 bytes for firmware module loading.
Jul 21 00:49:20 localhost kernel: firmware size: 42324 bytes
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=8)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=2056)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=4104)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=6152)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=8200)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=10248)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=12296)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=14344)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=16392)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=18440)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=20488)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=22536)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=24584)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=26632)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=28680)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=30728)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=32776)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=34824)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=36872)
Jul 21 00:49:20 localhost kernel: uploading firmware (2048 bytes, offset=38920)
Jul 21 00:49:20 localhost kernel: uploading firmware (1356 bytes, offset=40968)
Jul 21 00:49:20 localhost kernel: Finished booting, returning from probe().
Jul 21 00:49:20 localhost kernel: usbcore: registered new driver acx_usb
Jul 21 00:49:20 localhost kernel: usb 1-1: USB disconnect, address 2
Jul 21 00:49:21 localhost kernel: usb 1-1: new full speed USB device using ohci_hcd and address 6
Jul 21 00:49:27 localhost kernel: # of endpoints: 2
Jul 21 00:49:27 localhost kernel: bulkout ep: 0x1
Jul 21 00:49:27 localhost kernel: bulkin ep: 0x1
Jul 21 00:49:27 localhost kernel: acx_usb: txbufsize=2326 rxbufsize=2944
Jul 21 00:49:27 localhost kernel: allocating device name
Jul 21 00:49:27 localhost kernel: registering network device
Jul 21 00:49:27 localhost kernel: divert: not allocating divert_blk for non-ethernet device wlan0
Jul 21 00:49:27 localhost kernel: ************* acx_init_mac_1 *************
Jul 21 00:49:27 localhost kernel: ERROR, USB device is not responding!
Jul 21 00:49:27 localhost kernel: ctlMemoryMapRead FAILED
Jul 21 00:49:27 localhost kernel: divert: no divert_blk to free, wlan0 not ethernet
Jul 21 00:49:27 localhost kernel: acx_usb: failed to register network device for USB WLAN (errcode=-5), giving up.
Jul 21 00:49:27 localhost kernel: acx_usb: probe of 1-1:1.0 failed with error -12


does anyone have a clue as to what this means?

Your help will be greatly appreciated,

fkacct

---

