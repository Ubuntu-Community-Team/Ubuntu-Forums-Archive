---
title: "Finding Files"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2011-01-30
I'm working on setting up a project using TISCH and openkinect.  I have installed all the necessary files (I think) but am told I need to do some editing to get the two to talk to each other.  No problem, I am capable of doing that (and even understanding what I'm doing ;-) but I'm new to Ubuntu and have no idea how to find the files to edit them.

Install was done using (for Tisch)

 sudo apt-add-repository ppa:floe/libtisch
    sudo apt-get update && sudo apt-get install libtisch libtisch-dev libtisch-csharp libtisch-java libtisch-python

and (for openkinect)
sudo add-apt-repository ppa:arne-alamut/freenect[FONT=Verdana]
[/FONT]sudo apt-get update
sudo apt-get install freenect

Now I need to find directory openkinect/c/
and edit a file, then install the latest tisch library.

I can't seem to find the openkinect directory, cd doesn't find it either.  Any ideas?  Where do programs go when they install?

I would presume tisch is installed (an attempted reinstall said it was already there) but can't seem to find it to put the new lib in the same place.  Is that necessary?  Its a tarball, so where should I extract it to?

I ran into this in openCV too.  Can't seem to find the damned thing, but I know its ther.

regards, Richard

---

### Post by cogier on 2011-01-30
If you know the name of the file the following command run in **Terminal** should find it for you.

find / -name 'filename.ext'

More help on this is available here [http://www.computerhope.com/unix/ufind.htm]("http://www.computerhope.com/unix/ufind.htm")

---

### Post by philinux on 2011-01-30
```
sudo updatedb
```

Wait for this to finish. There's no output.

Then

```
locate xxxxx
```

You can use * in the search.

---

### Post by Robing Goodfellow on 2011-01-30
Thanks, locate was exactly what I was looking for.  Find worked, but as I understand it find checks all actual files, whereas locate checks the database that lists files so is much faster.

Thanks again, marking this one solved.

regards, Richard

---

