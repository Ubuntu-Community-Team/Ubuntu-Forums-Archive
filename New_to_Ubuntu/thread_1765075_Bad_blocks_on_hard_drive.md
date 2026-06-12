---
title: "Bad blocks on hard drive"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by sunwatt on 2011-05-22
This used 32gb SSD hard drive has been unstable, so I looked in these forums and ran this test using terminal, and badblocks.

There are NINE (9) bad blocks, I dont know much, does that mean I should trash this SSD drive?

If it can be fixed, how? If not and its gunna always be unstable, it needs to be trashed.

Im running Ubuntu 10.04 Dell Vostro A90 (virtual Mini 9 clone) 2ghz ram

Thanks

Jim

jim@jim-laptop:~$ 
jim@jim-laptop:~$ sudo badblocks -s -v /dev/sda1
[sudo] password for jim: 
Checking blocks 0 to 28855295
Checking for bad blocks (read-only test): 10323840done, 4:56 elapsed
10323896done, 4:57 elapsed
10323897
10323898
10323899
10323900
10323901
10323902
10323903
done                                
Pass completed, 9 bad blocks found.
jim@jim-laptop:~$

---

### Post by prshah on 2011-05-22
> **sunwatt said:**
> There are NINE (9) bad blocks, 

If it can be fixed, how? If not and its gunna always be unstable, it needs to be trashed.


Nine bad blocks are minor, and you can run an fsck with the "-c" switch (from a live CD, on the unmounted partition) to ensure that the blocks are marked as such and not used again to store data.

However, if you find that fresh badblocks keep appearing, then it's probably time for a replacement. Since SSDs have no moving parts, if more badblocks keep appearing then it is likely that the memory chips themselves are failing (which is always ultimately expected in an SSD).

You may need to run the check about once a week initially, then, after a month or so you can either dispense with it or run a check once a month/quarter, whatever.

As a point of interest: I do believe that it will still be under a warranty, so if I was in your place, I'd attempt a warranty replacement.

---

### Post by sunwatt on 2011-05-23
"Nine bad blocks are minor, and you can run an fsck with the "-c" switch  (from a live CD, on the unmounted partition) to ensure that the blocks  are marked as such and not used again to store data".

Please tell me... I bootup with a live CD, and what is the bash I enter into terminal? 

Thats the terminal on the live CD I guess.

I just booted up, and operation is very erratic. I had to shut down & remove the battery and was very difficult.

Thanks for the help...

---

### Post by prshah on 2011-05-23
> **sunwatt said:**
> Please tell me... I bootup with a live CD, and what is the bash I enter into terminal? 

Thats the terminal on the live CD I guess.


Boot off the live CD; then open the terminal (Applications-Accessories-Terminal), then give the command```
sudo fsck -c /dev/sda1
```Replace sda1 with the actual partition device for your Ubuntu partition. To check, look at the output of fdisk```
sudo fdisk -l
#or you can use
sudo fdisk -l |grep -i ext
``` and look for ext2/3/4 (Extended) partitions.

---

### Post by sunwatt on 2011-05-23
sda1 is all there is

---

