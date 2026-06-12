---
title: "Grub-rescue kicks in unexpectedly on boot"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by bwallum on 2010-07-08
Hi

I've been trying to work out why I can't boot up an AMD64 bit machine, fresh install, 10.4, did previously work on the same install ok.

There is just the one hard drive (500MB sata WDC WD5000AVVS-63M8B0) mounted on /dev/sda, just the one partition for grub files, partition 1 (the first).

Every time I boot I get dumped to the grub-rescue prompt. The only way out is ```
insmod normal
```then```
normal
```The system then boots up as expected.

```
sudo update-grub
```runs ok but still, upon reboot, I'm dumped to grub-rescue. It tells me device (long string, assume UUID) is not present.

What is going on, why, and can you help me fix it please?

---

### Post by bwallum on 2010-07-08
Is this part of the '64bit' problem?

---

### Post by bwallum on 2010-07-09
I can now replicate the problem on 32 bit 10.04. The actual error message just before dropping to grub-rescue prompt is:-> error: no such device: 15129e1b-82d0-4cd7-844e-6ca1ab5eed25which is the UUID of an external harddrive that I have tried to configure to run Ubuntu. I've managed this before successfully with another USB external harddrive.

When I run ```
sudo blkid
```I get the following:> *-scsi
          physical id: 1
          bus info: usb@1:1
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdc
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=00097f1c
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sdc1
                version: 1.0
                serial: 15129e1b-82d0-4cd7-844e-6ca1ab5eed25
                size: 462GiB
                capacity: 462GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2010-07-09 09:10:50 filesystem=ext4 lastmountpoint=/media/15129e1b-82d0-4cd7-844e-6ca1ab5eed25y&#65533;;X&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;&#65533;&#65533;K modified=2010-07-09 09:41:11 mounted=2010-07-09 09:39:36 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sdc2
                size: 2935MiB
                capacity: 2935MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdc5
                   capacity: 2935MiB
                   capabilities: nofsThe ? symbols show as question marks in the terminal too.

The external drive is 500Mb, I've previously been successful with 320Mb drives, no idea if this makes any difference or not.

The curious thing is, even with the external drive removed and the cmos set to boot the internal hard drive first, I still get the error.

I've tried to zero the external hard drive with 'dd' which took over a day but succeeded. I then did a complete new reinstall. Same problem comes back.

Any help would be appreciated. I'm beginning to think the Chinese are  tweaking their hardware to deliver hardware viruses!

---

