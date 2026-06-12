---
title: "File Redundancy on Ubuntu Server 11.04?"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by morganmoller on 2011-05-11
Hi all, 

I'm quite new to Ubuntu, and Linux in general, but the latest releases have really made an impression on me I'm willing to convert. 

I have a simple home server used for file backup and printing duties that runs on Windows Home Server. 

However, the upcoming release of this requires a dual-core pc, and frankly, i'm not willing to upgrade my pc for it's simple use as a file server. 

On WHS i have folders (Documents/Music/Photos/Videos/...) that contain the respective files. WHS organises an automatic file redundancy over the 3 HD's that my pc contains (250 ATA BOOT/500 GB SATA DATA/ 1 TB SATA DATA) so that in the event of a crash, there is always a backup copy. 

Is this possible on Ubuntu Server 11.04? I'd be willing to install it as the main server OS and install some GUI over it since i'm fairly new to Ubuntu/Linux. 

I hope you can help me!

Cheers

---

### Post by seawolf167 on 2011-05-11
There are tons of ways to backup your data automatically. The easiest to setup and use (IMO) for file redundancy is *rsync*

A sample command

```
rsync -ruv --delete /source /destination
```

copies the directory tree and all files from /source to /destination, ensuring that there are no extraneous files in /destination that differ from /source

Of course this is only one sample usage, see

```
man rsync
```

for more options.

As usual, you can add this line to your *crontab* directory to run at specified intervals, or create your own bash script which you have run from *crontab*.

---

