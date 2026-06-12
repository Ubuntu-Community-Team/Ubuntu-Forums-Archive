---
title: "how to create shortcut to program?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by kiridude on 2009-04-07
I have downloaded foxit because the included pdf viewer is pretty weak.

2 questions: 

1. After installing, I run the program from command line but do not know how to create a shortcut. I would like a shortcut in the "office" list.

2. How do I make this program my default program. In other words, when ever I open a pdf doc for it to automatically open in foxit.

As a side note, can someone recommend an open source pdf viewer that has at least a word search option, or is foxit the best choice if I don't want adobe?

---

### Post by Simian Man on 2009-04-07
1. Right-Click the main menu and select "Edit Menus".  Then select "New Item" under the sub menu you like.  Enter the command and give it a name.

2. Open Nautilus and navigate to a pdf file.  Right click one and click "Properties".  Then under the "Open With" tab you can choose the default application.

I like Evince, the default viewer best, but have never tried Foxit.  Adobe's takes way to long to load for me.

---

### Post by kiridude on 2009-04-07
Thanx for your reply but I am using Cairo-dock, with which I have replaced the default panel on top of the screen. I looked in the configure tab of the applications applet that handles my menus, and strangely, there is no option for adding or removing items on the submenus. 

Cairo dock must be getting the info of what to put in the menus from somewhere in Ubuntu. For example, when I install something that's in synaptic, it automatically gets added to the menus.

---

### Post by Simian Man on 2009-04-07
> **kiridude said:**
> Thanx for your reply but I am using Cairo-dock, with which I have replaced the default panel on top of the screen. I looked in the configure tab of the applications applet that handles my menus, and strangely, there is no option for adding or removing items on the submenus. 
Ah I don't know.

> **kiridude said:**
> Also, any idea how to make the new program default?

I answered that under #2 above.

---

### Post by kiridude on 2009-04-07
yeah, sorry, i edited it after you read it.

Thing is that when I go to properties on a pdf, foxit does not even appear as an option - even when I click "add." What I am trying to do is to get it into Ubuntu's program list somehow...

---

### Post by Simian Man on 2009-04-07
To add something not on the automatic list you can expand the "Use a custom command" tab and enter the command to launch foxit (presumably just 'foxit').

---

### Post by kiridude on 2009-04-07
Ok, that did it! 

I just did a mv to /usr/bin so it could be with all the other programs, fixed the permissions, and now its working.

Now I'm working on creating an icon...

---

