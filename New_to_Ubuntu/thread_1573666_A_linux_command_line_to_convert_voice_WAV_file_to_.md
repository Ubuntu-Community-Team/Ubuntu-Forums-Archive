---
title: "A linux command line to convert voice WAV file to Text file format?"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-13
Hello,

What is the command line to convert a WAV file to Text file? It is some kind of voice recognition, similar to Windows. What is the command under LINUX ? 

I recorded my voice from a regular device, and would like to have it as text like under MS Windows.

---

### Post by Temposs on 2010-09-13
There is no Speech to Text program included in Ubuntu. You would have to find a Linux program that can do what you want and install it.

---

### Post by honeybear on 2010-09-13
> **Temposs said:**
> There is no Speech to Text program included in Ubuntu. You would have to find a Linux program that can do what you want and install it.

Really? - I cant believe... - I am surprised still. Indeed there is few only ..  :(

I had come to that into the repositories at my first instance which conducted to my first believe:
```
docgenerator - generator plugin for python bindings documentation
libsphinx-search-perl - Perl module for Sphinx search engine
mscgen - Message Sequence Chart (MSC) generator
python-sphinx - tool for producing documentation for Python projects
libsphinx2-dev - speech recognition library - development kit
libsphinx2g0 - speech recognition library
sphinx2-bin - speech recognition utilities
sphinx2-hmm-6k - speech recognition library - default acoustic model
sphinxsearch - Fast standalone full-text SQL search engine
```

---

### Post by Temposs on 2010-09-13
Those packages are not installed by default, which is what I meant in my previous remark.

sphinx is a speech recognition engine. I've worked with it some in my academic research. So, you can use this. I just did a little research on the easiest way. Probably your best bet would be to install the sphinx2-bin package. Then, run this command in the terminal:

```
sphinx2-simple
```

This will run the program and when it says "READY...", it's waiting for you to say something. Try saying a few simple words very clearly and after you are finished, it will process your words and tell you in text what it thinks you said. 

The results are not very good because it doesn't train on your voice; it only uses a default training that is not your voice, and on a limited vocabulary, but you can try it out :-)

---

### Post by honeybear on 2010-09-13
> **Temposs said:**
> Those packages are not installed by default, which is what I meant in my previous remark.

sphinx is a speech recognition engine. I've worked with it some in my academic research. So, you can use this. I just did a little research on the easiest way. Probably your best bet would be to install the sphinx2-bin package. Then, run this command in the terminal:

```
sphinx2-simple
```

This will run the program and when it says "READY...", it's waiting for you to say something. Try saying a few simple words very clearly and after you are finished, it will process your words and tell you in text what it thinks you said. 

The results are not very good because it doesn't train on your voice; it only uses a default training that is not your voice, and on a limited vocabulary, but you can try it out :-)

Tried. The problem is that the sphinx is not using my USB microphone. It is located at hw:3.0 of alsa :(

---

