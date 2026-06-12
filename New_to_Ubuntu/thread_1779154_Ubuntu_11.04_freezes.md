---
title: "Ubuntu 11.04 freezes"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by robro on 2011-06-10
At random times Ubuntu just freezes, I don't think its a hardware issue because in ubuntu 10.10 it didn't freeze.
Most of the time it freezes when I'm browsing the web or working with files and its very frustrating because thats all I really do :-x
I'm not really sure what info to give, haven't really had to deal with anything like this before...

Edit: oh and I forgot to mention that I can still move the mouse for some reason, but I cant click on anything

---

### Post by jtarin on 2011-06-10
How do you recover?

---

### Post by robro on 2011-06-10
Should have mentiond this but was in kinda hurry (and mad)
The virtual terminals still work only the gui freezes.. so I go to tty6, login, and sudo service gdm restart

---

### Post by jtarin on 2011-06-10
Then next time it happens go to another terminal an use the command ```
cat /var/log/syslog
``` and look through the last 20 lines or so and see if you notice anything.

---

### Post by robro on 2011-06-19
Alright it just freezed again, so I switched to a virtual terminal and tried to log in, but for some strange reason it keeps on spamming an error message every 3 seconds and not letting me type,
I restarted with alt+shift+print screen+REISUB, and tried to login with gnome, but it freezed the instant I saw my background, so I restarted again and logged in with xfce and its doing good so I'll stick with it until I can get this fixed :(
Heres the error, I got from syslog:
```

Jun 19 01:59:14 Natty-AOD260 kernel: [  838.899070] end_request: I/O error, dev sdb, sector 0
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.899082] Buffer I/O error on device sdb, logical block 0
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.899522] ldm_validate_partition_table(): Disk read failed.
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.899933] Dev sdb: unable to read RDB block 0
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.900578]  sdb: unable to read partition table
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.920070] sd 6:0:0:0: [sdb] No Caching mode page present
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.920084] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.946043] sd 6:0:0:0: [sdb] No Caching mode page present
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.946059] sd 6:0:0:0: [sdb] Assuming drive cache: write through

```
I'm actually quite happy it's messing up, it gets pretty boring with everything working perfectly :D

---

### Post by jtarin on 2011-06-19
> but for some strange reason it keeps on spamming an error message every 3 seconds What was the message?

---

### Post by robro on 2011-06-19
```

Jun 19 01:59:14 Natty-AOD260 kernel: [  838.899070] end_request: I/O error, dev sdb, sector 0
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.899082] Buffer I/O error on device sdb, logical block 0
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.899522] ldm_validate_partition_table(): Disk read failed.
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.899933] Dev sdb: unable to read RDB block 0
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.900578]  sdb: unable to read partition table
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.920070] sd 6:0:0:0: [sdb] No Caching mode page present
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.920084] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.946043] sd 6:0:0:0: [sdb] No Caching mode page present
Jun 19 01:59:14 Natty-AOD260 kernel: [  838.946059] sd 6:0:0:0: [sdb] Assuming drive cache: write through

```

---

### Post by jtarin on 2011-06-19
Looks like you might have some partitions problems. Do you have Gparted installed to take a look?

---

### Post by robro on 2011-06-19
Sure do.

---

### Post by dFlyer on 2011-06-19
Check you disk with disk utilities to see if you have some bad sectors.

---

### Post by jtarin on 2011-06-19
> **robro said:**
> Sure do.Take a screenshot and let see what we can see. If not sufficient then next step would be to go to [Boot Info Script: How to ]("http://ubuntuforums.org/showthread.php?t=1291280")

---

### Post by robro on 2011-06-19
How?

---

### Post by wildmanne39 on 2011-06-20
> **robro said:**
> How?Hi, have gparted open with your partitions showing, then hit the print screen key on your keyboard. Then click on the paper clip on the window when you open to type a post and add it to your post.

---

### Post by robro on 2011-07-02
I finally found what the problem is I think, I have a usb internet modem that doubles as a mini sd card reader/writer and I accidentally formated it couple of weeks ago (luckily I was able to get the data back).
I have no idea why or how formating a mini sd card could result in ubuntu freezing, but whenever I plug that thing in it stars showing that error again in the virtual consoles.
I powered off the computer, took out the modem, booted back into ubuntu and no more freezes or errors :|
the weird part is that if I plug it back in after it boots, no more freezes or errors come up too (so far).

Thanks for all the help :)

Edit: I have no idea how or when, but it looks like the problem just flew away :)

---

