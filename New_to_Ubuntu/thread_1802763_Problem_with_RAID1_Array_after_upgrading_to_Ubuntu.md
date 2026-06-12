---
title: "Problem with RAID1 Array after upgrading to Ubuntu 11.04"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by martijnburger on 2011-07-12
Hi everyone,

I cannot get my (fake) RAID1 Array up and running after upgrading to Ubunut 11.04. Can anyone help me figure out what the problem is?

Some addintional data:
```
martijn@demoserver:~$ sudo dmraid -r -vvv
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sdd
NOTICE: skipping removable device /dev/sde
NOTICE: skipping removable device /dev/sdf
NOTICE: skipping removable device /dev/sdg
WARN: missing dm serial file for /dev/dm-0
NOTICE: /dev/dm-0: asr     discovering
NOTICE: /dev/dm-0: ddf1    discovering
NOTICE: /dev/dm-0: hpt37x  discovering
NOTICE: /dev/dm-0: hpt45x  discovering
NOTICE: /dev/dm-0: isw     discovering
NOTICE: /dev/dm-0: jmicron discovering
NOTICE: /dev/dm-0: lsi     discovering
NOTICE: /dev/dm-0: nvidia  discovering
NOTICE: /dev/dm-0: pdc     discovering
NOTICE: /dev/dm-0: sil     discovering
NOTICE: /dev/dm-0: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: isw metadata discovered
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
INFO: RAID devices discovered:

/dev/sdc: isw, "isw_bccajebghh", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdb: isw, "isw_bccajebghh", GROUP, ok, 1953523053 sectors, data@ 0
WARN: unlocking /var/lock/dmraid/.lock
martijn@demoserver:~$ sudo dmraid -s -vv
NOTICE: skipping removable device /dev/sdd
NOTICE: skipping removable device /dev/sde
NOTICE: skipping removable device /dev/sdf
NOTICE: skipping removable device /dev/sdg
NOTICE: /dev/dm-0: asr     discovering
NOTICE: /dev/dm-0: ddf1    discovering
NOTICE: /dev/dm-0: hpt37x  discovering
NOTICE: /dev/dm-0: hpt45x  discovering
NOTICE: /dev/dm-0: isw     discovering
NOTICE: /dev/dm-0: jmicron discovering
NOTICE: /dev/dm-0: lsi     discovering
NOTICE: /dev/dm-0: nvidia  discovering
NOTICE: /dev/dm-0: pdc     discovering
NOTICE: /dev/dm-0: sil     discovering
NOTICE: /dev/dm-0: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: isw metadata discovered
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
NOTICE: added /dev/sdc to RAID set "isw_bccajebghh"
NOTICE: added /dev/sdb to RAID set "isw_bccajebghh"
*** Group superset isw_bccajebghh
--> Active Subset
name   : isw_bccajebghh_DATA
size   : 1953519872
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
martijn@demoserver:~$ sudo dmraid -ay
RAID set "isw_bccajebghh_DATA" already active
ERROR: dos: partition address past end of RAID device
```

---

### Post by psusi on 2011-07-12
The partition table appears to be corrupt.  Post the output of sudo fdisk -lu /dev/mapper/isw_bccajebghh_DATA.

---

### Post by martijnburger on 2011-07-12
Hi Psusi,

thanks for helping me out. Here's the output of the fdisk command:

```
martijn@demoserver:~$ sudo fdisk -lu /dev/mapper/isw_bccajebghh_DATA

Disk /dev/mapper/isw_bccajebghh_DATA: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b7ad

                          Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bccajebghh_DATA1              63  1953520064   976760001   fd  Linux raid autodetect
```

---

### Post by psusi on 2011-07-12
Yep, the partition is longer than the whole disk.  Can you post the output of dmraid -n?

---

### Post by martijnburger on 2011-07-13
Here it is:
```

martijn@demoserver:~$ sudo dmraid -n
/dev/sdc (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.1.00"
0x020 check_sum: 1819296130
0x024 mpb_size: 480
0x028 family_num: 1220941677
0x02c generation_num: 217854
0x030 error_log_size: 4600
0x034 attributes: 2147483648
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 0
0x040 orig_family_num: 3237443397
0x044 power_cycle_count: 0
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "  S13PJ9CS308086"
0x0e8 disk[0].totalBlocks: 1953523055
0x0ec disk[0].scsiId: 0x20000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "  S13PJ9CS308085"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x50000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 isw_dev[0].volume: "            DATA"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953519616
0x150 isw_dev[0].status: 0x8c
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].migr_priority: 0
0x159 isw_dev[0].num_sub_vol: 0
0x15a isw_dev[0].tid: 58
0x15b isw_dev[0].cng_master_disk: 0
0x15c isw_dev[0].cache_policy: 257
0x15e isw_dev[0].cng_state: 0
0x15f isw_dev[0].cng_sub_state: 0
0x188 isw_dev[0].vol.curr_migr_unit: 0
0x18c isw_dev[0].vol.check_point_id: 0
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fs_state: 0
0x194 isw_dev[0].vol.verify_errors: 0
0x196 isw_dev[0].vol.verify_bad_blocks: 0
0x1a8 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x1ac isw_dev[0].vol.map[0].blocks_per_member: 1953519880
0x1b0 isw_dev[0].vol.map[0].num_data_stripes: 7630936
0x1b4 isw_dev[0].vol.map[0].blocks_per_strip: 128
0x1b6 isw_dev[0].vol.map[0].map_state: 0
0x1b7 isw_dev[0].vol.map[0].raid_level: 1
0x1b8 isw_dev[0].vol.map[0].num_members: 2
0x1b9 isw_dev[0].vol.map[0].num_domains: 2
0x1ba isw_dev[0].vol.map[0].failed_disk_num: 255
0x1bb isw_dev[0].vol.map[0].ddf: 1
0x1d8 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x1dc isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1

/dev/sdb (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.1.00"
0x020 check_sum: 1819296130
0x024 mpb_size: 480
0x028 family_num: 1220941677
0x02c generation_num: 217854
0x030 error_log_size: 4600
0x034 attributes: 2147483648
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 0
0x040 orig_family_num: 3237443397
0x044 power_cycle_count: 0
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "  S13PJ9CS308086"
0x0e8 disk[0].totalBlocks: 1953523055
0x0ec disk[0].scsiId: 0x40000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "  S13PJ9CS308085"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x30000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 isw_dev[0].volume: "            DATA"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953519616
0x150 isw_dev[0].status: 0x8c
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].migr_priority: 0
0x159 isw_dev[0].num_sub_vol: 0
0x15a isw_dev[0].tid: 58
0x15b isw_dev[0].cng_master_disk: 0
0x15c isw_dev[0].cache_policy: 257
0x15e isw_dev[0].cng_state: 0
0x15f isw_dev[0].cng_sub_state: 0
0x188 isw_dev[0].vol.curr_migr_unit: 0
0x18c isw_dev[0].vol.check_point_id: 0
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fs_state: 0
0x194 isw_dev[0].vol.verify_errors: 0
0x196 isw_dev[0].vol.verify_bad_blocks: 0
0x1a8 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x1ac isw_dev[0].vol.map[0].blocks_per_member: 1953519880
0x1b0 isw_dev[0].vol.map[0].num_data_stripes: 7630936
0x1b4 isw_dev[0].vol.map[0].blocks_per_strip: 128
0x1b6 isw_dev[0].vol.map[0].map_state: 0
0x1b7 isw_dev[0].vol.map[0].raid_level: 1
0x1b8 isw_dev[0].vol.map[0].num_members: 2
0x1b9 isw_dev[0].vol.map[0].num_domains: 2
0x1ba isw_dev[0].vol.map[0].failed_disk_num: 255
0x1bb isw_dev[0].vol.map[0].ddf: 1
0x1d8 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x1dc isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1
```

---

### Post by psusi on 2011-07-13
It looks like there is a bug in dmraid causing it to make the array slightly larger than it really is, and your partition is even larger than that.  Also the partition type is Linux Raid Autodetect, which it should not be.

What does sudo blkid show?

---

### Post by martijnburger on 2011-07-13
Doesn't look like very helpful information:

```
martijn@demoserver:~$ sudo blkid
/dev/sda1: UUID="fe7f3a5a-291c-4fa8-a736-2258151b2a97" TYPE="ext4" 
/dev/sda5: UUID="bc05118a-85cb-46c5-b314-3cbfbd5c09b8" TYPE="swap" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
```


Is there a possibility to mount the drives seperate and build up a new RAID Array from one of the drives?

---

### Post by psusi on 2011-07-13
> **martijnburger said:**
> 
Is there a possibility to mount the drives seperate and build up a new RAID Array from one of the drives?

No, but if you boot with the "nodmraid" argument, that should prevent it from being recognized as a raid array, allowing you to access just one disk to back up your data, reformat, and reinstall.

You might want to read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

Unless you need to dual boot with windows, you should avoid the fakeraid stuff and stick to Linux mdadm software raid instead, as it is much better supported.

---

### Post by martijnburger on 2011-07-13
Sorry for not being able to figure this out myself, even after reading the fakeraid wiki. I booted with the nodmraid option. But after that I am still not able to mount any of the drives. My RAID Array is degraded because I reinstalled using 10.04 on the sda disk (raid is sdb and sdc disks) If I can reconver my data I will surely stop using the fakeraid, to many problems. But for now, please help me with recovering the data. Tnx!

---

### Post by psusi on 2011-07-13
Ok, so can you post the results from dmraid and fdisk in 10.04 so we can see what the differences are?

---

### Post by martijnburger on 2011-07-14
Here is the current information from dmraid, fdisk and blkid:

```
root@martijn-server:~# dmraid -r vvv
no raid disks and with names: "vvv"
root@martijn-server:~# dmraid -r -vvv
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sdd
NOTICE: skipping removable device /dev/sde
NOTICE: skipping removable device /dev/sdf
NOTICE: skipping removable device /dev/sdg
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: isw metadata discovered
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
INFO: RAID devices discovered:

/dev/sdc: isw, "isw_bfdbhjciee", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdb: isw, "isw_bccajebghh", GROUP, ok, 1953523053 sectors, data@ 0
WARN: unlocking /var/lock/dmraid/.lock
root@martijn-server:~# dmraid -s -vv
NOTICE: skipping removable device /dev/sdd
NOTICE: skipping removable device /dev/sde
NOTICE: skipping removable device /dev/sdf
NOTICE: skipping removable device /dev/sdg
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: isw metadata discovered
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
NOTICE: added /dev/sdc to RAID set "isw_bfdbhjciee"
NOTICE: added /dev/sdb to RAID set "isw_bccajebghh"
ERROR: isw: wrong number of devices in RAID set "isw_bccajebghh_DATA" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_bfdbhjciee_DATA" [1/2] on /dev/sdc
*** Group superset isw_bccajebghh
--> *Inconsistent* Subset
name   : isw_bccajebghh_DATA
size   : 1953519872
stride : 128
type   : mirror
status : inconsistent
subsets: 0
devs   : 1
spares : 0
*** Group superset isw_bfdbhjciee
--> *Inconsistent* Subset
name   : isw_bfdbhjciee_DATA
size   : 1953519872
stride : 128
type   : mirror
status : inconsistent
subsets: 0
devs   : 1
spares : 0
root@martijn-server:~# fdisk -lu /dev/mapper/isw_bccajebghh_DATA
root@martijn-server:~# fdisk -lu /dev/mapper/isw_bfdbhjciee_DATA
root@martijn-server:~# dmraid -n
/dev/sdc (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.1.00"
0x020 check_sum: 1672355511
0x024 mpb_size: 480
0x028 family_num: 1531792844
0x02c generation_num: 217873
0x030 error_log_size: 4600
0x034 attributes: 2147483648
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 0
0x040 orig_family_num: 3237443397
0x044 power_cycle_count: 0
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "S13PJ9CS308086:1"
0x0e8 disk[0].totalBlocks: 1953524992
0x0ec disk[0].scsiId: 0xffffffff
0x0f0 disk[0].status: 0x2
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "  S13PJ9CS308085"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x50000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 isw_dev[0].volume: "            DATA"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953519616
0x150 isw_dev[0].status: 0x8c
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].migr_priority: 0
0x159 isw_dev[0].num_sub_vol: 0
0x15a isw_dev[0].tid: 0
0x15b isw_dev[0].cng_master_disk: 0
0x15c isw_dev[0].cache_policy: 257
0x15e isw_dev[0].cng_state: 0
0x15f isw_dev[0].cng_sub_state: 0
0x188 isw_dev[0].vol.curr_migr_unit: 0
0x18c isw_dev[0].vol.check_point_id: 0
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 1
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fs_state: 0
0x194 isw_dev[0].vol.verify_errors: 0
0x196 isw_dev[0].vol.verify_bad_blocks: 0
0x1a8 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x1ac isw_dev[0].vol.map[0].blocks_per_member: 1953519880
0x1b0 isw_dev[0].vol.map[0].num_data_stripes: 7630936
0x1b4 isw_dev[0].vol.map[0].blocks_per_strip: 128
0x1b6 isw_dev[0].vol.map[0].map_state: 2
0x1b7 isw_dev[0].vol.map[0].raid_level: 1
0x1b8 isw_dev[0].vol.map[0].num_members: 2
0x1b9 isw_dev[0].vol.map[0].num_domains: 2
0x1ba isw_dev[0].vol.map[0].failed_disk_num: 0
0x1bb isw_dev[0].vol.map[0].ddf: 1
0x1d8 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x1000000
0x1dc isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1

/dev/sdb (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.1.00"
0x020 check_sum: 1819296132
0x024 mpb_size: 480
0x028 family_num: 1220941677
0x02c generation_num: 217856
0x030 error_log_size: 4600
0x034 attributes: 2147483648
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 0
0x040 orig_family_num: 3237443397
0x044 power_cycle_count: 0
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "  S13PJ9CS308086"
0x0e8 disk[0].totalBlocks: 1953523055
0x0ec disk[0].scsiId: 0x40000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "  S13PJ9CS308085"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x30000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 isw_dev[0].volume: "            DATA"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953519616
0x150 isw_dev[0].status: 0x8c
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].migr_priority: 0
0x159 isw_dev[0].num_sub_vol: 0
0x15a isw_dev[0].tid: 58
0x15b isw_dev[0].cng_master_disk: 0
0x15c isw_dev[0].cache_policy: 257
0x15e isw_dev[0].cng_state: 0
0x15f isw_dev[0].cng_sub_state: 0
0x188 isw_dev[0].vol.curr_migr_unit: 0
0x18c isw_dev[0].vol.check_point_id: 0
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fs_state: 0
0x194 isw_dev[0].vol.verify_errors: 0
0x196 isw_dev[0].vol.verify_bad_blocks: 0
0x1a8 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x1ac isw_dev[0].vol.map[0].blocks_per_member: 1953519880
0x1b0 isw_dev[0].vol.map[0].num_data_stripes: 7630936
0x1b4 isw_dev[0].vol.map[0].blocks_per_strip: 128
0x1b6 isw_dev[0].vol.map[0].map_state: 0
0x1b7 isw_dev[0].vol.map[0].raid_level: 1
0x1b8 isw_dev[0].vol.map[0].num_members: 2
0x1b9 isw_dev[0].vol.map[0].num_domains: 2
0x1ba isw_dev[0].vol.map[0].failed_disk_num: 255
0x1bb isw_dev[0].vol.map[0].ddf: 1
0x1d8 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x1dc isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1

root@martijn-server:~# blkid
/dev/sda1: UUID="c4109726-67e2-4fae-b74e-92ba36a90c01" TYPE="ext4" 
/dev/sda5: UUID="e9c4948c-c2b6-4667-a8ff-174954ddddd8" TYPE="swap" 
/dev/sdb1: UUID="8bde3bb8-b266-6406-c7f2-8b05883e23d7" LABEL=":DATA" TYPE="linux_raid_member" 
/dev/sdc1: UUID="8bde3bb8-b266-6406-c7f2-8b05883e23d7" LABEL=":DATA" TYPE="linux_raid_member"
```

---

### Post by martijnburger on 2011-07-14
Same output, but now with the nodmraid boot option:

```
root@martijn-server:~# dmraid -r -vvv
NOTICE: creating directory /var/lock/dmraid
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sdd
NOTICE: skipping removable device /dev/sde
NOTICE: skipping removable device /dev/sdf
NOTICE: skipping removable device /dev/sdg
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: isw metadata discovered
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
INFO: RAID devices discovered:

/dev/sdc: isw, "isw_bfdbhjciee", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdb: isw, "isw_bccajebghh", GROUP, ok, 1953523053 sectors, data@ 0
WARN: unlocking /var/lock/dmraid/.lock
root@martijn-server:~# dmraid -s -vv
NOTICE: skipping removable device /dev/sdd
NOTICE: skipping removable device /dev/sde
NOTICE: skipping removable device /dev/sdf
NOTICE: skipping removable device /dev/sdg
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: isw metadata discovered
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
NOTICE: added /dev/sdc to RAID set "isw_bfdbhjciee"
NOTICE: added /dev/sdb to RAID set "isw_bccajebghh"
ERROR: isw: wrong number of devices in RAID set "isw_bccajebghh_DATA" [1/2] on /dev/sdb
ERROR: isw: wrong number of devices in RAID set "isw_bfdbhjciee_DATA" [1/2] on /dev/sdc
*** Group superset isw_bccajebghh
--> *Inconsistent* Subset
name   : isw_bccajebghh_DATA
size   : 1953519872
stride : 128
type   : mirror
status : inconsistent
subsets: 0
devs   : 1
spares : 0
*** Group superset isw_bfdbhjciee
--> *Inconsistent* Subset
name   : isw_bfdbhjciee_DATA
size   : 1953519872
stride : 128
type   : mirror
status : inconsistent
subsets: 0
devs   : 1
spares : 0
root@martijn-server:~# fdisk -lu /dev/mapper/isw_bccajebghh_DATA
root@martijn-server:~# fdisk -lu /dev/mapper/isw_bfdbhjciee_DATA
root@martijn-server:~# dmraid -n
/dev/sdc (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.1.00"
0x020 check_sum: 1672355512
0x024 mpb_size: 480
0x028 family_num: 1531792844
0x02c generation_num: 217874
0x030 error_log_size: 4600
0x034 attributes: 2147483648
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 0
0x040 orig_family_num: 3237443397
0x044 power_cycle_count: 0
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "S13PJ9CS308086:1"
0x0e8 disk[0].totalBlocks: 1953524992
0x0ec disk[0].scsiId: 0xffffffff
0x0f0 disk[0].status: 0x2
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "  S13PJ9CS308085"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x50000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 isw_dev[0].volume: "            DATA"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953519616
0x150 isw_dev[0].status: 0x8c
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].migr_priority: 0
0x159 isw_dev[0].num_sub_vol: 0
0x15a isw_dev[0].tid: 0
0x15b isw_dev[0].cng_master_disk: 0
0x15c isw_dev[0].cache_policy: 257
0x15e isw_dev[0].cng_state: 0
0x15f isw_dev[0].cng_sub_state: 0
0x188 isw_dev[0].vol.curr_migr_unit: 0
0x18c isw_dev[0].vol.check_point_id: 0
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 1
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fs_state: 0
0x194 isw_dev[0].vol.verify_errors: 0
0x196 isw_dev[0].vol.verify_bad_blocks: 0
0x1a8 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x1ac isw_dev[0].vol.map[0].blocks_per_member: 1953519880
0x1b0 isw_dev[0].vol.map[0].num_data_stripes: 7630936
0x1b4 isw_dev[0].vol.map[0].blocks_per_strip: 128
0x1b6 isw_dev[0].vol.map[0].map_state: 2
0x1b7 isw_dev[0].vol.map[0].raid_level: 1
0x1b8 isw_dev[0].vol.map[0].num_members: 2
0x1b9 isw_dev[0].vol.map[0].num_domains: 2
0x1ba isw_dev[0].vol.map[0].failed_disk_num: 0
0x1bb isw_dev[0].vol.map[0].ddf: 1
0x1d8 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x1000000
0x1dc isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1

/dev/sdb (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.1.00"
0x020 check_sum: 1819296132
0x024 mpb_size: 480
0x028 family_num: 1220941677
0x02c generation_num: 217856
0x030 error_log_size: 4600
0x034 attributes: 2147483648
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a error_log_pos: 2
0x03c cache_size: 0
0x040 orig_family_num: 3237443397
0x044 power_cycle_count: 0
0x048 bbm_log_size: 0
0x0d8 disk[0].serial: "  S13PJ9CS308086"
0x0e8 disk[0].totalBlocks: 1953523055
0x0ec disk[0].scsiId: 0x40000
0x0f0 disk[0].status: 0x13a
0x0f4 disk[0].owner_cfg_num: 0x0
0x108 disk[1].serial: "  S13PJ9CS308085"
0x118 disk[1].totalBlocks: 1953525168
0x11c disk[1].scsiId: 0x30000
0x120 disk[1].status: 0x13a
0x124 disk[1].owner_cfg_num: 0x0
0x138 isw_dev[0].volume: "            DATA"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953519616
0x150 isw_dev[0].status: 0x8c
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].migr_priority: 0
0x159 isw_dev[0].num_sub_vol: 0
0x15a isw_dev[0].tid: 58
0x15b isw_dev[0].cng_master_disk: 0
0x15c isw_dev[0].cache_policy: 257
0x15e isw_dev[0].cng_state: 0
0x15f isw_dev[0].cng_sub_state: 0
0x188 isw_dev[0].vol.curr_migr_unit: 0
0x18c isw_dev[0].vol.check_point_id: 0
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fs_state: 0
0x194 isw_dev[0].vol.verify_errors: 0
0x196 isw_dev[0].vol.verify_bad_blocks: 0
0x1a8 isw_dev[0].vol.map[0].pba_of_lba0: 0
0x1ac isw_dev[0].vol.map[0].blocks_per_member: 1953519880
0x1b0 isw_dev[0].vol.map[0].num_data_stripes: 7630936
0x1b4 isw_dev[0].vol.map[0].blocks_per_strip: 128
0x1b6 isw_dev[0].vol.map[0].map_state: 0
0x1b7 isw_dev[0].vol.map[0].raid_level: 1
0x1b8 isw_dev[0].vol.map[0].num_members: 2
0x1b9 isw_dev[0].vol.map[0].num_domains: 2
0x1ba isw_dev[0].vol.map[0].failed_disk_num: 255
0x1bb isw_dev[0].vol.map[0].ddf: 1
0x1d8 isw_dev[0].vol.map[0].disk_ord_tbl[0]: 0x0
0x1dc isw_dev[0].vol.map[0].disk_ord_tbl[1]: 0x1

root@martijn-server:~# blkid
/dev/sda1: UUID="c4109726-67e2-4fae-b74e-92ba36a90c01" TYPE="ext4" 
/dev/sda5: UUID="e9c4948c-c2b6-4667-a8ff-174954ddddd8" TYPE="swap" 
/dev/sdb1: UUID="8bde3bb8-b266-6406-c7f2-8b05883e23d7" LABEL=":DATA" TYPE="linux_raid_member" 
/dev/sdc1: UUID="8bde3bb8-b266-6406-c7f2-8b05883e23d7" LABEL=":DATA" TYPE="linux_raid_member" 
```

---

### Post by psusi on 2011-07-14
Weird, it looks the same.  I wonder how your partition got to be larger than the disk.

---

### Post by martijnburger on 2011-07-14
Sorry I have no idea, all I know is the problems started when I upgraded to 11.04. Anyone can help me out here?

---

### Post by psusi on 2011-07-14
Use fdisk -u to delete the partition and recreate it with the same start sector, but have it end before the end of the disk.  The type should also be set to just Linux, not raid.

---

