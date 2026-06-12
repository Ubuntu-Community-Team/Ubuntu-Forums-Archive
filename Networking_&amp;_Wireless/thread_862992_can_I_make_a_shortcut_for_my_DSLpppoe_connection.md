---
title: "can I make a shortcut for my DSL/pppoe connection?"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by plastichero on 2008-07-18
Hey bosses,  I managed to make and use the dsl-connection using:

[COLOR="DarkOrange"]sudo pppoeconf
sudo pon dsl-connection
sudo poff[/COLOR]

now, can I make a shorcut for this connection in my desktop? Just like the shortcut that was possible in windows? I dont want to open up the terminal all the time and write the commands to connect/close. Is there any way to make a shortcut so that I can simply double click on it?

---

### Post by sonofusion82 on 2008-07-18
save the commands in a text file and also add the following the first line in the file:

#!/bin/sh

then in terminal, make it executable by:

chmod +x filename

now, u can just click on the file to launch it.

---

### Post by plastichero on 2008-07-18
thnx.
double clicking on the shell script will work? lemme check.

---

