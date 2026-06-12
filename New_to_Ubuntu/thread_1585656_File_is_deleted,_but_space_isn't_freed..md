---
title: "File is deleted, but space isn't freed."
date: 2010-09-30
forum: New to Ubuntu
---

### Post by labrat256 on 2010-09-30
Hello

I'm having a problem whereby I delete a film from the root directory of an SD card; the file is over a GiB in size. I then try to paste another film in it's place (about 350 MiB) and get a 'not enough free space' error. After checking that the wastebasket is empty and unmounting and remounting the SD card, I notice that it still says that the space remaining on the card is no different. I'm using Ubuntu 9.10 and if it at all matters, its a FAT formatted non-SDHC card being used in my built in card reader on a Toshiba Equium laptop.

I've searched for the file, gone into the terminal and looked at the directory, used "du -s -m *" to see the disk usage. "du -s -m" returns the number 400, but the individual files and folders when using "du -s -m *" sum only to about 250, and the original film isn't one of the listed files. 

So I've come to one conclusion, that the file is actually deleted, but nautilus for some reason hasn't noticed it isn't there, and hence thinks the space isn't free. Is there anyway to force nautilus to rescan a directory at all to actually check the files and folders therein? 

This isn't the first time I've had this problem. The last time, it was solved by plugging the offending medium into a windows machine and doing it that way, but its not possible now.


labrat256

---

### Post by Paqman on 2010-09-30
Linux is a bit funny in that it doesn't have one central trash bin. It puts one on every single device. So when you delete a file on an SD card, it doesn't go into the system trash, it goes into a trash folder on the SD card.

You can see this folder by hitting Ctrl-H to show hidden folders on your SD card. You can then navigate inside and delete your file again, this time for good. Alternatively, use Shift-Del to delete things on your SD card, and they won't be sent to the trash at all.

---

### Post by labrat256 on 2010-09-30
I have hidden files shown by default, and the trash on the SD card is definitely empty...

---

### Post by indaymadel on 2010-09-30
> **labrat256 said:**
> I have hidden files shown by default, and the trash on the SD card is definitely empty...

Unmount then mount your SD card again. It should update.

---

### Post by renkinjutsu on 2010-09-30
Not to mention he's already checked his directory with `du`

Have you tried copying the file over using the terminal?

---

### Post by labrat256 on 2010-09-30
That didn't work. I thought it did, but I accidentally copied it to the wrong place. "No space left on drive."

---

### Post by Daniel0108 on 2010-10-01
Eject the SD-Card restart your computer, then put the SD-Card in again, look if the trash of the SD-Card is empty(if not, make it empty). That should fix the problem :)
Yours,
Daniel

---

### Post by labrat256 on 2010-10-02
I'd already done that, with no effect...

---

### Post by ddonohu2 on 2010-10-02
I often see a similar problem when I clone drives. The solution in my case is to open Gparted and use the Partition>Check option to fix it. I don't know if that'll work here but it's the only thing I can think of.

---

### Post by abohsin on 2010-10-02
Better to try du with command line, browse to directory, run 'du -sh .*', step-by-step follow where the 1GB size is. I guess the file has to exist somewhere, right?

---

### Post by drs305 on 2010-10-02
Have you looked for a folder called .Trash-1000, which is often created for non-linux filesystems?

You can also do a search for any trash folder on the card:
```
sudo find /<path to SD card> -type d -iname *trash*
```

---

