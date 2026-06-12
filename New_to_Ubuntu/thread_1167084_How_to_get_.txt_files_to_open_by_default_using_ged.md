---
title: "How to get .txt files to open by default using gedit, rather than run as a program"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by swarup on 2009-05-22
I have hundreds of text files of format .txt that I want to open by default using the gedit text editor. I have tried right-clicking on given .txt files, selecting properties->open with->text editor. But still when I left-click on the text file, it still asks me whether I want to run it (as a program) or display its contents? And the default selection there is "cancel". So if I just hit "enter", then the window closes. If instead select "display", it does open into gedit. But that is a slow and convoluted way for me to open these files which I open a hundred times a day. I want to be able to just click on the file and have it open as a text file in gedit, rather than having to be asked every time whether I want to run it as a program or not. How can this be accomplished?

---

### Post by Mornedhel on 2009-05-22
Open Nautilus, click on Edit > Preferences, go to the Behavior tab, select "View executable files when they are opened".

---

### Post by swarup on 2009-05-22
Thank you Mornedhel, it worked perfectly. :p

---

### Post by Mornedhel on 2009-05-22
You're welcome. Please mark this thread as solved, unless you have other issues.

---

### Post by CoreyB. on 2009-05-22
> **Mornedhel said:**
> Open Nautilus, click on Edit > Preferences, go to the Behavior tab, select "View executable files when they are opened".

Cool, but will this have any adverse side effects?  Will double-clicking debs, for example, still install or will it open with the archive manager?

---

### Post by swarup on 2009-05-22
@Mornedhel: I hadn't seen the "mark thread as solved" option for some time. At your suggestion, I've just now looked again under "thread tools", but still it seems not to be there. Is it located somewhere else now? I also used to like the option to mark particular replies with a "thank you" when it was particularly helpful. But that seems to have been stopped as well?

---

### Post by Mornedhel on 2009-05-22
CoreyB: At worst, right-clicking will still give you the usual "Open With..." options.

swarup: My mistake. I have just come back to this forum after a few months. I didn't realize "mark as solved" and the thanks button had disappeared.

I was wondering why no threads seemed to be marked solved anymore... :(

---

### Post by pricetech on 2009-05-22
Just thinking;  Would it not be better to remove the executable attribute from the text files ??

---

### Post by Cheesemill on 2009-05-22
To mark threads as solved, the OP needs to edit his first post and edit the title to [SOLVED]..........

Cheesemill

---

### Post by Didius Falco on 2009-05-22
> **Cheesemill said:**
> To mark threads as solved, the OP needs to edit his first post and edit the title to [SOLVED]..........

Cheesemill

I was recommending that myself, but one of the Mods gently told me that the preferred method was for the OP to click the "Edit Tags" button at the bottom of the page and add a "solved" tag.

Apparently, the reason they disabled the "Solved" and "Thanks" buttons was because it was causing problems with the forum database.

Now I just say "Thanks" in a final post and edit the tags. Besides, it seems more genuine to actually type out a "thank you!" rather than robo-form it. <G>

Regards,

Didius

---

### Post by swarup on 2009-05-22
> **Didius Falco said:**
> ...one of the Mods gently told me that the preferred method was for the OP to click the "Edit Tags" button at the bottom of the page and add a "solved" tag.

I have just now tried clicking on this "Edit Tags" button. but nothing happens when I do so.

---

### Post by asmoore82 on 2009-05-22
```
find ~ -iname "*.txt" -print0 | xargs -0 chmod -x
```
... only if you feel up to it.

Disabling "run text scripts" in Nautilus is not an altogether bad idea in general either.

---

### Post by raymondh on 2009-05-22
> **swarup said:**
> I have just now tried clicking on this "Edit Tags" button. but nothing happens when I do so.

go to your first post > edit > advanced > type SOLVED in front of your title > save

Regards,

---

### Post by swarup on 2009-05-23
> **raymondhenson said:**
> go to your first post > edit > advanced > type SOLVED in front of your title > save
Perhaps it would be good if there were another way of marking this. For example in this case, the thread title would have to be truncated in order to fit [SOLVED] on the same line, and that would make the thread title unclear. Also, someone else has written in this thread that the [SOLVED] adjunct to the thread title was objected to by the administrators because it was causing problems with the forum database.

So, I do not know what the solution is. I agree that having a way to mark the thread as solved is very important, so people who are searching the support forum database can see at a glance whether the problem has a solution in the thread or not. 

I thought the option in "thread tools" for "matter solved", was a great way to do it.

---

