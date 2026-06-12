---
title: "cannot download FLV."
date: 2010-12-10
forum: New to Ubuntu
---

### Post by mikee55 on 2010-12-10
Hi all, Firefox will not download FLV. I installed different plugins to download some youtube video, the Downloads box opens, lists the video, but sits at 0 bytes. Everything else will download ok. Ive tried One click, Easy you tube downloader, Download Video helper, and get the same thing.

Thanks

Mike

10.04

---

### Post by NikoC on 2010-12-10
Hmmz,

You can always do it 'the old school way'. Open a terminal and go to the tmp folder: cd /tmp

Flash movies are stored there as FlashXXXXXX. Just use the cp command to copy it to your deskop. E.g. let's say the file is called FlashXX5DN:
open terminal
cd /tmp
cp FlashXX5DN ~/Desktop/movie1.flv

This will copy the file to your desktop including the flv extension.

---

### Post by mikee55 on 2010-12-10
Curiously, that didn't work, however, I Copy(ied) the file and saved it im my Video folder and that worked. Is FLV better than MP4?

Cheers

Mike:D

---

### Post by CharlesA on 2010-12-10
Just an FYI: Downloading videos off YouTube that don't have a download link, is breaking YouTube's ToU.

---

