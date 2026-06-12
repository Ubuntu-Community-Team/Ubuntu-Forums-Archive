---
title: "Recover files after &quot;sudo rm&quot;"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by josiano on 2009-01-10
Hello all.
I am terribly confused...
I typed too fast on my girlfriend's computer and forgot a folder name in a rm command and typed:
```
sudo rm /*
```
I know it was very stupid...
Now, the computer won't boot (of course).
*But*, more horrible, I deleted important files that were in her home folder...
Is there a way of recovering those files somehow ?
It would be really cool !
Thanks for your help.
_j
ps: her os was Ubuntu 7.10

---

### Post by perlluver on 2009-01-10
You can try some recovery software like [http://www.data-recovery-software.net/Linux_Recovery.shtml](http://www.data-recovery-software.net/Linux_Recovery.shtml), however when you sudo rm your root directory plus a * that pretty much deletes everything that was there.

---

### Post by josiano on 2009-01-10
Thanks for the advice... I will give it a try tomorrow, I made enough stoopid things for today...

Cheers,

_j

---

### Post by BGFG on 2009-01-10
not really familiar with linux recovery tools, but if you have a windows machine that you can slap that drive into, Recuva by piriform is pretty good.

---

### Post by theinnercityhippy on 2009-01-10
When you remove a file from a computer, it is not removed in the strictest sense, it is simply made available to be oerwritten by the computer.

O'Reilly publish an excellent book called Knoppix Hacks which details the procedures you can take to recover deleted data using knoppix.

The most important thing is that you don't try to mount the drive AT ALL. This could mean that you will inadvertantly save over the inodes that you wish to recover.

The best way to recover a drive is to make an exact copy of it to a new drive or other media such as a DVD if it is a small enough hard drive. Working on this new media will avoid any further changes being made to the original.

Once this is done, you can then mount the backup within knoppix and search for the correct inods to recover.

Doing this yourself would involve quite a lenghty explanation here so like I say, I would suggest getting hold of a copy of the above book, which comes with a live disk with all the reuired utilities, and following the steps they outline.

I will reiterate though that it is extremely important that you don't try to mount, or worse save anything to, the drive in question until you are ready to begin the recovery.

Good luck,

-JimDog-

---

### Post by jflaker on 2009-01-10
> **josiano said:**
> Hello all.
I am terribly confused...
I typed too fast on my girlfriend's computer and forgot a folder name in a rm command and typed:
```
sudo rm /*
```
I know it was very stupid...
Now, the computer won't boot (of course).
*But*, more horrible, I deleted important files that were in her home folder...
Is there a way of recovering those files somehow ?
It would be really cool !
Thanks for your help.
_j
ps: her os was Ubuntu 7.10

K
Boot from the LiveCD and copy off files from your /home/UserID directory.  Don't forget the hidden files for such as .evolution et al

Once you are satisfied that you have all your important things, do a reinstall and tell the installer to use the whole disk and you should be good to go.

Once reinstalled, copy back your data.

Sorry, that is the best way to make sure you are completely operational instead of trying to guess what was deleted.

---

### Post by handydan918 on 2009-01-10
> **jflaker said:**
> K
Boot from the LiveCD and copy off files from your /home/UserID directory.  Don't forget the hidden files for such as .evolution et al

Once you are satisfied that you have all your important things, do a reinstall and tell the installer to use the whole disk and you should be good to go.

Once reinstalled, copy back your data.

Sorry, that is the best way to make sure you are completely operational instead of trying to guess what was deleted.

You must have missed the part about rm /*

All of those files have been dereferenced.

---

### Post by josiano on 2009-01-11
Hi and thanks for your advices.
The OReilly book is really interesting.
But I came to some weird results that I cant explain...
I followed the recovery of deleted files with the use of **fls** and **icat**.
Now, I have a new partition on a new drive with those deleted files and directories.
If I select all the files (hidden ones included), the total size is 1Mo (!?).
If I look at the same partition properties (right-click on partition name), it says that the partition uses 4Go of datas ???
I guess that some of the files were recovered but I don't seem to be able to see/read them...
Any help is much appreciated.
Thanks again.
_j

---

### Post by josiano on 2009-01-15
Hello.

For the sake of the archives:
I couldn't recover anything except some image files.
I tried with Knoppix tools and with R-Linux (windows) with no luck.

The only good thing is that I learnt a lot from this.
While looking for some solutions, I found this interesting article that explains why one *can't* recover deleted Ext3 files:

[http://linux.sys-con.com/node/117909](http://linux.sys-con.com/node/117909)

Anyway, thanks for the help everyone !

_j

---

