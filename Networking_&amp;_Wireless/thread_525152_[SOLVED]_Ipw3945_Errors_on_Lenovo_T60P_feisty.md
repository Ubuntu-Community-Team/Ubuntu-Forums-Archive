---
title: "[SOLVED] Ipw3945 Errors on Lenovo T60P feisty"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by linuxworks on 2007-08-14
Greetings all,

I've had Ubuntu 7.04 installed since April of this year. All was fine until about 1 week ago when suddenly the wireless nic stop responding. 

The Wireless nic is ipw3945. 

I get the following errors:

[   19.640000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   19.640000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.644000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   21.508000] ipw3945: Unable to int nic


# lsmod  |grep 3945
ipw3945               118816  1 
ieee80211              34760  1 ipw3945


Any ideas?


 cat /var/log/kern.log |grep error
Aug 12 20:43:08 namohamm-linux kernel: [    4.148000] usb 1-1: device not accepting address 2, error -71
Aug 12 23:52:23 namohamm-linux kernel: [    3.964000] usb 1-1: device not accepting address 2, error -71
Aug 12 23:55:32 namohamm-linux kernel: [   20.451904] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 12 23:55:32 namohamm-linux kernel: [    6.688000] usb 1-1: device not accepting address 2, error -71
Aug 13 00:09:31 namohamm-linux kernel: [    4.248000] usb 1-1: device not accepting address 2, error -71
Aug 13 00:12:06 namohamm-linux kernel: [    4.328000] usb 1-1: device not accepting address 2, error -71
Aug 13 01:48:45 namohamm-linux kernel: [    4.188000] usb 1-1: device not accepting address 2, error -71
Aug 13 09:36:13 namohamm-linux kernel: [    4.124000] usb 1-1: device not accepting address 2, error -71
Aug 13 09:36:13 namohamm-linux kernel: [   18.728000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   19.884000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   22.956000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   23.132000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   23.304000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   23.476000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   23.652000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   26.780000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   29.944000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   30.116000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   33.236000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   33.404000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   36.484000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   36.652000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   39.816000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   39.984000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   43.060000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   43.228000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   46.392000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   46.564000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   49.704000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   49.872000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   53.036000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   53.212000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   56.376000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   56.544000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   59.708000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   59.880000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   63.044000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   63.220000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   66.384000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   66.556000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   69.720000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   69.892000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   73.056000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   73.224000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   76.388000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   79.552000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   82.712000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   85.876000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   86.096000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   89.632000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   92.876000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   93.052000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   96.212000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:13 namohamm-linux kernel: [   96.388000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:15 namohamm-linux kernel: [   99.520000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:19 namohamm-linux kernel: [  102.676000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:22 namohamm-linux kernel: [  103.000000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:25 namohamm-linux kernel: [  106.132000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:28 namohamm-linux kernel: [  106.300000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:31 namohamm-linux kernel: [  109.464000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:35 namohamm-linux kernel: [  112.568000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:41 namohamm-linux kernel: [  115.704000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:41 namohamm-linux kernel: [  118.868000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:44 namohamm-linux kernel: [  121.948000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:50 namohamm-linux kernel: [  125.024000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:57 namohamm-linux kernel: [  128.104000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:57 namohamm-linux kernel: [  128.180000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:36:57 namohamm-linux kernel: [  128.244000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:00 namohamm-linux kernel: [  128.328000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:03 namohamm-linux kernel: [  128.732000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:06 namohamm-linux kernel: [  131.808000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:14 namohamm-linux kernel: [  132.924000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:14 namohamm-linux kernel: [  136.024000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:20 namohamm-linux kernel: [  139.068000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:20 namohamm-linux kernel: [  139.368000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:23 namohamm-linux kernel: [  142.424000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:27 namohamm-linux kernel: [  142.596000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:30 namohamm-linux kernel: [  145.648000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:33 namohamm-linux kernel: [  148.716000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:36 namohamm-linux kernel: [  148.892000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:39 namohamm-linux kernel: [  151.948000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:42 namohamm-linux kernel: [  152.120000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:46 namohamm-linux kernel: [  155.176000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:49 namohamm-linux kernel: [  155.352000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:52 namohamm-linux kernel: [  158.420000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:55 namohamm-linux kernel: [  158.612000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:37:58 namohamm-linux kernel: [  161.668000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:02 namohamm-linux kernel: [  162.716000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:05 namohamm-linux kernel: [  165.816000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:09 namohamm-linux kernel: [  166.796000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:13 namohamm-linux kernel: [  169.896000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:16 namohamm-linux kernel: [  170.356000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:19 namohamm-linux kernel: [  173.404000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:23 namohamm-linux kernel: [  173.576000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:26 namohamm-linux kernel: [  176.628000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:29 namohamm-linux kernel: [  176.804000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:32 namohamm-linux kernel: [  179.848000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:35 namohamm-linux kernel: [  180.024000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:38 namohamm-linux kernel: [  183.072000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:41 namohamm-linux kernel: [  183.244000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:45 namohamm-linux kernel: [  186.308000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:48 namohamm-linux kernel: [  186.476000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:51 namohamm-linux kernel: [  189.528000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:54 namohamm-linux kernel: [  189.704000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:38:57 namohamm-linux kernel: [  192.776000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:00 namohamm-linux kernel: [  192.948000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:04 namohamm-linux kernel: [  196.004000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:07 namohamm-linux kernel: [  196.180000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:10 namohamm-linux kernel: [  199.240000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:13 namohamm-linux kernel: [  199.412000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:16 namohamm-linux kernel: [  202.480000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:19 namohamm-linux kernel: [  202.656000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:23 namohamm-linux kernel: [  205.712000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:26 namohamm-linux kernel: [  205.888000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:29 namohamm-linux kernel: [  208.944000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:32 namohamm-linux kernel: [  209.120000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:35 namohamm-linux kernel: [  212.180000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:38 namohamm-linux kernel: [  212.356000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:42 namohamm-linux kernel: [  215.404000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:45 namohamm-linux kernel: [  215.580000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:48 namohamm-linux kernel: [  218.624000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:51 namohamm-linux kernel: [  218.800000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:54 namohamm-linux kernel: [  221.864000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:39:57 namohamm-linux kernel: [  222.036000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:01 namohamm-linux kernel: [  225.092000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:04 namohamm-linux kernel: [  225.268000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:07 namohamm-linux kernel: [  228.320000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:10 namohamm-linux kernel: [  228.492000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:13 namohamm-linux kernel: [  231.540000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:16 namohamm-linux kernel: [  231.712000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:19 namohamm-linux kernel: [  234.768000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:23 namohamm-linux kernel: [  234.940000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:26 namohamm-linux kernel: [  237.988000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:29 namohamm-linux kernel: [  238.156000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:32 namohamm-linux kernel: [  241.204000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:35 namohamm-linux kernel: [  241.380000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:39 namohamm-linux kernel: [  244.432000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:42 namohamm-linux kernel: [  244.604000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:45 namohamm-linux kernel: [  247.652000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:48 namohamm-linux kernel: [  247.828000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:51 namohamm-linux kernel: [  250.880000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:54 namohamm-linux kernel: [  251.052000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:40:58 namohamm-linux kernel: [  254.104000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:01 namohamm-linux kernel: [  254.276000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:04 namohamm-linux kernel: [  257.328000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:07 namohamm-linux kernel: [  257.504000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:10 namohamm-linux kernel: [  260.568000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:13 namohamm-linux kernel: [  260.736000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:17 namohamm-linux kernel: [  263.788000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:20 namohamm-linux kernel: [  263.964000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:23 namohamm-linux kernel: [  267.024000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:26 namohamm-linux kernel: [  267.196000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:29 namohamm-linux kernel: [  270.256000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:32 namohamm-linux kernel: [  270.432000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:36 namohamm-linux kernel: [  273.496000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:39 namohamm-linux kernel: [  273.664000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:42 namohamm-linux kernel: [  276.720000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:45 namohamm-linux kernel: [  276.896000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:48 namohamm-linux kernel: [  279.960000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:51 namohamm-linux kernel: [  280.132000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:54 namohamm-linux kernel: [  283.192000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:41:58 namohamm-linux kernel: [  283.368000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:01 namohamm-linux kernel: [  286.416000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:04 namohamm-linux kernel: [  286.588000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:07 namohamm-linux kernel: [  289.636000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:10 namohamm-linux kernel: [  289.812000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:13 namohamm-linux kernel: [  292.864000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:17 namohamm-linux kernel: [  293.032000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:20 namohamm-linux kernel: [  296.084000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:23 namohamm-linux kernel: [  296.260000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:26 namohamm-linux kernel: [  299.316000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:29 namohamm-linux kernel: [  299.488000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:33 namohamm-linux kernel: [  302.540000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:36 namohamm-linux kernel: [  302.716000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:39 namohamm-linux kernel: [  305.788000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:42 namohamm-linux kernel: [  305.960000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:45 namohamm-linux kernel: [  309.012000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:48 namohamm-linux kernel: [  309.188000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:51 namohamm-linux kernel: [  312.248000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:42:55 namohamm-linux kernel: [  312.424000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:01 namohamm-linux kernel: [  315.484000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:01 namohamm-linux kernel: [  315.660000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:04 namohamm-linux kernel: [  318.712000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:07 namohamm-linux kernel: [  318.888000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:10 namohamm-linux kernel: [  319.000000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:14 namohamm-linux kernel: [  319.172000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:17 namohamm-linux kernel: [  319.284000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:20 namohamm-linux kernel: [  319.460000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:23 namohamm-linux kernel: [  319.584000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:26 namohamm-linux kernel: [  319.756000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:29 namohamm-linux kernel: [  319.856000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:33 namohamm-linux kernel: [  320.032000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:36 namohamm-linux kernel: [  320.144000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:39 namohamm-linux kernel: [  320.320000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:42 namohamm-linux kernel: [  320.424000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:45 namohamm-linux kernel: [  320.600000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:48 namohamm-linux kernel: [  320.680000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:52 namohamm-linux kernel: [  320.852000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:55 namohamm-linux kernel: [  320.944000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:43:58 namohamm-linux kernel: [  321.112000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:44:01 namohamm-linux kernel: [  321.220000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:44:04 namohamm-linux kernel: [  321.392000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:44:07 namohamm-linux kernel: [  321.512000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:44:14 namohamm-linux kernel: [  321.684000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 09:44:14 namohamm-linux kernel: [  321.772000] ipw3945: Microcode HW error detected.  Restarting.
Aug 13 20:36:51 namohamm-linux kernel: [  183.704000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0a failed for offset 0x0000 with error -19.
Aug 13 20:36:51 namohamm-linux kernel: [  183.704000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3028 with error -19.
Aug 13 20:36:51 namohamm-linux kernel: [  183.704000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3064 with error -19.
Aug 13 20:36:51 namohamm-linux kernel: [  183.704000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3040 with error -19.
Aug 13 20:36:51 namohamm-linux kernel: [  183.704000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3040 with error -19.
Aug 13 20:36:51 namohamm-linux kernel: [  183.704000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0c failed for offset 0x0000 with error -19.
Aug 13 20:41:52 namohamm-linux kernel: [  484.824000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0a failed for offset 0x0000 with error -19.
Aug 13 20:41:52 namohamm-linux kernel: [  484.824000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3028 with error -19.
Aug 13 20:41:52 namohamm-linux kernel: [  484.824000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3064 with error -19.
Aug 13 20:41:52 namohamm-linux kernel: [  484.824000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3040 with error -19.
Aug 13 20:41:52 namohamm-linux kernel: [  484.824000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3040 with error -19.
Aug 13 20:41:52 namohamm-linux kernel: [  484.824000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0c failed for offset 0x0000 with error -19.
Aug 13 20:44:43 namohamm-linux kernel: [  656.104000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0a failed for offset 0x0000 with error -19.
Aug 13 20:44:43 namohamm-linux kernel: [  656.104000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3028 with error -19.
Aug 13 20:44:43 namohamm-linux kernel: [  656.104000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3064 with error -19.
Aug 13 20:44:43 namohamm-linux kernel: [  656.104000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3040 with error -19.
Aug 13 20:44:43 namohamm-linux kernel: [  656.108000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3040 with error -19.
Aug 13 20:44:43 namohamm-linux kernel: [  656.108000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0c failed for offset 0x0000 with error -19.
Aug 13 20:57:41 namohamm-linux kernel: [ 1433.616000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0a failed for offset 0x0000 with error -19.
Aug 13 20:57:41 namohamm-linux kernel: [ 1433.616000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3028 with error -19.
Aug 13 20:57:41 namohamm-linux kernel: [ 1433.616000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3064 with error -19.
Aug 13 20:57:41 namohamm-linux kernel: [ 1433.616000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x07 failed for offset 0x3040 with error -19.
Aug 13 20:57:41 namohamm-linux kernel: [ 1433.616000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x06 failed for offset 0x3040 with error -19.
Aug 13 20:57:41 namohamm-linux kernel: [ 1433.616000] rt73usb->rt2x00_vendor_request: Error - vendor request error. Request 0x0c failed for offset 0x0000 with error -19.





# lshw |grep 3945
                product: PRO/Wireless 3945ABG Network Connection
                configuration: driver=ipw3945 latency=0

lspci -v  |grep 3945
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1010
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at edf00000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: Lenovo Thinkpad R60e model 0657
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at e4300000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
        Memory window 0: e0000000-e3fff000 (prefetchable)
        Memory window 1: 88000000-8bfff000
        I/O window 0: 0000a000-0000a0ff
        I/O window 1: 0000a400-0000a4ff
        16-bit legacy interface ports at 0001


Any ideas ?

please email to linuxworks at yahoo dot com

---

### Post by noob12 on 2007-08-14
Anything change recently (kernel)?  Do you dual-boot this machine?

Does booting with acpi=off help?

---

### Post by linuxworks on 2007-08-14
root@namohamm-linux:/home/namohamm# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:71d4]
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
root@namohamm-linux:/home/namohamm# 
root@namohamm-linux:/home/namohamm# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:e2:7e:dd
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=full firmware=0.5-1 ip=171.69.89.189 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: iomemory:ee000000-ee01ffff ioport:3000-301f irq:16
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:edf00000-edf00fff irq:21
root@namohamm-linux:/home/namohamm# 
root@namohamm-linux:/home/namohamm# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

root@namohamm-linux:/home/namohamm# 
root@namohamm-linux:/home/namohamm# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.


This is an update to my issue. Also nothing has changed in either bios or OS. I will try to acpi=off option and see where this may lead to .

---

### Post by linuxworks on 2007-08-22
The solution was to replace the wlan module internal to the laptop. Apparently, one of the updates the ubuntu offered was a ipw3945 firmware upgrade which render the card disabled. 

My suggestion is to not upgrade anything for ipw3945 that is the culprit.


I almost dumped ubuntu for OpenSuse 10.2 because its supported by IBM for the t60p and comes with the thinkadvantage tools. 

-nael

---

### Post by odin1965 on 2007-08-22
> **linuxworks said:**
> The solution was to replace the wlan module internal to the laptop. Apparently, one of the updates the ubuntu offered was a ipw3945 firmware upgrade which render the card disabled. 

My suggestion is to not upgrade anything for ipw3945 that is the culprit.


I almost dumped ubuntu for OpenSuse 10.2 because its supported by IBM for the t60p and comes with the thinkadvantage tools. 

-nael

How do you find out whether your 3945 card has had the firmware updated? Mine originally worked out of the box with Feisty installed and also with PCLinuxOS live CD, now it will not work with either. It worked for about a week, until around the first week of August, then stopped.

---

