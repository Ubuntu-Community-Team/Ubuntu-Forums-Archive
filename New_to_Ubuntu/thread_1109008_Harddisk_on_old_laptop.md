---
title: "Harddisk on old laptop"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by 2blue on 2009-03-28
Hi

I have an old laptop which runs surprisingly well with Xubuntu. I don't know all the hard ware detail but it is a Packard Bell Easy One 1712 Dc DVD. I have put in two new memory cards, each 512 MB, and system monitor reads about 10009 MB RAM. I think max RAM originally was set to 512MB, but still every ting runs better with twice that memory. It is not noticeably faster but I can have several windows open now and never having a "stand-still" anymore. Pocessor is a AMD Duron 700 MHz, and hard disk is 6 GB. 

I am really surprised at this laptop and Ubuntu, all work in office and online runs smothly and fairly fast. Compared to my new laptop with Vista, it is about the same which is a bit annoying. For plane office work, library and document search it works really well, but I would like a bit more than 6GB HD storage.

I have tried to figure out what type of hard drive the old laptop has, and have searched a bit in the terminal window. I know this computer is very small and limited, but I need an extra work station that doesn't cost anything, and is not particularly attractive to steal (it will live in a flimsy locker at a library).  

Do any of you think it is possible to fit a new harddrive in the old computer? Are Physical size and fittings of hard drive in old laptops about the same as today's standard?

This I what I find running "sudo lshw": 

           *-disk
                description: ATA Disk
                product: TOSHIBA MK6015MA
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: U8.1
                serial: 21242424T
                size: 5729MiB (6007MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3df93df8
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: b5a11822-2a56-4d00-93ce-572464ce10b0
                   size: 5428MiB
                   capacity: 5428MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-02-11 01:04:28 filesystem=ext3 modified=2009-03-28 14:58:02 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-03-28 14:34:46 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 298MiB
                   capacity: 298MiB
                   capabilities: primary extended partitioned partitioned:extended

---

### Post by kanikilu on 2009-03-28
One of these [ATA-6 drives](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150380%201035907889&name=ATA-6) should be backwards compatible with ATA-5, you just won't get the speed of ATA-6.

The main question is, can you even access the hard drive on this laptop? If so, it should be do-able, but you might want to check out the specs from the manufacturer for both the original and replacement to make sure the size is the same - they are all 2.5" wide, but there could be differences in height...

---

### Post by 2blue on 2009-03-29
You are right kanikilu, it is difficult to figure out where the harddrive is. I never expected that! I have opened all lids, and loosened the key-board, but I can't see it. Processor and other components like CD/DVD rom are easily accessed. I may have to separate the whole casing, something I hesitate to do.

---

