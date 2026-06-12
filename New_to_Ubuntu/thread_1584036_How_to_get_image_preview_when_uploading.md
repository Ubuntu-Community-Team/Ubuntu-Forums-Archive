---
title: "How to get image preview when uploading"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by zer010 on 2010-09-28
I was wondering if there is a way to get a preview of a selected image while in the file select window for uploads. If I remember correctly, 9.04 had this feature an the right side of the select window.

---

### Post by zer010 on 2010-09-28
A little off topic, but the thread editing options such as "Bold", "Italics", etc do not seem to be working...

---

### Post by zer010 on 2010-09-29
I suppose this feature was left out?

---

### Post by mcduck on 2010-09-29
Sorry, but no. It's not possible, and it wasn't left out at any point.

The thing is that Gnome provides a file selection dialog, used by most programs, which is able to show image preview or hide it, depending on what the application wants. And most applications choose not to enable the image preview. Usually because the application handles other file types than just images as well, and showing the preview when browsing non-image files wastes a lot of space and looks pretty stupid.

If yo check out the file open dialog in any strictly image-oriented application, like Gimp or gThumb, you'll notice they use exactly the same dialog but with the image preview enabled.

So, if I'm correct assuming it's Firefox that you are using to upload you images, it would be up to Firefox developers to start using the preview in the dialog.

(of course it *would* be nice if the dialog was be able to detect when it's only browsing for files that can be previewed, and would then automatically enable/disable the preview.)

---

### Post by zer010 on 2010-09-30
Thanks, so very much for clearing that up for me! I give you a thumbs up! Unfortunately, ubuntuforums doesn't have that emoticon... So here's a star instead!  :KS

---

