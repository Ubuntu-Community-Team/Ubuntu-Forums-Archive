---
title: "[SOLVED] md5"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by gridd on 2008-12-21
hi I'm having problems checking md5 for ubuntu  8.10 alternative.Using ubunto 8.04 desktop the hash f9e0494e91abb2de4929ef6e957f7753 doesn't seem to match
anything when I open md5sum.txt.

---

### Post by jamesrl on 2008-12-21
When you run md5sum -c on an md5sum.txt file it automatically checks everything.  If something is bad, you had a bad download (e.g., it got corrupted while downloading) .

---

### Post by jamesrl on 2008-12-21
Never mind.  A quick web search of the md5sum seems to indicate that the proper md5 sum works on the entire iso:
f9e0494e91abb2de4929ef6e957f7753 *ubuntu-8.10-alternate-i386.iso

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by gridd on 2008-12-21
> **jamesrl said:**
> When you run md5sum -c on an md5sum.txt file it automatically checks everything.  If something is bad, you had a bad download (e.g., it got corrupted while downloading) .

hi how do I run  md5sum -c do i copy and paste md5sum.txt into a terminal?

---

### Post by gridd on 2008-12-21
> **jamesrl said:**
> Never mind.  A quick web search of the md5sum seems to indicate that the proper md5 sum works on the entire iso:
f9e0494e91abb2de4929ef6e957f7753 *ubuntu-8.10-alternate-i386.iso

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

hi yes that is where i obtained that hash but it doesnt match anything in the iso md5 file when i open it using 'alt f'

cd download_directory
bash: cd: download_directory: No such file or directory.

I have the iso on my desktop do I have to burn it to a cd before i can go any further,

---

### Post by Partyboi2 on 2008-12-21
> **gridd said:**
> hi yes that is where i obtained that hash but it doesnt match anything in the iso md5 file when i open it using 'alt f'

cd download_directory
bash: cd: download_directory: No such file or directory.

I have the iso on my desktop do I have to burn it to a cd before i can go any further,
try
```
cd ~/Desktop
```then
```
md5sum ubuntu-8.10-alternate*
``` then make sure it matches to the correct hash.
If it does not you will need to download it again unless you used a torrent in which case you should be able to point the torrent program to the downloaded file and it should recheck it and download any missing parts.
Once the md5sum matches then you can proceed to burn it to disk at x4 or less speed.

---

### Post by ugm6hr on 2008-12-21
> **Partyboi2 said:**
> unless you used a torrent in which case you should be able to point the torrent program to the downloaded file and it should recheck it and download any missing parts.

Even if you didn't use torrent, if the md5 doesn't match, I'd suggest getting a torrent engine to check and fix the download.  It will save having to download the entire file again.

---

### Post by gridd on 2008-12-21
> **Partyboi2 said:**
> try
```
cd ~/Desktop
```then
```
md5sum ubuntu-8.10-alternate*
``` then make sure it matches to the correct hash.
If it does not you will need to download it again unless you used a torrent in which case you should be able to point the torrent program to the downloaded file and it should recheck it and download any missing parts.
Once the md5sum matches then you can proceed to burn it to disk at x4 or less speed.
 Thanks for your help and very fast responses I am trying to do this but got this :~$ cd~/Desktop
bash: cd~/Desktop: No such file or directory.

 I did use a torrent but don't know how to 'point'.my torrent program,I'me using Bit Torrent.

ive downloaded the file again

---

### Post by The Cog on 2008-12-21
There should be a space after 'cd'.
```
cd ~/Desktop
```
cd is the command to Change Dorectory
~ is a short-form for your home directory

---

### Post by ugm6hr on 2008-12-21
> **gridd said:**
> ive downloaded the file again

When you download it again (with any torrent engine), just select the same directory (i.e. ~/Desktop), and it will check the file and redownload necessary bits for you.

---

### Post by gridd on 2008-12-21
> **The Cog said:**
> There should be a space after 'cd'.
```
cd ~/Desktop
```
cd is the command to Change Dorectory
~ is a short-form for your home directory

yea :~/Desktop$ md5sum ubuntu-8.10-alternate*
f9e0494e91abb2de4929ef6e957f7753  ubuntu-8.10-alternate-i386.iso

I think that is correct. Who would have thought a tiny gap would make so much difference. Unless its between your ears mind.Thanks to all for your help.

---

