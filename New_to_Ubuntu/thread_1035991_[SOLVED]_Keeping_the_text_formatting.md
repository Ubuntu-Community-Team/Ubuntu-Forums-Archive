---
title: "[SOLVED] Keeping the text formatting"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by dpeters on 2009-01-10
When commands are executed (at the command line) they appear with a certain format on the screen: indentation, carriage returns, etc., making it easy to read.
But, when you create a file like this: ifconfig eth0 > ifconfig.txt then you copy that file to a thumb drive, taking it to another machine to post it in a forum like this or make an email attachment, all the formatting is gone and the text appears as one continuous stream of characters. It is difficult to read. I have been copying the command outputs verbatim and this is getting old in a hurry. Is there a way? or How is everyone else doing this?

---

### Post by cerealtx on 2009-01-10
u have to setup the encoding on the page that u save so that its recognizable by windows, a simple google search will probably help ya out

---

### Post by snova on 2009-01-10
It's not that the formatting is being lost, it's that Windows isn't smart enough to recognize it.

Ubuntu uses the \n character (ASCII 10) to denote line endings, whereas Windows expects \r\n (A 13 and then a 10). Since it never finds one, it regards your file as having one long line.

Either save your files in Ubuntu with Windows-style line endings, or use a better editor than Notepad in Windows. ;)

---

### Post by dpeters on 2009-01-10
I am using Ubuntu Server 8.04/10. No GUI
Is there a filter you could use with redirection or piping (on the command line)? Or is every one out there posting cmd outputs to forums or emails editing/formatting the text as a separate step? I have a variety of tools but I don't think any of them recognize linux formatting, even Microsoft Office 2003: Word).

---

### Post by dpeters on 2009-01-10
I just opened the files on Open Office: Writer on my wifes laptop. I received a popup window for ascii settings and went with all the defaults and it works. The command outputs appear just as they do on the server console. This works for me unless there is a shorter way.

---

### Post by lykwydchykyn on 2009-01-10
Last time I tried it, wordpad recognizes Unix newlines.  I could be wrong, though.

---

### Post by scorp123 on 2009-01-10
> **dpeters said:**
> I am using Ubuntu Server 8.04/10. No GUI
Is there a filter you could use ...  You could convert those files from UNIX into DOS format! It's very easy and definitely should work on Ubuntu Server too.

Read here:
[http://ubuntuforums.org/showpost.php?p=4570735&postcount=5](http://ubuntuforums.org/showpost.php?p=4570735&postcount=5)

So if you know that you will have to read a certain text file on a non-UNIX platform (such as Windows), you'd convert the file into DOS-format. And voila: no more messed up formatting. See the link I posted above.

---

