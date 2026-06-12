---
title: "Large file transfer over an unreliable network?"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by chrestomanci on 2008-11-10
Can anyone suggest a network file-system or method of file transfer that will work with large files over a WiFi network that occasional drops out?

I have a dual boot laptop (XP & Intrepid) on which I regularly generate large multimedia files of around 2-3 Gb in size. I need to transfer these files to my more powerful Ubuntu desktop machine for further processing. I would like to transfer the files over my WiFi network, but the network occasionally drops out for a minute or so due to interference. 

All the file transfer methods I have tried abort the connection and don't resume if the network is lost for more than a short time. As each file takes an hour or more to move, the chances of successfully transfering the whole file is low.

I have tried both smb, and ssh from both linux and windows. I have also tried filezilla under windows but it has a bug that prevents it resuming if more than 2Gb has been transfered. Even sneakernet with a USB stick does not work well, as FAT formated USB keys don't support files bigger than 2Gb. Can anyone suggest something better?

Currently my only solution is to move the laptop and connect it to a wired network, but that is more trouble than I prefer.

---

### Post by kidders on 2008-11-11
Hi there,

I have a few (not necessarily very good) suggestions ...

**Assume failure**
You could assume large file transfers will always fail, and copy your files in lots and lots of little chunks. For example, you could throw together a shell script that copies files a megabyte at a time, keeps retrying each chunk until it succeeds, and puts your file back together again when it's done.

**FTP**
You could install an FTP server on the source machine, and suck your files down from the other side. Again, it ought to be fairly easy to script something that keeps resuming downloads until they're complete.

**USB Stick**
The FAT filesystems are pretty terrible. You could put a JFS/Ext2/etc. filesystem on your USB stick instead. Depending on how much space you have on it, you could perhaps put a small FAT filesystem on it as well, so you can continue to use it on "dumb" devices like printers & Windows boxes.

---

### Post by jonobr on 2008-11-11
Hello,

Would creating a bit torrent help here?

Im thinking though you would need to attack the root of your problem and create more reliable network.

All in all kidders suggestion and mine, I think, would take more time then just doing the hardwire that your doing.

Regrettably I can image that your not going to get any really useful tips here that will make your life easier.

Cheers

BTW, Kidders, greetings from a member of the diaspora stuck against his will in the US. :-) , Slan agus beannacht a chairde!

---

### Post by chrestomanci on 2008-11-14
> **jonobr said:**
> 
Would creating a bit torrent help here?

That is a really good idea, which I am investigating. Vuze (Formally Azureus), has a built in BT server so it should be fairly easy to set-up an ad-hoc torrent to transfer the media files.

> **jonobr said:**
> 
Im thinking though you would need to attack the root of your problem and create more reliable network.
Sadly I don't think that will happen with wireless. I live in a residential area with lots of other WiFi networks, (I can pick up 5 others from my home), there must also be plenty of Microwaves, cordless phones, Baby monitors and other devices on the 2.4 GHz band, so in a way it is surprising that WiFi works at all.

> **kidders said:**
> **Assume failure**
You could assume large file transfers will always fail, and copy your files in lots and lots of little chunks. For example, you could throw together a shell script that copies files a megabyte at a time, keeps retrying each chunk until it succeeds, and puts your file back together again when it's done.

I dare say I could put together a perl script that does that. The thing is, fish (kde ssh transfer) uses perl for file transfer, and that kind of thing feels like I ought to be in KDE. I am thinking I should raise a feature against KDE requesting that fish should have the option to do a lot more retries.

> **kidders said:**
> **USB Stick**
The FAT filesystems are pretty terrible. You could put a JFS/Ext2/etc. filesystem on your USB stick instead. Depending on how much space you have on it, you could perhaps put a small FAT filesystem on it as well, so you can continue to use it on "dumb" devices like printers & Windows boxes.

I tried that, and at least from windows it did not work to well. I formated a 4Gb USB stick with NTFS. The problem was that windows took an absolute age to copy the files onto the stick. It was better than using WiFi at the moment but it was still frustratingly slow.

---

### Post by nixscripter on 2008-11-18
I would suggest rsync. It detects partial transfers, failed transfers, etc. and picks up where it left off.

It was my favorite tool of choice to get backups of a machine which went into a total I/O lock every 10 minutes (a terrible, long story in itself).

```
rsync --progress file1 file2 user@othermachine:/dest/dir
```

The flag will make a nice pretty progress bar (instead of just sitting there ominously).

Hope this helps.

---

### Post by jonobr on 2008-11-18
HI 


I have not used Rsync in a while for something like this, only quick backups, and maybe its different now,
however, I found the way it does the partial transfer it meant that memory and CPU requirements were high.

I did a bit of investigation at the time and found a few good articles matching the problems I found,
Just wondering if those things have changed with Rsync?

Thanks

---

### Post by Cracauer on 2008-11-18
rsync with the -c option.

No question.

---

### Post by chrestomanci on 2008-11-18
I am using bittorrent. It works quite nicely, and using Vuze, it was very easy to setup a server under windows. rsync would probably be harder from windows. I guess if it was linux at both ends rsync might be an option, but seeing as the files are generated under windows it is easer to send them using a windows tool, than to reboot to linux.

---

### Post by jonobr on 2008-11-19
hey 

using rsync on windows is actually not bad.
Once you setup your config file on windows, you can setup a batch script, that you can just double click on your desktop which will do the copy.
If you need info on that just look for cwrsync on the web.Thats the program which will work on windows.
Theres tons of examples 

However, seeing as how the torrent is wokring out for you, Ill count that as a win for jonobr:-)

Cheers

---

