---
title: "Input/Output error with USB Harddisk caused data loss!"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by dannelb on 2011-06-03
I'm having the same problem now...were you able to figure out how to retrieve your files? What did you do in the end?

---

### Post by lian1238 on 2011-06-03
Unfortunately, I was unable to recover it.
Have you tried reading it from a Windows machine?

---

### Post by Mariane on 2011-06-03
After you plug it in (straight into the computer, not via a hub), count slowly up to ten and then type: 

```

dmesg | tail

```

Please post the output here. 

Mariane

---

### Post by dannelb on 2011-06-03
Here's the output:

> [20080.291972] sd 15:0:0:0: Attached scsi generic sg3 type 0
[20080.305013] sd 15:0:0:0: [sde] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[20080.305862] sd 15:0:0:0: [sde] Write Protect is off
[20080.305875] sd 15:0:0:0: [sde] Mode Sense: 21 00 00 00
[20080.305883] sd 15:0:0:0: [sde] Assuming drive cache: write through
[20080.307736] sd 15:0:0:0: [sde] Assuming drive cache: write through
[20080.307771]  sde: sde1
[20080.363598] sd 15:0:0:0: [sde] Assuming drive cache: write through
[20080.363616] sd 15:0:0:0: [sde] Attached SCSI disk
[20109.024075] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
dan@FOH:~$ dmesg | tail
[20168.449813] sd 16:0:0:0: Attached scsi generic sg3 type 0
[20168.461897] sd 16:0:0:0: [sde] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[20168.462754] sd 16:0:0:0: [sde] Write Protect is off
[20168.462767] sd 16:0:0:0: [sde] Mode Sense: 21 00 00 00
[20168.462776] sd 16:0:0:0: [sde] Assuming drive cache: write through
[20168.464521] sd 16:0:0:0: [sde] Assuming drive cache: write through
[20168.464556]  sde: sde1
[20168.507407] sd 16:0:0:0: [sde] Assuming drive cache: write through
[20168.507423] sd 16:0:0:0: [sde] Attached SCSI disk
[20171.104094] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)


---

### Post by dannelb on 2011-06-03
And, no, I haven't tried a Windows machine. All the computers in my house have Ubuntu on them...

---

### Post by Mariane on 2011-06-03
OK. Now you can try: 

```

sudo mkdir /media/backup
sudo mount /dev/sde1 /media/backup

```

Either it works - you will see your files in /media/backup - or you get some error message. If you get an error message, like something about specifying the file system, please post it here. 

Mariane

---

### Post by Mariane on 2011-06-05
Did it work? 

Mariane

---

### Post by dannelb on 2011-06-08
I ended up being able to get some of my files back by using PhotoRec. I looked into the problem a bit more and it seems like the filesystem had an error (stupid vfat). So, I ran PhotoRec a few times, got my pictures, some videos and some music back. Still lost a good bit of stuff, but that's how life goes I guess.

I have since formatted the drive with ext3 filesystem, hopefully that holds up better.

Thanks for your help.

---

