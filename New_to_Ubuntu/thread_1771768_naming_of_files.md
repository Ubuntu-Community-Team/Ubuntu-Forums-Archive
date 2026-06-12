---
title: "naming of files"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by Jacobonbuntu on 2011-05-30
Hi people,
I am trying to get a grip on some settings:

On **ask ubuntu**, there is a very nice manual on how to edit the "home folder launcher quicklist", and also how to automatically synchronize the quicklist with the bookmarks, and I got it working well. 
What I don't understand; 

1.the manual tells me to copy the

/usr/share/applications/nautilus-home.desktop -file

obviously the settings-file of the launcher. However, out of curiousity I looked in the directory manually, but couldn't see such a file. when I search te file with "find", I get a file with another name?? ("Personal Folder")

how can that be?

2. Am I right that this file (whatever its nam is) is "overruled" by the local (personal) settings file in 
~/.local/share/applications?

thanks in advance!
Jacob

---

### Post by AlphaLexman on 2011-05-30
What is the output of:
```
ls -l /usr/share/applications
```
and,
```
ls -l ~/.local/share/applications
```

---

### Post by dFlyer on 2011-05-30
> **Jacobonbuntu said:**
> Hi people,
I am trying to get a grip on some settings:

On **ask ubuntu**, there is a very nice manual on how to edit the "home folder launcher quicklist", and also how to automatically synchronize the quicklist with the bookmarks, and I got it working well. 
What I don't understand; 

1.the manual tells me to copy the

/usr/share/applications/nautilus-home.desktop -file

obviously the settings-file of the launcher. However, out of curiousity I looked in the directory manually, but couldn't see such a file. when I search te file with "find", I get a file with another name?? ("Personal Folder")

how can that be?

2. Am I right that this file (whatever its nam is) is "overruled" by the local (personal) settings file in 
~/.local/share/applications?

thanks in advance!
Jacob

The file your looking for is in /usr/share/applications/nautilus-home.desktop. If you want to edit this file copy and paste this link in a terminal.

sudo gedit /usr/share/applications/nautilus-home.desktop

But before you make any changes first know what your doing and second back up the original file.

---

### Post by Jacobonbuntu on 2011-05-30
> **AlphaLexman said:**
> What is the output of:
```
ls -l /usr/share/applications
```and,
```
ls -l ~/.local/share/applications
```

both inputs generate a huge list, I am not sure the moderator will be happy if I paste it here :)

is that normal?

aha, I understand what you mean (stupid me, but ok, this is the absolute beginners department)
both lists contain a nautilus-home.desktop -file!
still cannot see it when I open the folders??

---

### Post by Jacobonbuntu on 2011-05-30
> **dFlyer said:**
> The file your looking for is in /usr/share/applications/nautilus-home.desktop. If you want to edit this file copy and paste this link in a terminal.

sudo gedit /usr/share/applications/nautilus-home.desktop

But before you make any changes first know what your doing and second back up the original file.


no, no, I already did the job, and all is working fine!!
I meant, I did the job in the terminal, and no problem occurred. I was just wondering why I couldn't find the file when I *looked *into the folder??
My question was meant educational; I want to understand why I see no nautilus-home.desktop file in the folder.

---

### Post by AlphaLexman on 2011-05-30
For some reason, (I don't know why) nautilus will give different filenames than the terminal for '/usr/share/applications'

---

### Post by Jacobonbuntu on 2011-05-30
> **AlphaLexman said:**
> For some reason, (I don't know why) nautilus will give different filenames than the terminal for '/usr/share/applications'



ok, now I know it is not me.... :)

thanks!

---

### Post by dFlyer on 2011-05-30
> **AlphaLexman said:**
> For some reason, (I don't know why) nautilus will give different filenames than the terminal for '/usr/share/applications'

Open nautilus-home.desktop. Look at the name section of file, it should read Home Folder. It uses the name under Name= when displaying in nautilus.

---

### Post by AlphaLexman on 2011-05-30
OK, a little bit of investigation reveals that the files in '/usr/share/applications' are just *.desktop files.

In each *.desktop file there is a variable 'Name=Program Name' and it seems that variable is used by nautilus instead of the actual filename.

EDIT: dFlyer beat me to it.

---

### Post by Jacobonbuntu on 2011-05-30
Wow, thanks!

this really *is *educational. the past few days I wondered , and I thought I was just being stupid somehow,

thanks again!

my second question: do these .local -files "overrule" the files in /usr/share/applications?
I noticed all manuals on editing make you copy it to your .local - directory and edit it there

---

### Post by AlphaLexman on 2011-05-30
> **Jacobonbuntu said:**
> do these .local -files "overrule" the files in /usr/share/applications?
Yeah, usually your options in your user $HOME will override **ANY** global settings.

---

### Post by dFlyer on 2011-05-30
> **Jacobonbuntu said:**
> Wow, thanks!

this really *is *educational. the past few days I wondered , and I thought I was just being stupid somehow,

thanks again!

my second question: do these .local -files "overrule" the files in /usr/share/applications?
I noticed all manuals on editing make you copy it to your .local - directory and edit it there

I'm not sure they override anything, but if you change the icon in the .local folder you will have 2 of the same applications names with different icons that display.

---

### Post by Jacobonbuntu on 2011-05-31
thanks for the great help!

Jacob

---

