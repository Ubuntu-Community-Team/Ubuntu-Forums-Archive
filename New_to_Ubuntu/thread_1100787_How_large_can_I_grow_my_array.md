---
title: "How large can I grow my array?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by thelamer on 2009-03-19
I am currently running 5 1.5TB drives in Raid 5. The blocksize is 4k and the filesystem is ext3. 

From what I have read on Wikipedia about ext3 the filesystem size limit with a 4k blocksize is 8TB. 

But I have also read some contradictory posts on this forum saying the limit is 16TB even with a 4k blocksize. 

Basically I am planning on doubling the array and adding 5 more drives this upcoming week. I would like to know if I need to convert my filesystem before growing the array to 13.5TB. 

Thanks!

---

### Post by Eisenwinter on 2009-03-19
why do you need so much space anyway?

---

### Post by mlentink on 2009-03-19
Perhaps he runs a Ubuntu mirror? 
I would say that's not necessarily relevant

---

### Post by thelamer on 2009-03-20
Eisenwinter; 

Get an uncapped cable modem and then tell me you have enough space. 

To all: 

If anyone knows the answer to this it would be much appreciated. I really don't want to convert to EXT4 or XFS unless it is absolutely necessary.

---

### Post by Ocxic on 2009-03-20
from wikipedia

**Size limits**

 ext3 has a maximum size for both individual files and the entire filesystem. For the filesystem as a whole that limit is 231&#8722;1 blocks. Both limits are dependent on the block size of the filesystem; the following chart summarizes the limits[[6]]("http://en.wikipedia.org/wiki/Ext3#cite_note-5"):
```

   Block size      Max file size       Max filesystem size
1 [KiB]("http://en.wikipedia.org/wiki/Kibibyte")                         16 [GiB]("http://en.wikipedia.org/wiki/Gibibyte")                     <2 [TiB]("http://en.wikipedia.org/wiki/Tebibyte")   
2 [KiB]("http://en.wikipedia.org/wiki/Kibibyte")                         256 [GiB]("http://en.wikipedia.org/wiki/Gibibyte")                    <4 [TiB]("http://en.wikipedia.org/wiki/Tebibyte")   
4 [KiB]("http://en.wikipedia.org/wiki/Kibibyte")                         2 [TiB]("http://en.wikipedia.org/wiki/Tebibyte")                        <8 [TiB]("http://en.wikipedia.org/wiki/Tebibyte")   
8 [KiB]("http://en.wikipedia.org/wiki/Kibibyte")[[1]]("http://en.wikipedia.org/wiki/Ext3#cite_note-6")                     2 [TiB]("http://en.wikipedia.org/wiki/Tebibyte")                        <16 [TiB]("http://en.wikipedia.org/wiki/Tebibyte")

```   
[LIST=1]
[*]**[^]("http://en.wikipedia.org/wiki/Ext3#cite_ref-6")** 8 [KiB]("http://en.wikipedia.org/wiki/Kibibyte") block size is only available on architectures which allow 8 KiB [pages]("http://en.wikipedia.org/wiki/Paging"), such as [Alpha]("http://en.wikipedia.org/wiki/DEC_Alpha")
[/LIST]

---

### Post by thelamer on 2009-03-20
Got it, so do you have any recommendations for file systems that will be painless to switch over to with no data loss?

---

