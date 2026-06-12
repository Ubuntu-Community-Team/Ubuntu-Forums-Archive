---
title: "Terminal: Navigate to directories with special characters in filename?"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by spielball on 2011-04-30
I have a NTFS partition which I share between Ubuntu and Windows. And I wanted to access a specific directory on this partition, using the terminal. This directory has a special character in its filename (character '#'):

*# Filename*

I wasn't able to manage getting to that directory with the cd command. What do I have to do? Everytime I type the '#' character, it takes me somewhere else.

---

### Post by spielball on 2011-04-30
I just found the solution myself by trial and error. I simply put the filename in quotation marks and it worked:

*cd "# Filename"*

:popcorn:Greetings from a newbie

---

### Post by falko on 2011-04-30
Try to use a backslash before that character (or let the shell complete the filename - type in the first characters of the filename and press TAB - if this is the only file that begins with the characters you type the shell will autocomplete the file name).

---

### Post by elliotcroft on 2011-04-30
You can use 'Open terminal here' utilities to do so, an example of which is the one included with KDE.

---

### Post by spielball on 2011-04-30
The backslash thingy works. But I have to use it for a blank space as well, e.g. for "# Directory" I have to type "\#\ Directory". The tab trick is also a very nice shortcut for long directory names. Thanks a lot.

As for the 'Open terminal here', I couldn't find such thing in Ubuntu. I don't use KDE though.

---

