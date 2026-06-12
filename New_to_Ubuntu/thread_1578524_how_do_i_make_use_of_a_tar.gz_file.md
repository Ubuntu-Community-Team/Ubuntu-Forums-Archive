---
title: "how do i make use of a tar.gz file?"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by hortstu on 2010-09-20
I don't know what to do with it.

I've googled it and entered it into the terminal and tried a few different suggestion without luck.

Thanks

---

### Post by sharathcshekhar on 2010-09-20
```

tar -xvzf /path/to/file.tar.gz

```
Will extract the contents in the present working directory

---

### Post by oldos2er on 2010-09-20
> **hortstu said:**
> I don't know what to do with it.


Depends entirely on what's in the tar.gz. What program, what's the full file name, from where did you download it?

---

### Post by s0rc3r3r on 2010-09-20
as you must have known by now that tar is like .zip file in windows.

You can just right click on it and extract it to a folder.

then depending on the file..you can decide what you want to do with it.
as what exactly you are trying to do with it  is not clear from your question.

If you just want to extract the content of a tar file..just right click on it and select the 'extract' option.

---

### Post by da burger on 2010-09-20
If you've downloaded a program as a .tar.gz then it's quite hard to install. It can be done, but uninstall can often be hell. If you tell us the program we can try and find a better way to install it for you. But here's a general guide:

1) Try to find something in the repositories. (Either Ubuntu Software Center or Synaptic).
2) Try to find a .deb file, these will integrate into synaptic quite nicely.
3) Try to find a user maintained repo on the internet. People on the forum will be happy to explain how to get one of these working.
4) Then and only then should you look at .tar.gz files. Again if there's no alternative, we'll be happy to help you install these.

Angus

---

### Post by hortstu on 2010-09-20
> **s0rc3r3r said:**
> as you must have known by now that tar is like .zip file in windows.

You can just right click on it and extract it to a folder.

then depending on the file..you can decide what you want to do with it.
as what exactly you are trying to do with it  is not clear from your question.

If you just want to extract the content of a tar file..just right click on it and select the 'extract' option.

Thanks that's exactly what I was looking for.  I apprecite the terminal code too though.  Anyone care to explain what it means and how it works?

---

### Post by da burger on 2010-09-20
> **hortstu said:**
> Thanks that's exactly what I was looking for.  I apprecite the terminal code too though.  Anyone care to explain what it means and how it works?

Sure, I'd be happy to :).

```
tar -xvzf /path/to/file.tar.gz
```

tar is the command that handles all operations on .tar files. -x tells it we want to extract the archive. -v tells it to tell us everything it's doing (verbose is what it's short for), in tar that just means listing all the files it's working on. -z tells it to use the gzip decompresser on the files (Deals with the .gz bit). -f tells it that the next bit is the name of the files we want to work with. 

Angus

EDIT: Just something else I thought of. If you have a .tar.bz2 then replace the z with a j. Alternatively you could just use -a which will work with .tar.gz, .tar.bz2 and just .tar provided the file names are correct.

---

