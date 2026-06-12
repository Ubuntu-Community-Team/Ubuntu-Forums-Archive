---
title: "Conflicting(?) information from GParted and fsck -c -f"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by Dondermans on 2011-04-14
I resized a nfts-partition in Windows XP on my external disk, since I am using Ubuntu more than Windows and Ext4 should allow my external disk to perform better. 

When I started GParted I got the following message:

[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/gparted.jpg[/IMG]

From the replies in another [_thread_]("http://ubuntuforums.org/showthread.php?t=1727298") I gathered that chkdsk /f /r did flag the filesystem dirty because I did not reboot the harddrive.

I am glad that the suggested solution worked, but the message 'The software has detected that the disk has at least 8 bad sectors' is cause for concern. I am trying to work out if it is a false positive or not.

I ran fsck -c -f to force fsck to read the badsectors, with the following result:

[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/badblocks-result.jpg[/IMG]

I would like to know what the health of my disk is. According to GParted it might be due for replacement, while according to fsck no badblocks are present.

I tried enabling S.M.A.R.T. information for the drive using the DOS-based program ESTOOLS. I ran ESTOOLS from a bootable CD, but the program does not detect the drive. It is a Freecom XS 3.0 (the disk itself is a Samsung HD103SI /Y which should be ATA S.M.A.R.T. compliant ([_datasheet_]("http://www.samsung.com/ae/consumer/computers-peripherals/hard-disk-drives/desktop-sata/HD103SI/index.idx?pagetype=prd_detail"))).

Regards,
Don

---

### Post by TeoBigusGeekus on 2011-04-14
Do you get the same message from gparted after the fsck check?

---

### Post by Dondermans on 2011-04-14
> **TeoBigusGeekus said:**
> Do you get the same message from gparted after the fsck check?

Thank you for your reply. 

No, I did not see the message in GParted again once I ran chkdsk /f /r and rebooted the harddrive (the solution suggested in the thread I [_linked to_]("http://ubuntuforums.org/showthread.php?t=1727298") in the OP).

---

### Post by TeoBigusGeekus on 2011-04-14
So, unless I'm missing something, everything is sorted out, isn't it?

---

### Post by Dondermans on 2011-04-14
> **TeoBigusGeekus said:**
> So, unless I'm missing something, everything is sorted out, isn't it?

It might be, but I am not quite sure. The reason *why* I am not sure is that I read that the bad sectors mentioned by the warning message in GParted could have been written to the 'bad sector table'. I ended up deleting the partion and creating two new partitions. I created a NTFS-partition using compmgmt.msc in Windows XP and a Ext4-partition using GParted.

I understand that bad sectors are a forebode of more misery and (not necessarily imminent) failure.

---

### Post by TeoBigusGeekus on 2011-04-14
It might be that your drive has started to show some signs of corruption, but I wouldn't worry that much. 
If you add the drive to your fstab file, make sure that the last parameter of its line is 2 and not 0: after every few mounts, the system will check it for errors.
To be on the safe side, backup any crucial data from that drive to something else from time to time.

---

### Post by psusi on 2011-04-14
You only checked the ext4 partition; the errors could be in the ntfs partition.

Also the disk utility ( on the administration menu ) will show the SMART status and let you run the self test.

Run sudo badblocks -b 512 /dev/sdb to test the whole disk.

---

### Post by Dondermans on 2011-04-14
> **psusi said:**
> You only checked the ext4 partition; the errors could be in the ntfs partition.

Also the disk utility ( on the administration menu ) will show the SMART status and let you run the self test.

Run sudo badblocks -b 512 /dev/sdb to test the whole disk.

Thank you for your reply. I will run badblocks and post a screenshot of the results.

**Edit:** *Running sudo badblocks -b 512 /dev/sdb does produce no output. It asks for my sudo-password and nothing appears to be happening:*
[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/sudo-badblocks.jpg[/IMG]
 

Is there a particular reason for recommending ```
sudo badblocks -b 512 /dev/sdb
``` instead of ```
sudo fsck -c -f /dev/sdb
```I tried accessing SMART-data through the Disk Utility, but is states SMART is not supported:
[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/diskutility.png[/IMG]

I gathered from another source that transmission of SMART-data is something that is not enabled by default for the HD103SI /Y. I should be able to enable/disable SMART data using ESTOOLS, but that program does not detect my external drive (yet it does detect the ATA Samsung HD161HJ shown in the picture above).

---

### Post by psusi on 2011-04-14
It takes a while; give it time.  SMART has trouble working correctly via USB.  fsck is for checking filesystems, so you can not run it on a whole disk.

---

### Post by Dondermans on 2011-04-14
> **psusi said:**
> It takes a while; give it time.  SMART has trouble working correctly via USB.  fsck is for checking filesystems, so you can not run it on a whole disk.

Thank you for your reply. I must admit that I wrote the edit of my previous message without thinking too hard about *why* nothing was happening. Having read the man page of fsck it is a bit ackward to realise that I did not catch this myself.

I will check sb1 and sdb2 separately. Do you recommend using fsck to check /dev/sdb1 (the NTFS-partition) instead of chkdsk /f /r in Windows XP? It seems prudent to use a Windows XP program to check a Windows XP native file system (as was suggested by Oldfred in another [_thread_]("http://ubuntuforums.org/showpost.php?p=10669433&postcount=4") I started).

---

### Post by psusi on 2011-04-14
I recommend running badblocks on the whole disk.  This will then give you a list of bad blocks which you can attempt to repair, and THEN fsck each filesystem.

---

### Post by Dondermans on 2011-04-14
I am terribly sorry, my brain is still suffering from years of microsoftening. It *is* getting better though. :D

I shall run ```
sudo badblocks -b 512 -s /dev/sdb
```[FONT=monospace]

By adding the -s switch badblocks should [/FONT]show the progress of the scan by writing out the block numbers as they are checked ([_source)_]("http://www.go2linux.org/linux/2010/11/linux-badblocks-man-page-841").
[FONT=monospace] 
**Edit:** *Well, the -s modifier actually writes out a percentage instead of block numbers, but at least I can track its progress...* 

[/FONT]

---

### Post by Dondermans on 2011-04-14
The results:```
don@don-GA-770TA-UD3:~$ sudo badblocks -b 512 -s /dev/sdb
[sudo] password for don: 
Checking for bad blocks (read-only test): 1292056512ne, 2:13:08 elapsed
1292056568ne, 2:13:15 elapsed
1292056569ne, 2:13:18 elapsed
1292056570ne, 2:13:20 elapsed
1292056571ne, 2:13:23 elapsed
1292056572ne, 2:13:25 elapsed
1292056573ne, 2:13:28 elapsed
1292056574ne, 2:13:30 elapsed
1292056575ne, 2:13:33 elapsed
1292062320ne, 2:13:35 elapsed
1292062344ne, 2:13:40 elapsed
1292062345ne, 2:13:43 elapsed
1292062346ne, 2:13:45 elapsed
1292062347ne, 2:13:48 elapsed
1292062348ne, 2:13:50 elapsed
1292062349ne, 2:13:52 elapsed
1292062350ne, 2:13:55 elapsed
1292062351ne, 2:13:57 elapsed
1434333440ne, 2:28:33 elapsed
1434333496ne, 2:28:38 elapsed
1434333497ne, 2:28:40 elapsed
1434333498ne, 2:28:42 elapsed
1434333499ne, 2:28:45 elapsed
1434333500ne, 2:28:47 elapsed
1434333501ne, 2:28:49 elapsed
1434333502ne, 2:28:52 elapsed
1434333503ne, 2:28:54 elapsed
1435490608ne, 2:29:04 elapsed
1435490648ne, 2:29:09 elapsed
1435490649ne, 2:29:12 elapsed
1435490650ne, 2:29:14 elapsed
1435490651ne, 2:29:16 elapsed
1435490652ne, 2:29:19 elapsed
1435490653ne, 2:29:21 elapsed
1435490654ne, 2:29:24 elapsed
1435490655ne, 2:29:26 elapsed
1435492304ne, 2:29:29 elapsed
1435492320ne, 2:29:33 elapsed
1435492321ne, 2:29:36 elapsed
1435492322ne, 2:29:38 elapsed
1435492323ne, 2:29:41 elapsed
1435492324ne, 2:29:43 elapsed
1435492325ne, 2:29:46 elapsed
1435492326ne, 2:29:48 elapsed
1435492327ne, 2:29:51 elapsed
1435496024ne, 2:29:53 elapsed
1435496080ne, 2:29:58 elapsed
1435496081ne, 2:30:01 elapsed
1435496082ne, 2:30:03 elapsed
1435496083ne, 2:30:05 elapsed
1435496084ne, 2:30:08 elapsed
1435496085ne, 2:30:10 elapsed
1435496086ne, 2:30:13 elapsed
1435496087ne, 2:30:15 elapsed
1435497736ne, 2:30:18 elapsed
1435497752ne, 2:30:23 elapsed
1435497753ne, 2:30:25 elapsed
1435497754ne, 2:30:28 elapsed
1435497755ne, 2:30:30 elapsed
1435497756ne, 2:30:33 elapsed
1435497757ne, 2:30:35 elapsed
1435497758ne, 2:30:37 elapsed
1435497759ne, 2:30:40 elapsed
1435499408ne, 2:30:42 elapsed
1435499424ne, 2:30:47 elapsed
1435499425ne, 2:30:50 elapsed
1435499426ne, 2:30:52 elapsed
1435499427ne, 2:30:55 elapsed
1435499428ne, 2:30:57 elapsed
1435499429ne, 2:30:59 elapsed
1435499430ne, 2:31:02 elapsed
1435499431ne, 2:31:04 elapsed
```I pulled this data from the var/log/messages (first and last entry of this kind):

```
Apr 14 23:54:00 don-GA-770TA-UD3 kernel: [10852.366682] sd 10:0:0:0: [sdb] Unhandled sense code
Apr 14 23:54:00 don-GA-770TA-UD3 kernel: [10852.366691] sd 10:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 14 23:54:00 don-GA-770TA-UD3 kernel: [10852.366699] sd 10:0:0:0: [sdb] Sense Key : Medium Error [current] 
Apr 14 23:54:00 don-GA-770TA-UD3 kernel: [10852.366708] sd 10:0:0:0: [sdb] Add. Sense: Unrecovered read error
Apr 14 23:54:00 don-GA-770TA-UD3 kernel: [10852.366717] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 4d 03 37 c0 00 00 40 00

Apr 15 00:11:56 don-GA-770TA-UD3 kernel: [11928.643534] sd 10:0:0:0: [sdb] Unhandled sense code
Apr 15 00:11:56 don-GA-770TA-UD3 kernel: [11928.643543] sd 10:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Apr 15 00:11:56 don-GA-770TA-UD3 kernel: [11928.643551] sd 10:0:0:0: [sdb] Sense Key : Medium Error [current] 
Apr 15 00:11:56 don-GA-770TA-UD3 kernel: [11928.643560] sd 10:0:0:0: [sdb] Add. Sense: Unrecovered read error
Apr 15 00:11:56 don-GA-770TA-UD3 kernel: [11928.643569] sd 10:0:0:0: [sdb] CDB: Read(10): 28 00 55 8f fb a0 00 00 08 00
```There are in total **81 medium errors** of this kind (I compared the time stamps from the badblocks result to the entries in the log file). If I understand the matter at hand correctly, bad blocks are a progressing failure. Although I could write these to the bad sectors table (using the method described [_here_](http://ubuntuforums.org/showpost.php?p=10461433&postcount=13), there is no real way of stopping it. At any time the disk could run out of spare sectors at which point the disk will 'live' until vital sectors are hit (the ones containing firmware for example).

I suppose the easiest way would be to buy a new disk, as the 1 year warranty has already expired, correct?

Thank you for your assistance, it is truly invaluable and a great asset of this community.

---

### Post by psusi on 2011-04-14
Physical damage to the disk often does grow worse over time, but bad sectors can also happen if you were in the middle of a write when the power went out or other causes.  In these cases there is nothing wrong physically, so you just need to write good data to the sector and it will work again.

Now that you have a list of bad sectors, you can try writing to them and see if they recover.  For each sector number in that list, do the following:

```

sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=NNNN
sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1 seek=NNNN

```

The first tries to read that sector.  Obviously it should fail.  This is to make sure you have the right location.  The second command tries to write all zeros to that sector.  If this succeeds, then continue to the next sector.

If you get through the whole list, run badblocks again and it should find no errors, then fsck each filesystem on the disk.  Run badblocks again about once a week for a month or two to make sure no new bad blocks develop.  If they don't, then you are probably fine and can drop back to running badblocks once every month or two just to make sure.

---

### Post by Dondermans on 2011-04-15
Ok, I have started on the list:

Much to my surprise the majority of the listed sectors do not generate input/ output errors. Instead I get this:

```

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1292056512
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0333961 s, 15.3 kB/s

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
seek=1292056512
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0154052 s, 33.2 kB/s
```However, there are a few sectors which generate input/output errors (as was to be expected):
```

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1434333497
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.23844 s, 0.0 kB/s

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
seek=1292062347
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0420278 s, 12.2 kB/s

1434333497ne, 2:28:40 elapsed
don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1434333497
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.22883 s, 0.0 kB/s

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
seek=1434333497
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.039945 s, 12.8 kB/s

1435490648ne, 2:29:09 elapsed
don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1435490648
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.43448 s, 0.0 kB/s

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
seek=1435490648
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0405753 s, 12.6 kB/s

1435492321ne, 2:29:36 elapsed
don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1435492321
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.42945 s, 0.0 kB/s

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
seek=1435492321
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0198579 s, 25.8 kB/s

1435496084ne, 2:30:08 elapsed
don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1435496084
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.42603 s, 0.0 kB/s

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
seek=1435496084
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0400162 s, 12.8 kB/s

1435497757ne, 2:30:35 elapsed
don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1435497757
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.42657 s, 0.0 kB/s

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
seek=1435497757
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0416945 s, 12.3 kB/s

1435499430ne, 2:31:02 elapsed
don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1435499430
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.43131 s, 0.0 kB/s

don@don-GA-770TA-UD3:~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
seek=1435499430
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0245836 s, 20.8 kB/s

```I added returns before each 'skip' and 'seek' part of the command line to remove the horizontal scrollbar. 

I will follow up on your recommendation and run: ```
sudo badblocks -b 512 -s /dev/sdb
``` again and see if it reports back any errors.

I would like to know whether a sector can be considered irrecoverable if I wrote zeroes to said sector using the seek command and it generates the same error when using the skip command for the second time.

---

### Post by psusi on 2011-04-15
It is imperative that you enter the commands EXACTLY as I said.  You were alternating back and forth between seek and skip, but keeping the drive as the input.  If, and only if, the read fails, move on to the second command where the input and output are swapped, in addition to skip changing to seek.

The second command you entered was still reading from the hard disk instead of writing, only it was reading from the first sector and trying to write the output to /dev/zero at a higher offset.

---

### Post by Dondermans on 2011-04-15
Hmm... I must have misunderstood the contents of message #14.

I suppose I did not quite interpret the results of badblocks -b 512 -s /dev/sdb correctly. I did apply both

```

sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=NNNN
```and```

sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1 seek=NNNN 
```to all sectors listed by badblocks.

Did I aggravate the problem by misinterpreting your message? I did make a backup, perhaps restoring the backup is in order?

**Edit:** [i]On the second run of the badblocks command, badblocks appears to be listing the same sectors again:
[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/badblocks-2nd_run.jpg[/IMG]

Does this have to do with the misinterpretation of message #14?[/i]

---

### Post by psusi on 2011-04-15
```

sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=NNNN
sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1 seek=NNNN
               ^                ^^^^         ^^^^^^

```

Note the difference.  You didn't swap those arguments.

---

### Post by Dondermans on 2011-04-15
I see. 

I'll start over, thank you for your patience.

**Edit:** [I]Done:

```
I applied both the skip and the seek command to these sectors:

1292056575ne, 2:13:33 elapsed
~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1292056575
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.56565 s, 0.0 kB/s

~$ sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1
seek=1292056575
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0794526 s, 6.4 kB/s

1292062347ne, 2:13:48 elapsed
~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1
skip=1292062347
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.97286 s, 0.0 kB/s

~$ sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1
seek=1292062347
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0409883 s, 12.5 kB/s

1434333497ne, 2:28:40 elapsed
~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=1434333497
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.28934 s, 0.0 kB/s

~$ sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1 seek=1434333497
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.097871 s, 5.2 kB/s

1435490648ne, 2:29:09 elapsed
~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=1435490648
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.48123 s, 0.0 kB/s

~$ sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1 seek=1435490648
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0763503 s, 6.7 kB/s

1435492321ne, 2:29:36 elapsed
~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=1435492321
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.47805 s, 0.0 kB/s

~$ sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1 seek=1435492321
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0307338 s, 16.7 kB/s

1435496084ne, 2:30:08 elapsed
~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=1435496084
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.44828 s, 0.0 kB/s

~$ sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1 seek=1435496084
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.046906 s, 10.9 kB/s

1435497757ne, 2:30:35 elapsed
~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=1435497757
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.52467 s, 0.0 kB/s

~$ sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1 seek=1435497757
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.030358 s, 16.9 kB/s

1435499430ne, 2:31:02 elapsed
~$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=1435499430
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.48053 s, 0.0 kB/s

~$ sudo dd bs=512 oflag=direct if=/dev/zero of=/dev/sdb count=1 seek=1435499430
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0407358 s, 12.6 kB/s
```The other sectors did not generate Input/output errors. I will run ```
sudo badblocks -b 512 -s /dev/sdb
``` again and post the results.[/I]

---

### Post by Dondermans on 2011-04-15
The good news:
Only one sector is marked as bad after following up on the suggestions in message [_#14_]("http://ubuntuforums.org/showpost.php?p=10678144&postcount=14").

The bad news:
It is a sector which did not appear on the list I posted in message [_#13_]("http://ubuntuforums.org/showpost.php?p=10677775&postcount=13"): 

```
~$ sudo badblocks -b 512 -s /dev/sdb
Checking for bad blocks (read-only test): 1435488960ne, 2:30:19 elapsed
done                                

```Executing
```

sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=1435488960

```results in:

```
$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=1435488960
[sudo] password for don: 
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0377768 s, 13.6 kB/s
```e.g. no Input/output error.

I just ran badblocks for a third time and this time there are no bad sectors to list: 
```
$ sudo badblocks -b 512 -s /dev/sdb

```Results:
```
$ sudo badblocks -b 512 -s /dev/sdb
[sudo] password for don: 
Checking for bad blocks (read-only test): done
```On to checking /dev/sdb2 using:
```
sudo fsck -c -f /dev/sdb2
```Since /dev/sdb1 is a NTFS-partition I suppose that I should check it using chkdsk /f /r in Windows XP, rebooting the drive twice after that is done? I have found several sources stating that fsck-support for NTFS is limited ([_1_]("http://ubuntuforums.org/showthread.php?t=1435461&highlight=fsck.ntfs%3A"), [_2_]("http://linux.die.net/man/8/ntfsfix")). I created the partition in Windows XP using compmgmt.msc.

---

### Post by psusi on 2011-04-15
Yes, you should chkdsk NTFS from windows.  It looks good so far.  Run badblocks one or two more times to be sure, then give it a few days to a week and run it again.

---

### Post by Dondermans on 2011-04-16
Perhaps the harddrive is not failing after all. No bad sectors were detected on the fourth run of ```
badblocks -b 512 -s /dev/sdb
```The NTFS partition does not have bad sectors either, according to ```
chkdsk /f /r
```Will repeat this a couple of times as advised in message [_#14_]("http://ubuntuforums.org/showpost.php?p=10678144&postcount=14"). If bad sectors develop in the coming weeks I won't be taking any chances and buy a new harddrive, but it looks good at the moment.

I will mark this thread solved shortly. Thanks to everyone who contributed.

---

### Post by Dondermans on 2011-04-16
The plot thickens...

Results of the fifth run of badblocks:```
$ sudo badblocks -b 512 -s /dev/sdb
[sudo] password for don: 
Checking for bad blocks (read-only test): 1435488960ne, 2:27:13 elapsed
done
```Sector #1435488960 was also listed when the second run of badblocks finished (see message [_#20_]("http://ubuntuforums.org/showpost.php?p=10680464&postcount=20")). Shortly after the second run finished I executed:
```
$ sudo dd bs=512 iflag=direct if=/dev/sdb of=/dev/zero count=1 skip=1435488960
```The sector could be read so I did not write zeroes. I executed the same code after the fifth run of badblocks, it could still be read.

Is it possible this is a false positive? It would explain why badblocks lists a readable sector on two seperate runs.

On a separate note:

I ran: ```
sudo fsck -c -f /dev/sdb2
```

After the first run it stated 'Updating bad block inode'

---

### Post by psusi on 2011-04-17
It looks like that one can be read sometimes, and not others.  Try reading it with dd at different times and temperatures.  In other words, try it (a few times) when you first turn the computer on in the morning, then again (a few times) after it has had time to warm up.

---

