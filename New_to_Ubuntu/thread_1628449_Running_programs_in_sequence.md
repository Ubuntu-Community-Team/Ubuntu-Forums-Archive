---
title: "Running programs in sequence"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by breandan_anraoi on 2010-11-22
Hey all
Basic question, for which apologies if it has been asked and answered already, I have searched the forums and the web but haven't found anything to help.

I have an image processing program (autopano-sift) that I want to run on multiple sets of images. But running multiple versions of the same process in different terminals slows each one down considerably. 

Ideally, what I would like to do it set the computer to run the process on each set of images one after another, starting it for the next set once the first is finished, so that I could leave it to run overnight without needing any input from me.

i.e. (simplified):
breandan@eddie:~$ autopano-sift -o outputfile1.pto ./jpg1/*.jpg
<runs><finishes>
breandan@eddie:~$ autopano-sift -o outputfile2.pto ./jpg2/*.jpg
<runs><finishes>
breandan@eddie:~$ autopano-sift -o outputfile3.pto ./jpg3/*.jpg
.....

and so on, without me needing to actually run the program every time.

Is there a way to do this? I'm guessing it should be possible to write a shell script to do it but I'm really not very good at writing scripts etc., so any help would be appreciated. 

Thanks!

---

### Post by sanderd17 on 2010-11-22
You could make a loop in bash, but I don't know what files are already present en what files need to be created. a loop would be something like this:

```
#!/bin/bash 
COUNTER=0
for f in *.jpg; do # get the jpg files
let COUNTER=COUNTER+1 
#execute your command with $COUNTER in it to change filenames
done
```

---

