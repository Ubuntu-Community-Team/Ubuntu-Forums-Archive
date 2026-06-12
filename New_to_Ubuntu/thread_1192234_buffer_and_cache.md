---
title: "buffer and cache"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by flylehe on 2009-06-19
Hi,
I wonder what is the difference between buffer and cache in outputs of top, ? Are they parts of RAM or CPU?
Thanks!

---

### Post by unutbu on 2009-06-19
In [http://ubuntuforums.org/showthread.php?t=992974](http://ubuntuforums.org/showthread.php?t=992974), JohnFH explains, "A buffer is something that has yet to be "written" to disk. A cache is something that has been "read" from the disk and stored for later use."

For example, if you type top and  see

```
Mem:   1032016k total,   893068k used,   138948k free,    28680k buffers
Swap:  4095984k total,     4992k used,  4090992k free,   456056k cached
```

Then it means you have 1032016k of physical RAM, and 4095984k of swap space.
The numbers associated with "buffers" and "cached" are part of RAM (despite "cached" being on the second line).

Of the 893068k of used RAM, 28680k is stuff that is to be written to disk, and 456056k 
is being used to hold data that has been read from files, and which the system is leaving in memory just in case some application tries to read it again.

Memory used for applications must be kept in either RAM or swap, but memory used for cache (such as recently accessed files) is good for performance but can be discarded at any time.

Every time a block device is accessed, the data is stored in RAM (in the cache).
Block devices are mainly disk drives, but could be other things as well -- video, webcam, etc. 

See [http://ubuntuforums.org/showthread.php?t=992974](http://ubuntuforums.org/showthread.php?t=992974).

---

### Post by flylehe on 2009-06-20
Thanks!

Did JohnFH mean that the operations for buffer and for cache have opposite directions: for buffer, CPU->buffer->disk; for cache, disk->cache->CPU?

Can the direction for buffer the other way around? 

I wonder When "the terms are used interchangably"?

---

### Post by unutbu on 2009-06-20
Hi flylehe, yes I think you are generally correct though I don't know enough about the role of the CPU to say for sure. 
```

  YES     YES 
CPU->buffer->disk
```

According to JohnFH, the buffer is headed for the disk. I don't think its direction is ever reversed. 

```
   YES    Not
    |   necessarily
    v      v
disk->cache->CPU
```

The stuff in the cache may never go back to the CPU. It depends on if the data is called upon again. For example, when I launch GIMP, it takes about 6 seconds to load. 
If I quit GIMP and launch it again, it takes about 4 seconds to load. The first time
the files had to be read from disk. The second time they were read from cache.

However, if I never launch GIMP again, those files would just sit around in cache until all my physical RAM was consumed. At that point, if some other application required RAM, the cache used for GIMP may be freed.

---

