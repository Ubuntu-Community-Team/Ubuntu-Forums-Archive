---
title: "[SOLVED] Where are temporary internet files stored in Firefox?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by gackt on 2009-01-06
I'm streaming a song from the Internet and i want to save it to my local harddisk. I can not download the file directly because of file limit restriction from my server, but if i stream the song it will be streamed at the end of the song without bothering the file size limit policy. So after i stream the song to 100% where do i find this file in my ubuntu. Thanks (i'm using firefox 3 anyway)

---

### Post by jerome1232 on 2009-01-06
> **gackt said:**
> I'm streaming a song from the Internet and i want to save it to my local harddisk. I can not download the file directly because of file limit restriction from my server, but if i stream the song it will be streamed at the end of the song without bothering the file size limit policy. So after i stream the song to 100% where do i find this file in my ubuntu. Thanks (i'm using firefox 3 anyway)

Should be in ~/.mozilla/firefox/cache

At least somewhere under ~/.mozilla/firefox

To navigate there using a gui file manager like nautilus just click places->home, hit ctrl+h to view hidden files, click .mozilla, firefox, cache, and search around.

---

### Post by Rhubarb on 2009-01-06
In addition to what jerome1232 had said, another place to look would be in:
```
/tmp
```
I know flash videos are temporarily cached there.

---

### Post by gackt on 2009-01-06
Thanks i found it. Thank you

---

### Post by Dudkarji on 2012-01-26
Hey, mate! well, where did you find the file you were looking for? and as what kind of file has it been saved (because the only thing I can find in firefox's cache is html, text-files and Gzip)? Sincerely, Dudkarji ;)

---

