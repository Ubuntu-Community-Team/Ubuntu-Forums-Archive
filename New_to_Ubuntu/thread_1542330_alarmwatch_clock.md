---
title: "alarm/watch clock"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by klirka on 2010-07-30
hello, 

i need an app for kubuntu that is easy to install and run and will produce a beep every 30 seconds. 

thank you!

---

### Post by themusicalduck on 2010-07-30
You could probably do this using a bash script of some kind.

This is something that would work:

```
#!/bin/bash

while [  true ]; do
	sleep 30
	aplay /path/to/beep.wav
	
done
```

I found a sample of a beep sound that would work to use with aplay and attached it to this post.

If you keep the sample in the same directory as the script is saved, then you don't need to use the whole path, just "aplay beep.wav"

```
#!/bin/bash

while [  true ]; do
	sleep 30
	aplay beep.wav
	
done
```

Or apparently if you install the program "beep" with ```
sudo apt-get install beep
``` then you could replace "aplay /path/to/beep.wav" with just "beep" and it would play a beep through the PC speaker.

```
#!/bin/bash

while [  true ]; do
	sleep 30
	beep
	
done
```

but I haven't tested this because I don't have a PC speaker.

Copy that text into a text editor and save the file with a .sh extension. Then run it from a terminal with ```
sh filename.sh
``` while in the right directory. e.g. If it's saved on the desktop, use ```
cd Desktop
``` first. Or right click on the script file, go to Permissions and Allow executing file as a program. Then just double click on it and select to run in terminal.

There is probably a better way of looping this, like using counters to determine how many times it loops, but I'm not sure of the best way to do that. Someone might, or you could probably find the answer with google.

---

### Post by klirka on 2010-07-30
many thanks, themusicalduck! 

it works like a charm with your beep.wav, *magic*, exactly what i wanted, thank you!!!

---

