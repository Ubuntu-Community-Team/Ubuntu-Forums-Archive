---
title: "Max number of files per directory for ext3/4?"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by chrisharrington on 2010-02-27
Hi,

Does anyone know the maximum number of files allowable for a single directory in the ext4 file system (and ext3, ext2 etc.)?

I'm running a script to generate thumbnails for every few seconds of some long video footage, and ffmpeg will not output thumbs from video anymore when the number of files in the output directory reaches exactly 16,383 files. That seems like a low number to me considering ext4 supposedly allows 32k or 64k subdirectories etc. (is that total for the file system or per directory?).

I'm posting this to absolute beginner because I assume it is one of those things that most people "just know" but funnily it is hard to find an answer via google search etc.

Thanks!

Chris@Japan

---

### Post by 2hot6ft2 on 2010-02-27
> **chrisharrington said:**
> Hi,

Does anyone know the maximum number of files allowable for a single directory in the ext4 file system (and ext3, ext2 etc.)?

I'm running a script to generate thumbnails for every few seconds of some long video footage, and ffmpeg will not output thumbs from video anymore when the number of files in the output directory reaches exactly 16,383 files. That seems like a low number to me considering ext4 supposedly allows 32k or 64k subdirectories etc. (is that total for the file system or per directory?).

I'm posting this to absolute beginner because I assume it is one of those things that most people "just know" but funnily it is hard to find an answer via google search etc.

Thanks!

Chris@Japan
I asked a similar question in this thread
[Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")

And the answer (shortened to just what's relevant here) was:
> **mcduck said:**
> 
If you have /usr on the same partiton as the /, then you have exactly the same amount of available space on /usr as you have available space on the partition itself. **There is no per-directory size limits (unless you enable quotas and set suych limits yourself)**.

---

### Post by falconindy on 2010-02-27
Well, that's somewhat false... at least for Ext2/3. Both define a maximum number of files across the entire filesystem, which is variable and based on the size of the drive. However, it seems a little too convenient that you seem to have hit **some** limit at (2^14)-1.

Also, it should be noted that the readdir() function which iterates over a directory gets extremely sluggish when you start getting into the thousands of files. Perhaps you should consider rearranging your data, if at all possible.

---

### Post by chrisharrington on 2010-02-27
> **2hot6ft2 said:**
> I asked a similar question in this thread
[Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")


Thanks, I think in this case it is a different issue. The drive in question is external.

> **falconindy said:**
> 
Also, it should be noted that the readdir() function which iterates over a directory gets extremely sluggish when you start getting into the thousands of files. Perhaps you should consider rearranging your data, if at all possible.

That sounds a bit more plausible. For whatever reason FFMPEG can't output the file to the directory when the number of files in there reaches the number in my post, so perhaps I should look into FFMPEG more and, as you say, just move some files around.

---

### Post by chrisharrington on 2010-02-27
Oh how embarrassing. I completely forgot that this particular external drive is the one I formatted as FAT32, not the EXT3 one.

That would explain the precise limitation I suppose.

Sorry for the confusion there ;)

---

