---
title: "Scripting Advice"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by ethnochemist on 2010-10-17
I honestly know very very little about bash scripting and wish I had the time become more fluent in it.

I'm using google chrome and as most of us have noticed, flash stinks on 64bit! It eats up at least 50% of the CPU, and I am aware that little can be done about it (I've optimized everything!).

I know that the flash files are stored in chrome's cache folder. So I want to write a simple script that will find (or sort) the most recently created flash file, and play it with mplayer. This way I can just pause the video that's currently playing, and just run the script (or command).

I feel that there is a simple way to do this, but I've already run into some problems such as...the cache files have no file extensions, I don't know how to distinguish between file types using BASH script. It really feels like this can be accomplished in one line of code.

Anyone got a quick fix? Its folder is "~/.cache/google-chrome/Cache"

Thanks!

Sorry if this question is easily answered, I am aware that I could probably figure this out if I read a lot of BASH tutorials and man pages...but I've just been swamped with work recently, this is my last resort.

---

### Post by ethnochemist on 2010-10-18
Well, here's what I could do after learning a little bit of scripting, it's awful and I'm ashamed....especially because I call it "FlashCache" haha

```

#!/bin/bash

cd ~/.cache/google-chrome/Cache
mplayer $(file * | grep "Flash Video" | tail -1 | cut -c1-8)
```

This for chrome only. Basically It identifies the file type, filters it down to Flash Video....finds the most recent one, and then cuts out everything but the first 8 characters which is the file name (chrome's cache...everything starts with f_####). 

Basically I just go to any flash video site, pause it, and click the button to run that script, and it so far has played it successfully. 

Just thought I'd post it if anyone else wanted to know.

---

