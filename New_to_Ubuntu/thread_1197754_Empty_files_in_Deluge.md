---
title: "Empty files in Deluge"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by bubbhasdance on 2009-06-26
Been using 9.04 for a couple of weeks now, like it so far. The only problem is that while using Deluge, I check off what songs I do not want to download, and this works fine, but my destination folder has every song that was unchecked as well, only empty mp3's or very small ones (6.8 KiB, etc.) and the songs that I checked are DL'ed in full.

Is there any way I can get Deluge to stop attempting to download the songs I uncheck?

---

### Post by lovinglinux on 2009-06-26
When someone creates a torrent for multiple files, like a music CD, the torrent client breaks down the original files into several small pieces of the exact same size to facilitate the transfer. Sometimes the last piece of a music file is not large enough so it takes a portion of the next music file. So, Deluge allows you to select which files you want, but eventually it will have to download the first piece of the next file to complete the one you are downloading.

There is no way to avoid this, no matter which OS or torrent client you use.

---

### Post by bubbhasdance on 2009-06-26
But using Win Vista, I never had this problem, the only files there were the ones I chose, there were no empty or fragmented files...but I guess I'll have to live with it. :(

---

### Post by lovinglinux on 2009-06-26
> **bubbhasdance said:**
> But using Win Vista, I never had this problem, the only files there were the ones I chose, there were no empty or fragmented files...but I guess I'll have to live with it. :(

I guess it was just coincidence.  :)

Anyways, you won't loose disk space because of this, because only the first piece and/or the last piece of files you didn't selected are eventually downloaded. I guess you can also delete the files you don't want after completing the download.

---

