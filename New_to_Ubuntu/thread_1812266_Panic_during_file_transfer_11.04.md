---
title: "Panic during file transfer 11.04"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by Petrovic on 2011-07-26
Am trying to copy some files from a usb HDD to a usb HDD and seem to be having some problems. I've no idea what's happening (I'm a total n00b when it comes to linux) nor if I can pull up a log from somewhere, but I end up with a page of text with the last line reading "Panic occured. Switching back to text console" and my Caps Lock and Scroll Lock lights on kb flash with a hung machine. This is the first time I've has something like this happen. It's a drive from my mates machine, which is also running 11.04. Have transferred stuff when we were on 10.10 with no drama, so I'm somewhat confused. There are no programs running other than boot default. 

Taa for any assistance.

Ok, it seems to be one or two files that are having the issue. I just sucessfully transferred 6gb to it with no drama. However, when I attempted to delete the files I was transferring earlier I end up with "Unable to trash file. Input/output error"

Renamed folder, and was able to delete the files which were previously causing error. Have now successfully transferred the files across? Highly confused as now I can't recreate the error...

---

### Post by hakermania on 2011-07-26
Please tell me the folder's previous name (before renaming)

---

### Post by Petrovic on 2011-07-26
> **hakermania said:**
> Please tell me the folder's previous name (before renaming)

The folder was called "Season 9" I hit F2, placed 'dd' in front of it and deletion was allowed.

---

### Post by amjjawad on 2011-07-26
> **Petrovic said:**
> Am trying to copy some files from a usb HDD to a usb HDD and seem to be having some problems. I've no idea what's happening (I'm a total n00b when it comes to linux) nor if I can pull up a log from somewhere, but I end up with a page of text with the last line reading "Panic occured. Switching back to text console" and my Caps Lock and Scroll Lock lights on kb flash with a hung machine. This is the first time I've has something like this happen. It's a drive from my mates machine, which is also running 11.04. Have transferred stuff when we were on 10.10 with no drama, so I'm somewhat confused. There are no programs running other than boot default. 

Taa for any assistance.

Ok, it seems to be one or two files that are having the issue. I just sucessfully transferred 6gb to it with no drama. However, when I attempted to delete the files I was transferring earlier I end up with "Unable to trash file. Input/output error"

Renamed folder, and was able to delete the files which were previously causing error. Have now successfully transferred the files across? Highly confused as now I can't recreate the error...

I have got some Panic Messages before but not when I was copying something.
I'm not sure if copying was the REAL issue of that panic? and yes, you have to restart whenever you face the same issue.

Perhaps someone else with better idea could help.

You couldn't produce the same error, right?
Perhaps it's because you were connecting two USB HDD and your machine couldn't handle that for some reason?
USB Power is from your machine. 

How did you install Ubuntu? is this a HDD installation?
This is 11.04 right?

---

