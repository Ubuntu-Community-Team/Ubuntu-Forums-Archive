---
title: "Where Can I find a List of C Libraries?"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by mattseanbachman on 2010-07-04
Hi,

I have been getting back into programming recently (in C), and I was looking for a list of non-standard C libraries.  I'm not sure if this is the proper term for these...in other words, extra libraries, libraries that aren't already included with Ubuntu.

This is more just for me to play around with, I'd like to have an easy to browse list of non-standard libraries.  Might anyone be able to provide me any helpful links or tips? I've done some Googling but it ends either in finding C++ equivalents or nothing of interest.

---

### Post by sandyd on 2010-07-04
> **mattseanbachman said:**
> Hi,

I have been getting back into programming recently (in C), and I was looking for a list of non-standard C libraries.  I'm not sure if this is the proper term for these...in other words, extra libraries, libraries that aren't already included with Ubuntu.

This is more just for me to play around with, I'd like to have an easy to browse list of non-standard libraries.  Might anyone be able to provide me any helpful links or tips? I've done some Googling but it ends either in finding C++ equivalents or nothing of interest.
look in /usr/include for the c libraries (providing you installed them)

---

### Post by mattseanbachman on 2010-07-04
Thanks for the response (no less from the most beautiful user of Ubuntu :) ) but I must not have been clear on my question.  I'm looking to expand what I can do with C with the help of* additional  libraries.  *

Let's say that I wanted a library to deal with tiffs.  I know there is a tiffio.h library out there...in fact, I already have it.  

What I'm hoping to find is a list that serves as a compilation of all the possible libraries that I *could install.*

I'll give this another example because I might not be very clear...I'm not an expert at C and I might be butchering what some things are called.  There's a GUI library called glib that I also installed to help me compose some GUI adaptations of CLI programs.  What I want is to know what other libraries (like glib) are out there...another way to say it, **what other libraries exist beyond what I already have installed?** Is there a list somewhere? Or a way to search with apt-cache/apt-get?

---

### Post by =CrAzYG33K= on 2010-07-05
I believe there is no exhaustive list anywhere. It all depends on what sort of manipulation/programming you'd want to do.

Say, for example, if you wanted to do some sort of image manipulation there's ImageMagick for that.

On the other side, what's the use of having all the libraries installed when you're not going to use most?

---

### Post by stderr on 2010-07-05
You can install all manner of libs, and indeed make your own, so you can never get a completely comprehensive list.

However, you can get some sort of idea by looking through the development libraries in the repositories:

```
apt-cache search '^lib[a-zA-Z0-9-]*dev'
```

edit: Actually there's a lot of output, you'll probably need to pipe that though less or grep... 

```
apt-cache search '^lib[a-zA-Z0-9-]*dev' | less
apt-cache search '^lib[a-zA-Z0-9-]*dev' | grep tiff
```

---

