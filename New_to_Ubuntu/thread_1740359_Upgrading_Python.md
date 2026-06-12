---
title: "Upgrading Python"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by Talruk6 on 2011-04-26
I have a really newbish question.  

I can't figure out how to upgrade Python to Python 3.  It's currently stuck on 2.6 and I can't find anything in the synaptic manager to fix that.  Is the only way to download it off the website [www.python.org/download](www.python.org/download) and use the command line to install it?

Also on a tangent, why is it not upgraded by default?

---

### Post by stoogiebuncho on 2011-04-27
In Ubuntu they don't update software in the official repositories until it has been tested and shown not to break anything.

Even then, they usually only do security updates and don't move to the next major version of the software until the next version of Ubuntu comes out.

Both of these things mean that there is a lag (sometimes a significant lag) between the time when a new version of software comes out, and the time that you'll see an update in your update manager.

I'm not sure about this, but with python, they might also be sticking to an older version for compatibility reasons.  That's only a guess.  I would NOT try upgrading the default python installation unless you have a very good reason.


That said, if you want the latest version of any software, you will usually have to download and install it yourself, and do it again each time a new update comes out.

Sometimes you can find an alternate PPA that contains the latest packages.  That can save you a lot of work if you trust the source.  But it's probably not a good idea to use an alternate PPA to upgrade python, because, as I said before, upgrading the default python isn't a very good idea.

Wow, that's a wall of text.  Hopefully I answered your question.

---

### Post by earthpigg on 2011-04-27
python3 is not backwards compatible with python2, so replacing python2 with python3 will break your entire system. python2 should be used to run the existing python2 programs on your computer, and python3 for any python3 programs you come across or already have. this is generally already taken care of for you, in the background. 

this was all intentional. you cannot upgrade past python 2.6.X because .6.X is the most recent version of python2.

python3 should be regarded as ***completely separate*** language from python2; You can't upgrade from python2 to python3 anymore than you can upgrade from ice cream to a thumb tack.

you can have them both installed, though.

```
sudo apt-get install python3
```

then, to open a python3 console:

```
python3
```

programs in python2 should start with:
```
#! /usr/bin/python2
```

programs in python3 should start with:
```
#! /usr/bin/python3
```

---

### Post by earthpigg on 2011-04-27
your question was not noobish, btw.

when C is changed so much that the new thing is not backwards compatible, they don't call the new thing "C 3.0", they call it "C#" or "C++", to make it clear that it should be treated as a new product, and not simply a trivial revision to an existing product.

they mislead you a bit by calling it "python 3" and not "python++ 1.0" or "python# 1.0" or whatever.

btw, worth noting: python2 is still being developed. it is not obsolete, just *ahem* classic. ditto for C, what Linux is written in. :)

---

### Post by Talruk6 on 2011-04-27
I got it to work now, thanks.

> **earthpigg said:**
> your question was not noobish, btw.

when C is changed so much that the new thing is not backwards compatible, they don't call the new thing "C 3.0", they call it "C#" or "C++", to make it clear that it should be treated as a new product, and not simply a trivial revision to an existing product.

they mislead you a bit by calling it "python 3" and not "python++ 1.0" or "python# 1.0" or whatever.

btw, worth noting: python2 is still being developed. it is not obsolete, just *ahem* classic. ditto for C, what Linux is written in. :)

As for that, what I find really irritating is that the books on the subject aren't clear on this at all.  They barely even make the distinction, much less explain this mess.  I guess that's the benefit of having such a strong community though:D

---

