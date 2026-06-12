---
title: "wireless network card"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by rock4christ on 2007-04-10
im looking for a wireless network card that will work on [this]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=c00191338")

---

### Post by rock4christ on 2007-04-10
sorry for the double post, but does [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127145") look like a good one?


and, to avoid multiple threads, ill just throw this question in:

is there an easy way to put files on the pc on one partition(win 98 ) and load it in Xubuntu? because I dont really want to put my music on twice if i dont have to. its a waste of space.

---

### Post by darkwill on 2007-04-10
I'm currently having wireless problems myself so I can't really help you there ( from my experience, I would recommend staying away from Belkin wireless products unless you want to go through a LOT of configuration), but on your other question.
YES! (X)Ubuntu natively reads fat32 partitions.
You'll have to create a separate partition for Xubuntu during the installation process, and I would suggest creating a separate fat32 partition for any and all personal files keeping them separated from the Linux installation (Just in case anything ever goes wrong... which is rare, but it could happen... theoretically)

Will

---

### Post by rock4christ on 2007-04-11
an additional FAT32 on top of the one for windows? would it be easy to store the files in this partition from my windows 98 os,instead of linux, because im so used to the pc file browsing?
both win98 and xub should have no problem getting to the 3rd partition and reading it right?

---

### Post by jakev383 on 2007-04-11
Ubuntu will be able to read your win partitions. It works better with FAT16/32 partitions, but it can read/write to NTFS as well. I think it doesn't write to them by default.
As far as wireless goes, pick a card and then search the forums to see if you can see any postings about that particular card. The Linksys USB adapters have worked for me in the past, Intel 2100/2200 worked for me, Intel 3945 did NOT, Broadcom is what I'm running now via ndiswrapper.

---

### Post by SactoBob on 2007-04-11
For the most hassle-free wireless, check this thread
[http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871)

A bridge will work with any computer that has a standard ethernet port, and give you multiple lines and the best performance IMO.

---

