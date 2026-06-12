---
title: "Video thumbnails not working in Jaunty"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by andy_blah on 2009-04-28
I have recently installed the GStreamer codecs to be able to play videos coded into XviD, H.264 and others, and I notice that the thumbnails aren't working, the icon changes so it means that it tries to generate a thumbnail, but after a few seconds, the thumbnail doesn't show up, instead it just displays that video icon. Is there any way to fix this problem?

---

### Post by Tibuda on 2009-04-28
What videos format are those files? Can Totem-gstreamer play those files?

---

### Post by andy_blah on 2009-04-28
XviD in .avi container, and H.264 in .mkv, didn't try other formats/containers. Yes, they play fine in Totem (not sure about Totem-gstreamer tho :?. Is it the same, or it is a standalone player?)

---

### Post by lovinglinux on 2009-04-28
Have you enabled the preview of "Other Previewable Files" in Nautilus "Edit >> Preferences >> Preview"?

They work fine here, including mkv files.

Edit: sorry, I noticed your comment about the icons changing. Maybe you could try deleting the thumbnails folder.

---

### Post by andy_blah on 2009-04-28
I noticed that it was set to preview only files under 10MB, set it to under 1GB now, hopefully this fixes the problem, any way to check this? Also, where is the thumbnail folder?

---

### Post by lovinglinux on 2009-04-28
> **andy_blah said:**
> I noticed that it was set to preview only files under 10MB, set it to under 1GB now, hopefully this fixes the problem, any way to check this? Also, where is the thumbnail folder?

Yep, I forgot to consider the size limit. The thumbs are in ~/.thumbnails

---

### Post by andy_blah on 2009-04-29
It works now, deleted everything under .thumbnails, and the thumbnails in videos show ^_^

Thank you for assistance

---

