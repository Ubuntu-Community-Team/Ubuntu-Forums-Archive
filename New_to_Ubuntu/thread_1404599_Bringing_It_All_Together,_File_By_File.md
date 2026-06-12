---
title: "Bringing It All Together, File By File"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by oldefoxx on 2010-02-11
A bit of info to start with first.  There are times when you want to
bring information together to one place for future reference, something
has gone wrong and you want to go back to a previous condition, or you now have something better and you want to replace the old with the new.

With computers, Informations (organized data) and raw data are generally stored in files.  Files can be separated from other files by names, places where they are stored (like folders or other drives), and all files are assigned date and time references.  In addition, files can have different sizes, based on their content and structure, and can have different ownership and rights associated with them.

You cannot have two files of exactly the same name in the same place at the same time, because the software depends on each having a unique name in order to tell the files apart.  To the software, where a file is and its name are treated as part of the whole path and name designation, which is how files with the same name can be used in different places and have no problems as a result.  But copies of the same file can appear in different places as well, so files with the same name but different paths may still reflect the same contents.

So you can have files in different places that share the same name, but then you have a problem if you seek to bring all those files together into the same place, and you may have to ask the software to help you deal with this, based on other available information, such as what size the file has, or what is the last date and time when it was updated?  If this information is the same as well, then it would suggest that the contents of each is exactly the same, so it might be just a copy.  But one copy could have been updated, so now the choice might be to either keep the older copy or to replace it with the newer copy.  So which gets kept, the older or the younger one, can be an important decision.

Why keep the older one?  Maybe the new one got messed up, the data or the information inside isn't good any more.  Why keep the newer one?  Because the whole idea is usually to collect more data and derive more information from it, so newer is sometimes better or more useful.  Why not keep both?  Well, you can I suppose, but if the old data and information is really outdated, why bother?

I don't remember every address and phone number that my family had when I was a child, and I don't think it would make much difference if I did. I only remember the names of a few schools that I attended, and the one that comes to mind when I think about this was the one named Anscar Larsen.  It just struck me as an odd name at the time, as I was early teens, and I had to work hard to commit it to memeory.

Okay.  So files can be important. and we might want to do one thing or another with them.  Why go into all this?  Because if you know what it is that you intend to do, you next need to know how to get it done, and that is not always obvious or easy to work out.  You go under Places, find your sources, indicate that you want to copy them, find your destination, then indicate that you want to paste them there.  I think it should be obvious that if a destination folder or file does ot already exist, that the copy will create it.

But there are times where this is not what you want, as information and data can become so outdated that you deleted those folders or files at the destination, and you don't those brought back by your efforts to bring back what you still want to get.

Okay, give you one practical instance where you might want to do any of this.  How about bringing back some, but not all, backup files?  How about just keeping all the folders and files synchronized between two or more computers, say a desktop and a laptop?   This is stuff that really happens, and there are even special programs written to make it easier, but this has been an ongoing problem since computers came along, and there are methods that work that date back that far.

I just had to do something similar with Windows and an external drive.  There I found I could get by with xcopy with the /s /t /y switches to duplicate the file structure, then I had to follow that with xcopy /d /y to get the newer files to overwrite the older ones at the destination.  You repeat that, switching the source and destination passed to the xcopy command, and you can synchronize the files between the source and destinaton.  They did not really provide a means of having older files overwrite newers ones with xcopy, so I;m not quite certain how to go at that.

But now I need to perform the same task again under Ubuntu, and I have multiple problems.  First, my user may lack the priveleges needed for this task, and this can up and hit you on a by file or by folder bases.
Second, it is not clear what happens under the GUI if you attempt a copy and paste operation, and some of the source already exists on the destination side.  If this does occur, you then find out what is meant by merge within Linux, but that assumes you do not have your own idea of what merge should mean, which might conflict with what actually happens.

Third, you can do something like you do under Windows, which is get to the command line (Terminal mode) and issue some bash commands or call upon some utility program to help you do it.  Be interesting to find out what some of the more experienced hands at Linux or Ubuntu might suggest in this respect.

So this is the problem:  I have outlined a number of situations where some type of merge action is called for, and I wonder what might be the best way to do this for that particular situation and need?  Anyone care to provide some answers?

---

### Post by Satoru-san on 2010-02-11
WOW! If you want to get an answer you can do one of 2 things.

either at the bottom put a tl;dr and then a synopsis, hardly anyone will want to read the entire thing until they are sure that they can solve it.
**also use bold it is easier to catch important things that are bolded**

I read a bit and if I am right you are asking for a terminal command that will merge files.  try this

```
cat file1.txt file2.txt file3.txt > file.txt
```

I read a little more for xcopy do this

```
cp -Rv /path/to/folder /path/to/location
```

---

### Post by oldefoxx on 2010-02-12
I can appreciate your remarks concerning the extent of my post.  But as you learn over time. there are specific challenges to handling information, meanng files, in constructive ways and not risk blowing up a lot of prior work that it took to accumulate that information.

To me, to recognize all the factors involved, you have to lay out a roadmap of all the dead ends and dangerous turns.  Anyhbody that bothers to look at the map can then come to appreciate what is involved with finding a path from one end to the other, and how to avoid mistakes.

So much for my answer to why I wrote so much.  Now **bold** or *italics* or even _underscores_ may impress some, but I am too busy staying focused on what to say and where I want the subject to go next.  I'm the guy behind the wheel, and you want me to work in a lot of texting at the same time?  Not my idea of a good thing to do.

I had a son-in-law that used gimmicks to impress customers with his prowlness as an engineer, coming in at night initially, finding out all that the night crew had to say on the subject and looking at the problem, then coming in all relaxed and assured the next day and spelling it out to the manager like he had just picked it all up out of the air, no mention of the visit the night before and no credit to the people who told him so much.

But that was not enough, after he took care of the problem, he would coach the manager to sing his praises back with the company that sent him, and then hang around for a few days to make it seem like it must have been a major job to fix, WHILE WRITING UP A LAVISH REPORT IN THE SOLITARY OF THE COMPANY-PAID HOTEL ROOM, ALL IN CAPITALS, TO SHOW WHAT A WHIZ BANG JOP HE HAD GOTTEN DONE ON THIS DIFFICULT AND PROLONGED TRIP.  And a lot of people believed what he had to say about himself.

I am not into those gimmicks, never have been.  If there is anything to be found in what I have to say, just dig it out, or don't bother.  I just tell it the way I see it.

First notion about joining files together?  Not bad, but not related either.  Works for some text files, but that is only one file type, text, and then only on the assumption that each file listed is a precessor to all the ones following.  How do you know that?  These are not like pages out of the same book, you know, with page numbers to tell you the order in which they should go.  So does not apply here.

Second effort?  Quite a bit better.  Would not hurt to put into words exactly what it does, and what each switch adds to the process.  More like that for each of the cases I outlined would be welcomed.  And others are also welcomed to share their knowledge and methods if they want to.

---

