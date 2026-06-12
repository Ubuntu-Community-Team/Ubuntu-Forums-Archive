---
title: "command question"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by punkaceratop on 2011-09-08
Hi guys,
I have a question about the command.
I've seen this before but I forgot and dont know what it is so I couldn't google it.

What I'm trying to do is for example type the command
"google" instead of "firefox google.com" in the terminal and it will open google in firefox
something like that.

Or if I type in "trash" it will run the script that i wrote trash.sh which is saved in the Desktop folder.

So what is this process called? and how do I do it?

Thanks for your time

---

### Post by sisco311 on 2011-09-08
Use a function or alias:

[http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions)
[http://mywiki.wooledge.org/BashGuide/CompoundCommands#Aliases](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Aliases)

BTW, the trash-cli package provides a command line interface trashcan utility.

---

### Post by punkaceratop on 2011-09-14
thank you for your reply, I am able to do this with the function, but the thing is whenever i reboot my system the function will be gone. Is there anyway I can create this function permanently?  Thank you

---

### Post by booshire on 2011-09-14
Hello -

You can create a simple script named "google" and put it in your bin folder (with other commands). Just include something like this:

#!/usr/bin/bash
firefox google.com

Make it executable and you should be good to go

As long as the script is in one of your PATH's, it should work from anywheres

---

### Post by sisco311 on 2011-09-14
Add the function to the ~/.bashrc file.

---

### Post by punkaceratop on 2011-09-14
I got it, thank you guys

---

### Post by Chiel92 on 2011-09-14
> **sisco311 said:**
> Add the function to the ~/.bashrc file.

Or put it in the ~/.bash_aliases, file. That one is 'invented' especially for those things. By default ~/.bashrc includes ~/.bash_aliases.

---

