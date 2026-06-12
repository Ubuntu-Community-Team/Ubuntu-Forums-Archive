---
title: "Open given file type with given application"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by dannyboytward on 2011-06-03
Hello,

I currently have Ubuntu 11.04 with Unity desktop.

I have been working with triangulated surfaces, which are formatted text files with extension ".byu".  I want them to open with a custom OpenGL application when I double click them.  I can do this with no problem.

The problem is that now all text files ".txt" will open in this custom application by default.  Is there a way to open one type of text file with one application (gEdit), and a different type with a different application (my OpenGL application) based on their extension?

Looking at "open with" in "properties" shows that I can only change the program for my ".byu" files AND other files of type "plain text document".


Thanks for any help!

---

### Post by Anuovis on 2011-06-03
If all else fails... Ubuntu Tweak had detailed lists where you could assign file types to applications, might work.

But that app also attracts some criticism from the community and is a rather clumsy choice for such a simple problem.

---

### Post by dannyboytward on 2011-06-04
Thanks I will give that a try on my laptop.  My work computer has Kubuntu installed.   Do you know if there is something similar for Kubuntu?

---

### Post by Anuovis on 2011-06-05
I have a suspicion it might work on KDE as well but never really tried. 

If you use Kubuntu, however, there is a chance somebody wrote a separate tool for your environment. KDE is known for all sorts of gadgets, you might try asking in their forums. 

As I never used Kubuntu, I can't really help you further.

---

### Post by dannyboytward on 2011-06-05
I got this working.  I wanted to post the procedure in case anybody else is reading this.

I ended up getting this working using File Types Editor from the Ubuntu Software Center.

I created a new file type under the 3D models category.  I filled in these four entries and left everything else blank.

Name: model/byu

Description: byu surface

Related Types: Parent Types: text/plain

Filename pattern: *.byu

Then logged out and back in.  I can now change the program to open "byu surface" file types without affecting plain text file types.

Now, I also wanted to figure out exactly what "File Types Editor" was doing.  I undid all the changes in File Types Editor, and through finding all the changes File Types Editor made to files on my disk, and skimming this website [http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-database.html.en](http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-database.html.en) , I found the following 3 steps give the same results.

1. in ~/.local/share/mime/packages/Override.xml I write this text (this is all the text the file contains)

<?xml version="1.0"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info"><mime-type type="model/byu"><glob pattern="*.byu"/><sub-class-of type="text/plain"/><comment>byu surface</comment><comment xml:lang="en_US">byu surface</comment></mime-type></mime-info>

2. in ~/.local/share/mime/types I add the line "model/byu" in alphabetical order among the other entries

3. run "update-mime-database ~/.local/share/mime" in the terminal (without the quotes)

As far as I can tell, this gave exactly the same affect as using the File Types Editor.  In fact, after doing this, there is an entry in the File Types Editor browser that is exactly the same as the one I created in the first method.

I'm marking this as solved.  I'll update if a similar procedure works in kubuntu when I get a chance to try it out.

---

### Post by dannyboytward on 2011-06-07
Yes this last method I posted works in Kubuntu also.

---

