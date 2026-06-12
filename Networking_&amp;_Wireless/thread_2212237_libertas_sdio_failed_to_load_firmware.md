---
title: "libertas_sdio: failed to load firmware"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by veerabhaskar on 2014-03-20
I am using sd8688 marvell board, it has already "sd8688.bin". But the "sd8688.bin" file has been genetate by me. I renamed my coustom *.bin to "sd8688.bin" and insterted my board. but it gives the error "libertas_sdio: failed to load firmware". Could some body help me to overcome this problem.

The below is the syslog deamon information...
-------------------------------------------------------------------
000:04:00.0/mmc_host/mmc0/mmc0:0001/mmc0:0001:1'
Mar 20 14:48:56 test kernel: [ 6911.500483] bus: 'sdio': driver_probe_device: matched device mmc0:0001:1 with driver libertas_sdio
Mar 20 14:48:56 test kernel: [ 6911.500488] bus: 'sdio': really_probe: probing driver libertas_sdio with device mmc0:0001:1
Mar 20 14:48:56 test kernel: [ 6911.501935] driver: 'mmc0:0001:1': driver_bound: bound to device 'libertas_sdio'
Mar 20 14:48:56 test kernel: [ 6911.501946] bus: 'sdio': really_probe: bound device mmc0:0001:1 to driver libertas_sdio
Mar 20 14:48:56 test kernel: [ 6911.501966] __allocate_fw_buf: fw-libertas/sd8688_helper.bin buf=e38ee780
Mar 20 14:48:56 test kernel: [ 6911.517994] libertas_sdio mmc0:0001:1: firmware: direct-loading firmware libertas/sd8688_helper.bin
Mar 20 14:48:56 test kernel: [ 6911.518006] fw_set_page_data: fw-libertas/sd8688_helper.bin buf=e38ee780 data=f857d000 size=2616
Mar 20 14:48:56 test kernel: [ 6911.518016] __allocate_fw_buf: fw-libertas/sd8688.bin buf=e38eec60
Mar 20 14:48:56 test kernel: [ 6911.518190] libertas_sdio mmc0:0001:1: firmware: direct-loading firmware libertas/sd8688.bin
Mar 20 14:48:56 test kernel: [ 6911.518197] fw_set_page_data: fw-libertas/sd8688.bin buf=e38eec60 data=f9455000 size=196608
Mar 20 14:48:56 test kernel: [ 6911.653976] libertas_sdio: failed to load firmware
Mar 20 14:48:56 test kernel: [ 6911.653990] __fw_free_buf: fw-libertas/sd8688_helper.bin buf=e38ee780 data=f857d000 size=2616
Mar 20 14:48:56 test kernel: [ 6911.654001] __fw_free_buf: fw-libertas/sd8688.bin buf=e38eec60 data=f9455000 size=196608
-----------------------------------------------



Thanks 
Veerabhaskar

---

