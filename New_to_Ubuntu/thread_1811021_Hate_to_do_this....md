---
title: "Hate to do this..."
date: 2011-07-24
forum: New to Ubuntu
---

### Post by Green Growbot on 2011-07-24
I know there is an azzload of posts about adding apps to the menu but none seem to fit my criteria.   I needed a program that could do some simple, fast compression to cut down on space on my external drive (full of movies). Ive used 7zip on Windows and loved it but here its more of an archiver and I may be wrong but IM pretty sure thats NOT what I am looking for. So, what I found that sounded good was a program called "lrzip". Problem is, is that it does not appear on the menu anywhere and I cant seem to find a basic run command from the terminal so that I can add it to the menu. ???
   So I guess I need 2 things then. First I need the name of an actual zip or rar or similar compression program that will do what I need it to do and secondly, I need to know if there is a basic run command for all programs or an easy way of tracking them down.

Specs:1.7ghz Single core Intel, 512MB RAM, Ubuntu 10:04.[COLOR="Red"][/COLOR]



[COLOR="Navy"]***side note:if anyone knows how I can talk to anyone that wrote or controls the rights to a program in the software center named "Devede", I would love to get the source so that I can put in an auto shutdown.(maybe thats another forum though)***[/COLOR]

THANKS TO ALL IN ADVANCE-GG

---

### Post by nothingspecial on 2011-07-24
lrzip is a command line app.

You run it by opening a terminal and typing

```
lrzip <options> <file(s)>
```

Type ```
man lrzip
``` for instructions.

You download the source like this

```
apt-get source devede
```

License: 2005 Sergio Costas
  DeVeDe is free software; you can redistribute it and/or modify
  it under the terms of the GNU General Public License as published by
  the Free Software Foundation; either version 3 of the License, or
  (at your option) any later version.

---

### Post by Green Growbot on 2011-07-24
```
lrzip <options> <file(s)>
```

On this, I get an error with a caret as the culprit... heres the exact error

 "bash: syntax error near unexpected token `<'"

(ran as sudo and without)

---

### Post by nothingspecial on 2011-07-24
Don't actually use the <>

type ```
man lrzip
```

---

### Post by hakermania on 2011-07-24
> **Green Growbot said:**
> ```
lrzip <options> <file(s)>
```On this, I get an error with a caret as the culprit... heres the exact error

 "bash: syntax error near unexpected token `<'"

(ran as sudo and without)
This is just an example of the use of the command:
```
lrzip <options> <file(s)>
```
You should use it with your own <options> and <file(s)>
A real example i.e. would be:
```
lrzip -m -a myfile
```

---

### Post by Green Growbot on 2011-07-24
cool. Thats works atleast as far as getting into the program if I want to run the whole damn thing in terminal which is fine I guess but there has to be a better program. It will let me add it to the menu but will not let me run it from their, just does nothing. Which tells me that im using the wrong command when adding it to the menu to find the program, just **not sure what its supposed to be.**
   Really appreciate all the help and would like to give you a plus one, ill have to check it out here in a minute.
   Ive got experience creating websites and you have to use the <carets> at the beginning and end of every damn line so, my bad typing them into the terminal.


**[COLOR="Red"]EDIT***ok, give up. How do I give you guys a good rating?[/COLOR]**

---

### Post by sanderd17 on 2011-07-24
There are no ratings here. Competition sometimes has a bad effect on community effort.

You are able to run it from a menu, but you won't see it running. If you want to see what's happening, you need to execute the terminal app with that particular command.

Something like
```

gnome-terminal -x lrzip <options> <file(s)>

```

than you will see a terminal appear, it will execute the lrzip code and afterwards the terminal will close.

If you are willing to put it in your own script, it might be handy to read this: [http://linuxcommand.org/](http://linuxcommand.org/) It's a really short guide but a great help.

---

### Post by 3rdalbum on 2011-07-24
First thing: On Linux, 7zip is a tool that allows graphical archive managers such as Ubuntu's *File Roller* to decode 7zip archives. It might even be able to create them - I'm not 100% sure of this. Once you've installed the 7zip package, File Roller will understand the 7zip format.

Secondly, from your post it seems like you want to compress movies. Videos are already compressed and they don't go down much further if you try to compress them again using 7zip or bzip2. Not worth the effort. Your best bet might possibly be to re-encode the source material (for instance, the original DVDs) to a more compressed video format such as H.264.

---

### Post by ziekfiguur on 2011-07-24
> **Green Growbot said:**
> I needed a program that could do some simple, fast compression to cut down on space on my external drive (full of movies). 

Unless your movies are in some ridiculously large filetype there is no way that's going to work. Lossy filetypes like avi and mp4 are already compressed much smaller than any lossless compression algorithm can do, no matter what program you use. Your best option is to buy another drive.

---

### Post by Green Growbot on 2011-07-24
ok Sanderd, Im skimming through linuxcommand.org right now and seems like it will be really helpful and tried the command that you gave to see it running and it opened the other terminal and now says "Copying from stdin.". not sure what that means but ill see if i can figure it out when done.

---

### Post by Green Growbot on 2011-07-24
there is also pics and program downloads and such on the drive. not much $ for a new drive right now and when ill likely go with an internal and toss this pathetic 80 gb drive thats in here right now when i get around to it (all $ is going towards moving now). Had a 500gb but opted to have a super ps3 instead of going with a crappy old pc with only 512 RAM and a 1/4 monster drive in the thing. For some reason cant find any system specific RAM for the thing and not sure where to go with this old POS right now.

I know this isnt what the post is about BUT please someone give me an idea of what to do when you lose a key (namely the important *** E key). there gotta be some household or hardware store thing to use right?

---

### Post by Green Growbot on 2011-07-24
another thing thats killing the space on the drive is that a lot of the movies are iso format so all i have to do if i want another disc is just to burn the thing. 2 hour conversion times kill me.

---

