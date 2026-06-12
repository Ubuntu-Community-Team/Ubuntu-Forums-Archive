---
title: "gedit alternatives"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by wheel_walker on 2011-01-05
I need an alternative to gedit that will not do this when I upload a *.txt or copy something from a *.txt and save it to something else.

If it matters, I use Ubuntu 10.04 Lucid Lynx, Linux 2.6.32, Gnome 2.30 and Xorg 7.4.

If you can't see my attachment, try this:

This is typed.  Line 1.
This is typed.  Line 2.
This is typed.  Line 3.

This is copied and pasted from gedit.  Line 1.

This is copied and pasted from gedit.  Line 2.

This is copied and pasted from gedit.  Line 3.

---

### Post by libssd on 2011-01-05
Using gedit in exactly the same environment, I do not have (and have never had) the behavior you report. I checked gedit preferences, and can see nothing that would account for the difference.

---

### Post by 12apennachi on 2011-01-05
If you use a terminal program like nano, which I like, or vim, which other people like you won't get any problems, but the nice interface is gone. That doesn't really matter to me so I always use nano, I think it comes default. Just type nano in a terminal followed by the path of the document you want to open, or the document you want to make. i.e.
 pennachi@pennachi-laptop~$ nano ~/Documents/some_random_document.txt

And to paste in a terminal it is ctrl-shift-v not just ctrlv

---

### Post by kimberlite on 2011-01-05
> **wheel_walker said:**
> I need an alternative to gedit that will not do this when I upload a *.txt or copy something from a *.txt and save it to something else.

This is something very weird. Just for clarification: when you "upload" a txt, does it means you open (or double click) on a file with txt extension? However it seems to be something wrong with international character encodings... What kind of characters are you using (Latin, Chinese, etc)?

---

### Post by wheel_walker on 2011-01-05
[http://www.verve-fanworks.com/SMF/index.php?action=dlattach;topic=300.0;attach=300](http://www.verve-fanworks.com/SMF/index.php?action=dlattach;topic=300.0;attach=300)

Are there spaces between addresses when view this?  (Is it just me, I'm asking.)  There weren't spaces - or line breaks or whatever it's called when you hit Enter - when I uploaded it.

EDIT

Upload = upload to a website.
Download = download same file from site to check it worked.

If I copy from gedit and post in a forum, when I post it those extra spaces appear.

EDIT

It's supposed to look like the attachment.

---

### Post by 12apennachi on 2011-01-05
I found some of these, never tried them but they are there.

leafpad
mousepad
geany
nedit

---

### Post by wheel_walker on 2011-01-05
Thanks, I'll try them out.

---

### Post by anystupidname1 on 2011-01-05
Another vote for Geany!

---

### Post by hansolo4949 on 2011-01-05
One that I really like, and have never had any problems with, is openoffice writer, which I think you can download seperately from the openoffice package in the software center. It might be a little slower than some of the other editors, but offers a wide range of compatibility, and you can make files, and save them in just about any format you would want.


 I hope that helps!


 hansolo4949

---

### Post by cgroza on 2011-01-05
Geany is made more for programming, but you can take out the tools you don't need from the toolbar.

---

### Post by psusi on 2011-01-05
emacs!

I still don't understand what the problem is.  The screen shot shows a file with a bunch of hex numbers in it.  Are you saying that when you copy and paste "0x1231234545" it comes out as "This is typed.  Line 3"?

---

### Post by TeoBigusGeekus on 2011-01-05
I've opened your file with geany, nano and libreoffice writer.
No go - it comes out just like with gedit. Must be the uploader's fault; an exotic encoding maybe?

Open terminal, navigate to the file and give
```
 sed '/^$/d' to_tkol_class_data.txt > to_tkol_class_data_corrected.txt
```
to delete all the empty lines from the file.

---

### Post by wheel_walker on 2011-01-05
[I]I still don't understand what the problem is.  The screen shot shows a  file with a bunch of hex numbers in it.  Are you saying that when you  copy and paste "0x1231234545" it comes out as "This is typed.  Line 3"?

[/I]Let's say that I type up a snarky, hilariously funny reply to a message on an internet forum that flummoxed me earlier this day.  I open up gedit, type the aforementioned snarky reply:

This is my cleverly worded reply.
Feel my wrath!
Die, vile woman!

Satisfied, I save it and go to sleep.

THe next day, I go to the forum and log in.  I check the message and, yes, it is still there.  I open snarky_reply.txt and it is just as witty as it was last night.

I highlight the entirety of snarky_reply.txt, right-click, and copy it.

On the forum, I paste the text of snarky_reply.txt to the Quick Reply text box, and click preview.

It now looks like this:

This is my cleverly worded reply.

Feel my wrath!

Die, vile woman!

I shrug, delete the spaces, and click Post.

****

I admit, it's not a huge deal, but it is annoying.  Thanks for the alternatives, I'll try them out.

---

### Post by A_M_S on 2011-01-05
> **12apennachi said:**
> If you use a terminal program like nano, which I like, or vim, which other people like you won't get any problems, but the nice interface is gone. That doesn't really matter to me so I always use nano, I think it comes default. Just type nano in a terminal followed by the path of the document you want to open, or the document you want to make. i.e.
 pennachi@pennachi-laptop~$ nano ~/Documents/some_random_document.txt

And to paste in a terminal it is ctrl-shift-v not just ctrlv

You can redefine nano Key Bindings by editing the file /etc/nanorc. You can define the ctr+c e ctr+v to copy and paste your text inside nano.

Below is part of my nanorc Where i define some key bindings

```

## Key bindings
## Please see nanorc(5) for more details on this
##
## Here are some samples to get you going
##
# bind M-W nowrap main
# bind M-A casesens search
# bind ^S research main
bind ^L searchagain main
bind ^X cut main
bind ^C copytext main
bind ^V uncut main
bind ^B mark main
bind ^Q exit main

```

for more information read [this]("http://manpages.ubuntu.com/manpages/lucid/man5/nanorc.5.html")

---

### Post by TeoBigusGeekus on 2011-01-05
> **wheel_walker said:**
> [I]I still don't understand what the problem is.  The screen shot shows a  file with a bunch of hex numbers in it.  Are you saying that when you  copy and paste "0x1231234545" it comes out as "This is typed.  Line 3"?

[/I]Let's say that I type up a snarky, hilariously funny reply to a message on an internet forum that flummoxed me earlier this day.  I open up gedit, type the aforementioned snarky reply:

This is my cleverly worded reply.
Feel my wrath!
Die, vile woman!

Satisfied, I save it and go to sleep.

THe next day, I go to the forum and log in.  I check the message and, yes, it is still there.  I open snarky_reply.txt and it is just as witty as it was last night.

I highlight the entirety of snarky_reply.txt, right-click, and copy it.

On the forum, I paste the text of snarky_reply.txt to the Quick Reply text box, and click preview.

It now looks like this:

This is my cleverly worded reply.

Feel my wrath!

Die, vile woman!

I shrug, delete the spaces, and click Post.

****

I admit, it's not a huge deal, but it is annoying.  Thanks for the alternatives, I'll try them out.
Ahh, I see now...
Try with geany and convert the line endings of your documents to windows line endings (Document>Line Endings).
Does this happen in ubuntuforums as well?

---

### Post by wheel_walker on 2011-01-05
Most of my text files are originally from Windows.  I carry a flashdrive with me, and I use notepad when I'm on my parent's desktop.  I think that's the problem.  Some weird interaction between notepad's encoding and GEdit.

EDIT

Testing

Short Story Collections 
The Dark Country (1982) 
Red Dreams (1984) 
The Blood Kiss (1987) 
The Death Artist (2000)

EDIT

Nope, these forums are fine.

---

