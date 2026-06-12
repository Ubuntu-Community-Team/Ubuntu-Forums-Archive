---
title: "Joining wmv files"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by m_ad on 2009-12-27
I've done some extensive research on this, and I can't find the best method for joining wmv files. I have four wmv files and I'm trying to join them using any method out there.

I've tried avidemux, and the output file is over 5 hours! (should be around 22 mins).

I've tried mencoder from the command line, and the output is under 22 mins with iffy statistics via mplayer (1000 fps?).

What's the best method?

---

### Post by MrWES on 2009-12-27
> **m_ad said:**
> I've done some extensive research on this, and I can't find the best method for joining wmv files. I have four wmv files and I'm trying to join them using any method out there.

I've tried avidemux, and the output file is over 5 hours! (should be around 22 mins).

I've tried mencoder from the command line, and the output is under 22 mins with iffy statistics via mplayer (1000 fps?).

What's the best method?

try this:

```
cat file1.wmv file2.wmv file3.wmv > joined.wmv
```

Bill

---

### Post by m_ad on 2009-12-27
Should have specified that I tried this method as well - the resulting "joined.wmv" file is only the first file.

---

### Post by Bachstelze on 2009-12-27
You're probably toast. Those must have a VFR or some other quirk, so doing what you want would require some deep knowledge about video encoding.

---

### Post by m_ad on 2009-12-27
Hmm, what is vfr?

---

### Post by MrWES on 2009-12-27
> **m_ad said:**
> Should have specified that I tried this method as well - the resulting "joined.wmv" file is only the first file.


Check out this old thread, might be of some use.

[http://ubuntuforums.org/showthread.php?t=316158]("http://ubuntuforums.org/showthread.php?t=316158")


~Bill

---

### Post by andrew.46 on 2009-12-27
Hi m_ad,

> **m_ad said:**
> I've done some extensive research on this, and I can't find the best method for joining wmv files. I have four wmv files and I'm trying to join them using any method out there.

Perhaps first convert the wmvs to something a little more malleable:

```

ffmpeg -i input1.wmv -sameq intermediate1.mpg
ffmpeg -i input2.wmv -sameq intermediate2.mpg
cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg

```

This is adapted from the [FFmpeg FAQs]("http://ffmpeg.org/faq.html#SEC29").

All the best,

Andrew

---

### Post by jmore9 on 2009-12-27
Try winff it is in the repos.  Works pretty good for me.  Also version for windows as the name indicates.

---

### Post by m_ad on 2009-12-28
Thanks everyone. I'll go ahead and try the recommendations and post the results.

EDIT: using ffmpeg to convert the wmv to mpg failed. The output file is around 200mb larger than the input.

---

### Post by 3rdalbum on 2009-12-28
> **m_ad said:**
> Thanks everyone. I'll go ahead and try the recommendations and post the results.

EDIT: using ffmpeg to convert the wmv to mpg failed. The output file is around 200mb larger than the input.

Use a lower bitrate then.

Why don't you try using Kdenlive to put the videos together, and then render it out as a good video format?

---

### Post by andrew.46 on 2009-12-28
Hi m_ad,

> **m_ad said:**
>  using ffmpeg to convert the wmv to mpg failed. The output file is around 200mb larger than the input.

Perhaps convert the final *joined* .mpg file to the format of your choice? If you were keen on wmv this would make the *complete* example:

```

ffmpeg -i input1.wmv -sameq intermediate1.mpg
ffmpeg -i input2.wmv -sameq intermediate2.mpg
cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg
*ffmpeg -i intermediate_all.mpg -vcodec wmv2 -sameq -acodec wmav2 -f asf outfile.asf*

```

Although perhaps there are better formats for the final conversion...

Andrew

---

### Post by m_ad on 2009-12-28
Thanks everyone. I'll figure this out - probably using ffmpeg to convert everything to mpg, then join.

Thanks again.

---

### Post by m_ad on 2009-12-28
AAHH, even using ffmpeg to convert the intermediate files to mpg, then cat them together gives me an output file of the length of only one of the intermediate files (5 mins).

Maybe mencoder can help with this?

---

### Post by lotharmat on 2009-12-28
> **m_ad said:**
> Hmm, what is vfr?

vfr = Variable Frame Rate 

iirc!

---

### Post by pushpsmarty on 2009-12-31
Where should be put the files so that it can take in use after giving command.
I have problem given as-

pushpsmarty@Revolution:~$ mencoder -oac copy -ovc copy -idx -o output.avi video1.avi video2.avi video3.avi video4.avi
MEncoder SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
File not found: 'video1.avi'
Failed to open video1.avi.
Cannot open file/device.

Exiting...

So where should i save the files before giving command.
I am a beginer.

---

### Post by pushpsmarty on 2010-10-04
Thanks

---

