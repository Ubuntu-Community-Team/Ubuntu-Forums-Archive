---
title: "some .mov files no video"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by zpzpzp on 2011-01-30
Hi

I use VLC player. For some .mov files, there is no video and only sound. For other .mov files, there is video. So I know that I have the codec. However I don't know why some .mov files video is not shown. If I play these files in QuickTime in Windows, there is video.

Any ideas why some .mov files would not work in VLC Player?

I was able to get it to work properly using Quicktime 7.1.6; but is there a way to get it to run in VLC Player or any other native linux players?

Thanks,

Paul

---

### Post by Nixarter on 2011-01-30
no video means no co/dec (at least, not one that is properly installed).  mov is an extension, not a format.  Formats are not co/decs, and there can more than one co/dec (coder/decoder) for a given format-- such as lavc and xvid co/decs for MPEG-4 ASP (i.e., most files ending with the *.AVI extension).  All that being said, most of the files with mov extensions are in some version of the quicktime format.  The problem is, there is more than one version, and not all co/decs can handle all versions-- and there is no requirement that the mov extension contain a quicktime format file.  To complicate things further, audio formats don't come out as often as video formats.  So, with your file, the format of the audio stream is recognized, but the (apparently newer) format of the video stream is not.

Now that you're confused, you just need to update the co/dec(s) you use to handle your quicktime format files.  I'm not very familiar with the quicktime format (as it brings nothing to the table IMHO), but I imagine if you update your ubuntu-restricted-extras version you'll be set.

---

### Post by zpzpzp on 2011-01-30
Hi Nixarter

Thanks so much for your reply! It makes sense.

I just checked and my ubuntu-restricted-extra is the latest version. Maybe there is something else wrong...

Does anyone have any idea?

Thanks again.

Paul

---

