---
title: "Help needed with command!"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by towoha on 2009-01-22
Hi.
I need to know how I can get the command "New E-Mail" in the Evolution mail program to work under opera. Where is the folder I need???

---

### Post by towoha on 2009-01-22
Is there no one here to help me?

---

### Post by PirateChef on 2009-01-22
I don't understand the question.
I can't find the "New E-mail" command in Evolution.

First, what are you trying to do? Are you trying to get mailto: links to open Evolution in Opera?

---

### Post by jpoRS on 2009-01-22
Hey towoha,

In the future, it might help you to use more descriptive post titles.  "Help Needed With Command" is pretty vague, and some people who could help you may just be overlooking your post because they don't know they can help.

Anyway, I am not sure I understand your question.  You want to check Evolution e-mail from Opera?  I am not sure what you mean by this, so could you please be more specific with your needs.

I hope I can help,
jim

---

### Post by towoha on 2009-01-22
> **jpoRS said:**
> Hey towoha,

In the future, it might help you to use more descriptive post titles.  "Help Needed With Command" is pretty vague, and some people who could help you may just be overlooking your post because they don't know they can help.

Anyway, I am not sure I understand your question.  You want to check Evolution e-mail from Opera?  I am not sure what you mean by this, so could you please be more specific with your needs.

I hope I can help,
jim

Hi Jim. 
Sorry for the vage description, but I tried to post a detailed description of my problem earlyer, but got no respond on that so I thought I should try this in stead... 
I'm trying to get a "Mailto" from Opera to start a new mail in Evolution, Is that a good enough description?

---

### Post by towoha on 2009-01-22
> **PirateChef said:**
> I don't understand the question.
I can't find the "New E-mail" command in Evolution.

First, what are you trying to do? Are you trying to get mailto: links to open Evolution in Opera?

Not exactely, I want this to happen: When I click a mailto adress in Opera I want the Evolution to open a new mail window.

---

### Post by towoha on 2009-01-22
!SOLVED!
I got it working now! 

Press Ctrl + F12 and go to programs.
There you must edit the option mailto or if you don't have this option add it.
It should be:
protocol: mailto
action: uncheck the open with opera and set to open with default application if evolution is your system wide default email client or set it to open with other application and select evolution in /usr/bin/evolution

---

### Post by jpoRS on 2009-01-23
towoha,

Now that I see what you were looking for I am sorry I didn't figure that out.  It is equally my fault for not trying to understand better.

Make sure to mark the thread [SOLVED] under options up there.  Makes things easier for future readers.

Peace!
jim

---

### Post by Muffinabus on 2009-01-23
> **jpoRS said:**
> towoha,

Now that I see what you were looking for I am sorry I didn't figure that out.  It is equally my fault for not trying to understand better.

Make sure to mark the thread [SOLVED] under options up there.  Makes things easier for future readers.

Peace!
jim

I believe the [SOLVED] tool is still broken.

---

### Post by snova on 2009-01-23
> **Muffinabus said:**
> I believe the [SOLVED] tool is still broken.

Not broken, temporarily disabled. See:

[http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)

---

