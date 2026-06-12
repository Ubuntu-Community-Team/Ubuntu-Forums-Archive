---
title: "[SOLVED] How can I know the file format of a tar ball ?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2009-01-03
Hi
How can I know the file format of a tar file ?
I have a file I what to decompress.  It works under Ubuntu, but not on an other Linux distribution (Debian based) I'm using on an Arm based computer.

The file name is :
pgSlideShow.tar.gz

under Ubuntu, tar zxvf works fine
under my Arm computer using Debian based TS-Linux, this is the error message :
gzip:stdin:not in gzip format
tar:Child returned status 1
tar:Error exit delayed from previous errors

I tried this:
tar xf pgSlideShow.tar.gz

This is the error message I got :
tar:This is not like a tar archive
tar:Skipping to next header
tar:Error exit delayed from previous errors

Any idea how I can point the problem?
Is the file format, or tar command on TS-Linux cause this problem ?
I updated tar, but got same behavior.

Thanks

---

### Post by Pierrot Lafouine on 2009-01-03
Any application I can run to tell me what algorithm was used to create and archive file ?

Thanks ?

---

### Post by Pierrot Lafouine on 2009-01-03
My last post here ?
Got so few answers so far.
Maybe I was expecting too much from this kind of forum
:-(

---

### Post by Dedoimedo on 2009-01-03
Relax! People actually do other things that wait for new posts.

That said, use the file command to check ay file format:

```

file <file-name>

```

And for more info, use man file:
[http://linux.die.net/man/1/file](http://linux.die.net/man/1/file)

Dedoimedo

---

### Post by MighMoS on 2009-01-03
If all else fails you can ```
gunzip $FILENAME.tar.gz
``` which will decompress it and remove the .gz extension, leaving an uncompressed tarball, where you can just "tar -xf $FILENAME.tar" on the other.

---

### Post by handydan918 on 2009-01-03
If ```
tar -zxvf pgSlideShow.tar.gz
```works fine on Ubu, on the same tarball, I would have to believe that the issue is with the version of busybox on your ts-linux install. busybox is highly configurable, so it may not have full support for tar built in. 

OTOH, maybe that tarball just doesn't speak ARM...

---

### Post by Pierrot Lafouine on 2009-01-03
> **Dedoimedo said:**
> Relax! People actually do other things that wait for new posts
I agree with you.
But this is not the first thread I post questions and... got very
few answers so far.  I'm not angry, just a little disappointed.

> **Dedoimedo said:**
> 
```

file <file-name>

```


That worked, the file is in gunzip format.

For an unknown reason, the wget command I made on Arm computer worked,
but pgSlideShow file was corrupted.  I transferred tar file from my
Ubuntu to ARM system with openssh, and tar zxvf worked fine on ARM.

Thank you very much for your help

---

### Post by Pierrot Lafouine on 2009-01-03
> **MighMoS said:**
> If all else fails you can ```
gunzip $FILENAME.tar.gz
``` which will decompress it and remove the .gz extension, leaving an uncompressed tarball, where you can just "tar -xf $FILENAME.tar" on the other.

Thanks for this hint, I will put in my HELP file, were I accumulate helpful
stuff until I remember them.

---

