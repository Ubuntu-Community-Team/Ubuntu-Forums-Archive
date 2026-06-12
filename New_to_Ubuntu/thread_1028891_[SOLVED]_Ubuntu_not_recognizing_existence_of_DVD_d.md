---
title: "[SOLVED] Ubuntu not recognizing existence of DVD drive"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by amazingtaters on 2009-01-02
So, I'm having a problem that's rather annoying. Ubuntu has decided that it's not going to play nice with the DVD drive in my Acer Aspire 5100-5033 laptop, to the point that it doesn't recognize its existence. I've been looking for a fix, and I'm stymied. I know that the drive works, because I've got a flash drive with Mint 6 that I booted to, then popped in a DVD which started playing right off the bat. So, the problem lies with software not hardware, but I can't seem to find a similar problem. Perhaps my google-foo has failed me, or I'm just plain stupid, but can anyone think of why this is happening?

---

### Post by blueridgedog on 2009-01-02
Can you post the output of 

```
sudo lshw
```

Mine shows my two DVD drives as follows:

pata_amd
        *-cdrom
             description: DVD writer
             product: DVDR   PX-708A
             vendor: PLEXTOR
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.04
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi4
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW LH-20A1S
             vendor: LITE-ON
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 9L05
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

---

