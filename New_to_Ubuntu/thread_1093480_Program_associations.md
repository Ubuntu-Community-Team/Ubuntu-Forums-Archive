---
title: "Program associations"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-11
I actually have two questions:

1) How can I find out the default program associated with certain filetypes? I have a PDF on my desktop which opens with "Document Viewer" but I have no idea what the program actually is. I did a ps -A and after wading through the entire list found something called "pdflush" which I assume is this program. Is there an easier way to do this? Also, how can I find where this program resides?

2) How can I add an icon for this PDF onto the top panel? Dragging the icon onto the panel brings up a Create Launcher box with the info already filled in so I just type a name. But clicking the icon does nothing. :( What am I doing wrong?

---

### Post by kanikilu on 2009-03-11
> **Volt9000 said:**
> I actually have two questions:

1) How can I find out the default program associated with certain filetypes? I have a PDF on my desktop which opens with "Document Viewer" but I have no idea what the program actually is. I did a ps -A and after wading through the entire list found something called "pdflush" which I assume is this program. Is there an easier way to do this? Also, how can I find where this program resides? The Document Viewer is actually called "evince". Whenever you don't know what the program is actually called behind the "user-friendly" name, the easiest way to find out is to go to System > Preferences > Main Menu. Find the item in question, click on it and then click Properties to find out the real command. For instance, the "Main Menu" editor command is actually "alacarte"...go figure ;)

> 2) How can I add an icon for this PDF onto the top panel? Dragging the icon onto the panel brings up a Create Launcher box with the info already filled in so I just type a name. But clicking the icon does nothing. :( What am I doing wrong? I guess I don't understand what you're trying to do. Are you trying to create a launcher for that *specific* PDF file, or do you want to create a launcher for the document viewer (evince)?

---

### Post by andrewsomething on 2009-03-11
The default PDF viewer is called "evince" they give it the generic name Document Viewer in menus though. By default it isn't shown in the applications menu, as most people only need it when opening a file and that happens automatically. To add it to the menu go to Preference>Main Menu. In the menu editor, go to Applications>Graphics and check off the box by Document Viewer.

To see what program opens a file, right click on the file and select Properties and go to the Open With tab.

As for your second question, dragging the icon onto the panel works for me... Are you given any error message? What version of Ubuntu are you using?

---

### Post by Volt9000 on 2009-03-11
Thanks for the speed reply, guys. Unfortunately as is the case with me, when one question gets answered it always brings up several others. :D

> **kanikilu said:**
> The Document Viewer is actually called "evince". Whenever you don't know what the program is actually called behind the "user-friendly" name, the easiest way to find out is to go to System > Preferences > Main Menu. Find the item in question, click on it and then click Properties to find out the real command. For instance, the "Main Menu" editor command is actually "alacarte"...go figure ;)

Ok, I found it. But what if the application I'm looking for isn't listed anywhere in these menus?
Also, how do I know the full path of evince? I know that Linux paths work a bit differently than Windows paths, but is there some kind of environment variable in Linux similar to Windows' %PATH%?

> 
I guess I don't understand what you're trying to do. Are you trying to create a launcher for that *specific* PDF file, or do you want to create a launcher for the document viewer (evince)?
I'm trying to launch this SPECIFIC PDF file.

> **andrewsomething said:**
> 
As for your second question, dragging the icon onto the panel works for me... Are you given any error message? What version of Ubuntu are you using?

I'm not getting any error. Running Intrepid Ibex, vanilla Ubuntu.
Here's what I do:
- Drag PDF icon from desktop onto panel at top
- "Create Launcher" dialog shows up, with "Command" already populated with the file and full path
- I type in a name under "Name" and click OK

Now the icon shows up on the panel at the top, but when I click it nothing happens. No error, no cursor change, nothing.

---

