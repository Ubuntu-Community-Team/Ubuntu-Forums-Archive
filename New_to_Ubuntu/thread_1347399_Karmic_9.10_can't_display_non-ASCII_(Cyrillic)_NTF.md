---
title: "Karmic 9.10 can't display non-ASCII (Cyrillic) NTFS partition names"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2009-12-06
Hi all.

I'm having this quite annoying problem for some time now. My Karmic won't display non-latin (Cyrillic) NTFS partition labels properly. Instead, it shows a bunch of question marks.

Previously I had a Jaunty 9.04 persistently installed on my USB flash memory and this problem didn't exist. The partitions' names were displayed correctly.

Now I have Karmic 9.10 Installed on my Acer Aspire 5738z laptop and also on my work desktop. They both have the same problem. Please see the screen-shot:
[ATTACH]138762[/ATTACH]

I tried renaming my partitions through **Disk Utility**, but it didn't work. I tried finding some solution which uses **GParted**, but since I'm a beginner, I soon gave up because I don't want to mess anything up.

Can anyone guess the cause of this problem? Any help would be greatly appreciated. Also, is there any way for me to get these labels read properly?

Thanks in advance.

---

### Post by 0cton on 2009-12-06
did you rename them in windows? Cause AFAIK windows does not use unicode, and there are so many Cyrillic encodings out there , without knowing directly witch one you have you may be lost...
There should be in the repositories support for those character encodings,
I remember when I was using an English version of Windows, programs with Cyrillic letters ended up as ? and I had to change the default language to Russian IIRC.
to rename you just go to My Computer right click it and there should be a name there for you to edit.
edit: try installing Russian language support , even if you don't use  it may help.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2009-12-06
Octon thank you very much for the quick reply. :)

> **0cton said:**
> did you rename them in windows? Cause AFAIK windows does not use unicode, and there are so many Cyrillic encodings out there , without knowing directly witch one you have you may be lost...

Yes, I set the volumes' labels in Windows, so if I'm not mistaking, the encoding should be CP1251. Thank you for reminding me about Windows' encoding. I guess I should've known that is the root of the problem. But is there any solution? Can I somehow use UTF-8 for naming my volumes in Windows? Or to somehow force Karmic to read the windows-encoded labels, as Jaunty did?

> **0cton said:**
> There should be in the repositories support for those character encodings,

Can you please help me more specifically with what exactly should I search and install?

> **0cton said:**
> I remember when I was using an English version of Windows, programs with Cyrillic letters ended up as ? and I had to change the default language to Russian IIRC.

Yes, my Windows' default encoding for non-unicode programmes is set to Serbian (which is also Cyrillic CP1251).

> **0cton said:**
> to rename you just go to My Computer right click it and there should be a name there for you to edit.
edit: try installing Russian language support , even if you don't use  it may help.

Can you please clarify are you talking about Windows here or Ubuntu? If you're talking about Ubuntu, I am not able to rename any NTFS label from My Computer, I get an error:

> Sorry, could not rename "250 GB Hard Disk: ??????" to "250 GB Hard Disk: &#1085;&#1072;&#1079;&#1080;&#1074;": Operation not supported by backend

---

### Post by Gemnoc on 2010-02-04
I have the same problem on a French-language system. Some of my NTFS partitions' labels have accented letters. The accented character and all other following won't show. For example I've got a drive labeled "M" instead of its full name!

What I don't understand is from 7.10 to 8.10, everything was fine. This problem started with 9.10.

I'm still looking for a solution... [-o<

---

### Post by slobo on 2010-02-12
Tomica, Did you get this fixed ?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2010-04-15
No, couldn't solve this problem, unfortunately. I found out though that the problem was known to Ubuntu developers and that they were working on solving it. As a result, the problem is gone in 10.04 Lucid Lynx - my volume labels are back to normal :)

---

### Post by Gemnoc on 2010-04-15
That's great news!!! :)

Because to me it means that occidental accented letters should now work again too.

Now I'm going to tell that to the stupid moron who kept arguing that I shouldn't use non-ASCII characters in my volumes names, because it does not follow the "international standard" or such other cr*p. :rolleyes:

---

