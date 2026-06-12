---
title: "How Do You Rename A Massive Number of MP3's???"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-10
Ubunteros,

I got this MP3 player that does not have a Shuffle feature :(  .

I also have over 200+ MP3's. Because my player hasn't a shuffle feature, things are getting boring rather quickly.

HOW CAN I TAKE THE FOLDER THAT MY MP3'S RESIDE IN AND RENAME RANDOMLY EACH MP3 FILE INSIDE????

The idea being that when the MP3's are copied into the player they aren't in any specific order resembling the exact and precise order of the original folder and files!

Thank You All!!!!!

---

### Post by dgoosens on 2009-03-10
well...
I'm pretty sure that your MP3 player is not that stupid...
It probably uses the metatags and thus, renaming your files makes no sence...

Maybe you could generate a random playlist though ?

---

### Post by suomalainen on 2009-03-10
That's not an accurate statement.

---

### Post by hansdown on 2009-03-10
Hi suomalainen.

You could try thunar. It's in synaptic.

---

### Post by suomalainen on 2009-03-10
Isn't there any sort of program into which you can dump MP3s and then have the program randomly assign new names?

Thanks

---

### Post by mister_pink on 2009-03-10
Make a file in the same folder called "randomize.sh", and put the following contents into it:
```
#!/bin/bash
files=`ls -1 *.mp3"`
for file in $files; do
 yes n | mv -i $file $RANDOM.mp3;
done;
```
Right click in and go to properties, tick the box to give it execute permissions. Double click and run it - all files in the directery will be renamed randomly.

Edit: Changed it slightly. Can't quite work out why I did it in such an odd way the first time.

---

### Post by Malalo on 2009-03-10
Sounds complicated, why not just use a MP3 player that does random ? There are many out there....

---

### Post by suomalainen on 2009-03-10
I don't know if this is possible but does anyone know if when You use VLC's shuffle feature if the files get dumped somewhere temporarily?

If so, I'd like to take a look at this folder and see what the contents look like. Maybe I could just use it?????


Any ideas????


Thanks!

---

### Post by mister_pink on 2009-03-11
When you use shuffle in VLC it probably just stores a list in memory.

Was there a problem with my previous suggestion? It seemed to do exactly what you asked for in your first post.

---

### Post by The Cog on 2009-03-11
This program should do it. 
```
#!/usr/bin/env python

import os
import random

used = set()
for before in os.listdir("."):
    if before.endswith(".mp3"):
        used.add(before)
        after = before
        while after in used:
            after = "x%s.mp3" % random.randint(1000000, 9999999)
        used.add(after)
        os.rename(before, after)


```
You could save it in your mp3 folder as (say) shuffle. Then make it executable like this:
> chmod +x shuffle
then do the shuffle like this:
> cd ~/mp3folder
./shuffle

---

### Post by suomalainen on 2009-03-13
I would like to say a BIG thank you to The Cog and Mister Pink for the code you wrote for me as per the "shuffle" option. I tested it out and it works perfectly!

I'd like to let you know why I needed it. I recently purchased on ebay a MP3 player that transmits the audio  through the car stero system via FM connection. Although this player is inexpensive (only $10USD) it does not have shuffle feature. BUT now with your code it does!!!!

Thanks so much for solving this problem for me!!!!


Ebay MP3 player

[http://cgi.ebay.com/Auto-Car-USB-SD-Slot-MP3-Player-FM-Transmitter-Remote_W0QQitemZ250385662033QQihZ015QQcategoryZ86537QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Auto-Car-USB-SD-Slot-MP3-Player-FM-Transmitter-Remote_W0QQitemZ250385662033QQihZ015QQcategoryZ86537QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by LowSky on 2009-03-13
for what it is, that thing is kinda cool

---

### Post by suomalainen on 2009-03-13
I can post results if you want after I get it. I think it will need another 2 weeks or so. The company said it was already sent....

---

