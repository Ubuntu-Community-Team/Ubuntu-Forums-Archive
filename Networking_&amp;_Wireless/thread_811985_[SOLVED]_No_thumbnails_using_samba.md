---
title: "[SOLVED] No thumbnails using samba"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by eidauk on 2008-05-29
I access my Windows server with Hardy using Nautilus and Samba. However, I can never get thumbnails for image files on the server to display on my laptop. This makes it difficult to see which JPG I'm selecting since I only see a default icon and the file name. Thumbnails display perfectly when accessing image files on my laptop.

This has always been the case since I switched to Linux (Ubuntu) two years ago. Is this a limitation of Samba or can I fix this?

---

### Post by Zimmer on 2008-05-29
Have you checked your preferences in Nautilus? Are they set to thumbnails for Local Files only?

---

### Post by eidauk on 2008-05-29
That worked! That was simple. I'm not sure I understand why that isn't the default to see thumbnails for remote files. Thanks.

---

### Post by Zimmer on 2008-05-29
You may like to know that a program called GQview has a clever facility for deleting old cached thumbnails. I loaded it for that specific purpose, since old thumbnails can take up a fair bit of disk space...

---

