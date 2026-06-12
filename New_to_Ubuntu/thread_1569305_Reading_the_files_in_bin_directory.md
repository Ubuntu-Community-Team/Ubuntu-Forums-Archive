---
title: "Reading the files in bin directory"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by -A- on 2010-09-06
So I wanted to see the implementation of the different commands like ls or date etc etc.

So, without bothering to think, I opened the files in the bin folder with vi, just to find gibberish.

So..umm..why exactly cant I read it? And how do I find the implementation/code for these functions? Aren't they stored somewhere?

---

### Post by col48 on 2010-09-06
I think these would be 'binary' files - ie compiled code.  So instead of human-readable instructions they are machine code.  Depending what language the original code was written in, even that is quite likely to be rather opaque. 

The gibberish is an attempt to convert the binary code to text as if it plain text (like this text, for example).  Since it isn't, it will not make sense.  As long as you only read it and don't try to save it you can't do any harm.

---

### Post by The Cog on 2010-09-06
The majority of files in /bin and /usr/bin will be "machine code" files, as col48 said. These will probably have been compiled from source code written in the C language. Compiling is the act of converting readable source code into machine readable instructions in a "binary" file. 

I presume that you aren't familiar with the C language or compiling. It may be worth googling around to find a better description of what compiling is all about that I have managed to give.

The source code for these programs is available from the Ubuntu package system, but I can't remember the details. It won't mean much to you until you have learned a bit of C programming though.

---

