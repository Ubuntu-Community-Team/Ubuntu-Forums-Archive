---
title: "JabRef, gpapers, kBibTeX... help?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by agm. on 2010-02-06
Hi,

I've been researching for the last few days several different options for managing _both_ pdf files and a BiBTeX database.  Here is what I am really trying to find and I was wondering if there is a way for any of the following programs to do it that I haven't found (through extensions or plug-ins).

Basically, I want to use one of these programs to manage my library of pdf articles and have it searchable by tags.

I see that JabRef does both of these, but there is a big issue that I have with its management system.  Many of my PDF files have the same author and so I use the following naming scheme:  LastName_Year_NameofJournal.pdf.  JabRef only allows you to "name" your PDF files as the BibTeX key, which I normally reduce to something like LastnameYR.  

This difference is important because I often reference these articles from my Dropbox account via the internet when I am not using the JabRef database.  So I would really like to be able to link PDF's to a database without renaming everything to the BiBTeX key.  Is there a way to do that in JabRef?  

Also, in looking over gpapers (though not installing it as there seems to be issues with that), it seems like a very interesting program, but is it still actively developed?  If not, do people still use it and find it helpful?  

Your thoughts are greatly appreciated!

---

### Post by agm. on 2010-02-08
btt

---

### Post by agm. on 2010-03-07
Well,  I've figured out how to do this through JabRef.  Just as an FYI and for anyone who possibly searches for this in the future.  JabRef does NOT need you to change the names of your files to have them hotlinked within the program.

The steps to link files are simple, but a bit hidden and there is not a good help file anywhere that I could find. 

Here are the steps to link a pdf to your database by file

Steps to link pdf to database entry:
1. Create the entry as normal
2. Go to "General" tab
3. Under this tab, there is a subsection called "File"
4. Under file there is a green "+" button; Click it
5. A new dialogue box will pop-up and ask you to name the file, Click "Browse"
6. Browse to the file you want to link and double-click on it.
7. You will return to the dialogue box, and now just need to click "Ok"
8. Your file is now linked!

The only problem I had with this method is that I have my files located on a DropBox location because I use 2 computers (one windows based at school, one linux based at home).  Because this method "links" the _exact_ file name, even though it is the same file, you have to create 2 links.  One for the Windows verson, the other for the linux mapping, even though it is the same file.

Also, if you change the pdf name, the link will be broken and you have to update it (remove the old link by using the red "-" sign in same area as step 4 above).  All in all, I'm very happy with this.

Hope this might help someone in the future if they ever search for similar problems!

---

### Post by hydmeganne on 2010-05-26
Shortcuts in JabRef

Is there a shortcut key in Jabref which closes the edit window? I mean, instead of actually pressing the cross in the upper left corner?

I translated the shortcut-list from the german manual
[http://jabref.sourceforge.net/help/manual_pdf/JabRef-UserManual_de.pdf](http://jabref.sourceforge.net/help/manual_pdf/JabRef-UserManual_de.pdf) but could not find anything which closes the editor.

 
Save file        Ctrl+S
Save as            Ctrl+Shift+S
Close file        Ctrl+W
Close JabRef        Ctrl+Q
Open file         Ctrl+O

New entry (reference)     Ctrl+N
New article         Ctrl+Shift+A
New book         Ctrl+Shift+B
New PhD thesis             Ctrl+Shift+T
New chapter in book     Ctrl+Shift+I
New Master thesis     Ctrl+Shift+M
New Proceedings     Ctrl+Shift+P
New Unpublished     Ctrl+Shift+U

Edit reference        Ctrl+E
Generate BibTeX keys    Ctrl+G
copy \cite{BibTeX key}  Ctrl+K
Edit preamble        Ctrl+P    
Edit strings        Ctrl+T

Paste from LyX            Ctrl+L
Paste from WinEdit    Ctrl+Shift+W
Open Url/DOI            F3
Open PDF        F4
Synchronise PDF-links   Shift+F4
Synchronise PS-links    Ctrl+F4
Go to Medline         F5
Go to CiteSeer        F6
Search            Ctrl+F
Search and replace    Ctrl+R

Undo / redo        Ctrl+Z / Ctrl+Y
Copy/Cut&copy/paste     Ctrl+C / Ctrl+X / Ctrl+V
Mark all         Ctrl+A
Mark entries        Ctrl+M
Delete marked entries    Ctrl+Shift+M  / Del
Display groups        Ctrl+Shift+G
Remove preview            Ctrl+F9
Change preview layout    F9

---

### Post by viktormas on 2012-09-28
Escape...

---

### Post by overdrank on 2012-09-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

