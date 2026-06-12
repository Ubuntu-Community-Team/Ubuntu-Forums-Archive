---
title: "Help! torrent paused: disk write error"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by norlandbuntu2 on 2009-01-10
I started getting the following error message a few days ago:
torrent paused: disk write error, seek failed: 'Invalid argument'
I am running Ubuntu 8.04 which I upgraded online to 8.10, Deluge on a Dell 240 with dsl.
Can anybody help with this problem?
Thank you.

---

### Post by Guille Damke on 2009-01-10
Hi,

Do you have space in your hard disk?

You can check it doing in a terminal:
```
df -h
```

---

### Post by pmagnin1 on 2009-11-11
Hi!

I had the same problem today with Deluge...

Is it in a FAT32 partition that Deluge want to save files?

If it's the case, FAT32 do not allow files bigger than 4.0 Go...

So if you have a unic file wich is more than 4 Go, you'll have to save it on an ext3 or ntfs partition... and if you can't, just delete it from Deluge and forget to dl it...

That's not the case if you have a torrent with many "little" files... (less than 4 Go each).

If it can help you...

Take care!

P.S: sorry for my english :).

---

### Post by dumblebee100 on 2009-11-11
> **norlandbuntu2 said:**
> I started getting the following error message a few days ago:
torrent paused: disk write error, seek failed: 'Invalid argument'
I am running Ubuntu 8.04 which I upgraded online to 8.10, Deluge on a Dell 240 with dsl.
Can anybody help with this problem?
Thank you.

first of all you may have torrent data which is more than 4 gb ..because fat32 filesystem doesnt support more than 4gb file 
then you may have some bad file fragments which made disk writing impossible ..
solution is to do a fsck after unmounting the device

then you may have problem with bad chunks ....better you check manually I mean hash check the chunks

or may be you dont have sufficient space left on the partition to write more data on it

---

### Post by shaunak1111 on 2010-06-02
i am running a dual boot vista and ubuntu 10.04 lucid lynx, whatever torrent client i run it gives me a disk write error if i try to store the file on the windows ntfs partition. i have 250 gb free space & i guess disk space is not the issue.plzzzz help

---

