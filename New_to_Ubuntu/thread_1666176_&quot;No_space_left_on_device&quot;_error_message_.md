---
title: "&quot;No space left on device&quot; error message : NOT TRUE (while writing to a SD card)"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Loda.103 on 2011-01-13
Hi,

I'm news to Ubuntu and until now I manage to fix all my smalls problems searching this forum and google.

But, now I'm stuck.


**I want to copy some picture** and a few video **to a 2GB SD card** (brand: Kentron, pre-formated FAT32) for a digital picture frame.

[B]after copying 168mb, I receive an error *"No space left on device"*. But, the SD still have over 90% free space.
[/B]

I cannot copy more file from my HD to the SD, duplicate files already present on the SD nor creating empty folder/file in the SD.
[COLOR="Gray"]My files names don't have any special char. eg: "2010-04-11 20.45.02.jpg"[/COLOR]


Following some advices from thread about similar problem, I run "**df -h**". It returned what I expected:
```
...
/dev/mmcblk0p1        1.9G  165M  1.7G   9% /media/disk-1

```

I also tried to unmunt it and run "**sudo fsck /dev/mmcblk0p1**"
```
fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
/dev/mmcblk0p1: 172 files, 5277/60281 clusters

```

I also tried unmounting/re-mounting the SD and rebooting my machine [COLOR="gray"](I was a windows user)[/COLOR]

[COLOR="gray"]Looks like the more typical raison for this problem is a not properly mounted disk or an iNode/FS limitation. Since the SD is in FAT32 and was automaticaly mounted by Ubuntu, I think I got an other problem.
[/COLOR]

I got a dual boot with Ubuntu 9.04 [COLOR="gray"](yes, I know, I need to update, I will do it after doing my backups)[/COLOR] running on a Vostro 1510 (with an internal SD reader). I install it from an official LiveCD.

because i'm new and am not a terminal guru, I posted this issue in the "beginner" section. please, redirect me if I'm wrong.

Any adivce / direction / help is more than appreciate,

Loda

---

### Post by Kirboosy on 2011-01-13
It might be hitting a bad sector on the flash media. Causing it to say its full when its really not.

I saw that you mentioned you dual boot. Does it still have problems in Windows?

---

### Post by Loda.103 on 2011-01-13
"bad sector" hum. good question. but the fsck did not return any error. anyway I tried to format my SD using "**sudo mkfs.vfat /dev/mmcblk0p1**
"

this fixed the problem ! I hope the digital frame will read the SD.

maybe the pre-format was not really good/compatible.

thanks

---

### Post by Kirboosy on 2011-01-13
I was actually going to suggest reformatting it for safe measure but good for you.

You seem like a terminal guru to me because you know how to format your cards in it ;)

You could of used the GUI and right clicked the media and hit Format :)

---

### Post by christophski on 2011-01-13
The problem could have been that there was stuff in the trash folder, which is usually hidden (named .trash or .trash1000 or something). This has happened to me a couple of times.

---

### Post by Loda.103 on 2011-01-13
> **christophski said:**
> The problem could have been that there was stuff in the trash folder, which is usually hidden (named .trash or .trash1000 or something). This has happened to me a couple of times.

the content of the trash should appear as used space when running "df -h", no?
And I forgot to specify, but the SD was new.

Anyway, thanks for the tips, i keep it in mind if I get a similar problem in the future.

---

### Post by iceman30ad on 2011-01-13
most  os don't count trash as used space so even if you had done the ctrl -h it wouldnt have made any diffrence

---

### Post by Loda.103 on 2011-01-13
> **Caboose885 said:**
> I was actually going to suggest reformatting it for safe measure but good for you.

You seem like a terminal guru to me because you know how to format your cards in it ;)

You could of used the GUI and right clicked the media and hit Format :)


me? a terminal guru :P ! (but I cheated, I asked google.)

My GUI does not ofer a "format" entry in the contextual menu. nor in the properties tabs. I was surprise, but I plan to update soon, so I will worry about this an other day.

---

### Post by Loda.103 on 2011-01-13
> **iceman30ad said:**
> most  os don't count trash as used space so even if you had done the ctrl -h it wouldnt have made any diffrence

Thanks for the info. I did not knew this.

---

### Post by Kirboosy on 2011-01-13
> **Loda.103 said:**
> me? a terminal guru :P ! (but I cheated, I asked google.)

My GUI does not ofer a "format" entry in the contextual menu. nor in the properties tabs. I was surprise, but I plan to update soon, so I will worry about this an other day.


Hmmm well I know in 9.10+ it has that option. Its been so long since I've used 9.04. Just update and then you should be able to use the GUI more. :)

Glad you got everything sorted out.

---

### Post by John Coulthard on 2011-04-15
I got the same error writing to an XD card. I tried reformatting the card but it made no difference. Then I noticed that the failure occurred after copying 255 files (out of the 453 I had - this was for a photo frame). The magic number 255 triggered all sorts of old memories and suspecting there might be some limit on the number of files allowed in a folder on a FAT device I created two folders and had no problems copying all my files over, splitting them between the two folders of course. And my photo frame seems to be quite happy with this arrangement too.

---

