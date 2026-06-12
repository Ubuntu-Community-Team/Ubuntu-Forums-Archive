---
title: "Organizing files from lost+found"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by Dark Aspect on 2011-04-17
Hello,

I have an external 1TB hard drive (ext4) that has recently crashed complaining about multiply-claimed blocks. After running fsck for hours, it moved my entire home folder to lost+found and renamed them to the file's inodes. For example:

```
#12716299  #12795943
#2015469   #27895218
```

About half of the files aren't too critical but I'd like to recover my music library at least and the files appear to be intact as rhythmbox can play them when set to scan the entire drive. Is there a way to organize the files based on type? and possibly organize the music based on the tag information, for example ~/artist/album?

Googling found this script:

```
    #!/bin/sh

    mkdir -p ~/test-imgs;
    mkdir -p ~/test-vids;
    mkdir -p ~/test-music;

    for i in $*
    do
        ( [ -n "`file $i | grep image`" ] && mv $i ~/test-imgs )  ||
        ( [ -n "`file $i | grep video`" ] && mv $i ~/test-vids )  ||
        ( [ -n "`file $i | grep Audio`" ] && mv $i ~/test-music ) ||
        ( [ -n "`file $i | grep III`" ]   && mv $i ~/test-music )
    done

```

But regardless of what I put in place of images, video, etc. It always copies/moves the mp3 files and it appears that my images, videos, texts made it out as well. Following the instructions [here]("http://http://karuppuswamy.com/wordpress/2010/06/09/how-to-recover-files-from-lostfound-after-fsck-in-linux-how-i-did-it-in-ubuntu/") failed to give me the parent directory information and it would be my guess that they are gone. The entire drive reports 30 GB less than what it had before the crash but I haven't came across mixed files at this point.

Ideas for making the organizing process would be awesome. I suspect the drive is bad and I am copying the data as I find it to a new 2TB drive.

---

