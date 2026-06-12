---
title: "File extension and format change in Python"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by skirmishdirmish on 2010-12-08
Hi all,

I need a script that can change all of the extensions in a directory from .au to .snd, and then I need to call a function "fixsndR" which I normally call in the terminal command line, to run on all of the new .snd files in my directory. The format required is fixsndR <input.snd> <output.snd> and I want to automate it so that the filename for my input become filenameR for my output.

Can someone help with this? I have very limited experience and no formal training in programming.

So far, I've gotten this far;

import os
import glob

os.chdir(dir)

for fi in glob.glob("*.snd"):
    os.rename(fi, fi[:-3] + "au")

but I'm getting the error: "TypeError: coercing to Unicode: need string or buffer, builtin_function_or_method found"

Thank you, 
skirmishdirmish

---

### Post by TeoBigusGeekus on 2010-12-08
Don't know about python, but in bash it would be something like
```
#!/bin/bash
for i in $(ls *.au)
do
	fn=$(basename $i)
	n=${fn%.*}
	cp $n.au $n.snd
done
rm *.au
for i in $(ls *.snd)
do
	fn=$(basename $i)
	n=${fn%.*}
	fixsndR $n.snd $nR.snd
done
```

---

