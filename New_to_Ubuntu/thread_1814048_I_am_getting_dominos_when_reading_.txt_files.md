---
title: "I am getting dominos when reading .txt files"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by n4pgw on 2011-07-28
[IMG]http://9t9z.com/images/temp/Screenshot.png[/IMG]                 [IMG]http://9t9z.com/images/temp/Screenshot-2.png[/IMG]   

When reading .txt files, created presumably in Windows, I often get these little dominos where apostrophies, question marks, quotes and other characters belong... or where no character belongs such as in this example.  

This text file is probably a bad example as all the dominos are at the beginning of sentences. In this case, the file was converted from a Word .doc file to a text file and probably has extranious characters.  But in many cases, it is just a plain text file being ported over from Windows or possibly Mac.

---

### Post by AlphaLexman on 2011-07-28
Those 'dominoes' are actually [ANSI escape codes]("http://en.wikipedia.org/wiki/ANSI_escape_code").

Although that may not be important to your situation, you may need to find a different (better) conversion method for your documents.

[OpenOffice.org]("http://www.openoffice.org/") and [LibreOffice.org]("http://www.libreoffice.org/") can both import MS Office files.

---

### Post by pierreyy on 2011-07-28
what kind of text editor are you using?

---

### Post by n4pgw on 2013-02-16
> **pierreyy said:**
> what kind of text editor are you using?

GEdit or OpenOffice, and now LibreOffice.  A similar problem occurs when I post something created by on Ubuntu and it is read on Windows machines, only they get other strange characters.

I have come to the conclusion that it may have something to do with a setting in Ubuntu about what version or flavor of ANSI, ISO, or whatever standard.  

Just like what I am experiencing here.  You can't see it, but the word "flavor" is underlined as misspelled because the !@#$%^&* languages settings on my system keep reverting back to English (United Kingdom) or English (Australia) regardless of the fact that I have changed it everywhere I can find to change it, whether in the system or the installed packages such as OpenOffice.

---

