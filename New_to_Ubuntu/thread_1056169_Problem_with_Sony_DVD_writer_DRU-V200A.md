---
title: "Problem with Sony DVD writer DRU-V200A"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by MattPendley on 2009-01-31
I recently purchased a Sony DVD writer (DRU-V200A) but for some reason, the only thing I can get it to do is read CD's.  I've tried to get it to read DVD's but it wont work.  (I think the problem might be the region code but for some reason I can't get it to change.)  When ever I try to write a .iso file to a CD, Brasero gives me an error that says something to the extent of "CD over burned."  It won't write DVD's properly either.  If any one has any knowledge of this burner, any help would be graciously accepted.  Thanks!

[Edit]After trying to burn a Mythbuntu .iso file using K3b at 8x speed, I get this message, "/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'"  I saved the error report this time if anyone needs to have a look at it.

---

### Post by conryf on 2009-02-11
I'm having the same problem with my Sony DRX-S7OU-R, I got it to handle a cd ok, but trying to rip a DVD and DvdRip just hangs. Any help out there?

---

### Post by mc4man on 2009-02-11
If this is a new drive you installed to replace an older one there are 2 things worth checking.
While it's not always needed, many drives need a region set.

For that you install regionset and with a disk in the drive run 
```
regionset
```

or if the drive is something other than /dev/scd0 run
regionset /dev/scdx where x is what your drive is.

If line 4 says "type: set" your good and answer n, if it says "type: none" then ans. y and set to your region.

To find your drives device node and other info run
```
sudo lshw -C disk
```

Also many new drives need an 80 wire ide cable and most older drives came with a 40 wire.
Run this to ck. if it's an issue (note you can have an 80 wire and still see a line suggesting you don't, your usually looking for an dma error line instead.

```
grep 'UDMA' /var/log/dmesg
```

And the standard 'do you have libdvdcss2 installed (2nd poster

---

