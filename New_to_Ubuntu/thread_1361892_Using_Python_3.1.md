---
title: "Using Python 3.1"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by BioVirtual on 2009-12-22
I Installed Python3.1 . I want to to run my Python code with Python 3. But typing Python in terminal returns Python 2.6.4. How can I do That?
Thanks.

---

### Post by KommaH on 2009-12-22
If you installed python3 using apt-get/aptitude, then you need to type
```

python3

```in the terminal instead of
```

python

```

---

### Post by JairunCaloth on 2009-12-22
It looks like /usr/bin/python is a symlink to /usr/bin/python2.6. You could remove the symlink and replace it with one to python3

```
ls -l /usr/bin/python
```

will show you where the symlink points

If you want to change the symlink

```
sudo rm /usr/bin/python
sudo ln -s /usr/bin/python3 /usr/bin/python
ls -l /usr/bin/python
```

now when you call python, python3 will run by default. If you want to explicitly call python2.6 you can still do that by typing python2.6

---

