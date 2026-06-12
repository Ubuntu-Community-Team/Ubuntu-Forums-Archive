---
title: "LG DVD writer does not work with 9.04"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by panorack on 2009-06-20
I cannot get Ubuntu versions later than 8.04 to work with my LG DVD rewriter. It worked perfectly with 8.04 but since upgrading to 8.10 and now to 9.04 it will not work. 

Inserting a blank CD brings up the Dialogue Box asking what I wish to do so it seems the drive is mounted ok. But when I try to select a file for writing I am asked to insert a blank CD, even though there is one in the drive that has been seen. Removing and re-inserting the blank CD simply starts the cycle again. I get the same results if I approach it by loading a program like Brasero and trying to write using that application.

The strange thing is that if I re-boot with the 8.04 live CD I can use the drive with no problem so something has changed since the 8.04 distribution. Can anyone offer any help in sorting this?

Many thanks in anticipation,

Derek

---

### Post by MrWES on 2009-06-20
> **panorack said:**
> I cannot get Ubuntu versions later than 8.04 to work with my LG DVD rewriter. It worked perfectly with 8.04 but since upgrading to 8.10 and now to 9.04 it will not work. 

Inserting a blank CD brings up the Dialogue Box asking what I wish to do so it seems the drive is mounted ok. But when I try to select a file for writing I am asked to insert a blank CD, even though there is one in the drive that has been seen. Removing and re-inserting the blank CD simply starts the cycle again. I get the same results if I approach it by loading a program like Brasero and trying to write using that application.

The strange thing is that if I re-boot with the 8.04 live CD I can use the drive with no problem so something has changed since the 8.04 distribution. Can anyone offer any help in sorting this?

Many thanks in anticipation,

Derek

Please output the following command from the terminal after inserting the blank cd:
```
dmesg | tail 
```

---

### Post by panorack on 2009-06-20
> **MrWES said:**
> Please output the following command from the terminal after inserting the blank cd:
```
dmesg | tail 
```

I think I have done what you requested? Put the disc in the drive (dialogue box popped up) then put the above command into a terminal and the output was as follows:

[   83.930950] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   83.930976] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   83.931053] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   87.248467] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   97.572023] eth0: no IPv6 routers present
[  367.366910] cdrom: This disc doesn't have any tracks I recognize!
[  369.351395] end_request: I/O error, dev sr1, sector 0
[  369.351409] Buffer I/O error on device sr1, logical block 0
[  369.372965] end_request: I/O error, dev sr1, sector 0
[  369.372979] Buffer I/O error on device sr1, logical block 0

I noticed the line about the disc not having recognisable tracks but can't understand why.

Let me know if this is not what you wanted.

Derek

---

