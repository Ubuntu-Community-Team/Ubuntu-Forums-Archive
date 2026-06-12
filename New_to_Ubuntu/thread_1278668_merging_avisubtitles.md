---
title: "merging avi/subtitles"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by mirado on 2009-09-29
This thread won't be as stupid as my last one.... I think
I'm trying to merge the the srt and the avi while using this command-line

mencoder -oac copy -ovc raw -sub video.srt -sub-bg-alpha 220 -utf8 -o  video.avi video1.avi 

I have all of the software I need, but terminal is telling me:
File not found: 'video1.avi'
Failed to open video1.avi.
Cannot open file/device.

and ending the command

I was under the assumption that video1.avi would be my output file
I was wrong

---

### Post by styrofoam cup on 2009-09-30
if its any help DeVeDe can do it without the command line.

---

### Post by MrWES on 2009-09-30
> **mirado said:**
> This thread won't be as stupid as my last one.... I think
I'm trying to merge the the srt and the avi while using this command-line

mencoder -oac copy -ovc raw -sub video.srt -sub-bg-alpha 220 -utf8 -o  video.avi video1.avi 

I have all of the software I need, but terminal is telling me:
File not found: 'video1.avi'
Failed to open video1.avi.
Cannot open file/device.

and ending the command

I was under the assumption that video1.avi would be my output file
I was wrong

first, try this code for adding a subtitle:
```
mencoder movie.avi -sub movie.srt -subfont-autoscale 1 -o movie.hardsubs.avi -oac copy -ovc lavc -lavcopts vbitrate=1800

```

Secondly, I normally like to recommend native linux apps, but I have to admit AVIAddXSubs works very well under Wine. The biggest advantage is you don't have to remux the video to add the sub. You can download it here: [http://www.calcitapp.com/AVIAddXSubs.php]("http://www.calcitapp.com/AVIAddXSubs.php")

If you want a native GUI app, Avidemux will also add subs to the avi file, but again, you have to remux the video and that takes alot longer than the 3 minutes AVIAddXSubs takes under Wine.

~Bill

---

### Post by mirado on 2009-09-30
It previews with subtitles but there are no subtitles when the preview file was opened AFTER I close devede
Good software, though
Thanks

---

### Post by mirado on 2009-09-30
Becoming very frustrating
I think I'll just have to retrograde to MSDOS for this one

---

### Post by styrofoam cup on 2009-10-03
when I burnt a dvd with the subs, I had to press the subs button on the remote to get them to display. Kind of not what you asked but it might help.

---

