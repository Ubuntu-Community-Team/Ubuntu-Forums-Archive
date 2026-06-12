---
title: "Chromium download stops at 40mb"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-09-16
Yesterday I was downloading a file that was about 200mb. It was a patch for Unreal Tournament 2004. I used one of those file hosting sites (filefront.com). When the download stopped at 40mb EACH and every time I assumed there was something wrong with this particular site.

Then I used another (similar type of download site) to download the same file, and it stopped at 40mb again. At this point I assumed that there was something wrong with the patch.

Today I was trying to download an image file from a friend that was about 100mb from megaupload. Again it stopped at 40mb.

Downloading the SAME files in Firefox 3.5 yields no problems.

Any thoughts? Thanks!

---

### Post by Perfect Storm on 2009-09-16
Well Chromium is still "unstable" released, so there can be some bug.
You could try use the wget command to grab the file.

---

### Post by Paqman on 2009-09-16
Cool, you found a bug!

---

### Post by abhiroopb on 2009-09-16
Thats true, but this has only happened recently (since yesterday) and I thought perhaps it was a known bug.

---

### Post by abhiroopb on 2009-09-16
> **Paqman said:**
> Cool, you found a bug!
errr thanks

---

### Post by Perfect Storm on 2009-09-16
> **abhiroopb said:**
> Thats true, but this has only happened recently (since yesterday) and I thought perhaps it was a known bug.

You can check at the chrom bug tracker; [http://code.google.com/p/chromium/issues/list](http://code.google.com/p/chromium/issues/list)
If your bug isn't list, I suggest you make them aware of the bug you found.

---

### Post by abhiroopb on 2009-09-16
I think I found the appropriate bug:

[http://code.google.com/p/chromium/issues/detail?id=406&q=40mb%20download&colspec=ID%20Stars%20Pri%20Area%20Type%20Status%20Summary%20Modified%20Owner%20Mstone](http://code.google.com/p/chromium/issues/detail?id=406&q=40mb%20download&colspec=ID%20Stars%20Pri%20Area%20Type%20Status%20Summary%20Modified%20Owner%20Mstone)

---

### Post by LewRockwell on 2009-09-16
> **abhiroopb said:**
> I think I found the appropriate bug:

[http://code.google.com/p/chromium/issues/detail?id=406&q=40mb%20download&colspec=ID%20Stars%20Pri%20Area%20Type%20Status%20Summary%20Modified%20Owner%20Mstone](http://code.google.com/p/chromium/issues/detail?id=406&q=40mb%20download&colspec=ID%20Stars%20Pri%20Area%20Type%20Status%20Summary%20Modified%20Owner%20Mstone)

super

.

---

