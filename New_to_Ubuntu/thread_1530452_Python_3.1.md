---
title: "Python 3.1"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by hdtvman on 2010-07-13
How do I install Python 3.1 in Ubuntu 10.04?

The Python site has the source for 3.1 and Windows & Mac installers but not much more info on installing it in Liux.

---

### Post by ankit singh on 2010-07-13
```
sudo apt-get install python3.1
```

---

### Post by hdtvman on 2010-07-13
Thanks for such a quick reply.  Also I went to the Ubuntu Software Center and a search for IDLE and then selected the 3.1 version.  It was downloaded & installed.  I think this installed Python 3.1 also.

---

### Post by ankit singh on 2010-07-13
Yes since that idle was dependent in python3.1,and this ain't like other OS where u you have to think for dependencies.

---

### Post by staf0048 on 2010-07-13
You will need to download the tarball (first option on the downlaod site), then extract the file (right click, extract here).  Then, from the command line navigate to the directory that you extracted the files to (such as # cd /home/computer/downloads/Python3.1) and type:

```
./configure
```

Then: 
```
make
```

Finally:

```
make install
```


***Obviously I took way too long to type this up***

---

### Post by hdtvman on 2010-07-13
Are these 3 steps the usual process for installing a program from source code?  This seems to imply that Python 3.1 is written in Python.  Is this the case?

---

### Post by mbzn on 2010-07-13
They are, usually... You'll sometimes have a text file in the tar-ball to give the steps. But this one is almost always the case.

---

### Post by Paqman on 2010-07-13
> **hdtvman said:**
> Are these 3 steps the usual process for installing a program from source code?  This seems to imply that Python 3.1 is written in Python.  Is this the case?

Yes, although it's always preferable to get your software from the repos instead of compiling it yourself.

Python isn't written in Python. It's job is to interpret Python. If it was written in Python, what would run it?

---

