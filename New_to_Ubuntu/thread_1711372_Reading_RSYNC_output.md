---
title: "Reading RSYNC output"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by tg3793 on 2011-03-21
I tell you. It is sure hard to read this rsync output until you know what you are doing [and I don't]. I've been staring at this stuff for an hour and I just can't get to a point (even after several dry runs) where I feel confident about what I'm looking at.

So, does something like the below mean something is going to be changed or something is 'not' going to be changed?:

```
  p, li { white-space: pre-wrap; }  Number of files: 10119
 Number of files transferred: 0
 Total file size: 25.23G bytes
 Total transferred file size: 0 bytes
 Literal data: 0 bytes
 Matched data: 0 bytes
 File list size: 205.15K
 File list generation time: 0.076 seconds
 File list transfer time: 0.000 seconds
 Total bytes sent: 235.87K
 Total bytes received: 30.72K
 
 sent 235.87K bytes  received 30.72K bytes  11.85K bytes/sec
 total size is 25.23G  speedup is 94637.21 (DRY RUN)

 
```

And in case you really want to see the whole thing I put it in Pastebin here:
[http://pastebin.com/Sjcev00A]("http://pastebin.com/TTvvGSWs")

Anyone know of any line by line explanations of rsync output. Or anyone willing to help me with the 'key' lines that I should paying attention to?

What I'm 'looking' for is something that tells me that 'these' files are the ones that will be added or deleted (shows me a visual of why rsync thinks the two files are different).

Thanks.

---

### Post by Wobblybob on 2011-03-21
If you want to see a list of files that are to be changed etc. I seem to think the unison package [in repos] which is a gui front end for rsync may be what you are looking for.

---

### Post by seawolf167 on 2011-03-21
Try running rsync with the -nv switches so you can see the changes that will be made

i.e.

```
rsync -ru**nv** /source /destination > rsync-output
gedit rsync-output
```

Then if all looks good, remove the -n switch to run for real

---

### Post by tg3793 on 2011-03-21
I'm running the dryrun switch already:

```
rsync -nh --progress --stats -r -tgo -p -l -D --update /home/scribe/Tin/J/Audio/ /media/SignatureMini/J/Audio/
```But I'll try your line of switches and see if I get something a little better than what I have now.

- - - - - - - - - - - 

I'll also try Unison and see how that looks. When I was reading about Unison I didn't consider it as seriously because I didn't see it being recommended by anyone since 2007 or 2008.

---

### Post by AbsolutIggy on 2011-05-05
```

 Number of files: 10119
 Number of files transferred: 0
 Total file size: 25.23G bytes
 Total transferred file size: 0 bytes
 
```

In case you hadn't found the answer yet (and for others asking the same questions:

The 4 lines above are the most important lines. They tell you, in order:
1. The total number of files rsync considers in the backup set (on the source)
2. The number of files it found which were (or would be if using -n) transferred)
3. The total size of all the files in the backup set (ie 10119 files totalling 25.23G)
4. The total size of the files transferred.

In this case, nothing would have been transferred, even without a dry-run

---

### Post by tg3793 on 2011-05-06
> **AbsolutIggy said:**
> ```

 Number of files: 10119
 Number of files transferred: 0
 Total file size: 25.23G bytes
 Total transferred file size: 0 bytes
 
```

In case you hadn't found the answer yet (and for others asking the same questions:

The 4 lines above are the most important lines. They tell you, in order:
1. The total number of files rsync considers in the backup set (on the source)
2. The number of files it found which were (or would be if using -n) transferred)
3. The total size of all the files in the backup set (ie 10119 files totalling 25.23G)
4. The total size of the files transferred.

In this case, nothing would have been transferred, even without a dry-run

Thanks for the tip. Sadly I wasn't able to get this worked out before I got pulled away in some other direction. ... I 'will' get back to this; hopefully before I have any data loss <sigh> :-)

---

