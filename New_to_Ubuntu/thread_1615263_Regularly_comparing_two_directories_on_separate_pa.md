---
title: "Regularly comparing two directories on separate partitions."
date: 2010-11-06
forum: New to Ubuntu
---

### Post by Bluenoser81 on 2010-11-06
[FONT=Arial]Ok, so I have 10.10 on one partition, and Win 7 on another.  What I'm trying to do is write some kind of script (or otherwise), that would compare two directories on different partitions(ie. ~/home/documents in 10.10 and c:/users/home/documents in my win 7 partition), look for new or updated files (some kind of compare command?) and then copy the newer file(s) to the other partition.  An example, to show how I would like this to work: every night this program would compare these two directories (and its sub-directories), and compare which files (mostly .doc files, btw) are newest, and copy and replace the newer files over the older versions on the other partition.  

I can do this by hand, which i have been doing by dragging and dropping and choosing "copy and replace" for newest files, but I am looking to make this automatic.  The reason for this is because I am constantly switching back and forth between Win 7 and Ubuntu for school, and want to be able to have the newest version of a .doc available, without having to double-check against the other partition. Any quick scripts or ideas of how to do this? 
[/FONT]

---

### Post by mikechant on 2010-11-07
Why don't you just have one copy - probably the Window version? Ubuntu can access and update the Windows NTFS files OK.

The Windows filesystem should appear in your 'places' menu in Ubuntu.

---

### Post by rampageoberon on 2010-11-07
You might find the application unison useful. [http://www.cis.upenn.edu/~bcpierce/unison/index.html](http://www.cis.upenn.edu/~bcpierce/unison/index.html)

---

### Post by Bluenoser81 on 2010-11-07
> **rampageoberon said:**
> You might find the application unison useful. [http://www.cis.upenn.edu/~bcpierce/unison/index.html]("http://www.cis.upenn.edu/%7Ebcpierce/unison/index.html")

This looks like exactly what I need, thanks!

---

### Post by Bluenoser81 on 2010-11-07
> **mikechant said:**
> Why don't you just have one copy - probably the Window version? Ubuntu can access and update the Windows NTFS files OK.

The Windows filesystem should appear in your 'places' menu in Ubuntu.

The reason I don't have one copy of my documents folder is because I have to work with .docx files in Win 7 which are lengthy, and .ppt's also, that get horribly mangled when I try to save them to another format so I could just use them in OpenOffice.  When I'm writing my own stuff I use OpenOffice and save as .doc, which still doesn't translate perfect into Word 2010, but close enough. I guess the easiest solution would be to switch completely to Word, but I like to support FLOSS as much as possible.

 As a work around I've decided to use Dropbox to synchronize the files on both systems, which is working fine--and as a bonus it is backing up the files to my cloud, which saves me grief in the event of a catastrophic hardware failure.

---

### Post by HermanAB on 2010-11-07
Rsync (or unison) is your friend.  Do read the man pages.  It will be time well spent.

---

