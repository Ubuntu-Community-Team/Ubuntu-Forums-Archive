---
title: "Marvell SD8686 WiFi - lock-up when device is powered up - how to troubleshoot?"
date: 2020-01-17
forum: Networking &amp; Wireless
---

### Post by wb0gaz on 2020-01-17
I posted this to "hardware" but so far no replies, so duplicating my initial postings here in hopes this area is more appropriate:

1. 

Running xubuntu 18.04 32-bit (fresh install, fully updated) on an Atom-based machine which includes a Marvell SD8686 wifi device. When the SD8686 is powered up, the machine locks up and must be manually rebooted. I have not attempted to install drivers or firmware for the SD8686 (I think this is an issue).

When the machine (a Viliv S5 "MID") powers up and is started, the SD8686 is not powered up so it is not seen as a peripheral by Ubuntu. A small program "viliv-ec" was written (not by me) and I have installed, that lets the user power up the SD8686 once the machine is running. The same program can be used to power up the bluetooth peripheral and the touchscreen (both of those peripherals do power up using the program, so I think the program is working as expected.) When I use the program to power up the SD8686, several messages are printed by the program indicating that it was successful at powering up the SD8686. The program does not exit on completion (it does this for the other two peripherals I mentioned), instead the machine goes into a hard lock-up state.

I have looked at the output of dmesg and /var/log/kern.log but I do not find any mention of the SD8686 (I do see mention of the bluetooth peripheral when it was tested), so perhaps the log file isn't getting flushed to disc before the machine locks up.

Two questions -

(1) can I diagnose this any further beyond what I have described above?

(2) where can I find a how-to that would help me properly set up the device driver and/or firmware that is likely needed? I understand the SD8686 is included in "libertas" but I have no experience with that.

Thanks very much for any advice/help,

Dave 

2.

Some further effort, but lock-up problem not yet solved:

This page lead me to the marvell sd8686 firmware (.bin) files:
[http://labs.isee.biz/index.php/How_t...8686_SDIO_wifi](http://labs.isee.biz/index.php/How_t...8686_SDIO_wifi)

Firmware (sd_helper.bin and sd8686.bin) was downloaded using:
[https://www.marvell.com/support/downloads/search.do](https://www.marvell.com/support/downloads/search.do)
which were found in the file:
SD-8686-LINUX26-SYSKT-9.70.3.p24-26409.P45-GPL.zip

This instructed me to rename sd_helper.bin to sd8686_helper.bin and copy both .bin files to /lib/firmware:
[https://wiki.ubuntu.com/Marvell8686Firmware](https://wiki.ubuntu.com/Marvell8686Firmware)

I confirmed that the current configuration of xubuntu has libertas_sdio.ko

So to start (after copying the firmware files into /lib/firmware),

$ modprobe libertas_sdio
(returns immediately with nothing printed)
$ sudo viliv-ec -e 2
(prints the following, then lockup)

I/O ports successfully opened
EC_DEBUG: POWER_ON=80, address=ICE
EC_DEBUG: ack ret. value=55, should match ack_success=55
Success ack returned from embedded controller (EC) for device power on
EC_DEBUG: device hex cmd byte=7, address=ICE

(this was manually retyped as machine was in lock-up state after the last line above was printed)

The machine was imaged prior to making any changes related to this, so I can easily recover to a blank slate if need be.

Hope this helps point me in the right direction!

Dave 

3.

Tried this to see if anything showing up in dmesg:

watch -n 0.1 "dmesg | tail -n $((LINES-6))"

After running viliv-ec -e 2 (turn on the SD8686 wifi device) I got one new line from dmesg:

[ 188.973720] mmc1: new SDIO card at address 0001

After that, the machine freezes 

4.

Repeated this experiment with quicker polling of dmesg:

watch -n 0.01 "dmesg | tail -n $((LINES-6))"

After running viliv-ec -e 2 (turn on the SD8686 wifi device) I got three new lines from dmesg:

[ 360.989206] mmc1: new SDIO card at address 0001
[ 361.184984] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[ 361.215326] cfg80211: Loaded X.509 cert 'sforshee: 00b......'

After that, the machine freezes 

###

Thank you for any suggestions, pointers or advice!

Dave

---

