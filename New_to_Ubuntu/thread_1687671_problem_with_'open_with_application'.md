---
title: "problem with 'open with application'"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by granda on 2011-02-14
help needed:

If I go to Places > Home Folder  or Places > videos  or places > desktop instead of the location opening I go immediately into  into a video player

The problem is with the 'open with application' which by default on my system Ubuntu 10.10 is that the open with another application has by default already got the 'remember this application for this type of file' checked by default.

Is there any way of reversing  this really annoying feature. having the dialogue window unchecked by default making it a conscious decision to open all similar files same way

Did I say really annoying. absolutely

---

### Post by Linyx on 2011-02-14
Right-Click on any folder on a desktop and select the option "**Open with other Application**" and their Select the **File-browser**, and tick the **Remember** option below...



Better now..?

---

### Post by nick_goodfate on 2011-02-14
Or you can use [Ubuntu tweak]("http://ubuntu-tweak.com/").
[ATTACH]183455[/ATTACH]

---

### Post by vanadium on 2011-02-14
This problem pops up all over the place. I guess this is due with the "Remeber" option being set by default in Ubuntu 10.10, which obviously was a bad idea.

---

### Post by nick_goodfate on 2011-02-14
> **vanadium said:**
> This problem pops up all over the place. I guess this is due with the "Remeber" option being set by default in Ubuntu 10.10, which obviously was a bad idea.

It's true. I was wondering why. And if the reason is what you said, why in every case folders open with media player? coincidence?

---

### Post by shunan on 2011-02-14
well i did not get your question really...

so i am guessing...

you can right-click on any file/program and select properties and go to the tab "Open With" and add/remove all you want. So you don't have to select Open With -> Other Application... but select the application you just want...

---

### Post by nick_goodfate on 2011-02-14
> **shunan said:**
> well i did not get your question really...

so i am guessing...

you can right-click on any file/program and select properties and go to the tab "Open With" and add/remove all you want. So you don't have to select Open With -> Other Application... but select the application you just want...

I think there is no "Open with" tab in folders properties ...

---

### Post by mc4man on 2011-02-14
> why in every case folders open with media player? coincidence? 
Not really, it (the default folder handler), could be switched to anything, just that most people tend to use the 'Open With -> Other Application' on folders that contain media

The bug is that the "Remember this..." option changes the default to the app chosen - this occurs on **both** files and folders.
In the case of files most people probably don't notice, and is somewhat useful. (a 2nd way to change the default for that filetype

On folders the 'Remember this.. " option is of no value and causes immediate issues as seen.

(I spent 5 months trying to have this changed, did get the option to be disabled by default, unfortunately the patch was only applied to natty and unlikely to be in maverick unless there is a rebuild of nautilus, in that case the maintainer could apply the patch if he remembers.

---

### Post by shunan on 2011-02-14
> **nick_goodfate said:**
> I think there is no "Open with" tab in folders properties ...

That is strange, I got it in mine... Nautilus 2.32.0!

Oops! I was using nautilus elementary and have been using it for so long...

[https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa](https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa)

---

### Post by nick_goodfate on 2011-02-14
> **shunan said:**
> That is strange, I got it in mine... Nautilus 2.32.0!

Oops! I was using nautilus elementary and have been using it for so long...

[https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa](https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa)

I think you have not understand the problem of "granda". When he tries to open a _folder_(not a file) it opens with media player.

---

### Post by shunan on 2011-02-14
> **nick_goodfate said:**
> I think you have not understand the problem of "granda". When he tries to open a _folder_(not a file) it opens with media player.

Ohh! thanks for clarifying, i never used open with feature on a folder, ever... but i can understand the annoyance... 

it seems like this bug was raised and fixed
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)

nautilus (1:2.32.2-0ubuntu2) natty

---

### Post by jamesdonaldson on 2011-02-18
> **Linyx said:**
> Right-Click on any folder on a desktop and select the option "**Open with other Application**" and their Select the **File-browser**, and tick the **Remember** option below...



Better now..?

It certainly is thank you!

---

### Post by jamesdonaldson on 2011-02-18
> **Linyx said:**
> Right-Click on any folder on a desktop and select the option "**Open with other Application**" and their Select the **File-browser**, and tick the **Remember** option below...



Better now..?

It is thank you!

---

