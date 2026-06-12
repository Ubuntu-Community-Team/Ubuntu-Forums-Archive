---
title: "Output the verbose information into a file  (2&gt;1&amp;)?"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-30
Hello, 

I have read that  2>1&  can help to put whatever arrives from info into the bash commaand line to is sort of not considered;

is it possible to output whatever comes out of the command line? 

Example: 

```
mplayer video.mpg 2>1& >> outputtomyfile.log
# or
cp -r -v source1 target1  2>1& >> outputtomyfile.log
# ... and so on ... to ouptut log into a file 
# with zenity too ...

```

---

### Post by tgalati4 on 2010-12-01
I'm not familiar with that syntax, but the following should work:

mplayer video.mpg > outputtomyfile.log &

> is an output redirection pipe and the & puts it into the background until the thread is finished.

>> is the append redirection pipe and it appends to the existing file

< is an input redirection pipe and it can be used to feed information from the standard input to a command.

---

### Post by honeybear on 2010-12-01
> **tgalati4 said:**
> I'm not familiar with that syntax, but the following should work:

mplayer video.mpg > outputtomyfile.log &

> is an output redirection pipe and the & puts it into the background until the thread is finished.

>> is the append redirection pipe and it appends to the existing file

< is an input redirection pipe and it can be used to feed information from the standard input to a command.

well this is too simple for overriding several programs, surely. In order words your reply is not answering. Thank you anyhow for trying

---

