---
title: "Nautilus using lots of memory"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by zorblek on 2010-06-18
Ever since upgrading from Karmic to Lucid, Nautilus is using a lot of memory. I've got only got a gig of RAM, but Nautilus is always taking up at least 10%, even if there are no Nautilus windows open, and often it's a lot more. If I kill the process it just comes back, using just as much memory (if not more). I don't recall it doing this before I upgraded. Is this normal?

---

### Post by Beta Tester on 2010-06-18
I haven't noticed much problems on my system. Nautilius uses 5mb of ram for me. How much exactly for you. Is this after using it a while, or from a clean boot?

Have you tried changing priority?

---

### Post by zorblek on 2010-06-18
It's currently using 204M (I think the 10% figure includes the additional gig of virtual memory). And this is from a clean boot.

I don't think anything's been done to the priority, so it should be whatever the default is. I'm not sure how to check.

---

### Post by vallvi on 2010-06-19
What's the size of your swap file? Have you tried increasing or decreasing it? The issue might be there.

---

### Post by zorblek on 2010-06-21
I have 1076M of total swap; it's actually in a couple of files if that matters (I added some a while before I upgraded). I don't recall what the individual file sizes are and I'm not sure how to check.

---

### Post by Linuxforall on 2010-06-21
Ideally swap should be at double the size of your installed ram and in one single file.

---

### Post by zorblek on 2010-06-21
Ideally, yes. This laptop has a small hard drive, so I haven't increased the swap further.

Would the amount of swap affect the amount of RAM Nautilus uses, or does it just matter because of the total amount of memory available?

---

### Post by wilee-nilee on 2010-06-21
204 ram is standard your worrying about nothing, relax and use the computer. Here is my system monitor with FF open on the UF.
[ATTACH]161067[/ATTACH]

---

### Post by Thelasko on 2010-06-21
Hi everybody!  I've been using Ubuntu for quite a while now, and am having the same issue.  Nautilus is using about 180 MB of RAM on my machine.  This was not normal for other releases of Ubuntu, and I doubt the amount of swap has anything to do with this.

On Hardy, I would have a typical system-wide RAM usage of ~800MB.  I am currently using ~1 GB.  My #1 user of RAM is Nautilus.  This cannot be normal.

---

### Post by Thelasko on 2010-06-21
Zorblek:  Have you tried to access any Samba shares in Nautilus recently?

---

### Post by zorblek on 2010-06-22
> **Thelasko said:**
> Zorblek:  Have you tried to access any Samba shares in Nautilus recently?

No, but I did use it to access an SFTP server.

---

### Post by Thelasko on 2010-06-22
> **zorblek said:**
> No, but I did use it to access an SFTP server.

I don't know if that would do it.  I've heard about a bug where Nautilus gets caught in a loop when it tries to access Samba.  You would also see high CPU usage.

---

### Post by zorblek on 2010-06-22
Huh, I will try deleting the bookmark to that server and see if that has any effect. Nautilus does occasionally use a lot of CPU, but not very frequently.

---

### Post by lkjoel on 2010-06-22
Click on LinuxEssentials in my sig.
Extract it, then type in a Terminal window (Applications->Accessories->Terminal)
```
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```That will restart nautilus.
Do that everytime nautilus takes a lot of RAM.

---

### Post by Thelasko on 2010-06-22
> **lkjoel said:**
> Click on LinuxEssentials in my sig.
Extract it, then type in a Terminal window (Applications->Accessories->Terminal)
```
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```That will restart nautilus.
Do that everytime nautilus takes a lot of RAM.

That would be all of the time.

---

### Post by zorblek on 2010-06-23
> **lkjoel said:**
> Click on LinuxEssentials in my sig.
Extract it, then type in a Terminal window (Applications->Accessories->Terminal)
```
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```That will restart nautilus.
Do that everytime nautilus takes a lot of RAM.

Unfortunately that just opened a Nautilus window and made one of my panels disappear. I didn't see a change in memory usage.

I forgot to mention that when I kill Nautilus, when it initially comes back it uses a lot less ram, but it uses 90% CPU until its memory usage increases to around 10% again (then the CPU use drops off).

---

### Post by lkjoel on 2010-06-28
> **zorblek said:**
> Unfortunately that just opened a Nautilus window and made one of my panels disappear. I didn't see a change in memory usage.

I forgot to mention that when I kill Nautilus, when it initially comes back it uses a lot less ram, but it uses 90% CPU until its memory usage increases to around 10% again (then the CPU use drops off).

Don't worry about the Nautilus window popping up, just close it.
If a panel disappears, run it again, or type
```
./gnome-panel.sh
```
If you see any other problems, check in my sig for the bug links.

---

### Post by zorblek on 2010-06-28
I was able to deal with the panel issue, but unfortunately it didn't have an effect on memory use.

---

### Post by lkjoel on 2010-06-29
Are you using Gnome?

Check in System Monitor (System->Administration->System Monitor) for the highest (or pretty close to the highest) process.
If it is something like "polkitd", you can kill it.
The process will restart.

---

### Post by evyavan on 2010-09-01
Am using a Dell machine with Lucid LTS installed and now suffering from Nautilus as its taking too much memory. I have 2GB of RAM and 3GB of SWAP. But when I try to open a folder with more than a 1000 files [pictures and sub-folders] Nautilus takes around 1 minute to fully load the files and am left to sit looking at the monitor. When I checked with System Monitor, I saw Nautilus is using around **95% of the RAM** and about a **half of my SWAP** space is used! Any tips to get rid of this problem?

---

### Post by lkjoel on 2010-09-01
> **evyavan said:**
> Am using a Dell machine with Lucid LTS installed and now suffering from Nautilus as its taking too much memory. I have 2GB of RAM and 3GB of SWAP. But when I try to open a folder with more than a 1000 files [pictures and sub-folders] Nautilus takes around 1 minute to fully load the files and am left to sit looking at the monitor. When I checked with System Monitor, I saw Nautilus is using around **95% of the RAM** and about a **half of my SWAP** space is used! Any tips to get rid of this problem?
[http://ubuntuforums.org/showpost.php?p=9498130&postcount=14](http://ubuntuforums.org/showpost.php?p=9498130&postcount=14)

---

### Post by sj005 on 2010-09-26
Hey If you are running a certain program like clam antivirus, then that could be causing the problem. I have 2 gb of ram and before i installed clam, my system never used to exceed 500 mb of ram usage, even with multiple programs running. However, after my first scan with Clam AV, the usage just increased way up to 900 mb during the scan and about 650 after the scan finished. Nautilus was using up a massive amount. So, i decided to remove clam and so i went to the software center and removed virus scanner but still i realized that nautilus was using 200 mb of ram. thats not at all usual. I finally went to the synaptic package manager and searched for "clam" and found that there was still some applications related to clam installed . I removed all software associated with clam and when i restarted my computer, my system ram usage was at 350mb and nautilus at only 7 mb. So you should check for problems like this.

---

### Post by Thelasko on 2010-09-26
> **sj005 said:**
> Hey If you are running a certain program like clam antivirus, then that could be causing the problem. I have 2 gb of ram and before i installed clam, my system never used to exceed 500 mb of ram usage, even with multiple programs running. However, after my first scan with Clam AV, the usage just increased way up to 900 mb during the scan and about 650 after the scan finished. Nautilus was using up a massive amount. So, i decided to remove clam and so i went to the software center and removed virus scanner but still i realized that nautilus was using 200 mb of ram. thats not at all usual. I finally went to the synaptic package manager and searched for "clam" and found that there was still some applications related to clam installed . I removed all software associated with clam and when i restarted my computer, my system ram usage was at 350mb and nautilus at only 7 mb. So you should check for problems like this.
Interesting...

---

### Post by zorblek on 2010-09-26
I'm not using ClamAV or anything like that. The only thing I can think of that might have something to do with it is Dropbox, but I had problems even when I disabled it.

---

### Post by CyRaid on 2010-10-06
@zorblek: Just to check, look in your synaptic package manager for "nautilus-clamscan" package and see if it's installed.. Also, you might want to check to see if "nautilus-dropbox" is installed as well.  If so, remove it and see if it's the cause of the major RAM increase.  And you would need to clear out some dropbox cache (it's located in $HOME/.dropbox/cache) so remove the folders/files in there (but leave the cache folder intact)

---

### Post by zorblek on 2010-10-24
I checked, and nautilus-clamscan was not installed. I removed nautilus-dropbox and the cache files as instructed, but I'm still having the same problem, unfortunately.

---

### Post by Eskobar on 2011-01-10
I had this same problem and it was driving me nuts for about 2 weeks...I found the solution to my problem here 

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/669594]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/669594")

After I read that post, I realized that Nautilus started lagging and chewing up RAM, when I was copying files from my external hard drive to my cpu.  I must have interrupted Nautilus while it was copying...and ever since it has been trying to complete that action...even after rebooting and reinstalling Nautilus & removing all add on's. Hopefully these steps will help other "Newbies" like myself!  

1.  SYSTEM >>> ADMINISTRATION >>> SYSTEM MONITOR

2.  Click on "Processes" & right click on "Nautilus", click on "Memory Maps" and click on the column that says "VM Size" (this will sort the column so you can see what specific folder or file is hogging up the memory).  There is nothing else you can do here, but you can leave it open so you can remember the file location!

3.  (OPTIONAL) If your computer is lagging due to Nautilus chewing memory, open a terminal and type in "nautilus -q"...that will quit & restart Nautilus.

4.  Open "Nautilus" and navigate to the folder or file that was chewing up all of the memory and delete it!  

I hope this helps someone out.  After I found the folder that was causing trouble & deleted it....my Ubuntu Studio 10.10 is running FLAWLESSLY!

---

