---
title: "USB flash memory size"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by SteelCore on 2009-08-30
I have a 4Gb Kingston memory stick (Datatraveler).  Even if completely empty there would only be 3.3 Gb available space.  Right click>Properties shows 400 Mb used space.  Is this normal?  using 9.04
Thanks

---

### Post by Cheezespread on 2009-08-30
If you delete the file in the data traveler from within the drive , i believe those are moved to a trash file location within it . As in it might not have been completely removed. Can you check if a folder similar to .Trash-1000 is present ? And try to remove the contents and try to see the disk usage.

---

### Post by MelDJ on 2009-08-30
i think thats because of the conversion of gigs to megabytes and so on.

---

### Post by SteelCore on 2009-08-30
Yes, the trash file .Trash-1000 is there and it's empty.  The weird thing is that on R_click>Properties the total capacity is shown to be 3.7 in addition to the 400 Mb used space and 3.3 Gb free space.  I still dont understand how that adds up.

---

### Post by SteelCore on 2009-08-30
> **MelDJ said:**
> i think thats because of the conversion of gigs to megabytes and so on.

4 Gb is equal to 4096 Mb
Suppose I have only 4000 Mb then that's equal to 3.9 Gb. The properties show that I only have 3.3 Gb available space.

---

### Post by MelDJ on 2009-08-30
try reading this [http://74.125.153.132/search?q=cache:UzOhp1-_OlkJ:mydellmini.com/forum/mac-os-x/6890-7-2-gb-8-0-hard-drive.html+8gb+shows+7.2+gb&cd=1&hl=en&ct=clnk&gl=my](http://74.125.153.132/search?q=cache:UzOhp1-_OlkJ:mydellmini.com/forum/mac-os-x/6890-7-2-gb-8-0-hard-drive.html+8gb+shows+7.2+gb&cd=1&hl=en&ct=clnk&gl=my)
might be helpful

---

### Post by SteelCore on 2009-08-30
> **MelDJ said:**
> try reading this [http://74.125.153.132/search?q=cache:UzOhp1-_OlkJ:mydellmini.com/forum/mac-os-x/6890-7-2-gb-8-0-hard-drive.html+8gb+shows+7.2+gb&cd=1&hl=en&ct=clnk&gl=my](http://74.125.153.132/search?q=cache:UzOhp1-_OlkJ:mydellmini.com/forum/mac-os-x/6890-7-2-gb-8-0-hard-drive.html+8gb+shows+7.2+gb&cd=1&hl=en&ct=clnk&gl=my)
might be helpful

Well, at least it's not just me though I still wish I could better understand how the numbers add up.

---

### Post by MelDJ on 2009-08-30
did you read this part:
Judging by my 4GB STEC SSD, that's only half of the discrepancy.
 
My "4GB" drive's capacity is exactly 3,791,241,216 bytes. That's only 3.8 **GB** metric (drive manufacturer measurement) and 3.5 **GB** binary (file manager measurement).
 
The STEC is the only drive of mine which comes in below the rated metric capacity (5% below [IMG]http://www.mydellmini.com/forum/images/smilies/frown.gif[/IMG]), all my other drives come in slightly ahead of where you'd expect. For example, my Kingston **8GB** SDHC card's capacity is 8,199,864,320 bytes = 8.2**GB** = 7.6 GiB (the unambiguous abbreviation for binary **GB** is "GiB"). My conventional hard drives tend to come in almost exactly at the rated capacity in metric.

---

### Post by SteelCore on 2009-08-30
> **MelDJ said:**
> did you read this part:
Judging by my 4GB STEC SSD, that's only half of the discrepancy.
 
My "4GB" drive's capacity is exactly 3,791,241,216 bytes. That's only 3.8 **GB** metric (drive manufacturer measurement) and 3.5 **GB** binary (file manager measurement).
 

Seems my 4Gb Kingston and his 4Gb STEC are behaving similarly. But how can one figure out the 'exact capacity' in bytes of a memory stick. The Properties window, in my case, shows 3.7 GB total capacity.

---

### Post by MelDJ on 2009-08-30
go to terminal and type df

---

### Post by SteelCore on 2009-08-30
> **MelDJ said:**
> go to terminal and type df

```
/dev/sdb1              3919844    409912   3509932  11% /media/KINGSTON
```

I also used an online converter ([http://www.t1shopper.com/tools/calculate/](http://www.t1shopper.com/tools/calculate/))
Now the numbers make sense.  Thanks.

One last thing.  What is exactly the 409912 Kb used for. Thats quite a big chunk.

---

### Post by MelDJ on 2009-08-30
is it empty? maybe there are hidden files. some pendrives tend to come with security apps nowadays

---

### Post by SteelCore on 2009-08-30
Yes, it's completely empty. Even the Properties window says "Contents: nothing"

---

### Post by MelDJ on 2009-08-30
i really don't know this one. normally pendrives will show a few KB in use but not this much. i am guessing its a hidden folder. Maybe formatting it cleanly might do the trick. i am guessing though:lolflag:

---

### Post by SteelCore on 2009-08-30
I'll strech your patience a bit here.  How do I format a pendrive on Uubntu?

Terima Kasih in advance :)

---

### Post by MelDJ on 2009-08-30
wow! haha... good Malay:KS

open gparted select your pendrive then select partition and press format to. then you will be able to choose the filesystem you want..
always willing to help:popcorn:

---

### Post by SteelCore on 2009-08-30
Being in KL, I'm bound to know a few words.

Gparted downloaded via Applications>Add/Remove
I opened it by typing its name in the terminal coz couldn't find it in the app menu.
Chose /dev/sdb from the drop down menu on the left then it showed on the list in the pane below. But when I r-click the 'format to' option is greyed out!

---

### Post by MelDJ on 2009-08-30
I c.

you could try doing it again or restarting your computer then doing it

---

### Post by SteelCore on 2009-08-30
Tried it again and then restarted but the same result.

---

### Post by MelDJ on 2009-08-30
maybe try the alternative method here:
[http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/](http://www.cyberciti.biz/faq/howto-format-usb-pen-drive/) 
but be careful though:guitar:

---

### Post by SteelCore on 2009-08-30
That link gave a good hint. The drive needs to be unmounted before formating. I did that and successfully used gparted to format it to FAT32 (coz I also need to use it on xp).  Now the available space is 3.7 Gb
```
/dev/sdb1              3919844         4   3919840   1% /media/disk
```
The mysterious 400 Mb are gone.  I really wonder what that was but being unidentified it was surely safer to delete it.
Thanks again and Regards.

---

### Post by MelDJ on 2009-08-30
no problem:KS

---

