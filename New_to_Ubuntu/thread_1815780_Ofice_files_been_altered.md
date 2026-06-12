---
title: "Ofice files been altered"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by Zundap on 2011-07-31
Hi, Coul any one pl;ease help, Something has gone wrong with saved documents, when i try to open them now, this pops on the screen as per the screen shot

When i click to open the file, the words are no longer there, what i get now in my documents as per the screen shot.

This happened, at the same time that i was experiencing virus type problems, like the scroll bar on Firefox, would stay down when i dragged it down to the bottom of the page, it just sprung back up to the top. The problem with scroll has stopped, it works perfect.

My files are rather important to me, so any help with this would be sincerely welcome. Thanks.[IMG]file:///home/truth/Desktop/Screenshot.png[/IMG]

The picture on the right is comes on screen, when i try to open any document.

---

### Post by AlphaLexman on 2011-07-31
> **Zundap said:**
> My files are rather important to me
Everyone has important files...

Can you open your *odt files in the 'Archive Manager' ??

Try starting OOo from the command line...
```
oowriter -norestore ~/Documents/filename.odt
```

Good Luck!

---

### Post by Wim Sturkenboom on 2011-07-31
Although I don't know what to search for (would by trial and error), I suggest that you do a search. This has come along one or two weeks ago.

---

### Post by amanchesterman on 2011-08-01
Have you tried opening the files with a different wordprocessor, to see if the problem is specific to OpenOffice? AbiWord will open and edit .doc files.

---

### Post by Zundap on 2011-08-04
Thanks for the replies everyone, sorry to be so late in replying but i have just had a doozzy of a flue, i have tried to open O//O via the command line with the code given, but i get an error message saying as below

> /home/truth/documents/filename.odt does not exist

> 
I have installed Abiword and tries to open the files  with that, but when i try, i get the error message below.

Error importing file file///home/truth/desktop/documents/scudo.odt 

**(Scudo being the name of the document)**


I did try searching but nothing even vaguely similar to the search term came up.

Could any one tell me if it is possible to delete Open Office, without screwing up the O/S.

Thanks again to everyone who made a suggestion.

---

### Post by The Cog on 2011-08-04
a .odt is a zip file. Try opening it with archive manager. Then the file content.xml is the one you are really interested in. You might be able to make sense of content.xml by looking at it in firefox, or in gedit. This should let you get a good idea if the content is still there.

I suspect that you were suffering from a stuck key that kept your document scrolling, and putting lots of # characters in the documents (you might find the original text at the bottom if you're lucky). But this is only a guess though - I could be completely wrong.

EDIT
Oops, I'm talking rubbish. I should have noticed it's a .doc file and not .odt.

---

### Post by Wim Sturkenboom on 2011-08-04
[http://ubuntuforums.org/showthread.php?t=1802783](http://ubuntuforums.org/showthread.php?t=1802783) (unsolved)

google results for [open office file corrupt filter](http://www.google.co.za/#q=open+office+file+corrupt+filter&hl=en&prmd=ivnsfd&ei=sdQ6TqvhN4KbOuOvpcsD&start=10&sa=N&fp=bd1d9530468a5532&biw=1280&bih=578)

Plenty of hits but I could not easily find one that was succesfully solved.

And yes, you can uninstall without a problem.

---

### Post by Hagar Delest on 2011-08-04
Sadly, nothing to do: [22 page term paper replaced with pound signs](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=17677).

Check the temporary folder of the system (see in OOo Tools>Options>OOo>Paths). If there are folders like sgmlf.tmp with a file having the same name inside, make a copy of that file, rename it in .odt and cross your fingers.

Else, nothing to do I fear.

What OOo version BTW? The one delivered with Ubuntu I guess?
On Ubuntu 11.04?

---

### Post by grahammechanical on 2011-08-04
It seems to me that you are opening a file called Albums.doc. Is this correct? You are opening a file created by a Microsoft word processor in Openoffice. So, you need to set the filter options. I suggest that you are using the wrong character set.

From your screenshot the character set is Western Europe (DOS/OS2-85). DOS? OS2? How old is this document?

Try Unicode (UTF-8 ) or Western (Windows-1252).

Regards.

---

### Post by Hagar Delest on 2011-08-05
Don't bother, the file is dead (have you read the topic I've linked)?

BTW, I recalled [that post](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=42815#p197562), it may help.

---

