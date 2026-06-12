---
title: "HELP! Can't read or write to external FAT drive in 10.04"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by mistaphi on 2010-09-10
[FONT="Arial Black"][COLOR="Red"][SIZE="7"]I'M TEARING MY HAIR OUT![/SIZE][/COLOR][/FONT]

I have an external drive, a 320 GB Western Digital My Passport, that I'd like to use under Lucid. But as a regular user, I am unable to write to the drive because it mounts as read-only. After countless frustrating hours of googling and trial-and-error (no trial-and-success, unfortunately), I still cannot fix the problem. This is a summary of my most recent attempt to remedy the situation:

**1.** I created a folder called 'myp' in /media.
```
sudo mkdir /media/myp
```

**2.** I gave myself ownership of, and proper permissions to, that folder.
```
sudo chown -R mistaphi:mistaphi /media/myp
sudo chmod -R 777 /media/myp
```

**3.** I added the following line to /etc/fstab after determining the UUID of the drive:
```
UUID=9E38-835E /media/myp vfat rw,users,owner,noauto,sync 0 0
```

**4.** I refreshed (or whatever you'd call it) the fstab.
```
sudo mount -a
```

**5.** I mounted the drive by clicking on its name in the sidebar of the nautilus browser.

But even after doing this, I can't add any new files to the disk, or delete existing files from it. I tried the chmod and chown commands from step 2 again AFTER mounting the disk (even with a manual [FONT="Courier New"]mount /media/myp[/FONT], but the terminal threw 'Read-only file system' errors at me. ](*,)


How can I mount it with read-write permissions? :?

---

### Post by sharathcshekhar on 2010-09-10
Some disks come with write protection. You ll probably have to check that with yours. Are you able to write to it in Windows, with out using any software provided by that manufacturer?

---

### Post by coffeecat on 2010-09-10
This is your problem:

> **mistaphi said:**
> Western Digital My Passport

They're causing all sorts of grief on the Mac forums as well. It seems they have firmware which presents a small flash drive as a separate partition. The flash drive has what's called ['Smartware']("http://www.wdc.com/en/products/wdsmartware/") (sic) on it. The Smartware is, of course, Windows software, but this odd partition seems to hide the main drive from OSs other than Windows. Or something like that.

Normally, if you plug a FAT-formatted drive in Ubuntu it simply gets automounted. You don't have to jump through all those hoops that you've been trying. I'm sorry I don't have an immediate answer, but I'll do a search and post back if I find anything. Perhaps someone has found an answer for the Linux community. WD have produced a firmware update for MacOS users, but I doubt they would do the same for Linux users.

Actually I do have an answer. Buy a generic USB enclosure, take the WD HD out and put it in the generic enclosure. Then take a large lump hammer and flatten the WD enclosure.

---

### Post by mistaphi on 2010-09-10
> Some disks come with write protection. You ll probably have to check that with yours. Are you able to write to it in Windows, with out using any software provided by that manufacturer? *- sharathcshekhar*

Here's the weird thing: I was able to write to it just fine when I was running 9.10. It was only after upgrading to 10.04 (not through the updater but by a drive reformat and fresh install) that I began having this issue. So I don't think write protection is the issue.

> Actually I do have an answer. Buy a generic USB enclosure, take the WD HD out and put it in the generic enclosure. Then take a large lump hammer and flatten the WD enclosure. *- coffeecat*

Great idea. In fact, if I didn't have 7 months of un-backed up pictures, my entire music library, and seasons 1 and 2 of Mad Men on it, I'd probably just hammer the drive itself in utter frustration! My problem is that I live in Uganda, an extremely poor, landlocked country in East Africa. There is very little market for things like USB enclosures, so it's probably next to impossible to find one here. But good to know in case I find one, thanks.

The fact that I was able to write to the drive when I was running Karmic gives me some hope. So please give me more suggestions, people!

---

### Post by coffeecat on 2010-09-10
> **mistaphi said:**
> There is very little market for things like USB enclosures, so it's probably next to impossible to find one here. But good to know in case I find one, thanks.

If you do come across one, there's one thing to beware of. There are two type of hard drive connectors. The newer serial 'SATA', and the older parallel, sometimes called 'PATA', but more correctly 'IDE'. Clearly, you'd need the correct one. They're easily distinguished visually - the older PATA has a wide connector with 40 pins, the SATA a narrower connector.

Re-reading your first post, I see that you can mount the drive read-only which suggests the problem is not the one I described. But it does seem to be a WD firmware issue. Perhaps there's something that interferes with the later version USB drivers in Lucid. I haven't found anything else useful but I'll post back if I do.

---

### Post by jtarin on 2010-09-10
Nevermind...I left my glasses at coffecats awhile ago.

---

### Post by jtarin on 2010-09-10
Sounds like a dumb question but, right click on the drive in question and see if write is on or off.

or run the command on the drive ```
lsattr
```Might not be available for ext4

---

### Post by cjv8888 on 2010-09-10
I have exactly the same drive ie WD My Passport 320G and it mounts automatically in Lucid. Do other external drives and flash drives mount automatically in the computer?
Have you tried using a live CD to mount the drive?  If you can mount it with a live CD, then backup all your files and try deleting all the partitions there using Gparted and format it again.

---

### Post by -kg- on 2010-09-10
If none of the other above suggestions work for you, you might want to [check this out]("http://nixliving.blogspot.com/2010/01/enjoy-your-wd-my-book-1tb-drive-no-more.html") as a possible solution.

---

### Post by mistaphi on 2010-10-14
I tried cjv8888's suggestion: backup the whole drive, reformat, and put everything back on. Problem solved! Thanks for the help, everyone. I've marked this post as solved.

---

