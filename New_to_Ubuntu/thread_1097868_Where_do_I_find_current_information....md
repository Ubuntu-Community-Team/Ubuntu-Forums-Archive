---
title: "Where do I find current information..."
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Gaphumbala on 2009-03-16
...about sound card driver development?  The ALSA page has not been updated since 21 January 2008.  I have a Soundblaster X-Fi audio extreme card that has only very limited support in Ubuntu at this time and as I really like good quality sound, this is my only disappointment with Linux.

---

### Post by khelben1979 on 2009-03-16
When it comes to good sound with Linux you're better off with the [Sound Blaster Audigy]("http://en.wikipedia.org/wiki/Sound_Blaster#Sound_Blaster_Audigy_series") 2 ZS card. This is a really good soundcard and is supported by Linux.

So my advice on this is to either replace or insert this sound card in your computer and use this instead.

However, if you're on a laptop, then this is it, I suppose.

---

### Post by Gaphumbala on 2009-03-16
Well, that is an option of course, but I just bought this card shortly before installing Linux.  It works well in XP, but I don't like Windows... I know, that could be considered blasphemous(sp) in some circles but there it is.

---

### Post by taurus on 2009-03-16
[http://www.phoronix.com/scan.php?page=article&item=creative_xfi_gift&num=1](http://www.phoronix.com/scan.php?page=article&item=creative_xfi_gift&num=1)
[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)
[http://www.linuxscrew.com/2007/09/27/creative-sound-blaster-x-fi-linux-driver/](http://www.linuxscrew.com/2007/09/27/creative-sound-blaster-x-fi-linux-driver/)

---

### Post by Gaphumbala on 2009-03-16
Excellent!  Thank you very much!

---

### Post by markbuntu on 2009-03-16
If you are having problems getting your Creative X-FI card to work you can try the newest driver from creative, it seems to actually work for a few people:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

Or you can switch to OSS4:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

Or you can recompile your kernel with a patch. To recompile your kernel and apply the patch (take extreme care doing this, recompiling a kernel is serious business and can break your system. Do not do this unless you are absolutely sure you know what you are doing):

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

---

### Post by Gaphumbala on 2009-03-16
I will try the latest driver from Creative.  I already have stereo working but would prefer surround sound.  The OSS can only provide stereo.
Recompiling the kernel is way beyond me at this point.  :-P

---

### Post by Gaphumbala on 2009-03-16
Unfortunately, it is still only stereo.  Oh well...

---

### Post by markbuntu on 2009-03-16
If you want surround sound you need to edit the /etc/pulse/daemon.conf file. Find the line

default-sample-channels = 2

change the 2 to 5 for 4.1, 6 for 5.1 and 8 for 7.1

---

### Post by Gaphumbala on 2009-03-16
Thank you for your assistance.  I am getting a permission denied message when I try to open that file.  I am in root, in terminal.

---

### Post by Gaphumbala on 2009-03-16
Ok, I edited the conf file  ( I wasn't in root after all)  It did not fix the issue.

---

### Post by khelben1979 on 2009-03-17
> **markbuntu said:**
> If you want surround sound you need to edit the /etc/pulse/daemon.conf file. Find the line

default-sample-channels = 2

change the 2 to 5 for 4.1, 6 for 5.1 and 8 for 7.1

Can't he just use [Alsamixer]("http://en.wikipedia.org/wiki/Alsamixer") for that?

---

